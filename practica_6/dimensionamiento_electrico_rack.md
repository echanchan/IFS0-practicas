# Práctica 6 – Dimensionamiento Eléctrico, UPS y Densidad de Rack
## 1. Datos generales

- **Carrera:**  
- **Asignatura:** IFS0 – Analizando Necesidades de Infraestructura de Servidores  
- **Docente:**  
- **Unidad:** 2  
- **Práctica:** 6 – Dimensionamiento Eléctrico y Térmico de Infraestructura  
- **Nombre del estudiante / integrantes:** 
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
----------

## 2 Introducción

En este documento se presenta el análisis eléctrico y térmico de una infraestructura de servidores instalada en un rack estándar de centro de datos.

El objetivo de la práctica es calcular el consumo eléctrico total de la infraestructura, evaluar la capacidad del circuito eléctrico, estimar la autonomía del sistema de respaldo UPS y analizar la densidad térmica generada dentro del rack.

Este análisis permite comprender cómo el diseño eléctrico y térmico influye en la disponibilidad y estabilidad de los servicios de infraestructura.

----------

## 3 Equipos analizados

| Equipo | Modelo |
|---|---|
| Servidor de aplicaciones | HPE ProLiant DL380 Gen11 |
| Servidor de base de datos | Dell PowerEdge R760 |
| Servidor de archivos | TrueNAS M50 Enterprise |
| Switch de red | Cisco Catalyst 9300-48P |
| Firewall | FortiGate 100F |
| Almacenamiento SAN | Dell PowerStore 1200T |

----------

## 4 Investigación de especificaciones técnicas

Complete la siguiente tabla con las especificaciones investigadas.

| Equipo | Potencia Máxima (W) | BTU/h | Tamaño (U) | Fuente |
|---|---|---|---|---|
| Servidor aplicaciones | | | | |
| Servidor base de datos | | | | |
| Servidor archivos | | | | |
| Switch | | | | |
| Firewall | | | | |
| SAN | | | | |

----------

## 5 Selección del UPS

| Característica | Valor |
|---|---|
| Modelo seleccionado | |
| Capacidad VA | |
| Capacidad W | |
| Eficiencia | |
| Disipación térmica | |
| Tamaño rack (U) | |
| Autonomía aproximada | |
| Fuente de información | |

----------

## 6 Cálculo de carga eléctrica total

Realice el cálculo del consumo eléctrico total de la infraestructura.
```
Potencia total = suma de potencia de todos los equipos
```

**Resultado**
```
Carga eléctrica total = ______ W
```

----------

## 7 Cálculo de amperaje del circuito

Utilice la fórmula:
```
I = P / V
```

Donde:

-   **I** = Corriente (A)    
-   **P** = Potencia (W)    
-   **V** = Voltaje (V)    

Considere una alimentación de **120V**.
```
Amperaje requerido = ______ A

```

----------

## 8 Evaluación de capacidad del circuito

| Circuito | Capacidad segura | ¿Soporta la carga? |
|---|---|---|
| 15A | 1440 W | |
| 20A | 1920 W | |

**Análisis**

Explique si el circuito es suficiente para soportar la infraestructura y si sería necesario utilizar un circuito dedicado.

----------

## 9 Estimación de autonomía del UPS

```
Porcentaje de carga = (Carga real / Capacidad UPS) × 100
```

**Resultado**

```
Porcentaje de carga = ______ %
Autonomía estimada = ______ minutos
```

----------

## 10 Cálculo de carga térmica total

```
1 W = 3.412 BTU/h
```

```
BTU/h = Watts × 3.412
```

**Resultado**

```
Carga térmica total = ______ BTU/h
```

----------

## 11 Densidad térmica del rack

| Equipo | Tamaño (U) |
|---|---|
| Servidor aplicaciones | |
| Servidor base de datos | |
| Servidor archivos | |
| SAN | |
| Switch | |
| Firewall | |
| UPS | |
```
Total U utilizadas = ______ U
```

```
Densidad térmica = BTU total / U utilizadas
Densidad térmica = ______ BTU/U
```

----------

## 12 Diagrama del rack

Incluya aquí el diagrama del rack con la distribución de equipos.

Puede utilizar herramientas como:

- [Rackula](https://github.com/RackulaLives/Rackula)
- [NetBox](https://github.com/netbox-community/netbox)
    

----------

## 13 Análisis técnico final

Explique:
-   si el circuito eléctrico es suficiente    
-   si el UPS seleccionado es adecuado    
-   si la autonomía estimada es suficiente    
-   si la densidad térmica del rack representa un riesgo    
-   qué mejoras podrían realizarse en la infraestructura
