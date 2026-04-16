<hr>
<h1 id="ifs0-practicas-virtualizacion-kvm">
  IFS0 – Prácticas de Infraestructura de Servidores
</h1>

<h2 id="guia-trabajo-practica-9">📘 Guía de Trabajo – Práctica 9</h2>
<p><strong>Práctica:</strong> Virtualización con KVM en Rocky Linux 10</p>

<hr>

<h2 id="competencia">1️ Competencia a desarrollar</h2>
<p>
  <strong>
    Implementa y administra virtualización con KVM en Rocky Linux 10, verificando el soporte del hardware, gestionando el ciclo de vida de máquinas virtuales y monitoreando recursos del sistema, para optimizar el uso de la infraestructura física y garantizar el aislamiento de servicios.
  </strong>
</p>

<hr>

<h2 id="contexto">2️ Contexto de la práctica (escenario)</h2>

<p>
  Una organización cuenta con un servidor físico con alta capacidad instalada que ejecuta Rocky Linux 10 en instalación minimal. Sin embargo:
</p>

<ul>
  <li>solo ejecuta un servicio por servidor físico</li>
  <li>el hardware está subutilizado (CPU &lt; 15 %, RAM &lt; 20 %)</li>
  <li>no existe aislamiento entre aplicaciones</li>
  <li>el tiempo de aprovisionamiento de nuevos servicios es elevado</li>
</ul>

<p>
  El equipo de infraestructura debe implementar una solución de virtualización que:
</p>

<ul>
  <li>maximice el uso del hardware mediante KVM</li>
  <li>permita ejecutar múltiples servicios aislados</li>
  <li>garantice administración desde CLI</li>
  <li>facilite la escalabilidad y gestión de snapshots</li>
</ul>

<hr>

<p><strong>Entorno de trabajo</strong></p>

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
      <td>VirtualBox con Rocky Linux 10 Minimal (VM entregada)</td>
    </tr>
    <tr>
      <td>ISO para VMs internas</td>
      <td>Rocky Linux 10 Minimal ISO (descargada en el host)</td>
    </tr>
    <tr>
      <td>Tecnología de virtualización</td>
      <td>KVM + QEMU + libvirt</td>
    </tr>
    <tr>
      <td>Interfaz de gestión</td>
      <td>virsh (CLI) + virt-install</td>
    </tr>
    <tr>
      <td>Rack de referencia</td>
      <td>Guía Rocky Linux – Administración de Servidores (IFS0)</td>
    </tr>
  </tbody>
</table>

<hr>

<h2 id="actividades">3 Actividades de laboratorio</h2>

<hr>

<h3 id="actividad-1">🧪 Actividad 1 – Verificación del entorno y soporte de virtualización</h3>

<p><strong>Objetivo</strong><br>
Confirmar que el sistema Rocky Linux 10 soporta KVM y obtener información del entorno base.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
Antes de instalar cualquier plataforma de virtualización, el administrador debe verificar que la CPU expone las instrucciones de extensión de virtualización (Intel VT-x / AMD-V). Sin estas instrucciones, KVM no puede operar como hipervisor Tipo 1.</p>

<hr>

<p><strong>Paso 1 – Información general del sistema</strong></p>

<pre><code>hostnamectl
uname -r
cat /etc/rocky-release
uptime -p
</code></pre>

<hr>

<p><strong>Paso 2 – Verificar soporte de virtualización en CPU</strong></p>

<pre><code># Contar flags vmx (Intel) o svm (AMD) en todos los núcleos
grep -Ec '(vmx|svm)' /proc/cpuinfo

# Detalle de capacidades de virtualización
lscpu | grep -i 'virtualization\|hypervisor'

# Detectar si el host ya corre dentro de una VM
systemd-detect-virt
</code></pre>

<hr>

<p><strong>Paso 3 – Verificar módulos del kernel</strong></p>

<pre><code>lsmod | grep kvm
# Resultado esperado: kvm_intel (o kvm_amd) + kvm

# Si no aparecen, cargar manualmente:
modprobe kvm
modprobe kvm_intel   # Intel
# modprobe kvm_amd   # AMD

# Confirmar dispositivo KVM
ls -la /dev/kvm
</code></pre>

<hr>

<p><strong>Resultado esperado</strong><br>
Completar la siguiente tabla:</p>

<table>
  <thead>
    <tr>
      <th>Verificación</th>
      <th>Resultado obtenido</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Versión del kernel</td>
      <td></td>
    </tr>
    <tr>
      <td>Flags vmx/svm presentes (cantidad)</td>
      <td></td>
    </tr>
    <tr>
      <td>Módulo kvm cargado</td>
      <td></td>
    </tr>
    <tr>
      <td>Módulo kvm_intel / kvm_amd cargado</td>
      <td></td>
    </tr>
    <tr>
      <td>Dispositivo /dev/kvm existe</td>
      <td></td>
    </tr>
    <tr>
      <td>systemd-detect-virt</td>
      <td></td>
    </tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-2">🧪 Actividad 2 – Instalación del stack KVM/QEMU/libvirt</h3>

<p><strong>Objetivo</strong><br>
Instalar y habilitar la plataforma completa de virtualización en Rocky Linux 10.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
libvirt es la capa de abstracción que permite administrar diferentes hipervisores (KVM, QEMU, Xen) con una API uniforme. <code>virsh</code> es su cliente CLI. <code>virt-install</code> automatiza la creación de VMs desde la terminal.</p>

<hr>

<p><strong>Paso 1 – Instalar paquetes</strong></p>

<pre><code># Habilitar EPEL
sudo dnf install -y epel-release

# Instalar stack completo
dnf install -y qemu-kvm libvirt libvirt-devel \
    virt-install virt-viewer virt-manager \
    bridge-utils libguestfs-tools guestfs-tools
</code></pre>

<hr>

<p><strong>Paso 2 – Habilitar e iniciar libvirtd</strong></p>

<pre><code>systemctl enable --now libvirtd
systemctl status libvirtd
</code></pre>

<hr>

<p><strong>Paso 3 – Agregar usuario al grupo libvirt</strong></p>

<pre><code>usermod -aG libvirt $(whoami)
newgrp libvirt
</code></pre>

<hr>

<p><strong>Paso 4 – Validar instalación</strong></p>

<pre><code>virt-host-validate
# Todos los ítems deben mostrar PASS o WARN (no FAIL)

virsh list --all
# Debe responder sin errores (lista vacía es normal)
</code></pre>

<hr>

<p><strong>Resultado esperado</strong><br>
Completar la siguiente tabla:</p>

<table>
  <thead>
    <tr>
      <th>Verificación</th>
      <th>Resultado obtenido</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>libvirtd activo (active/running)</td>
      <td></td>
    </tr>
    <tr>
      <td>virt-host-validate: KVM</td>
      <td></td>
    </tr>
    <tr>
      <td>virt-host-validate: QEMU</td>
      <td></td>
    </tr>
    <tr>
      <td>virsh list --all responde sin error</td>
      <td></td>
    </tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-3">🧪 Actividad 3 – Preparación del almacenamiento y red virtual</h3>

<p><strong>Objetivo</strong><br>
Configurar el pool de almacenamiento de libvirt y verificar la red virtual NAT predeterminada.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
libvirt gestiona el almacenamiento mediante pools (directorios, LVM, NFS). La red <code>default</code> es una red NAT virtual que permite a las VMs acceder a internet a través del host. Sin pool y sin red, <code>virt-install</code> no puede crear VMs.</p>

<hr>

<p><strong>Paso 1 – Verificar y activar el pool por defecto</strong></p>

<pre><code># Ver pools disponibles
virsh pool-list --all

# Si el pool default no existe, crearlo
virsh pool-define-as default dir - - - - /var/lib/libvirt/images
virsh pool-build default

# Iniciar el pool default si está inactivo
virsh pool-start default
virsh pool-autostart default

# Verificar directorio del pool
virsh pool-dumpxml default | grep -i target
ls -lh /var/lib/libvirt/images/
</code></pre>

<hr>

<p><strong>Paso 2 – Verificar y activar la red virtual NAT</strong></p>

<pre><code># Ver redes virtuales
virsh net-list --all

# Activar la red default si está inactiva
virsh net-start default
virsh net-autostart default

# Ver configuración de la red
virsh net-dumpxml default

# Confirmar interfaz bridge virbr0
ip addr show virbr0
</code></pre>

<hr>

<p><strong>Paso 3 – Subir la ISO de Rocky Linux 10 al pool</strong></p>

<pre><code># Crear directorio para ISOs (si no existe)
mkdir -p /var/lib/libvirt/images

# Verificar que la ISO está disponible (se asume subida previamente)
ls -lh /var/lib/libvirt/images/*.iso

# Descargar la ISO
wget -O /var/lib/libvirt/images/Rocky-10.1-x86_64-minimal.iso https://download.rockylinux.org/pub/rocky/10/isos/x86_64/Rocky-10.1-x86_64-minimal.iso
curl -o /var/lib/libvirt/images/Rocky-10.1-x86_64-minimal.iso -L https://download.rockylinux.org/pub/rocky/10/isos/x86_64/Rocky-10.1-x86_64-minimal.iso

# Verificar integridad con checksum
sha256sum /var/lib/libvirt/images/Rocky-10*.iso
</code></pre>

<hr>

<p><strong>Resultado esperado</strong><br>
Completar la siguiente tabla:</p>

<table>
  <thead>
    <tr>
      <th>Verificación</th>
      <th>Resultado obtenido</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Pool default activo</td>
      <td></td>
    </tr>
    <tr>
      <td>Red default activa</td>
      <td></td>
    </tr>
    <tr>
      <td>Interfaz virbr0 presente</td>
      <td></td>
    </tr>
    <tr>
      <td>ISO Rocky Linux 10 disponible en /var/lib/libvirt/images/</td>
      <td></td>
    </tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-4">🧪 Actividad 4 – Creación de una máquina virtual con virt-install</h3>

<p><strong>Objetivo</strong><br>
Crear y configurar una VM con Rocky Linux 10 Minimal utilizando <code>virt-install</code> desde CLI.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
<code>virt-install</code> automatiza la creación de VMs definiendo CPU virtual, RAM, disco e ISO en un solo comando. El flag <code>--os-variant</code> optimiza los parámetros de la VM según el sistema operativo seleccionado. La instalación desatendida (<code>--extra-args</code>) permite usar Kickstart.</p>

<hr>

<p><strong>Paso 1 – Crear la VM</strong></p>

<pre><code># Crear VM Rocky Linux 10 con 1 vCPU, 1 GB RAM, 10 GB disco
virt-install \
  --name vm-rocky10-lab \
  --ram 1024 \
  --vcpus 1 \
  --os-variant rocky9 \
  --disk pool=default,size=10,format=qcow2,bus=virtio \
  --network network=default,model=virtio \
  --graphics none \
  --console pty,target_type=serial \
  --cdrom /var/lib/libvirt/images/Rocky-10-minimal.iso \
  --extra-args 'console=ttyS0,115200n8'

# La instalación abrirá una consola de texto en la terminal
# Sigue el asistente de instalación de Rocky Linux
</code></pre>

<hr>

<p><strong>Paso 2 – Monitorear el proceso de creación</strong></p>

<pre><code># En otra terminal, monitorear estado de la VM
virsh list --all

# Ver información de la VM durante instalación
virsh dominfo vm-rocky10-lab

# Ver consola (si se desconectó)
virsh console vm-rocky10-lab
# Para salir de la consola: Ctrl + ]
</code></pre>

<hr>

<p><strong>Paso 3 – Verificar VM creada</strong></p>

<pre><code># Listar VMs
virsh list --all

# Información detallada de la VM
virsh dominfo vm-rocky10-lab

# Ver discos asignados
virsh domblklist vm-rocky10-lab

# Ver interfaces de red
virsh domiflist vm-rocky10-lab

# Ver configuración XML completa
virsh dumpxml vm-rocky10-lab
</code></pre>

<hr>

<p><strong>Resultado esperado</strong><br>
Completar la siguiente tabla:</p>

<table>
  <thead>
    <tr>
      <th>Parámetro de la VM</th>
      <th>Valor observado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Nombre de la VM</td>
      <td></td>
    </tr>
    <tr>
      <td>Estado</td>
      <td></td>
    </tr>
    <tr>
      <td>UUID</td>
      <td></td>
    </tr>
    <tr>
      <td>vCPUs asignadas</td>
      <td></td>
    </tr>
    <tr>
      <td>RAM asignada</td>
      <td></td>
    </tr>
    <tr>
      <td>Disco virtual (ruta)</td>
      <td></td>
    </tr>
    <tr>
      <td>Red asignada</td>
      <td></td>
    </tr>
  </tbody>
</table>

<hr>

<h2 id="evidencia">5️ Evidencia a entregar</h2>

<p><strong>Repositorio:</strong><br>
<code>practica_9/</code><br>
<code>&nbsp;&nbsp; └── virtualizacion_con_kvm.md</code></p>

<hr>

<p><strong>El archivo debe contener</strong></p>

<ol>
  <li>Verificación de soporte KVM (tablas de Actividad 1 y 2 completadas)</li>
  <li>Evidencia de instalación del stack libvirt (capturas de pantalla o salida de comandos)</li>
  <li>Configuración de pool y red virtual (Actividad 3)</li>
  <li>Datos de la VM creada con virt-install (tabla de Actividad 4)</li>
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
      <td>Verificación de soporte KVM</td>
      <td>Completa y documentada</td>
      <td>Parcial</td>
      <td>Incorrecta</td>
    </tr>
    <tr>
      <td>Instalación del stack</td>
      <td>Correcta y funcional</td>
      <td>Con errores menores</td>
      <td>Incompleta</td>
    </tr>
    <tr>
      <td>Creación y gestión de VM</td>
      <td>Completa con snapshots</td>
      <td>Parcial</td>
      <td>No funcional</td>
    </tr>
  </tbody>
</table>
