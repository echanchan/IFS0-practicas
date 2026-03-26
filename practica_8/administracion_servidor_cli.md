
# IFS0 – Práctica 8  
## Administración de Servidores Linux mediante CLI


## 1. Datos generales

- **Carrera:**  
- **Asignatura:** IFS0 – Analizando Necesidades de Infraestructura de Servidores  
- **Docente:**  
- **Unidad:** 3  
- **Práctica:** 8 – Administración de Servidores Linux  
- **Fecha de entrega:**  
- **Nombre del estudiante / integrantes:** 
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
---

## 2. Introducción

En este documento se presenta el análisis del estado de un servidor Linux utilizando herramientas de línea de comandos (CLI).

El objetivo es evaluar el comportamiento del sistema en términos de:

- uso de CPU
- uso de memoria
- almacenamiento
- red
- servicios
- usuarios

y demostrar la capacidad de interpretar métricas para la toma de decisiones técnicas.

---

## 3. Información del sistema

### Comandos ejecutados

```bash
uname -a
hostnamectl
uptime
```

----------

## Resultados

(Pegar salida de comandos)

----------

## Análisis

-   Versión del sistema operativo:
-   Arquitectura:
-   Tiempo de actividad:
-   Load average:

**Interpretación técnica:**

(Explique si el sistema presenta carga normal o elevada)

----------

## 4. Análisis de CPU y procesos

## Comandos ejecutados

```bash
top
ps aux
ps aux --sort=-%cpu | head
```

----------

## Resultados

(Pegar salida relevante)

----------

## Análisis

-   Proceso con mayor uso de CPU:
-   % de CPU utilizado:

**Interpretación técnica:**

-   ¿Existe sobrecarga del sistema?
-   ¿Qué podría causar ese consumo?
    

----------

## 5. Análisis de memoria

## Comandos ejecutados

```bash
free -h
vmstat 1
```

----------

## Resultados

(Pegar salida)

----------

## Análisis

-   Memoria total:
    
-   Memoria usada:
    
-   Memoria libre:
    
-   Uso de swap:
    

**Interpretación técnica:**

-   ¿El uso de memoria es adecuado?
    
-   ¿Existe uso de swap? ¿Qué implica?
    

----------

## 6. Análisis de almacenamiento

## Comandos ejecutados

```bash
df -h
du -sh /var/log
lsblk

```

----------

## Resultados

(Pegar salida)

----------

## Análisis

-   Partición con mayor uso:
    
-   Directorios con mayor consumo:
    

**Interpretación técnica:**

-   ¿Existe riesgo de saturación?
    
-   ¿Qué acciones recomendaría?
    

----------

## 7. Análisis de red

## Comandos ejecutados

```bash
ip a
ping 8.8.8.8
ss -tuln

```

----------

## Resultados

(Pegar salida)

----------

## Análisis

-   Dirección IP del servidor:
    
-   Conectividad:
    
-   Puertos abiertos:
    

**Interpretación técnica:**

-   ¿El servidor está accesible?
    
-   ¿Hay servicios expuestos?
    

----------

## 8. Gestión de servicios

## Comandos ejecutados

```bash
systemctl status ssh
systemctl restart ssh
systemctl enable ssh

```

----------

## Resultados

(Pegar salida)

----------

## Análisis

-   Estado del servicio:
    
-   Acción realizada:
    

**Interpretación técnica:**

-   ¿Por qué es crítico este servicio?
    
-   ¿Qué impacto tendría su falla?
    

----------

## 9. Gestión de usuarios y permisos

## Comandos ejecutados

```bash
who
useradd usuario_prueba
passwd usuario_prueba
chmod 755 archivo.txt

```

----------

## Resultados

(Pegar evidencia)

----------

## Análisis

-   Usuario creado:
    
-   Permisos asignados:
    

**Interpretación técnica:**

-   ¿Qué implica el permiso 755?
    
-   ¿Qué riesgos existen con permisos incorrectos?
    

----------

## 10. Automatización con Bash

## Script desarrollado

```bash
(Pegar script aquí)

```

----------

## Explicación del script

-   ¿Qué hace el script?
-   ¿Qué comandos utiliza?
----------

## Resultado de ejecución

(Pegar salida del script)

----------

## Mejora propuesta

(Explique cómo podría mejorar el script para uso real en producción)

----------

## 11. Conclusión

Explique:

-   ¿Qué componente del sistema representa mayor riesgo?
-   ¿El servidor está en condiciones estables?
-   ¿Qué recomendaciones haría como administrador?
    

----------

## Restricciones

-   No usar interfaz gráfica (GUI)
-   No omitir comandos solicitados
-   No presentar resultados sin análisis
-   Todo debe ejecutarse en CLI
