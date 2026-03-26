<hr>
<h1 id="ifs0-practicas-dimensionamiento-electrico-ups-rack">
  IFS0 – Prácticamiento-etrcu-r">
  IFS0 – Prácticas de Infraestructura de Servidores
</h1>

<h2 id="guia-trabajo-practica">📘 Guía de Trabajo – Práctica</h2>
<p><strong>Unidad :</strong> Infraestructura de servidores</p>
<p><strong>Práctica:</strong> Diseño de Rack de Servidores Basado en Normativas de Centrnsrur de Datosmensionamiento Eléctrico, UPS y Densii</p>

<hr>

<h2 id="competencia">1️ Competencia a desarrollar</h2>
<p>
  stron
    ic e un <strong>
    Diseña la arquitectura físAnaliza el consumo eléctrico y térmicao de un rack de servidores aplicando estándares de centros de datos y buenas prácticas de ingeniería de infraestructura, justificando técnicamente la ubicación de equipos, gestión de energía, ventilación y cableadoa infraestructura de servidores para dimensionar circuitos eléctricos, autonomía de UPS y capacidad de rack, justificando decisiones técnicas mediante cálculos de potencia, amperaje y densidad térmica.
  </strong>
</p>

<hr>

<h2 id="contexto">2️ Contexto de la práctica (escenario)</h2>

<p>
  Una organización planea implementar una infraestructura de servidores en un rack estándar de 42U<strong>pequeña sala de infraestructura TI</strong> para soportar <strong>servicios críticos del negociointernos críticos</strong>.
</p>

<p>
  El equipo de infraestructura ha definido el hardwarelos equipos principales que serán instalado, pero no existe aún un diseño físico del rack.
</p>

<p>
  El área de TI solicita a un Analista de Infraestructura diseñar la distribución del rack considerando:
</p>

<ul>
  <li>seguridad</li>
  <li>estabis en un <strong>rack estándar de 42U</strong>, pero aún no se ha realidzad mecánica</li>
  <li>distribución eléctrica</li>
  <li>flujo de aire</li>
  <li>gestión de cableado</li>
  <li>buenas prácticas de centros de datos</li>
</ul>

<p>El diseño deberá basarse en estándares de la industrio el análisis eléctrico ni térmico del sistema.
</p>

<p><strong>Equipos disponibles para el rackprevistos:</strong></p>

<table>
  <thead>
    <tr>
      <th>Equiplemento</th>
      <th>Modelo sugerido</th>
      <th>Notas de configuración</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Servidor de aplicaciones</td>
      <td>HPE ProLiant DL380 Gen11</td>
      <td>Fuentes redundantes Platinum</td>
    </tr>
    <tr>
      <td>Servidor de base de datos</td>
      <td>Dell PowerEdge R760</td>
      <td>Configuración de alto rendimiento (NVMe)</td>
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
  <li>Cable Managersdor de arcios<td>
      <>re  nterrise</t>
    </li>
  <li>Brush Panels</li>
  <li>Blank Panels</li>
  <li>KVM Switch</li>
  <li>Console Drawer    <td>vidor e alicaciones</>
      <> roiant  en</>
    </</li>
  <liU</l<p><strong>Rack disponible:</strong><br>
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
  <li>🚫 No ignorar los elementos de infraestructura  <td>Configuración High Availability</td>
    </tr>
    <tr>
      <td>Switch de red (PoE)</td>
      <td>Cisco Catalyst 9300-48P</td>
      <td>Incluye carga completa de dispositivos PoE+</td>
    </tr>
    <tr>
      <td>Firewall (NGFW)</td>
      <td>FortiGate 100F</td>
      <td>Procesadores ASIC SPU</td>
    </tr>
    <tr>
      <td>Almacenamiento (SAN)</td>
      <td>Dell PowerStore 1200T</td>
      <td>Sistema All-Flash</td>
    </tr>
  </tbody>
</table>

<p>La infraestructura se instalará en un rack estándar de <strong>42U</strong> con:</p>
<ul>
  <li>circuito eléctrico dedicado</li>
  <li>distribución eléctrica mediante PDU</li>
  <li>sistema de respaldo eléctrico mediante UPS</li>
  <li>sistema de ventilación controlada</li>
</ul>

<hr>

<h3 id="seleccion-ups">Selección del UPS</h3>
<p>
  El estudiante deberá seleccionar uno de los siguientes UPS empresariales para realizar los cálculos de autonomía y carga térmica.
</p>

<table>
  <thead>
    <tr>
      <th>Modelo UPS</th>
      <th>Tipo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>APC Smart-UPS SRT 5000VA (SRT5KRMXLT)</td>
      <td>Online Double Conversion</td>
    </tr>
    <tr>
      <td>Eaton 9PX 6kVA</td>
      <td>Online Double Conversion</td>
    </tr>
    <tr>
      <td>Vertiv Liebert GXT5 6kVA</td>
      <td>Online Double Conversion</td>
    </tr>
  </tbody>
</table>

<hr>

<h3 id="importante">Importante</h3>
<p>Antes de realizar los cálculos, el estudiante deberá investigar en documentación técnica:</p>
<ul>
  <li>potencia máxima (Watts)</li>
  <li>disipación térmica (BTU/h)</li>
  <li>tamaño en rack (U)</li>
  <li>especificaciones del UPS</li>
</ul>

<p><strong>Fuentes recomendadas:</strong></p>
<ul>
  <li>datasheets oficiales del fabricante</li>
  <li>documentación técnica del producto</li>
  <li>manuales de instalación</li>
</ul>

<hr>

<h3 id="rol-estudiante">Rol del estudiante</h3>
<p>El estudiante asume el rol de <strong>Analista de Infraestructura</strong>, responsable de:</p>
<ul>
  <li>investigar consumo eléctrico del hardware</li>
  <li>calcular carga eléctrica total</li>
  <li>calcular amperaje requerido</li>
  <li>evaluar capacidad del circuito eléctrico</li>
  <li>estimar autonomía del UPS</li>
  <li>calcular carga térmica del rack</li>
  <li>determinar densidad térmica</li>
  <li>diseñar distribución física del rack</li>
</ul>

<hr>

<h2 id="desempenos">3️⃣ Desempeños esperados (observables)</h2>
<p>El estudiante demuestra competencia cuando:</p>
<ul>
  <li>✔ Investiga correctamente especificaciones de hardware empresarial.</li>
  <li>✔ Calcula la carga eléctrica total del rack.</li>
  <li>✔ Determina amperaje requerido del circuito.</li>
  <li>✔ Evalúa seguridad eléctrica aplicando la regla del 80 %.</li>
  <li>✔ Calcula autonomía aproximada del UPS.</li>
  <li>✔ Calcula la carga térmica total del rack.</li>
  <li>✔ Determina densidad térmica del rack.</li>
  <li>✔ Diseña una distribución física coherente del rack.</li>
</ul>

<hr>

<h2 id="actividades">4️⃣ Actividades guiadas</h2>

<h3 id="actividad-1">🧪 Actividad 1 – Investigación técnica del hardware</h3>
<p><strong>Objetivo:</strong> Identificar las características eléctricas, térmicas y físicas de los equipos para realizar el dimensionamiento eléctrico y térmico.</p>

<p><strong>Concepto técnico:</strong> Los servidores y equipos de red generan consumo eléctrico y calor. Estos valores permiten dimensionar:</p>
<ul>
  <li>circuitos eléctricos</li>
  <li>UPS</li>
  <li>refrigeración</li>
  <li>espacio en el rack</li>
</ul>

<p><strong>Paso 1 – Investigación:</strong> Investigue en documentación técnica:</p>
<ul>
  <li>potencia máxima (W)</li>
  <li>disipación térmica (BTU/h)</li>
  <li>tamaño en rack (U)</li>
</ul>

<p><strong>Paso 2 – Completar tabla:</strong></p>
<table>
  <thead>
    <tr>
      <th>Equipo</th>
      <th>Potencia Máxima (W)</th>
      <th>BTU/h</th>
      <th>Tamaño (U)</th>
      <th>Fuente</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Servidor aplicaciones</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Servidor base de datos</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Servidor archivos</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Switch</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>Firewall</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
    <tr><td>SAN</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>tabla completa</li>
  <li>fuentes técnicas consultadas</li>
</ul>

<hr>

<h3 id="actividad-2">🧪 Actividad 2 – Investigación del UPS</h3>
<p><strong>Objetivo:</strong> Seleccionar el UPS y obtener sus características técnicas.</p>

<p><strong>Concepto técnico:</strong> Los UPS de centros de datos utilizan tecnología <strong>Online Double Conversion</strong>, que protege los equipos frente a:</p>
<ul>
  <li>interrupciones eléctricas</li>
  <li>variaciones de voltaje</li>
  <li>ruido eléctrico</li>
</ul>

<p><strong>Paso 1 – Seleccionar UPS:</strong> Seleccione uno de los siguientes modelos:</p>
<ul>
  <li>APC Smart-UPS SRT 5000VA</li>
  <li>Eaton 9PX 6kVA</li>
  <li>Vertiv Liebert GXT5 6kVA</li>
</ul>

<p><strong>Paso 2 – Investigar características:</strong></p>
<table>
  <thead>
    <tr>
      <th>Característica</th>
      <th>Valor</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Modelo seleccionado</td><td>&nbsp;</td></tr>
    <tr><td>Capacidad VA</td><td>&nbsp;</td></tr>
    <tr><td>Capacidad W</td><td>&nbsp;</td></tr>
    <tr><td>Eficiencia</td><td>&nbsp;</td></tr>
    <tr><td>Disipación térmica</td><td>&nbsp;</td></tr>
    <tr><td>Tamaño rack (U)</td><td>&nbsp;</td></tr>
    <tr><td>Autonomía nominal aproximada</td><td>&nbsp;</td></tr>
    <tr><td>Fuente</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>especificaciones completas del UPS</li>
  <li>referencia del datasheet utilizado</li>
</ul>

<hr>

<h3 id="actividad-3">🧪 Actividad 3 – Cálculo de carga eléctrica total</h3>
<p><strong>Objetivo:</strong> Determinar la energía eléctrica que consumirá toda la infraestructura.</p>

<p><strong>Concepto técnico:</strong> La potencia total del rack es la suma del consumo de todos los equipos conectados. Esto permite dimensionar:</p>
<ul>
  <li>circuitos eléctricos</li>
  <li>UPS</li>
  <li>PDU</li>
</ul>

<p><strong>Paso 1 – Sumar potencias:</strong> Utilice los valores investigados en la Actividad 1.</p>

<p><strong>Fórmula:</strong></p>
<pre><code>Potencia total = suma de todos los equipos (Watts)</code></pre>

<p><strong>Paso 2 – Registrar resultado:</strong></p>
<pre><code>Carga eléctrica total = ______ W</code></pre>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>cálculo detallado</li>
  <li>potencia total del rack</li>
</ul>

<hr>

<h3 id="actividad-4">🧪 Actividad 4 – Cálculo de amperaje y evaluación del circuito</h3>
<p><strong>Objetivo:</strong> Determinar si el circuito eléctrico puede soportar la carga del rack.</p>

<p><strong>Concepto técnico:</strong> La corriente eléctrica se calcula mediante la relación entre potencia y voltaje.</p>

<pre><code>I = P / V</code></pre>

<p><strong>donde:</strong></p>
<ul>
  <li>I = corriente (A)</li>
  <li>P = potencia (W)</li>
  <li>V = voltaje (V)</li>
</ul>

<p><strong>Paso 1 – Calcular amperaje:</strong> El sistema utiliza 120V AC.</p>
<pre><code>Amperaje requerido = ______ A</code></pre>

<p><strong>Paso 2 – Aplicar la regla del 80 %:</strong> Las cargas continuas no deben superar el 80 % de la capacidad del circuito.</p>

<table>
  <thead>
    <tr>
      <th>Circuito</th>
      <th>Capacidad segura</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>15A</td><td>1440 W</td></tr>
    <tr><td>20A</td><td>1920 W</td></tr>
  </tbody>
</table>

<p><strong>Paso 3 – Evaluar el circuito:</strong></p>
<table>
  <thead>
    <tr>
      <th>Circuito</th>
      <th>Capacidad segura</th>
      <th>¿Soporta la carga?</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>15A</td><td>1440 W</td><td>&nbsp;</td></tr>
    <tr><td>20A</td><td>1920 W</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>cálculo de amperaje</li>
  <li>evaluación de seguridad eléctrica</li>
</ul>

<hr>

<h3 id="actividad-5">🧪 Actividad 5 – Estimación de autonomía del UPS</h3>
<p><strong>Objetivo:</strong> Estimar el tiempo que el UPS podrá alimentar la infraestructura durante un corte eléctrico.</p>

<p><strong>Concepto técnico:</strong> La autonomía depende de la relación entre:</p>
<ul>
  <li>capacidad del UPS</li>
  <li>carga conectada</li>
</ul>

<p><strong>Paso 1 – Determinar carga conectada:</strong> Utilice el resultado de la Actividad 3.</p>
<pre><code>Carga total del rack = ______ W</code></pre>

<p><strong>Paso 2 – Determinar porcentaje de carga del UPS:</strong></p>
<pre><code>Porcentaje de carga = (Carga real / Capacidad UPS) × 100</code></pre>

<p><strong>Paso 3 – Estimar autonomía (aproximación):</strong></p>
<table>
  <thead>
    <tr>
      <th>Carga del UPS</th>
      <th>Autonomía aproximada</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>25 %</td><td>18 – 22 minutos</td></tr>
    <tr><td>50 %</td><td>10 – 12 minutos</td></tr>
    <tr><td>75 %</td><td>6 – 8 minutos</td></tr>
    <tr><td>100 %</td><td>3 – 5 minutos</td></tr>
  </tbody>
</table>

<pre><code>Autonomía estimada = ______ minutos</code></pre>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>cálculo de porcentaje de carga</li>
  <li>estimación de autonomía</li>
  <li>análisis de continuidad operativa</li>
</ul>

<hr>

<h3 id="actividad-6">🧪 Actividad 6 – Cálculo de carga térmica</h3>
<p><strong>Objetivo:</strong> Determinar la cantidad total de calor generado por el rack.</p>

<p><strong>Concepto técnico:</strong> La energía eléctrica consumida se transforma en calor. Conversión utilizada en ingeniería:</p>
<pre><code>1 W = 3.412 BTU/h</code></pre>

<p><strong>Paso 1 – Calcular carga térmica:</strong></p>
<pre><code>BTU/h = Watts × 3.412</code></pre>

<p><strong>Paso 2 – Registrar resultado:</strong></p>
<pre><code>Carga térmica total = ______ BTU/h</code></pre>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>cálculo de carga térmica total</li>
</ul>

<hr>

<h3 id="actividad-7">🧪 Actividad 7 – Análisis de densidad térmica del rack</h3>
<p><strong>Objetivo:</strong> Evaluar la concentración de calor dentro del rack.</p>

<p><strong>Paso 1 – Determinar espacio ocupado:</strong></p>
<table>
  <thead>
    <tr>
      <th>Equipo</th>
      <th>Tamaño (U)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Servidor aplicaciones</td><td>&nbsp;</td></tr>
    <tr><td>Servidor base datos</td><td>&nbsp;</td></tr>
    <tr><td>Servidor archivos</td><td>&nbsp;</td></tr>
    <tr><td>SAN</td><td>&nbsp;</td></tr>
    <tr><td>Switch</td><td>&nbsp;</td></tr>
    <tr><td>Firewall</td><td>&nbsp;</td></tr>
    <tr><td>UPS</td><td>&nbsp;</td></tr>
  </tbody>
</table>

<p><strong>Total U utilizadas:</strong></p>
<pre><code>Total U utilizadas = ______</code></pre>

<p><strong>Paso 2 – Calcular densidad térmica:</strong></p>
<pre><code>Densidad térmica = BTU total / U utilizadas
Densidad térmica = ______ BTU/U</code></pre>

<p><strong>Paso 3 – Interpretación:</strong></p>
<table>
  <thead>
    <tr>
      <th>Tipo de rack</th>
      <th>BTU/U</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Baja densidad</td><td>&lt; 300</td></tr>
    <tr><td>Media densidad</td><td>300 – 800</td></tr>
    <tr><td>Alta densidad</td><td>&gt; 800</td></tr>
  </tbody>
</table>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>cálculo de densidad térmica</li>
  <li>clasificación del rack</li>
</ul>

<hr>

<h3 id="actividad-8">🧪 Actividad 8 – Diseño del rack</h3>
<p><strong>Objetivo:</strong> Diseñar la distribución física del rack.</p>

<p><strong>Concepto técnico:</strong> Una correcta distribución mejora:</p>
<ul>
  <li>ventilación</li>
  <li>mantenimiento</li>
  <li>estabilidad</li>
</ul>

<p><strong>Paso 1 – Diseñar distribución:</strong> Considere:</p>
<ul>
  <li>UPS en la parte inferior</li>
  <li>equipos pesados abajo</li>
  <li>equipos de red arriba</li>
  <li>espacio para ventilación</li>
</ul>

<p><strong>Paso 2 – Crear diagrama:</strong> Puede utilizar herramientas open-source como:</p>  
<ul>  
<li>  
Rackula:  
<a  href="https://github.com/RackulaLives/Rackula">https://github.com/RackulaLives/Rackula</a>  
</li>  
<li>  
NetBox:  
<a  href="https://github.com/netbox-community/netbox">https://github.com/netbox-community/netbox</a>  
</li>  
</ul>

<p><strong>Resultado esperado:</strong> El estudiante debe entregar:</p>
<ul>
  <li>diagrama del rack</li>
  <li>justificación técnica de la distribución</li>
</ul>

<hr>

<h2 id="evidencia">5️⃣ Evidencia a entregar</h2>
<p><strong>Archivo obligatorio:</strong></p>
<pre><code>practica_6/
   └── dimensionamiento_electrico_rack.md</code></pre>

<p><strong>El archivo debe contener:</strong></p>
<ol>
  <li>Investigación de consumo eléctrico</li>
  <li>Investigación del UPS</li>
  <li>Cálculo de carga eléctrica total</li>
  <li>Cálculo de amperaje del circuito</li>
  <li>Evaluación del circuito eléctrico</li>
  <li>Cálculo de autonomía del UPS</li>
  <li>Cálculo de carga térmica</li>
  <li>Densidad térmica del rack</li>
  <li>Diagrama del rack</li>
  <li>Justificación técnica final</li>
</ol>

<hr>

<h2 id="criterios">6️⃣ Criterios de evaluación</h2>
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
      <td>Investigación técnica</td>
      <td>Completa y confiable</td>
      <td>Parcial</td>
      <td>Incorrecta</td>
    </tr>
    <tr>
      <td>Cálculo eléctrico</td>
      <td>Correcto</td>
      <td>Parcial</td>
      <td>Incorrecto</td>
    </tr>
    <tr>
      <td>Cálculo UPS</td>
      <td>Correcto</td>
      <td>Aproximado</td>
      <td>Incorrecto</td>
    </tr>
    <tr>
      <td>Cálculo térmico</td>
      <td>Correcto</td>
      <td>Parcial</td>
      <td>Incorrecto</td>
    </tr>
    <tr>
      <td>Densidad de rack</td>
      <td>Bien calculada</td>
      <td>Parcial</td>
      <td>Incorrecta</td>
    </tr>
    <tr>
      <td>Diseño del rack</td>
      <td>Coherente</td>
      <td>Poco claro</td>
      <td>Incoherente</td>
    </tr>
  </tbody>
</table>

<hr>

<h2 id="restricciones">7️⃣ Restricciones</h2>
<ul>
  <li>🚫 No modificar los equipos del escenario.</li>
  <li>🚫 No agregar hardware adicional.</li>
</ul>
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNTI5NTc1MzJdfQ==
-->