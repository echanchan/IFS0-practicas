# Guía de Trabajo - Practica 4

# Implementación y Gestión de Arreglos RAID y Consolas de Administración

---

## 1. Competencia a desarrollar

Implementa y administra arreglos RAID por software en Linux, integrando mecanismos de persistencia, monitoreo, simulaci¢n de fallos y recuperaci¢n, complementando la gesti¢n mediante herramientas gr ficas de administraci¢n segura en entorno servidor.

---

## 2. Contexto de la práctica (escenario)

Una organización tecnológica requiere fortalecer su infraestructura de almacenamiento local para:

* Garantizar continuidad operativa ante fallos de disco
* Evaluar rendimiento en escenarios críticos
* Implementar monitoreo centralizado del servidor
* Gestionar almacenamiento tanto por CLI como por interfaz web

El estudiante asume el rol de Administrador de Infraestructura, responsable de:

* Implementar distintos niveles RAID (0,1,5,6,10)
* Evaluar tolerancia a fallos
* Configurar persistencia del sistema
* Integrar paneles de administración (Cockpit y Webmin)
* Aplicar controles básicos de seguridad en acceso remoto

---

## 3. Desempeños esperados

El estudiante demuestra que es capaz de:

* Configurar arreglos RAID utilizando `mdadm`
* Diferenciar niveles RAID según rendimiento y redundancia
* Implementar montaje persistente mediante `/etc/fstab`
* Simular fallos controlados y ejecutar procesos de recuperación
* Interpretar estado del sistema mediante `/proc/mdstat`
* Gestionar almacenamiento desde Cockpit y Webmin
* Aplicar reglas b sicas de firewall para proteger servicios administrativos

---

# BLOQUE I - RAID 0, 1 y 10

---

## 4. Actividades guiadas

### Actividad 1 - Preparación del entorno

1. Verificar instalación de `mdadm`
2. Identificar discos disponibles con `lsblk`
3. Confirmar que no existan metadatos RAID previos

---

### Actividad 2 - Creación de RAID 0, 1 y 10

Implementar:

* RAID 0 (2 discos - alto rendimiento)
* RAID 1 (2 discos - espejo)
* RAID 10 (4 discos - balance rendimiento/redundancia)

Cada creación debe:

* Formatearse con `mkfs.ext4`
* Configurarse persistencia con:

  * `mdadm --detail --scan`
  * `/etc/mdadm/mdadm.conf`
  * `update-initramfs -u`
* Registrarse en `/etc/fstab`

Ejemplo de línea en fstab:

```
/dev/md0 /mnt/raid0 ext4 defaults 0 0
```

El estudiante debe explicar:

* Que representa cada campo
* Que implica el par metro `defaults`
* Por que se usan los dos £últimos valores en 0

---

### Actividad 3 - Pruebas de rendimiento

Utilizar:

```
dd if=/dev/zero of=/mnt/raidX/test.img bs=1G count=2 conv=fdatasync
```

Analizar:

* Velocidad en MB/s
* Diferencia entre RAID 0 y RAID 1
* Balance en RAID 10

---

### Actividad 4 - Simulación de fallos

1. Marcar disco como `faulty`
2. Verificar estado con `mdadm --detail`
3. Remover disco
4. Agregar disco nuevo
5. Monitorear reconstrucción con:

```
watch cat /proc/mdstat
```

Analizar:

* Estado `degraded`
* Proceso de `resync`
* Tiempo de reconstrucción

---

# BLOQUE II - RAID 5 y RAID 6

---

### Actividad 5 - Implementación de RAID 5 y 6

Crear:

* RAID 5 (5 discos)
* RAID 6 (5 discos)

Formatear, montar y configurar persistencia.

---

### Actividad 6 - Análisis de eficiencia

Ejecutar:

```
df -h
```

Comparar:

* Capacidad útil RAID 5 (N-1)
* Capacidad útil RAID 6 (N-2)

Explicar impacto de paridad simple vs doble paridad.

---

### Actividad 7 - Simulación de desastres

Escenario RAID 5:

* Fallo de un disco
* Verificación de persistencia de datos
* Reconstrucción

Escenario RAID 6:

* Fallo simultaneo de dos discos
* Verificación de acceso a datos
* Reconstrucción doble

Explicar diferencia estructural entre ambos niveles.

---

# BLOQUE III - Administración Gr fica

---

### Actividad 8 - Instalación de Cockpit

1. Instalar paquete
2. Habilitar servicio
3. Verificar puerto 9090
4. Instalar módulo de almacenamiento

Analizar:

* Que información muestra
* Cómo visualiza RAID
* Ventajas frente a CLI

---

### Actividad 9 - Instalación de Webmin

1. Agregar repositorio
2. Instalar paquete
3. Verificar puerto 10000
4. Acceder al módulo Linux RAID

Comparar:

* Nivel de detalle
* Superficie de exposición
* Configuraciones avanzadas

---

### Actividad 10 - Configuración de Firewall

Abrir puertos:

```
ufw allow 9090/tcp
ufw allow 10000/tcp
```

Explicar:

* Riesgo de exponer paneles administrativos
* Diferencia entre acceso local y acceso remoto
* Buenas prácticas (VPN, restricción por IP)

---

## 5. Evidencia a entregar

Archivo único obligatorio:

```
IFS0-practicas/
    practica_4/
        raid_5_6.md
```

Contenido mínimo:

1. Introducción del laboratorio
2. Tabla comparativa de niveles RAID
3. Evidencia de creación de RAID
4. Evidencia de fallos y reconstrucción
5. Capturas o descripción de Cockpit y Webmin
6. Análisis comparativo CLI vs GUI
7. Reflexión técnica final

---

## 6. Entrega en GitHub

```
IFS0-practicas/
    practica_4/
        raid_5_6.md
```

---

## 7. Criterios de evaluación

* Correcta implementación de niveles RAID
* Coherencia técnica en explicación de paridad
* Correcta configuración de persistencia
* Simulación adecuada de fallos
* Evidencia de reconstrucción
* Configuración funcional de Cockpit y Webmin
* Aplicación b sica de control de acceso por firewall
* Análisis crítico comparativo

---

## Errores que evitar en la práctica

* No monitorear proceso de reconstrucción
* No configurar persistencia
* No limpiar metadatos antes de reutilizar discos
* Exponer paneles sin firewall
* Limitarse a ejecutar comandos sin explicar su propósito

