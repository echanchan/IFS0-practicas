# IFS0 - Pr ctica 9  
## Virtualizaci¢n con KVM en Rocky Linux 10

---

# 1. Datos generales

- **Carrera:**  
- **Asignatura:** IFS0 - Analizando Necesidades de Infraestructura de Servidores  
- **Docente:**  
- **Unidad:** 3  
- **Pr ctica:** 9 - Virtualizaci¢n con KVM  
- **Nombre del estudiante / integrantes:** 
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet

---

# 2. Introducci¢n

Describa brevemente el objetivo de la pr ctica y el contexto de virtualizaci¢n con KVM.

---

# 3. Actividad 1 - Verificaci¢n del entorno y soporte de virtualizaci¢n

## Resultados obtenidos

| Verificaci¢n | Resultado obtenido |
|---|---|
| Versi¢n del kernel | |
| Flags vmx/svm presentes (cantidad) | |
| M¢dulo kvm cargado | |
| M¢dulo kvm_intel / kvm_amd cargado | |
| Dispositivo /dev/kvm existe | |
| systemd-detect-virt | |

---

## Evidencia

(Pegar salida de comandos ejecutados)

---

# 4. Actividad 2 - Instalaci¢n del stack KVM/QEMU/libvirt

## Resultados obtenidos

| Verificaci¢n | Resultado obtenido |
|---|---|
| libvirtd activo (active/running) | |
| virt-host-validate: KVM | |
| virt-host-validate: QEMU | |
| virsh list --all responde sin error | |

---

## Evidencia

(Pegar salida de comandos o capturas)

---

# 5. Actividad 3 - Preparaci¢n del almacenamiento y red virtual

## Resultados obtenidos

| Verificaci¢n | Resultado obtenido |
|---|---|
| Pool default activo | |
| Red default activa | |
| Interfaz virbr0 presente | |
| ISO Rocky Linux disponible | |

---

## Evidencia

(Pegar salida de comandos)

---

# 6. Actividad 4 - Creaci¢n de m quina virtual

## Resultados obtenidos

| Par metro de la VM | Valor observado |
|---|---|
| Nombre de la VM | |
| Estado | |
| UUID | |
| vCPUs asignadas | |
| RAM asignada | |
| Disco virtual (ruta) | |
| Red asignada | |

---

## Evidencia

(Pegar salida de comandos como:)
- `virsh list --all`
- `virsh dominfo`
- `virsh domblklist`
- `virsh domiflist`

---

# 7. An lisis t‚cnico

Responda:

- ¨El host soporta virtualizaci¢n correctamente?  
- ¨El stack KVM est  funcionando sin errores?  
- ¨La VM fue creada correctamente?  
- ¨Qu‚ ventajas observa al usar KVM en este entorno?  

---

# 8. Conclusi¢n

Explique:

- Beneficios de la virtualizaci¢n en servidores  
- Impacto en uso de recursos (CPU, RAM, almacenamiento)  
- Importancia de KVM en infraestructura moderna  

---

# Restricciones

- No omitir comandos solicitados  
- No modificar configuraci¢n base del entorno  
- No presentar resultados sin evidencia  
- Toda la administraci¢n debe realizarse v¡a CLI  

---

# Frase gu¡a

> "La virtualizaci¢n no solo permite ejecutar m£ltiples sistemas, permite optimizar la infraestructura y reducir costos operativos."
