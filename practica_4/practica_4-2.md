# 🧪 Guía de Laboratorio - Parte 2

# Implementación y Gestión de RAID 5 y RAID 6 con `mdadm`

# 🎯 Objetivo de esta segunda práctica

Implementar arreglos **RAID 5 y RAID 6** para:

-   Analizar eficiencia de espacio    
-   Evaluar tolerancia a fallos múltiples    
-   Observar comportamiento de reconstrucción (Rebuild)    
-   Comparar pérdida de capacidad por paridad    

----------

# 🔹 FASE 1 – Creación de Arreglos de Alta Capacidad

Utilizaremos 5 discos por cada RAID para evidenciar:
-   Diferencia de capacidad útil    
-   Diferencia en tolerancia a fallos    

----------

## 🔸 Crear RAID 5

```bash
sudo mdadm --create /dev/md5 --level=5 --raid-devices=5 \
/dev/nvme0n1 /dev/nvme0n2 /dev/nvme0n3 /dev/nvme0n4 /dev/nvme0n5
```

### 📘 Explicación del comando


|Parámetro|Significado|
|------------------------------------|-------------| 
|`--create`|Crea un nuevo arreglo RAID|
|`/dev/md5`|Nombre lógico del arreglo|
|`--level=5`|Nivel RAID 5 (paridad distribuida simple)|
|`--raid-devices=5`|Número total de discos|
|`/dev/nvme0nX`|Discos físicos incluidos|

### 📌 Concepto técnico

RAID 5:
-   Distribuye datos + paridad entre todos los discos    
-   Tolera **1 disco fallido**    
-   Capacidad útil = (N-1) discos    

----------

## 🔸 Crear RAID 6

```bash
sudo mdadm --create /dev/md6 --level=6 --raid-devices=5 \
/dev/nvme0n6 /dev/nvme0n7 /dev/nvme0n8 /dev/nvme0n9 /dev/nvme0n10
```

### 📘 Explicación


|Parámetro|Significado|
|------------------------------------|-------------| 
|`--level=6`|RAID 6 (doble paridad distribuida)|

### 📌 Concepto técnico

RAID 6:
-   Utiliza **doble paridad**    
-   Tolera **2 discos fallidos simultáneamente**    
-   Capacidad útil = (N-2) discos    

----------

# 🔹 FASE 2 – Formateo y Montaje Persistente

----------

## 🔸 Formatear arreglos

```bash
sudo mkfs.ext4 /dev/md5
sudo mkfs.ext4 /dev/md6
```

### 📘 `mkfs.ext4`

-   Crea sistema de archivos ext4    
-   Inicializa estructura lógica para almacenamiento    

----------

## 🔸 Crear puntos de montaje

```bash
sudo mkdir -p /mnt/raid5 /mnt/raid6
```
`-p` evita error si directorios ya existen.

----------

## 🔸 Guardar configuración RAID

```bash
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
```

### 📘 Desglose

-   `--detail --scan`: Detecta todos los RAID activos    
-   `tee -a`: Agrega información al archivo sin borrar contenido    
-   `/etc/mdadm/mdadm.conf`: Archivo persistente de configuración RAID    

----------

## 🔸 Actualizar initramfs

```bash
sudo update-initramfs -u
```

Actualiza imagen de arranque para incluir configuración RAID.

----------

## 🔸 Agregar a `/etc/fstab`

```bash
echo "/dev/md5 /mnt/raid5 ext4 defaults 0 0" | sudo tee -a /etc/fstab
echo "/dev/md6 /mnt/raid6 ext4 defaults 0 0" | sudo tee -a /etc/fstab
```

### 📘 Explicación de cada campo

```bash
/dev/md5   /mnt/raid5   ext4   defaults   0   0
```
|Parámetro|Significado|
|------------------------------------|-------------| 
|`/dev/md5`|Dispositivo|
|`/mnt/raid5`|Punto de montaje|
|`ext4`|Tipo de sistema de archivos|
|`defaults`|Opciones estándar (rw, auto, exec, etc.)|
|`0`|No usar dump backup|
|`0`|No verificar con fsck al arranque|

----------

## 🔸 Montar

```bash
sudo mount -a
```
Monta todos los sistemas definidos en fstab.

----------

# 🔹 FASE 3 – Análisis de Espacio Útil

```bash
df -h
```

### 📘 ¿Qué muestra?

-   Tamaño total    
-   Espacio usado    
-   Espacio disponible    

### 📊 Resultado esperado

Si cada disco es 5GB:
|RAID|Discos|Capacidad útil|
|-------------|-------------|-------------| 
|RAID 5|5|~20GB (pierde 1 disco)|
|RAID 6|5|~15GB (pierde 2 discos)|

----------

# 🔹 FASE 4 – Simulación de Fallos


## 🟥 Escenario A – RAID 5


## 🔸 Crear archivo de prueba

```bash
echo "Datos críticos RAID 5" | sudo tee /mnt/raid5/seguridad.txt
```

`tee` escribe el texto con privilegios sudo.

----------

## 🔸 Simular fallo

```bash
sudo mdadm /dev/md5 --fail /dev/nvme0n1
```

Marca disco como defectuoso.

----------

## 🔸 Verificar acceso

```bash
cat /mnt/raid5/seguridad.txt
```

El archivo debe seguir accesible.

----------

## 🔸 Reparación

```bash
sudo mdadm /dev/md5 --remove /dev/nvme0n1
sudo mdadm /dev/md5 --add /dev/nvme0n1
```

### 📘 Explicación

-   `--remove`: Quita disco fallido del arreglo    
-   `--add`: Agrega disco nuevo/inicializado    
-   Inicia proceso de reconstrucción automática   

----------

## 🔸 Monitorear reconstrucción

```bash
watch cat /proc/mdstat
```

Muestra progreso en tiempo real.

----------

## 🟥 Escenario B – RAID 6


## 🔸 Crear archivo

```bash
echo "Datos ultra seguros RAID 6" | sudo tee /mnt/raid6/seguridad.txt
```

----------

## 🔸 Simular doble fallo

```bash
sudo mdadm /dev/md6 --fail /dev/nvme0n6 --fail /dev/nvme0n7
```

### 📘 ¿Qué ocurre?

RAID 6 soporta hasta 2 discos fallidos simultáneamente.

----------

## 🔸 Detectar discos defectuosos

```bash
sudo mdadm --detail /dev/md6 | grep faulty
```

`grep faulty` filtra solo líneas relevantes.

----------

## 🔸 Verificar datos

```bash
cat /mnt/raid6/seguridad.txt
```

El archivo sigue disponible.

----------

## 🔸 Reparación masiva

```bash
sudo mdadm /dev/md6 --remove /dev/nvme0n6 /dev/nvme0n7
sudo mdadm /dev/md6 --add /dev/nvme0n6 /dev/nvme0n7
```

Se inicia doble reconstrucción.

----------

# 🔹 FASE 5 – Limpieza Total

## 🔸 Desmontar

```bash
sudo umount /mnt/raid5 /mnt/raid6
```

Desvincula sistemas de archivos.

----------

## 🔸 Limpiar entradas en fstab

```bash
sudo sed -i '/raid5/d' /etc/fstab
sudo sed -i '/raid6/d' /etc/fstab
```

### 📘 Explicación


|Parámetro|Significado|
|------------------------------------|-------------| 
|`sed`|Editor de texto en línea|
|`-i`|Edita archivo directamente|
|`/raid5/d`|Elimina líneas que contengan "raid5"|

----------

## 🔸 Detener arreglos

```bash
sudo mdadm --stop /dev/md5 /dev/md6
```

Detiene dispositivos RAID en memoria.

----------

## 🔸 Limpiar metadatos RAID

```bash
sudo mdadm --zero-superblock /dev/nvme0n[1-10]
```

Elimina firmas RAID de todos los discos.

----------

## 🔸 Limpiar configuración

```bash
sudo truncate -s 0 /etc/mdadm/mdadm.conf
sudo update-initramfs -u
```

Reinicia configuración persistente del sistema.

----------

# 📊 Comparación Técnica Final

|RAID|Discos|Paridad|Capacidad útil|Tolerancia|
|-------------|-------------|-------------|-------------|-------------| 
|RAID 5|5|1|N-1|1 fallo|
|RAID 6|5|2|N-2|2 fallos|

