<hr>
<h1 id="ifs0-practicas-conversion-requerimientos-infraestructura">
  IFS0 – Prácticas de Infraestructura de Seridores
</h1>

<h2 id="guia-trabajo-practica-5">📘 Guía de Trabajo – Práctica 5</h2>
<p><strong>Unidad 2:</strong> Diseño de infraestructura física</p>
<p><strong>Práctica:</strong> Conversión de Requerimientos a Infraestructura Física</p>

<hr>

<h2 id="competencia">1️⃣ Competencia a desarrollar</h2>
<p>
  <strong>
    Elabora un diseño de infraestructura de servidores a partir de requerimientos funcionales y no funcionales previamente validados, traduciendo necesidades del negocio en roles de servidor y componentes físicos, justificando decisiones técnicas sin realizar implementación.
  </strong>
</p>

<hr>

<h2 id="contexto">2️⃣ Contexto de la práctica (escenario)</h2>

<p>
  Una <strong>empresa de servicios profesionales</strong>, con <strong>25 empleados</strong>, utiliza un sistema interno
  para apoyar sus actividades administrativas y operativas diarias.
</p>

<p>El sistema debe permitir principalmente:</p>
<ul>
  <li>Almacenamiento y consulta centralizada de documentos administrativos.</li>
  <li>Acceso compartido a información entre distintas áreas.</li>
  <li>Registro y consulta de información básica de clientes y proyectos.</li>
</ul>

<p><strong>Requerimientos funcionales:</strong></p>
<ul>
  <li>Acceso centralizado a la información.</li>
  <li>Acceso simultáneo de múltiples usuarios.</li>
  <li>Disponibilidad durante la jornada laboral.</li>
</ul>

<p><strong>Requerimientos no funcionales:</strong></p>
<ul>
  <li>Protección contra accesos no autorizados.</li>
  <li>Reducción del riesgo de pérdida de información.</li>
  <li>Separación de componentes críticos.</li>
  <li>Capacidad de crecimiento gradual.</li>
</ul>

<p><strong>Condiciones adicionales y restricciones:</strong></p>
<ul>
  <li>No existe documentación técnica previa ni personal TI especializado.</li>
</ul>
<p><strong>Restricciones:</strong> No se implementa, no se seleccionan marcas y no se detallan configuraciones específicas.</li>


<hr>

<h2 id="actividades">3️⃣ Actividades</h2>

<h3 id="actividad-1">🧪 Actividad 1 – Matriz de Conversión Técnica</h3>
<p>Construya una tabla donde convierta cada requerimiento en atributos técnicos y componentes físicos impactados.</p>

<table>
  <thead>
    <tr>
      <th>Requerimiento</th>
      <th>Atributo Técnico</th>
      <th>Componente Físico</th>
      <th>Decisión Conceptual</th>
      <th>Riesgo si no se implementa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
  </tbody>
</table>

<p><strong>Debe incluir al menos los siguientes componentes:</strong> CPU, RAM, RAID, NIC, PSU (Energía) y Chasis/Expansión.</p>

<h3 id="actividad-2">🧪 Actividad 2 – Selección de Roles de Servidor</h3>
<p>Determine la necesidad de servidores de archivos, aplicaciones y bases de datos. Defina si conviene separar o consolidar roles.</p>

<table>
  <thead>
    <tr>
      <th>Rol de Servidor</th>
      <th>Justificación técnica</th>
      <th>Requerimientos que atiende</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
  </tbody>
</table>
<p><strong>Nota:</strong> No mencionar tecnologías ni sistemas operativos.</p>

<h3 id="actividad-3">🧪 Actividad 3 – Análisis de Componentes Físicos</h3>
<p>Para cada servidor propuesto, describa conceptualmente:</p>
<ul>
  <li><strong>CPU:</strong> Enfoque en concurrencia o carga específica.</li>
  <li><strong>RAM:</strong> Relación con procesos simultáneos.</li>
  <li><strong>Almacenamiento:</strong> Tipo de RAID conceptual, número mínimo de discos y riesgo en modo degradado.</li>
  <li><strong>Red:</strong> Cantidad de NICs y estrategia de segmentación.</li>
  <li><strong>Energía:</strong> ¿Fuente única o redundante?</li>
</ul>

<h3 id="actividad-4">🧪 Actividad 4 – Identificación de SPOF (Punto Único de Falla)</h3>
<table>
  <thead>
    <tr>
      <th>Componente</th>
      <th>¿Es SPOF?</th>
      <th>Mitigación Conceptual</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
  </tbody>
</table>

<hr>

<h2 id="evidencia">5️⃣ Evidencia a entregar</h2>
<p><strong>Archivo único obligatorio:</strong> <code>practica_5/conversion_requerimientos_a_infraestructura.md</code></p>

<p>El archivo debe contener:</p>
<ol>
  <li>Introducción al escenario.</li>
  <li>Matriz de conversión completa.</li>
  <li>Roles de servidor seleccionados.</li>
  <li>Análisis físico de cada servidor.</li>
  <li>Identificación de SPOF.</li>
  <li>Diagrama conceptual (Mermaid o imagen).</li>
  <li>Justificación técnica final.</li>
</ol>

<hr>

<h2 id="errores">🚫 Errores que evitar en la práctica</h2>
<ul>
  <li>❌ Uso de marcas (Dell, HP, Cisco) o modelos específicos.</li>
  <li>❌ Mencionar sistemas operativos (Windows, Linux) o software específico.</li>
  <li>❌ Diseñar sin alineación a los requerimientos del escenario de 25 empleados.</li>
</ul>
