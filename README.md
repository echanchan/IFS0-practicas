<hr>
<h1 id="ifs0-practicas-administracion-kvm">
  IFS0 – Prácticas de Infraestructura de Servidores
</h1>

<h2 id="guia-trabajo-practica-10">📘 Guía de Trabajo – Práctica 10</h2>
<p><strong>Unidad 3:</strong> Sistemas operativos para servidores</p>
<p><strong>Práctica:</strong> Administración y Monitoreo de Máquinas Virtuales KVM</p>

<hr>

<h2 id="competencia">1️ Competencia a desarrollar</h2>
<p>
  <strong>
    Administra y monitorea máquinas virtuales KVM en Rocky Linux 10 utilizando virsh, virt-top y libguestfs, aplicando operaciones del ciclo de vida completo (inicio, pausa, migración de estado, snapshots y clonado), inspección de recursos desde el host y recuperación de archivos sin arrancar la VM, para garantizar alta disponibilidad y trazabilidad de los servicios virtualizados.
  </strong>
</p>

<hr>

<h2 id="contexto">2️ Contexto de la práctica (escenario)</h2>

<p>
  El equipo de infraestructura de la organización ya cuenta con el hipervisor KVM operativo (Práctica 9) y la VM <code>vm-rocky9-lab</code> definida. Ahora debe demostrar que puede:
</p>

<ul>
  <li>Controlar el ciclo de vida de VMs sin interfaz gráfica.</li>
  <li>Capturar y restaurar snapshots ante cambios de configuración críticos.</li>
  <li>Clonar VMs para aprovisionar nuevos servicios en minutos.</li>
  <li>Monitorear consumo de CPU, RAM y disco desde el host sin acceder a la VM.</li>
  <li>Recuperar archivos de un disco virtual sin arrancar la VM.</li>
</ul>

<p><strong>Entorno de trabajo:</strong></p>

<table>
  <thead>
    <tr>
      <th>Elemento</th>
      <th>Detalle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Hypervisor Host</td>
      <td>Rocky Linux 10 Minimal (VM entregada con nested virt)</td>
    </tr>
    <tr>
      <td>ISO para VMs internas</td>
      <td>vm-rocky10-lab (creada en Práctica 9)</td>
    </tr>
    <tr>
      <td>Tecnología de virtualización</td>
      <td>KVM + QEMU + libvirt</td>
    </tr>
    <tr>
      <td>Interfaz de gestión</td>
      <td>virsh · virt-top · virt-df · virt-filesystems · qemu-img</td>
    </tr>
  </tbody>
</table>

<hr>

<h2 id="actividades">3 Actividades de laboratorio</h2>

<h3 id="actividad-1">🧪 Actividad 1 – Ciclo de vida de la VM</h3>

<p><strong>Objetivo</strong><br>
Dominar los comandos virsh para controlar todos los estados operacionales de una máquina virtual: inicio, pausa, reanudación, suspensión a disco y apagado.
</p>

<p><strong>Concepto técnico</strong><br>
Una VM administrada con libvirt puede estar en los siguientes estados:
</p>

<pre><code>running – ejecutándose
paused  – pausada en RAM
shut off – apagada
saved   – estado volcado a disco
crashed – error fatal</code></pre>

<p>
  virsh permite transicionar entre estados con comandos atómicos. La operación
  save/restore preserva el estado de RAM en disco sin apagar el SO invitado,
  equivalente a la hibernación de una VM.
</p>

<p><strong>Paso 1 – Levantar la VM e identificar su estado</strong></p>

<pre><code># Listar todas las VMs definidas
virsh list --all

# Iniciar la VM
virsh start vm-rocky10-lab

# Verificar estado actual
virsh domstate vm-rocky10-lab

# Información completa de la VM
virsh dominfo vm-rocky10-lab</code></pre>

<p><strong>Paso 2 – Pausar y reanudar</strong></p>

<pre><code># Pausar (congela CPU y RAM, no libera recursos)
virsh suspend vm-rocky10-lab
virsh domstate vm-rocky10-lab   # debe mostrar: paused

# Reanudar desde pausa
virsh resume vm-rocky10-lab
virsh domstate vm-rocky10-lab   # debe mostrar: running</code></pre>

<p><strong>Paso 3 – Guardar y restaurar estado (save/restore)</strong></p>

<pre><code># Guardar estado completo de la VM en disco
virsh save vm-rocky10-lab /var/lib/libvirt/images/vm-rocky10-lab.state

# Verificar que la VM ya no aparece como running
virsh list --all

# Restaurar desde el archivo de estado
virsh restore /var/lib/libvirt/images/vm-rocky10-lab.state

# Confirmar que la VM está running nuevamente
virsh domstate vm-rocky10-lab</code></pre>

<p><strong>Paso 4 – Apagado controlado</strong></p>

<pre><code># Apagado limpio (envía ACPI shutdown al SO invitado)
virsh shutdown vm-rocky10-lab

# Esperar confirmación (puede tardar ~30 s)
watch -n 2 'virsh domstate vm-rocky10-lab'

# Forzar apagado inmediato (equivale a quitar la energía)
virsh destroy vm-rocky10-lab

# Nota: destroy NO elimina la VM ni su disco; solo la detiene.</code></pre>

<p><strong>Resultado esperado - Completar tabla</strong></p>

<table>
  <thead>
    <tr>
      <th>Verificación</th>
      <th>Resultado obtenido</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Estado tras virsh start</td><td>&nbsp;</td></tr>
    <tr><td>Estado tras virsh suspend</td><td>&nbsp;</td></tr>
    <tr><td>Estado tras virsh resume</td><td>&nbsp;</td></tr>
    <tr><td>Archivo .state creado (ruta y tamaño)</td><td>&nbsp;</td></tr>
    <tr><td>Estado tras virsh restore</td><td>&nbsp;</td></tr>
    <tr><td>Estado tras virsh shutdown</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-2">🧪 Actividad 2 – Snapshots con virsh</h3>

<p><strong>Objetivo</strong><br>
Crear, listar, inspeccionar y restaurar snapshots de una VM para proteger el estado antes de cambios de configuración críticos.
</p>

<p><strong>Concepto técnico</strong><br>
Un snapshot captura el estado del disco (y opcionalmente la RAM) de una VM en un instante determinado. libvirt soporta dos tipos:
</p>

<pre><code>Interno (qcow2) – almacenado dentro del mismo archivo de disco.
                  Solo disponible con formato qcow2.

Externo         – crea un nuevo archivo qcow2 de diferencial (overlay).
                  Recomendado para producción.</code></pre>

<p>En esta práctica usamos snapshots internos por simplicidad didáctica.</p>

<p><strong>Paso 1 – Verificar formato de disco (requisito qcow2)</strong></p>

<pre><code># Verificar formato del disco de la VM
virsh domblklist vm-rocky10-lab

# Inspeccionar el archivo de disco directamente
qemu-img info /var/lib/libvirt/images/vm-rocky10-lab.qcow2

# El campo 'file format' debe ser: qcow2</code></pre>

<p><strong>Paso 2 – Iniciar la VM y crear un snapshot</strong></p>

<pre><code># Iniciar la VM si está apagada
virsh start vm-rocky10-lab

# Crear snapshot interno con nombre descriptivo
virsh snapshot-create-as vm-rocky10-lab \
  --name  'snap-baseline' \
  --description 'Estado inicial antes de configuración' \
  --atomic

# Listar todos los snapshots de la VM
virsh snapshot-list vm-rocky10-lab</code></pre>

<p><strong>Paso 3 – Simular un cambio y crear un segundo snapshot</strong></p>

<pre><code># Conectar a la consola de la VM
virsh console vm-rocky10-lab

# (dentro de la VM) crear un archivo de prueba
touch /root/archivo_de_prueba.txt
echo 'Cambio simulado Practica 10' > /root/archivo_de_prueba.txt
exit

# (Ctrl+] para salir de la consola)

# Crear segundo snapshot reflejando el cambio
virsh snapshot-create-as vm-rocky10-lab \
  --name  'snap-con-cambio' \
  --description 'Con archivo de prueba creado'

virsh snapshot-list vm-rocky10-lab --tree</code></pre>

<p><strong>Paso 4 – Restaurar al snapshot baseline</strong></p>

<pre><code># Apagar la VM antes de revertir (snapshot interno requiere VM apagada)
virsh shutdown vm-rocky10-lab

# Revertir al snapshot baseline
virsh snapshot-revert vm-rocky10-lab snap-baseline

# Iniciar la VM y verificar que el archivo NO existe
virsh start vm-rocky10-lab
virsh console vm-rocky10-lab
ls /root/archivo_de_prueba.txt   # debe dar: No such file or directory</code></pre>

<p><strong>Paso 5 – Eliminar un snapshot</strong></p>

<pre><code># Eliminar el snapshot de cambio (ya no necesario)
virsh snapshot-delete vm-rocky10-lab snap-con-cambio

# Confirmar que solo queda snap-baseline
virsh snapshot-list vm-rocky10-lab</code></pre>

<p><strong>Resultado esperado - Completar tabla</strong></p>

<table>
  <thead>
    <tr>
      <th>Verificación</th>
      <th>Resultado obtenido</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Formato del disco (qemu-img info)</td><td>&nbsp;</td></tr>
    <tr><td>Nombre del primer snapshot</td><td>&nbsp;</td></tr>
    <tr><td>Nombre del segundo snapshot</td><td>&nbsp;</td></tr>
    <tr><td>Árbol de snapshots (snapshot-list --tree)</td><td>&nbsp;</td></tr>
    <tr><td>Archivo presente en snap-con-cambio</td><td>&nbsp;</td></tr>
    <tr><td>Archivo ausente tras revertir a snap-baseline</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-3">🧪 Actividad 3 – Clonado de VMs con virt-clone</h3>

<p><strong>Objetivo</strong><br>
Clonar una VM existente para aprovisionar un segundo servidor idéntico en minutos, sin repetir la instalación del SO.
</p>

<p><strong>Concepto técnico</strong><br>
virt-clone genera una copia completa de la VM: XML de definición + copia del disco qcow2. La nueva VM tiene UUIDs y MAC addresses únicos para evitar conflictos en la red virtual. El clonado es la base de plantillas (golden images) en entornos de infraestructura como código.
</p>

<p><strong>Paso 1 – Asegurarse de que la VM origen está apagada</strong></p>

<pre><code>virsh shutdown vm-rocky10-lab
virsh list --all   # verificar estado: shut off</code></pre>

<p><strong>Paso 2 – Clonar la VM</strong></p>

<pre><code># Clonar vm-rocky10-lab hacia vm-rocky10-clone
virt-clone \
  --original  vm-rocky10-lab \
  --name      vm-rocky10-clone \
  --auto-clone

# El disco clonado se crea automáticamente en el mismo pool
# con nombre: vm-rocky10-lab-clone.qcow2</code></pre>

<p><strong>Paso 3 – Verificar el clon</strong></p>

<pre><code># Listar todas las VMs
virsh list --all

# Comparar configuración de ambas VMs
virsh dominfo vm-rocky10-lab
virsh dominfo vm-rocky10-clone

# Verificar que los UUIDs son distintos
virsh domuuid vm-rocky10-lab
virsh domuuid vm-rocky10-clone

# Verificar discos
virsh domblklist vm-rocky10-clone

# Verificar que la MAC del clon es distinta
virsh domiflist vm-rocky10-clone</code></pre>

<p><strong>Paso 4 – Iniciar el clon y comprobar independencia</strong></p>

<pre><code># Iniciar el clon
virsh start vm-rocky10-clone

# Conectar a la consola del clon
virsh console vm-rocky10-clone
hostname          # verificar nombre del host
ip addr show      # verificar IP asignada por DHCP
# Ctrl+] para salir

# Verificar que la VM original sigue apagada / independiente
virsh domstate vm-rocky10-lab</code></pre>

<p><strong>Resultado esperado - Completar tabla</strong></p>

<table>
  <thead>
    <tr>
      <th>Verificación</th>
      <th>Resultado obtenido</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Nombre del clon creado</td><td>&nbsp;</td></tr>
    <tr><td>UUID de vm-rocky10-lab</td><td>&nbsp;</td></tr>
    <tr><td>UUID de vm-rocky10-clone (diferente)</td><td>&nbsp;</td></tr>
    <tr><td>MAC de vm-rocky10-clone</td><td>&nbsp;</td></tr>
    <tr><td>Disco del clon (ruta completa)</td><td>&nbsp;</td></tr>
    <tr><td>Estado del clon tras virsh start</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-4">🧪 Actividad 4 – Monitoreo de recursos con virt-top y virsh</h3>

<p><strong>Objetivo</strong><br>
Monitorear en tiempo real el consumo de CPU, RAM, disco e interfaces de red de las VMs desde el host, sin necesidad de acceder al SO invitado.
</p>

<p><strong>Concepto técnico</strong><br>
virt-top es el equivalente de top para hipervisores: muestra en tiempo real el consumo de todas las VMs del host. Los comandos virsh domstats y virsh dommemstat permiten capturar métricas puntuales en scripts.
</p>

<p><strong>Paso 1 – Instalar y usar virt-top</strong></p>

<pre><code># Instalar virt-top (puede requerir EPEL)
dnf install -y virt-top

# Lanzar monitoreo (similar a top, presiona q para salir)
virt-top

# Monitoreo con intervalo de 3 segundos
virt-top -d 3

# Exportar métricas a CSV (útil para reportes)
virt-top --csv /tmp/virt-metrics.csv -n 5
cat /tmp/virt-metrics.csv</code></pre>

<p><strong>Paso 2 – Estadísticas puntuales con virsh domstats</strong></p>

<pre><code># Estadísticas completas de todas las VMs activas
virsh domstats

# Estadísticas de una VM específica
virsh domstats vm-rocky10-lab

# Solo estadísticas de CPU
virsh domstats --cpu vm-rocky10-lab

# Solo estadísticas de memoria
virsh domstats --balloon vm-rocky10-lab

# Solo estadísticas de disco (bloque)
virsh domstats --block vm-rocky10-lab

# Solo estadísticas de red
virsh domstats --interface vm-rocky10-lab</code></pre>

<p><strong>Paso 3 – Memoria detallada con dommemstat</strong></p>

<pre><code># Estadísticas de memoria del balloon driver
virsh dommemstat vm-rocky10-lab

# Campos relevantes:
#   actual       - RAM asignada actualmente (KB)
#   rss          - RAM física en uso por QEMU (KB)
#   available    - RAM disponible dentro de la VM
#   usable       - RAM que el SO invitado puede usar</code></pre>

<p><strong>Paso 4 – Uso de disco en tiempo real</strong></p>

<pre><code># Ver estadísticas de I/O de bloque
virsh domblkstat vm-rocky10-lab vda

# Campos: rd_req (lecturas), wr_req (escrituras),
#         rd_bytes, wr_bytes

# Tamaño del disco virtual
virsh domblkinfo vm-rocky10-lab vda

# Ver en el host el archivo qcow2
qemu-img info /var/lib/libvirt/images/vm-rocky10-lab.qcow2
# 'virtual size' = tamaño provisionado
# 'disk size'    = espacio real ocupado en el host</code></pre>

<p><strong>Resultado esperado - Completar tabla</strong></p>

<table>
  <thead>
    <tr>
      <th>Parámetro de la VM</th>
      <th>Valor observado</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Columnas mostradas por virt-top</td><td>&nbsp;</td></tr>
    <tr><td>CPU time de vm-rocky10-lab (virsh domstats)</td><td>&nbsp;</td></tr>
    <tr><td>RAM actual asignada – dommemstat</td><td>&nbsp;</td></tr>
    <tr><td>Lecturas de disco (rd_req) – domblkstat</td><td>&nbsp;</td></tr>
    <tr><td>Tamaño virtual vs tamaño real del disco qcow2</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<hr>

<h2 id="evidencia">5️ Evidencia a entregar</h2>

<p><strong>Repositorio:</strong><br>
<code>practica_10/</code><br>
<code>&nbsp;&nbsp; └── administracion_kvm.md</code></p>

<p><strong>El archivo debe contener</strong></p>

<ol>
  <li>Tablas de resultado de todas las actividades (1 a 4) completadas con los valores reales observados en el entorno.</li>
  <li>Salida de al menos tres comandos relevantes por actividad (texto copiado de la terminal).</li>
  <li>Capturas del árbol de snapshots (<code>virsh snapshot-list --tree</code>).</li>
  <li>Comparación de UUIDs entre la VM original y el clon.</li>
  <li>Archivo <code>/etc/hostname</code> extraído con <code>virt-copy-out</code> mostrado en el documento.</li>
</ol>

<hr>

<h2 id="criterios">6️ Criterios de evaluación</h2>

<table>
  <thead>
    <tr>
      <th>Criterio</th>
      <th>Nivel Alto</th>
      <th>Nivel Medio</th>
      <th>Nivel Bajo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Ciclo de vida (Act. 1)</td>
      <td>Todos los estados documentados con salida real</td>
      <td>Parcial, sin save/restore</td>
      <td>Solo start/stop</td>
    </tr>
    <tr>
      <td>Snapshots (Act. 2)</td>
      <td>Creación, árbol y restauración verificada</td>
      <td>Creación sin restaurar</td>
      <td>Listado solo</td>
    </tr>
    <tr>
      <td>Clonado (Act. 3)</td>
      <td>UUID y MAC distintos documentados</td>
      <td>VM clonada sin verificar</td>
      <td>Comando ejecutado sin evidencia</td>
    </tr>
    <tr>
      <td>Monitoreo (Act. 4)</td>
      <td>virt-top + domstats + dommemstat + domblkstat</td>
      <td>Solo virt-top</td>
      <td>No realizado</td>
    </tr>
    <tr>
      <td>libguestfs (Act. 5)</td>
      <td>Extracción de archivos documentada</td>
      <td>virt-df ejecutado</td>
      <td>Solo virt-filesystems</td>
    </tr>
  </tbody>
</table>
