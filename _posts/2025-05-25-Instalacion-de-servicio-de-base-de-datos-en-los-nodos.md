---
title: Instalación de servicio de base de datos en los nodos
date: 2025-05-25 09:00:00 
categories: [SERVIDORES]
tags: [linux, servidores]
description: El propósito inicial era automatizar un poco la creación de máquinas virtuales en un perqueño server de pruebas local.
image: /assets/132/preview1.png
---

## InstalaciÃ³n de servicio de base de datos en los nodos

En este artÃ­culo abordaremos la creaciÃ³n de un clÃºster de alta disponibilidad con GALERA. Esta herramienta permite agregar nodos de MariaDB a un clÃºster el cual replicarÃ¡ automÃ¡ticamente lo que suceda en un nodo. Esto sirve para aplicaciones con requerimiento de alta disponibilidad y puede agregarse un Proxy que gestione los servicios para se utilice el nodo que tenga menos carga.

Para hacer este laboratorio necesitaremos:

- Nodo 01 : SerÃ¡ nuestro maestro del clÃºster.
- Nodo 02 : FormarÃ¡ parte del clÃºster

Puedes agregar tantos nodos creas necesarios. La PoC se realizÃ³ sobre sistemas Debian 12 en instalaciÃ³n limpia.

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

Â¡Recuerda hacer una copia de seguridad del archivo!

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

Luego reiniciamos el servicio en ambos nodos:

```bash
systemctl start mariadb
```

### Pruebas de funcionamiento

Para probar que la replica funciona, vamos a ingresar a cualquiera de los nodos y desde mysql ejecutamos lo siguiente:

```sql
SHOW STATUS LIKE 'wsrep_cluster_size';
```

Esto nos darÃ¡ una salida similar a esta.

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

Para validar la rÃ©plica, bastarÃ¡ con ir al otro nodo y ver que tambiÃ©n existe la BD:

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

Y listo, ya tienes una configuraciÃ³n bÃ¡sica de un clÃºster de alta disponibilidad con MariaDB.
