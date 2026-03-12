<hr>
<h1 id="ifs0-practicas-dimensionamiento-electrico-ups-rack">
  IFS0 – Prácticas de Infraestructura de Servidores
</h1>

<h2 id="guia-trabajo-practica-7">📘 Guía de Trabajo – Práctica 7</h2>
<p><strong>Unidad 2:</strong> Infraestructura de servidores</p>
<p><strong>Práctica:</strong> Diseño de Rack de Servidores Basado en Normativas de Centros de Datos</p>

<hr>

<h2 id="competencia">1️ Competencia a desarrollar</h2>
<p>
  <strong>
    Diseña la arquitectura física de un rack de servidores aplicando estándares de centros de datos y buenas prácticas de ingeniería de infraestructura, justificando técnicamente la ubicación de equipos, gestión de energía, ventilación y cableado.
  </strong>
</p>

<hr>

<h2 id="contexto">2️ Contexto de la práctica (escenario)</h2>

<p>
  Una organización planea implementar una infraestructura de servidores en un rack estándar de 42U para soportar servicios críticos del negocio.
</p>

<p>
  El equipo de infraestructura ha definido el hardware que será instalado, pero no existe aún un diseño físico del rack.
</p>

<p>
  El área de TI solicita a un Analista de Infraestructura diseñar la distribución del rack considerando:
</p>

<ul>
  <li>seguridad</li>
  <li>estabilidad mecánica</li>
  <li>distribución eléctrica</li>
  <li>flujo de aire</li>
  <li>gestión de cableado</li>
  <li>buenas prácticas de centros de datos</li>
</ul>

<p>El diseño deberá basarse en estándares de la industria.</p>

<p><strong>Equipos disponibles para el rack</strong></p>

<table>
  <thead>
    <tr>
      <th>Equipo</th>
      <th>Modelo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Servidor de aplicaciones</td>
      <td>HPE ProLiant DL380 Gen11</td>
    </tr>
    <tr>
      <td>Servidor de base de datos</td>
      <td>Dell PowerEdge R760</td>
    </tr>
    <tr>
      <td>Servidor de archivos</td>
      <td>TrueNAS M50 Enterprise</td>
    </tr>
    <tr>
      <td>Almacenamiento SAN</td>
      <td>Dell PowerStore 1200T</td>
    </tr>
    <tr>
      <td>Switch de red</td>
      <td>Cisco Catalyst 9300</td>
    </tr>
    <tr>
      <td>Firewall</td>
      <td>FortiGate 100F</td>
    </tr>
    <tr>
      <td>UPS</td>
      <td>UPS Rackmount 6kVA</td>
    </tr>
  </tbody>
</table>

<p><strong>Componentes de infraestructura disponibles:</strong></p>
<ul>
  <li>Patch Panels</li>
  <li>Fiber Patch Panels</li>
  <li>Cable Managers</li>
  <li>Brush Panels</li>
  <li>Blank Panels</li>
  <li>KVM Switch</li>
  <li>Console Drawer</li>
  <li>PDU</li>
</ul>

<p><strong>Rack disponible:</strong><br>
Rack estándar 42U<br>
Ancho 19 pulgadas</p>

<hr>

<h2 id="desempenos">3️ Desempeños esperados (observables)</h2>
<p>El estudiante demuestra competencia cuando:</p>
<ul>
  <li>✔ Investiga estándares de centros de datos aplicables</li>
  <li>✔ Diseña la distribución física de un rack de 42U</li>
  <li>✔ Justifica la ubicación de cada equipo</li>
  <li>✔ Aplica buenas prácticas de ventilación y cableado</li>
  <li>✔ Documenta correctamente el diseño técnico del rack</li>
</ul>

<hr>

<h2 id="actividades">4️ Actividades de laboratorio</h2>

<h3 id="actividad-1">🧪 Actividad 1 – Investigación de normativas de centros de datos</h3>
<p><strong>Objetivo</strong><br>
Identificar estándares utilizados en el diseño de racks y centros de datos.</p>

<p><strong>Paso 1 – Investigar normativas</strong><br>
Investigue al menos tres estándares relacionados con infraestructura de centros de datos. Ejemplos posibles:</p>
<ul>
  <li>ANSI/TIA-942</li>
  <li>EIA-310-E</li>
  <li>TIA-606-C</li>
  <li>BICSI Data Center Design</li>
  <li>ISO/IEC 24764</li>
</ul>

<p><strong>Paso 2 – Completar tabla de investigación</strong></p>
<table>
  <thead>
    <tr>
      <th>Estándar</th>
      <th>Organización</th>
      <th>Área que regula</th>
      <th>Aplicación en racks</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-2">🧪 Actividad 2 – Análisis del hardware</h3>
<p><strong>Objetivo</strong><br>
Analizar las características físicas y funcionales de los equipos que se instalarán en el rack.</p>

<p>Los estudiantes deben investigar:</p>
<ul>
  <li>altura en unidades de rack (U)</li>
  <li>tipo de equipo</li>
  <li>función en la infraestructura</li>
  <li>consumo eléctrico aproximado</li>
</ul>

<p><strong>Completar la tabla:</strong></p>
<table>
  <thead>
    <tr>
      <th>Equipo</th>
      <th>Altura (U)</th>
      <th>Tipo</th>
      <th>Consumo aproximado</th>
      <th>Función</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Servidor de aplicaciones</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Servidor base de datos</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Servidor archivos</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>SAN</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Switch</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Firewall</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>UPS</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<hr>

<h3 id="actividad-3">🧪 Actividad 3 – Diseño del rack</h3>
<p><strong>Objetivo</strong><br>
Diseñar la distribución física del rack utilizando Rackula.</p>
<p>El estudiante debe ensamblar el rack aplicando las normativas investigadas.</p>

<p>El diseño debe considerar:</p>
<ul>
  <li>ubicación del UPS</li>
  <li>ubicación de almacenamiento</li>
  <li>ubicación de servidores</li>
  <li>ubicación de equipos de red</li>
  <li>distribución lógica del cableado</li>
</ul>

<p>También debe incluir:</p>
<ul>
  <li>patch panels</li>
  <li>cable managers</li>
  <li>blank panels</li>
</ul>

<hr>

<h3 id="actividad-4">🧪 Actividad 4 – Gestión térmica del rack</h3>
<p><strong>Objetivo</strong><br>
Aplicar principios de ventilación y flujo de aire en racks de servidores.</p>

<p><strong>Investigar:</strong></p>
<ul>
  <li>flujo de aire front-to-back</li>
  <li>concepto de pasillo frío / pasillo caliente</li>
</ul>

<p><strong>Responder:</strong></p>
<p>1️ ¿Por qué se utilizan blank panels en los racks?</p>
<p>2️ ¿Qué ocurre si se dejan espacios abiertos en el rack?</p>
<p>3️ ¿Cómo afecta esto al enfriamiento de los servidores?</p>

<hr>

<h3 id="actividad-5">🧪 Actividad 5 – Gestión eléctrica del rack</h3>
<p><strong>Objetivo</strong><br>
Analizar cómo se distribuye la energía eléctrica dentro del rack.</p>

<p><strong>Investigar:</strong></p>
<ul>
  <li>función de un UPS en rack</li>
  <li>función de una PDU</li>
  <li>relación entre UPS y servidores</li>
</ul>

<p><strong>Responder:</strong></p>
<p>1️ ¿Por qué el UPS se ubica normalmente en la parte inferior del rack?</p>
<p>2️ ¿Cómo se distribuye la energía hacia los servidores?</p>
<p>3️ ¿Qué ocurriría si no existiera UPS en la infraestructura?</p>

<hr>

<h3 id="actividad-6">🧪 Actividad 6 – Documentación del rack</h3>
<p><strong>Objetivo</strong><br>
Documentar el diseño final del rack.</p>
<p>El estudiante debe incluir:</p>
<ul>
  <li>diagrama del rack (captura de Rackula)</li>
  <li>explicación de la distribución</li>
  <li>justificación técnica basada en normas</li>
  <li>explicación del flujo de aire</li>
</ul>

<hr>

<h2 id="evidencia">5️ Evidencia a entregar</h2>
<p><strong>Repositorio:</strong><br>
<code>practica_7/</code><br>
<code>&nbsp;&nbsp; └── diseno_rack_normativas.md</code></p>

<p><strong>El documento debe incluir:</strong></p>
<ol>
  <li>Normativas investigadas</li>
  <li>Análisis del hardware</li>
  <li>Diseño del rack</li>
  <li>Captura del rack en Rackula</li>
  <li>Justificación técnica del diseño</li>
  <li>Explicación del flujo de aire</li>
</ol>

<hr>

<h2 id="restricciones">6 Restricciones</h2>
<ul>
  <li>🚫 No modificar el hardware del escenario</li>
  <li>🚫 No cambiar el tamaño del rack (42U)</li>
  <li>🚫 No eliminar el UPS del diseño</li>
  <li>🚫 No ignorar los elementos de infraestructura</li>
</ul>
