# IFS0 - Pr ctica 10  
## Administraci¢n y Monitoreo de M quinas Virtuales KVM

---

## 1. Datos generales

- **Carrera:**  
- **Asignatura:** IFS0 - Analizando Necesidades de Infraestructura de Servidores  
- **Docente:**  
- **Unidad:** 3  
- **Pr ctica:** 10 - Administraci¢n KVM  
- **Fecha de entrega:**  
- **Nombre del estudiante / integrantes:** 
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet
	- Nombre completo - Carnet

---

## 2. Introducci¢n

Describa el objetivo de la pr ctica y el contexto del uso de virtualizaci¢n en servidores.

---

## 3. Actividad 1 - Ciclo de vida de la VM

## Resultados obtenidos

| Verificaci¢n | Resultado obtenido |
|-------------|-------------------|
| Estado tras `virsh start` | |
| Estado tras `virsh suspend` | |
| Estado tras `virsh resume` | |
| Archivo `.state` (ruta y tama¤o) | |
| Estado tras `virsh restore` | |
| Estado tras `virsh shutdown` | |

---

## Evidencia

(Pegar salidas de comandos ejecutados)
````sh
virsh list --all  
virsh start vm-rocky10-lab  
virsh domstate vm-rocky10-lab
````
  
---  
  
## 4. Actividad 2 - Snapshots con virsh  
  
## Resultados obtenidos  
  
| Verificaci¢n | Resultado obtenido |  
|-------------|-------------------|  
| Formato del disco (qcow2) | |  
| Nombre del snapshot baseline | |  
| Nombre del snapshot con cambio | |  
| µrbol de snapshots | |  
| Archivo presente en snapshot con cambio | |  
| Archivo eliminado tras revert | |  
  
---  
  
## Evidencia  
  
(Pegar comandos y salidas)  
````sh
virsh snapshot-list vm-rocky10-lab --tree  
qemu-img info <ruta>
````
  
---  
  
## 5. Actividad 3 - Clonado de VM  
  
## Resultados obtenidos  
  
| Verificaci¢n | Resultado obtenido |  
|-------------|-------------------|  
| Nombre del clon | |  
| UUID VM original | |  
| UUID VM clon | |  
| MAC del clon | |  
| Disco del clon | |  
| Estado del clon | |  
  
---  
  
## Evidencia  
````sh
virt-clone ...  
virsh domuuid vm-rocky10-clone  
virsh domiflist vm-rocky10-clone
````
  
---  
  
## 6. Actividad 4 - Monitoreo de recursos  
  
## Resultados obtenidos  
  
| Par metro | Valor observado |  
|----------|----------------|  
| Columnas de virt-top | |  
| CPU time | |  
| RAM asignada | |  
| Lecturas de disco | |  
| Tama¤o virtual vs real | |  
  
---  
  
## Evidencia  
````sh
virt-top  
virsh domstats vm-rocky10-lab  
virsh dommemstat vm-rocky10-lab  
virsh domblkstat vm-rocky10-lab vda
````
  
---  
  
## 7. Extracci¢n de archivos con libguestfs  
  
## Resultados  
  
| Acci¢n | Resultado |  
|--------|----------|  
| Sistemas detectados | |  
| Uso de disco (virt-df) | |  
| Archivo extra¡do (/etc/hostname) | |  
  
---  
  
## Evidencia  
````sh
virt-filesystems -a <ruta>  
virt-df -a <ruta>  
virt-copy-out -a <ruta> /etc/hostname .
````
  
---  
  
## 8. An lisis tecnico  
  
Responda:  
  
- ¨Que ventajas ofrece el uso de snapshots en producci¢n?  
- ¨Por que el clonado es importante en entornos empresariales?  
- ¨Que riesgos existen si no se monitorean las VMs?  
- ¨C¢mo contribuye KVM a la alta disponibilidad (HA)?  
  
---  
  
## 9. Conclusi¢n  
  
Explique:  
  
- Importancia de la administraci¢n desde CLI  
- Impacto en eficiencia operativa  
- Aplicaci¢n en entornos reales  
  
---  
  
##  Restricciones  
  
- No omitir evidencias de comandos  
- No usar interfaces gr ficas  
- No inventar resultados  
- Todas las salidas deben ser reales del sistema  
  
---  
