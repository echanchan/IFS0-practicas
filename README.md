<hr>
<h1 id="ifs0-practicas-cli-servidores">
  IFS0 – Prácticas de Infraestructura de Servidores
</h1>

<h2 id="guia-trabajo-practica-8">📘 Guía de Trabajo – Práctica 8</h2>
<p><strong>Unidad 3:</strong> Sistemas operativos para servidores</p>
<p><strong>Práctica:</strong> Administración de Servidores Linux mediante CLI</p>

<hr>

<h2 id="competencia">1️ Competencia a desarrollar</h2>
<p>
  <strong>
    Administra un servidor Linux utilizando comandos de línea de comandos (CLI) para monitorear recursos, gestionar procesos, servicios, red y almacenamiento, interpretando métricas del sistema para la toma de decisiones técnicas.
  </strong>
</p>

<hr>

<h2 id="contexto">2️ Contexto de la práctica (escenario)</h2>

<p>
  Una organización ha implementado un servidor Linux para soportar servicios críticos:
</p>

<ul>
  <li>aplicaciones web</li>
  <li>base de datos</li>
  <li>servicios internos</li>
</ul>

<p>
  El área de infraestructura requiere validar que el sistema:
</p>

<ul>
  <li>funcione correctamente</li>
  <li>tenga estabilidad operativa</li>
  <li>mantenga disponibilidad (HA)</li>
  <li>no presente cuellos de botella (CPU, RAM, IOPS, red)</li>
</ul>

<hr>

<h2 id="actividades">3 Actividades de laboratorio</h2>

<hr>

<h3 id="actividad-1">🧪 Actividad 1 – Identificación del sistema</h3>

<p><strong>Objetivo</strong><br>
Obtener información general del servidor.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
Un administrador debe conocer:</p>

<ul>
  <li>sistema operativo</li>
  <li>kernel</li>
  <li>tiempo de actividad (uptime)</li>
</ul>

<p>Esto permite evaluar estabilidad y contexto del servidor.</p>

<hr>

<p><strong>Comandos a ejecutar</strong></p>

<pre><code>uname -a
hostnamectl
uptime
</code></pre>

<hr>

<p><strong>Resultado esperado</strong><br>
El estudiante debe documentar:</p>

<ul>
  <li>versión del kernel</li>
  <li>arquitectura del sistema</li>
  <li>tiempo de actividad</li>
  <li>carga promedio (load average)</li>
</ul>

<hr>

<h3 id="actividad-2">🧪 Actividad 2 – Monitoreo de CPU y procesos</h3>

<p><strong>Objetivo</strong><br>
Analizar el uso de CPU y procesos activos.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
El sistema operativo usa un scheduler para distribuir CPU.
El análisis de procesos permite detectar:</p>

<ul>
  <li>sobrecarga</li>
  <li>procesos anómalos</li>
  <li>consumo excesivo</li>
</ul>

<hr>

<p><strong>Comandos</strong></p>

<pre><code>top
ps aux
ps aux --sort=-%cpu | head
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Identificar el proceso que más CPU consume</li>
  <li>Explicar qué podría causar alta carga</li>
  <li>Determinar si existe riesgo de saturación</li>
</ol>

<hr>

<h3 id="actividad-3">🧪 Actividad 3 – Análisis de memoria</h3>

<p><strong>Objetivo</strong><br>
Evaluar el uso de RAM y memoria virtual.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
La memoria incluye:</p>

<ul>
  <li>RAM</li>
  <li>cache</li>
  <li>swap</li>
</ul>

<p>Un uso incorrecto puede afectar rendimiento.</p>

<hr>

<p><strong>Comandos</strong></p>

<pre><code>free -h
vmstat 1
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Identificar memoria usada vs disponible</li>
  <li>Verificar uso de swap</li>
  <li>Explicar impacto del uso de swap en rendimiento</li>
</ol>

<hr>

<h3 id="actividad-4">🧪 Actividad 4 – Análisis de almacenamiento</h3>

<p><strong>Objetivo</strong><br>
Evaluar uso de disco e I/O.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
El almacenamiento afecta:</p>

<ul>
  <li>IOPS</li>
  <li>latencia</li>
  <li>rendimiento de aplicaciones</li>
</ul>

<hr>

<p><strong>Comandos</strong></p>

<pre><code>df -h
du -sh /var/log
lsblk
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Identificar partición con mayor uso</li>
  <li>Detectar directorios con alto consumo</li>
  <li>Explicar riesgos de disco lleno</li>
</ol>

<hr>

<h3 id="actividad-5">🧪 Actividad 5 – Análisis de red</h3>

<p><strong>Objetivo</strong><br>
Verificar conectividad y estado de red.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
La red permite comunicación entre servicios.
Se analizan:</p>

<ul>
  <li>IP</li>
  <li>puertos abiertos</li>
  <li>conectividad</li>
</ul>

<hr>

<p><strong>Comandos</strong></p>

<pre><code>ip a
ping 8.8.8.8
ss -tuln
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Identificar IP del servidor</li>
  <li>Verificar conectividad externa</li>
  <li>Identificar puertos abiertos</li>
</ol>

<hr>

<h3 id="actividad-6">🧪 Actividad 6 – Gestión de servicios</h3>

<p><strong>Objetivo</strong><br>
Administrar servicios del sistema.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
Los servicios son procesos persistentes (daemons) que soportan aplicaciones.</p>

<hr>

<p><strong>Comandos</strong></p>

<pre><code>systemctl status ssh
systemctl restart ssh
systemctl enable ssh
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Verificar estado de un servicio</li>
  <li>Reiniciarlo</li>
  <li>Explicar impacto de detener un servicio crítico</li>
</ol>

<hr>

<h3 id="actividad-7">🧪 Actividad 7 – Gestión de usuarios y permisos</h3>

<p><strong>Objetivo</strong><br>
Administrar acceso al sistema.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
Linux es un sistema multiusuario.</p>

<hr>

<p><strong>Comandos</strong></p>

<pre><code>who
useradd prueba
passwd prueba
chmod 755 archivo.txt
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Crear un usuario</li>
  <li>Asignar permisos a un archivo</li>
  <li>Explicar impacto de permisos incorrectos</li>
</ol>

<hr>

<h3 id="actividad-8">🧪 Actividad 8 – Automatización básica (Bash)</h3>

<p><strong>Objetivo</strong><br>
Automatizar tareas administrativas.</p>

<hr>

<p><strong>Concepto técnico</strong><br>
Los scripts permiten:</p>

<ul>
  <li>reducir errores</li>
  <li>mejorar eficiencia</li>
  <li>automatizar mantenimiento</li>
</ul>

<hr>

<p><strong>Crear script</strong></p>

<pre><code>nano mantenimiento.sh
</code></pre>

<hr>

<p><strong>Script base</strong></p>

<pre><code>#!/bin/bash

echo "Estado del sistema:"
uptime

echo "Uso de memoria:"
free -h

echo "Uso de disco:"
df -h
</code></pre>

<hr>

<p><strong>Ejecutar</strong></p>

<pre><code>chmod +x mantenimiento.sh
./mantenimiento.sh
</code></pre>

<hr>

<p><strong>Tareas</strong></p>

<ol>
  <li>Ejecutar script</li>
  <li>Explicar qué hace cada comando</li>
  <li>Proponer mejora del script</li>
</ol>

<hr>

<h2 id="evidencia">5️ Evidencia a entregar</h2>

<p><strong>Repositorio:</strong><br>
<code>practica_8/</code><br>
<code>&nbsp;&nbsp; └── administracion_servidor_cli.md</code></p>

<hr>

<p><strong>El archivo debe contener</strong></p>

<ol>
  <li>Información del sistema</li>
  <li>Análisis de CPU y procesos</li>
  <li>Análisis de memoria</li>
  <li>Análisis de almacenamiento</li>
  <li>Análisis de red</li>
  <li>Gestión de servicios</li>
  <li>Gestión de usuarios</li>
  <li>Script Bash documentado</li>
  <li>Conclusiones técnicas</li>
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
      <td>Uso de comandos</td>
      <td>Correcto y completo</td>
      <td>Parcial</td>
      <td>Incorrecto</td>
    </tr>
    <tr>
      <td>Interpretación</td>
      <td>Técnica y clara</td>
      <td>Básica</td>
      <td>Incorrecta</td>
    </tr>
    <tr>
      <td>Análisis de recursos</td>
      <td>Completo</td>
      <td>Parcial</td>
      <td>Deficiente</td>
    </tr>
    <tr>
      <td>Automatización</td>
      <td>Funcional</td>
      <td>Básica</td>
      <td>Incorrecta</td>
    </tr>
  </tbody>
</table>
