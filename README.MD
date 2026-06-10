# Trabajo Práctico Integrador - Administración de Sistemas Linux

## Universidad de Palermo

### Integrantes

* Evangelina Mendez

---

## Descripción

El presente trabajo práctico fue realizado sobre una máquina virtual Debian GNU/Linux, cumpliendo con los requerimientos solicitados para la configuración, administración, almacenamiento, respaldo y documentación de servicios en un entorno Linux.

---

# Tareas Realizadas

## 1. Configuración Inicial

* Importación de la máquina virtual entregada.

* Restablecimiento de la contraseña de root.

* Configuración de la contraseña:

  ```bash
  palermo
  ```

* Configuración del hostname:

  ```bash
  TPServer
  ```

---

## 2. Servicios

### Actualización del Sistema Operativo

* Actualización completa de Debian 11 a Debian 12 (Bookworm).

### SSH

* Instalación y configuración de OpenSSH Server.
* Habilitación del acceso remoto mediante autenticación por clave pública/privada para el usuario root.

### Apache y PHP

* Instalación de Apache HTTP Server.
* Instalación y configuración de PHP.
* Publicación de los archivos:

    * index.php
    * logo.png

### MariaDB

* Instalación y configuración de MariaDB.
* Importación de la base de datos utilizando el archivo:

  ```text
  db.sql
  ```

---

## 3. Configuración de Red

* Configuración de dirección IP estática.

* Definición de:

    * Address
    * Netmask
    * Gateway

* Verificación de conectividad desde otras máquinas de la red.

---

## 4. Almacenamiento

### Nuevo Disco

* Agregado de un disco virtual adicional de 10 GB.

### Particionado

Se crearon dos particiones Linux (tipo 83):

| Partición | Tamaño | Punto de montaje |
| --------- | ------ | ---------------- |
| /dev/sdc1 | 3 GB   | /www_dir         |
| /dev/sdc2 | 6 GB   | /backup_dir      |

### Montaje Automático

Configuración de montaje automático mediante:

```text
/etc/fstab
```

### Apache

* Migración del contenido web al directorio:

  ```text
  /www_dir
  ```

* Actualización del DocumentRoot de Apache.

### Archivo particion

Generación del archivo:

```text
/opt/particion
```

a partir del contenido de:

```text
/proc/partitions
```

---

## 5. Backup

### Script

Se desarrolló el script:

```text
/opt/scripts/backup_full.sh
```

### Funcionalidades

* Soporte para parámetros origen y destino.

* Opción de ayuda:

  ```bash
  -help
  ```

* Validación de directorios.

* Validación del sistema de archivos destino.

* Generación de backups comprimidos en formato:

  ```text
  .tar.gz
  ```

### Formato de Nombres

Ejemplo:

```text
www_dir_bkp_20260610.tar.gz
```

### Destino de Backups

```text
/backup_dir
```

### Automatización

Cron configurado para:

#### Todos los días a las 00:00

```text
/var/log
```

#### Lunes, Miércoles y Viernes a las 23:00

```text
/www_dir
```

---

## 6. Entregables

Se generaron y almacenaron los siguientes archivos comprimidos:

```text
root.tar.gz
etc.tar.gz
opt.tar.gz
www_dir.tar.gz
backup_dir.tar.gz
```

Además, el directorio:

```text
/var
```

fue comprimido y dividido en múltiples partes para su almacenamiento y distribución.

---

## Tecnologías Utilizadas

* Debian 12 Bookworm
* OpenSSH
* Apache2
* PHP
* MariaDB
* Bash
* Cron
* VirtualBox
* GitHub

---

## Estado Final

Todos los requerimientos solicitados en el trabajo práctico fueron implementados y verificados correctamente.
