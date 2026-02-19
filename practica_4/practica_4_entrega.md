# FORMATO DE ENTREGA - PRACTICA 4

## RAID 5 y RAID 6

**Ruta obligatoria:**
```
IFS0-practicas/
    practica_4/
        raid_5_6.md <-- Crear este archivo
```

----------

# Practica - Implementaci¢n de RAID 5 y RAID 6

## 1. Introduccion

Objetivo de la practica y diferencia conceptual entre RAID 5 y RAID 6.

## 2. Configuracion del Arreglo

### 2.1 RAID 5

- Discos utilizados:
- Comando:
- Capacidad teorica esperada:
- Capacidad real observada:

---

### 2.2 RAID 6

- Discos utilizados:
- Comando:
- Capacidad teorica esperada:
- Capacidad real observada:

---

## 3. Analisis de Espacio

Salida de:

```
df -h
```

Tabla comparativa:

| RAID | Discos | Capacidad util | Perdida por paridad |
|------|--------|---------------|--------------------|
| RAID 5 | | | |
| RAID 6 | | | |

Explica los resultados obtenidos.

---

## 4. Simulacion de Fallos

### 4.1 RAID 5 - 1 fallo

- Disco fallado:
- Estado del arreglo:
- Evidencia de persistencia de datos:

---

### 4.2 RAID 6 - 2 fallos

- Discos fallados:
- Estado:
- Evidencia:

---

## 5. Reconstruccion

Salida relevante de:

```
cat /proc/mdstat
```
Tiempo aproximado de reconstruccion:

---

## 6. Comparacion Tecnica

- Diferencia en seguridad
- Diferencia en rendimiento
- Impacto del doble calculo de paridad
- ¨Cual usaria para almacenamiento critico?

---

## 7. Conclusion
Cada miembro del equipo debe escribir una conclusi¢n de aprendizaje obtenido durante la realizaci¢n de esta practica.


