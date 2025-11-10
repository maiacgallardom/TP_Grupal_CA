# TP Integrador – Computación Aplicada

### Integrantes: 
- Ignacio Pierri
- Maia Gallardo
- Franco Castillo
- Nicolas Esteban Abraham
- Yanel Ricarte

### Diagrama Topologico:
https://app.mural.co/t/tpgrupal9226/m/tpgrupal9226/1762649874160/af9e936122e732da74358d3de648cfc872d884e8?sender=ucd6712cf85ee0613a6bc9071

### Descripción:
Configuración completa de entorno GNU/Linux con servicios de red, almacenamiento, automatización de backups y servidor web Apache.

### Infraestructura:
- Sistema operativo: Debian (VM en VirtualBox)
- Hostname: TPServer
- Servicios instalados:
    - SSH (root con clave pública/privada)
    - Apache2 + PHP (sirviendo index.php y logo.png desde /www_dir)
    - MariaDB (base de datos ingenieria, con tablas alumnos, modulos, notas)

### Red:
- Configuración con IP estática en la VM.
- Conectividad validada vía SSH y HTTP desde el host.

### Almacenamiento:
- Disco adicional de 10 GB → dividido en:
    - /dev/sdb1 (3 GB) montado en /www_dir
    - /dev/sdb2 (6 GB) montado en /backup_dir
- Archivo /opt/particion con contenido de /proc/partitions.

### Backups:
- Script: /opt/scripts/backup_full.sh
- Funcionalidades:
    - Acepta parámetros <origen> <destino> y opción -help
    - Valida montajes antes de ejecutar
    - Genera archivos .tar.gz con fecha (YYYYMMDD)
- Ejemplos de uso:
    - /opt/scripts/backup_full.sh /www_dir /backup_dir --tag www
    - /opt/scripts/backup_full.sh /var/log /backup_dir --tag logs
- Automatización con cron:
    - Todos los días a las 00:00 → backup de /var/log
    - Lunes, Miércoles y Viernes a las 23:00 → backup de /www_dir

### Estructura:
- `/root.tar.gz`
- `/etc.tar.gz`
- `/opt.tar.gz`
- `/www_dir.tar.gz`
- `/backup_dir.tar.gz`
- `/var_partX.tar.gz` (dividido por tamaño)

### Fecha:
Noviembre 2025
