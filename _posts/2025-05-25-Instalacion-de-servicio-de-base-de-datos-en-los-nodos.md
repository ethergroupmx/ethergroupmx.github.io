---
title: Instalación de servicio de base de datos en los nodos
date: 2025-05-25 09:00:00 
categories: [SERVIDORES]
tags: [linux, servidores]
description: Crearemos un clúster de alta disponibilidad con Galera y MariaDB, con replicación automática y balanceo de carga mediante un proxy.
image: /assets/132/preview1.png
---


## Instalación de servicio de base de datos en los nodos

En este artí­culo abordaremos la creación de un clúster de alta disponibilidad con GALERA. Esta herramienta permite agregar nodos de MariaDB a un clúster el cual replicará automáticamente lo que suceda en un nodo. Esto sirve para aplicaciones con requerimiento de alta disponibilidad y puede agregarse un Proxy que gestione los servicios para se utilice el nodo que tenga menos carga.

Para hacer este laboratorio necesitaremos:

- Nodo 01 : Será nuestro maestro del clúster.
- Nodo 02 : Formará parte del clúster.

Puedes agregar tantos nodos creas necesarios. La PoC se realizá sobre sistemas Debian 12 en instalación limpia.

### Nodo 01
```bash
hostnamectl set-hostname nodo01
apt update && apt install mariadb-server -y
mysql_secure_installation
```

### Nodo 02
```bash
hostnamectl set-hostname nodo02
apt update && apt install mariadb-server -y
mysql_secure_installation
```

Ahora en ambos servidores se debe detener el servicio
```bash
systemctl stop mariadb
```

Luego editamos el archivo /etc/mysql/mariadb.conf.d/60-galera.cnf y agregamos lo siguiente:

¡Recuerda hacer una copia de seguridad del archivo!

Nodo 01:

```bash
[galera]
wsrep_on                 = 1
wsrep_cluster_name       = "Ethercloud MariaDB Cluster"
wsrep_provider           = /usr/lib/galera/libgalera_smm.so
wsrep_cluster_address    = gcomm://172.16.250.141,172.16.250.98
binlog_format            = row
default_storage_engine   = InnoDB
innodb_autoinc_lock_mode = 2

# Allow server to accept connections on all interfaces.
bind-address = 0.0.0.0
wsrep_node_address=172.16.250.141

```

Nodo 02:


```bash
[galera]
wsrep_on                 = 1
wsrep_cluster_name       = "Ethercloud MariaDB Cluster"
wsrep_provider           = /usr/lib/galera/libgalera_smm.so
wsrep_cluster_address    = gcomm://172.16.250.141,172.16.250.98
binlog_format            = row
default_storage_engine   = InnoDB
innodb_autoinc_lock_mode = 2

# Allow server to accept connections on all interfaces.
bind-address = 0.0.0.0

# Para este nodo (nodo02) tendremos que cambiar la ip del
# wsrep_node_address , ya que esta debe corresponder al nodo que estamos dando # # de alta.
wsrep_node_address=172.16.250.98

```


Ahora bien, con el servicio de mariadb detenido en el nodo  principal tendremos que generar el clúster:

```bash
galera_new_cluster
```

Luego reiniciamos el servicio en ambos nodos, comenzando por el nodo 01:

```bash
systemctl start mariadb
```

### Pruebas de funcionamiento

Para probar que la replica funciona, vamos a ingresar a cualquiera de los nodos y desde mysql ejecutamos lo siguiente:

```sql
SHOW STATUS LIKE 'wsrep_cluster_size';
```

Esto nos dará una salida similar a esta.

```terminal
MariaDB [(none)]> SHOW STATUS LIKE 'wsrep_cluster_size';
+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 2     |
+--------------------+-------+
1 row in set (0.001 sec)
```

Ahora que aparecen los dos nodos, crearemos una base de datos.

```
mysql -u root -p
create database BASEDEDATOSPRUEBA;
show databases;
```

```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| BASEDEDATOSPRUEBA  |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

Para validar la réplica, bastará con ir al otro nodo y ver que también existe la BD:

```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| BASEDEDATOSPRUEBA  |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

Y listo, ya tienes una configuración básica de un clúster de alta disponibilidad con MariaDB.

Documentación oficial:

https://mariadb.com/kb/en/getting-started-with-mariadb-galera-cluster/
