<hr>
<h1 id="ifs0-practicas-analisis-requerimientos-infraestructura-servidores">
  IFS0 – Prácticas de Infraestructura de Servidores
</h1>

<h2 id="guia-trabajo-practica-3">📘 Guía de Trabajo – Práctica 3</h2>
<p><strong>Unidad 1:</strong> Infraestructura de servidores</p>
<p><strong>Práctica:</strong> Diseño Conceptual de Infraestructura de Servidores</p>

<hr>

<h2 id="competencia">1️⃣ Competencia a desarrollar</h2>
<p>
  <strong>
    Elabora un esquema conceptual de infraestructura de servidores a partir de requerimientos priorizados,
    utilizando diagramas lógicos y justificando decisiones de diseño sin considerar marcas ni configuraciones específicas.
  </strong>
</p>

<hr>


<h2 id="relacion-clase">2️⃣ Contexto de la práctica (escenario)</h2>

<p>
  Una <strong>empresa de servicios profesionales</strong>, con <strong>25 empleados</strong>, utiliza un sistema interno
  para apoyar sus actividades administrativas y operativas diarias.
</p>

<p>El sistema debe permitir principalmente:</p>
<ul>
  <li>Almacenamiento y consulta centralizada de documentos administrativos</li>
  <li>Acceso compartido a información entre distintas áreas de la empresa</li>
  <li>Registro y consulta de información básica de clientes y proyectos</li>
</ul>

<p>Para efectos de esta práctica, se consideran los siguientes <strong>requerimientos funcionales</strong>:</p>
<ul>
  <li>Acceso centralizado a la información desde los equipos de trabajo de los empleados</li>
  <li>Acceso simultáneo de múltiples usuarios sin afectar el funcionamiento del sistema</li>
  <li>Disponibilidad del sistema durante la jornada laboral</li>
</ul>

<p>Asimismo, el sistema debe cumplir con los siguientes <strong>requerimientos no funcionales</strong>:</p>
<ul>
  <li>Protección de la información contra accesos no autorizados</li>
  <li>Reducción del riesgo de pérdida de información</li>
  <li>Separación de componentes críticos para mejorar seguridad y confiabilidad</li>
  <li>Capacidad de crecimiento gradual sin rediseñar completamente la infraestructura</li>
</ul>

<p>La empresa presenta además las siguientes condiciones:</p>
<ul>
  <li>No cuenta con documentación técnica del sistema actual</li>
  <li>No dispone de personal especializado en tecnologías de información</li>
  <li>Los requerimientos del sistema ya fueron <strong>identificados, validados y priorizados</strong>
      en una etapa previa.</li>
</ul>

<p>
  El estudiante asume el rol de <strong>analista de infraestructura</strong>, encargado de
  <strong>seleccionar los roles de servidores necesarios</strong> y
  <strong>proponer un diseño conceptual de la infraestructura</strong> que permita visualizar
  cómo deberían organizarse los componentes del sistema,
  <strong>sin realizar implementación ni seleccionar tecnologías específicas</strong>.
</p>

<hr>


<h2 id="desempenos">3️⃣ Desempeños esperados</h2>
<ul>
  <li>Traduce requerimientos en <strong>componentes de infraestructura</strong></li>
  <li>Identifica roles de servidores adecuados</li>
  <li>Propone una arquitectura <strong>lógica por capas</strong></li>
  <li>Representa el diseño mediante diagramas</li>
  <li>Justifica decisiones de diseño a nivel conceptual</li>
</ul>

<hr>

<h2 id="actividades">4️⃣ Actividades guiadas</h2>

<h3 id="actividad-1">🧪 Actividad 1 – Identificación de componentes de infraestructura</h3>
<ol>
  <li>Liste los <strong>requerimientos clave</strong> (mínimo 2).</li>
  <li>Para cada requerimiento identifique:
    <ul>
      <li>Rol del servidor necesario (Web, Aplicaciones, Base de Datos, etc.).</li>
    </ul>
  </li>
  <li>Justifique brevemente la selección de cada rol.</li>
</ol>
<p><strong>No incluir sistemas operativos, marcas ni tecnologías específicas.</strong></p>

<h3 id="actividad-2">🧪 Actividad 2 – Diseño conceptual de la arquitectura</h3>
<ol>
  <li>Organice los servidores en una <strong>arquitectura lógica por capas</strong>:
    <ul>
      <li>Capa de presentación</li>
      <li>Capa de aplicación</li>
      <li>Capa de datos</li>
    </ul>
  </li>
  <li>Defina:
    <ul>
      <li>Qué componentes estarán expuestos</li>
      <li>Qué componentes estarán protegidos en la red interna</li>
    </ul>
  </li>
</ol>

<h3 id="actividad-3">🧪 Actividad 3 – Diagrama de infraestructura</h3>
<ol>
  <li>Elabore un <strong>diagrama lógico de infraestructura</strong> utilizando:
    <ul>
      <li>Mermaid</li>
      <li>o una herramienta de diagramación (Draw.io, Network Notepad, etc.)</li>
    </ul>
  </li>
  <li>El diagrama debe mostrar:
    <ul>
      <li>Usuarios o sucursales</li>
      <li>Conectividad</li>
      <li>Servidores por rol</li>
      <li>Flujo general de comunicación</li>
    </ul>
  </li>
</ol>
<p><strong>El diagrama debe ser claro, legible y coherente, no decorativo.</strong></p>

<hr>

<h2 id="evidencia">5️⃣ Evidencia a entregar</h2>

<p><strong>Archivo único:</strong></p>
<p><code>practica_3/diseno_conceptual_infraestructura.md</code></p>

<p><strong>Contenido mínimo esperado:</strong></p>
<ol>
  <li>Introducción al escenario</li>
  <li>Requerimientos considerados</li>
  <li>Lista de servidores por rol</li>
  <li>Diagrama de infraestructura (Mermaid o imagen)</li>
  <li>Justificación técnica del diseño</li>
</ol>

<hr>

<h2 id="entrega-github">6️⃣ Entrega en GitHub</h2>
<pre><code>IFS0-practicas/
└── practica_3/
    └── diseno_conceptual_infraestructura.md
</code></pre>
<hr>

<h2 id="criterios">7️⃣ Criterios de evaluación (referencia)</h2>
<ul>
  <li>Coherencia entre requerimientos y diseño</li>
  <li>Correcta identificación de roles de servidor</li>
  <li>Uso adecuado de arquitectura por capas</li>
  <li>Claridad del diagrama</li>
</ul>

<hr>

<h2 id="errores">🚫 Errores que evitar en la práctica</h2>
<ul>
  <li>❌ Uso de marcas o modelos</li>
  <li>❌ Configuraciones técnicas detalladas</li>
  <li>❌ Comandos o instalación</li>
  <li>❌ Diseño sin relación con requerimientos</li>
</ul>
