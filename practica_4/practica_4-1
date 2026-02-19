# 🧪 Guía de Laboratorio - Parte 1

# Administración de RAID con `mdadm` 


# 🎯 Objetivo del laboratorio

Configurar, validar, simular fallos y recuperar arreglos RAID 0, RAID 1 y RAID 10 utilizando `mdadm`, comprendiendo **qué hace cada comando ejecutado** y su impacto en:

-   Persistencia del arreglo
-   Integridad de datos    
-   Proceso de reconstrucción (Resync)    
-   Limpieza de metadatos   

----------

# 🔹 FASE 1 – Preparación del Sistema

----------

## 1️⃣ Verificación / Instalación de `mdadm`

```bash
if ! command -v mdadm &> /dev/null; then
    sudo apt update && sudo apt install mdadm -y
else
    echo "mdadm ya está instalado."
fi

```

### 📘 Explicación detallada

|Comando|¿Qué hace?|
|------------------------------------|-------------| 
|`command -v mdadm`|Verifica si el binario `mdadm` existe en el PATH|
|`&> /dev/null`|Redirige salida estándar y error a null (no muestra nada)|
|`sudo apt update`|Actualiza el índice de paquetes|
|`sudo apt install mdadm -y`|Instala automáticamente `mdadm`|
|`-y`|Responde “sí” automáticamente|

----------

## 2️⃣ Identificar discos disponibles

```bash
lsblk
```

### 📘 ¿Qué hace?

`lsblk` = **List Block Devices**

Muestra:

-   Discos físicos    
-   Particiones    
-   Dispositivos RAID    
-   Puntos de montaje    

----------

# 🔹 FASE 2 – Creación de RAID

## 🔸 Crear RAID 0

```bash
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/nvme0n1 /dev/nvme0n2
```

### 📘 Desglose del comando

|Parámetro|Significado|
|------------------------------------|-------------| 
|`mdadm`|Administrador de RAID por software|
|`--create`|Crea un nuevo arreglo RAID|
|`/dev/md0`|Nombre del dispositivo RAID resultante|
|`--level=0`|Tipo de RAID (0 = striping)|
|`--raid-devices=2`|Número de discos que forman el arreglo|
|`/dev/nvme0n1`|Disco físico 1|
|`/dev/nvme0n2`|Disco físico 2|

----------

## 🔸 Crear RAID 1

```bash
sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/nvme0n3 /dev/nvme0n4

```

`--level=1` Tipo de RAID **mirroring**.

----------

## 🔸 Crear RAID 10

```bash
sudo mdadm --create /dev/md10 --level=10 --raid-devices=4 \
/dev/nvme0n5 /dev/nvme0n6 /dev/nvme0n7 /dev/nvme0n8

```

`--level=10` combina RAID 1 + RAID 0.

----------

# 🔹 FORMATEO Y MONTAJE

## 🔸 Formateo

```bash
sudo mkfs.ext4 /dev/md0
```

### 📘 Explicación

|Parámetro|Significado|
|------------------------------------|-------------| 
|`mkfs`|Make File System|
|`.ext4`|Tipo de sistema de archivos|
|`/dev/md0`|Dispositivo RAID a formatear|

Esto crea estructuras de sistema de archivos sobre el RAID.

----------

## 🔸 Crear puntos de montaje

```bash
sudo mkdir -p /mnt/raid0
```

|Parámetro|Significado|
|------------------------------------|-------------| 
|`mkdir`|Crear directorio|
|`-p`|Crea estructura completa si no existe|

----------

# 🔹 PERSISTENCIA DEL RAID

## 🔸 Guardar configuración del RAID

```bash
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
```

### 📘 ¿Qué hace realmente?


|Parámetro|Significado|
|------------------------------------|-------------|
|`mdadm --detail --scan`|Escanea todos los RAID activos y muestra su configuración|
|`tee -a`|Escribe salida en archivo sin borrar contenido anterior|
|`/etc/mdadm/mdadm.conf`|Archivo de configuración permanente de RAID|
|`-a`|Append (agregar al final)|

👉 Esto guarda la definición del RAID para que el sistema lo reconstruya al iniciar.

----------

## 🔸 Actualizar initramfs

```bash
sudo update-initramfs -u
```

### 📘 Explicación


|Parámetro|Significado|
|------------------------------------|-------------|
|`initramfs`|Sistema mínimo que carga el kernel al iniciar|
|`-u`|Update (actualiza imagen existente)|

👉 Incluye configuración RAID dentro del entorno de arranque.

----------

# 🔹 CONFIGURACIÓN DE /etc/fstab

Ejemplo:

```bash
/dev/md0 /mnt/raid0 ext4 defaults 0 0
```

### 📘 Desglose completo


|Parámetro|Significado|
|------------------------------------|-------------|
|`/dev/md0`|Dispositivo a montar|
|`/mnt/raid0`|Punto de montaje|
|`ext4`|Sistema de archivos|
|`defaults`|Opciones estándar de montaje|
|`0` (5° campo)|Dump backup (0 = no usar dump)|
|`0` (6° campo)|Orden de fsck (0 = no verificar al inicio)|

### 🔎 ¿Qué incluye "defaults"?

Equivale a:

```bash
rw,suid,dev,exec,auto,nouser,async
```

----------

## 🔸 Montar todo

```bash
sudo mount -a
```

Significa:  
Monta **todos los dispositivos definidos en ```fstab```**.

----------

# 🔹 PRUEBAS DE RENDIMIENTO

## 🔸 Prueba con `dd`

```bash
sudo dd if=/dev/zero of=/mnt/raid0/test_speed.img bs=1G count=2 conv=fdatasync
```

### 📘 Explicación detallada


|Parámetro|Significado|
|------------------------------------|-------------|
|`dd`|Herramienta de copia a bajo nivel|
|`if=`|Input file (archivo fuente)|
|`/dev/zero`|Genera datos vacíos infinitos|
|`of=`|Output file|
|`bs=1G`|Block size = 1 Gigabyte|
|`count=2`|Número de bloques|
|`conv=fdatasync`|Fuerza escritura real a disco antes de terminar|

👉 Crea archivo de 2GB y mide velocidad.

----------

# 🔹 SIMULACIÓN DE FALLA

## 🔸 Marcar disco como fallido

```bash
sudo mdadm /dev/md1 --fail /dev/nvme0n3
```


|Parámetro|Significado|
|------------------------------------|-------------|
|`/dev/md1`|RAID afectado|
|`--fail`|Marca disco como defectuoso|

----------

## 🔸 Ver estado detallado

```bash
sudo mdadm --detail /dev/md1
```

Muestra:

-   Estado   
-   Discos activos    
-   Discos faulty    
-   Nivel RAID    
-   UUID    

----------

## 🔸 Remover disco

```bash
sudo mdadm /dev/md1 --remove /dev/nvme0n3
```

Elimina el disco del arreglo.

----------

## 🔸 Agregar disco nuevo

```bash
sudo mdadm /dev/md1 --add /dev/nvme0n9
```

Inicia proceso de reconstrucción automática.

----------

# 🔹 MONITOREO DE RECONSTRUCCIÓN

```bash
watch -n 1 cat /proc/mdstat
```

### 📘 Explicación


|Parámetro|Significado|
|------------------------------------|-------------|
|`watch`|Ejecuta comando repetidamente|
|`-n 1`|Cada 1 segundo|
|`/proc/mdstat`|Archivo virtual con estado RAID|

----------

# 🔹 LIMPIEZA TOTAL

## 🔸 Desmontar

```bash
sudo umount /mnt/raid0
```

Desconecta sistema de archivos del sistema operativo.

----------

## 🔸 Detener RAID

```bash
sudo mdadm --stop /dev/md0
```

Detiene arreglo RAID en memoria.

----------

## 🔸 Limpiar metadatos

```bash
sudo mdadm --zero-superblock /dev/nvme0n1
```

### 📘 ¿Qué es el superblock?

Es el bloque donde RAID guarda:

-   UUID    
-   Nivel    
-   Configuración    
-   Estado    

`--zero-superblock` borra esa firma.

----------

## 🔸 Limpiar configuración

```bash
sudo truncate -s 0 /etc/mdadm/mdadm.conf
```
|Parámetro|Significado|
|------------------------------------|-------------|
|`truncate`|Reduce tamaño de archivo|
|`-s 0`|Lo deja en 0 bytes|

----------

# 🔹 Comandos adicionales usados

## `grep`

```bash
grep -E "faulty|spare"

```

Busca líneas que contengan palabras específicas.

----------

## `df -h`

Muestra uso de disco en formato legible.

----------

## `cat`

Muestra contenido de archivo.

----------
