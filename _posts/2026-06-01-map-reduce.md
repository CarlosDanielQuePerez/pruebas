---
title: "MapReduce: Procesamiento de Grandes Datos"
layout: post
permalink: /map-reduce/
theme: moon
number: 995
label: "Presentación"
---

<!-- SLIDE 1: Portada -->
<section data-background-gradient="linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%)">
    <h2>Presentación</h2>
    <h3 style="font-size: 1.1em; line-height: 1.2;">MapReduce: Procesamiento de Grandes Volúmenes de Datos</h3>
    <p style="font-size: 0.65em; color: #f97316;">Modelo de Programación Paralela para Big Data</p>
    <br>
    <p style="font-size: 0.5em; color: #94a3b8;">
        Cloud Data Processing — Verano 2026<br>
        Emmanuel Garcia Peñaloza<br>
        David Emanuel Jauregui Aban<br>      
        Universidad del Caribe<br>      
    </p>
</section>

<!-- SLIDE 2: ¿Qué es MapReduce? -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #f97316; font-size: 1.1em;">¿Qué es MapReduce?</h2>
    <div style="display: flex; align-items: center; justify-content: center; gap: 1.5em; margin-top: 0.5em;">
        <div style="flex: 1; text-align: center;">
            <img src="{{ site.baseurl }}/images/mapreduce/clusters.jpg" alt="Cluster de servidores procesando datos en paralelo" style="max-height: 32vh; width: auto; border-radius: 12px; border: 1px solid rgba(249,115,22,0.3);">
        </div>
        <div style="flex: 1; text-align: left;">
            <div class="highlight-box" style="border-left-color: #f97316; font-size: 0.6em;">
                Un <strong>modelo de programación</strong> y framework para procesar <strong>grandes volúmenes de datos</strong> de forma paralela en un cluster de computadoras.
            </div>
            <p style="font-size: 0.55em; margin-top: 0.6em; color: #cbd5e1;">
                La estrategia definitiva de<br><strong style="color: #f97316; font-size: 1.3em;">"Divide y Vencerás"</strong>
            </p>
            <p style="font-size: 0.42em; color: #64748b; margin-top: 0.3em;">Popularizado por Google para indexar la web.</p>
        </div>
    </div>
</section>

<!-- SLIDE 3: Las dos operaciones clave -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #f97316; font-size: 1.1em;">Dos Operaciones Fundamentales</h2>
    <div style="display: flex; gap: 1.5em; margin-top: 1em; align-items: stretch;">
        <!-- MAP -->
        <div style="flex: 1; background: rgba(249,115,22,0.08); border: 1px solid rgba(249,115,22,0.3); border-radius: 16px; padding: 1em; text-align: center;">
            <h3 style="color: #f97316; font-size: 0.9em; margin: 0.2em 0;">MAP</h3>
            <p style="font-size: 0.48em; color: #e2e8f0; margin: 0.2em 0;">(Mapear)</p>
            <hr style="border-color: rgba(249,115,22,0.3); margin: 0.4em 0;">
            <p style="font-size: 0.5em; color: #cbd5e1; text-align: left;">
                Cada nodo toma un fragmento de datos y lo transforma en <strong style="color: #f97316;">parejas clave-valor</strong>.
            </p>
            <div style="font-size: 0.45em; color: #94a3b8; margin-top: 0.4em; font-family: monospace; background: rgba(0,0,0,0.3); padding: 0.4em; border-radius: 6px;">
                entrada &rarr; [clave, valor]
            </div>
        </div>
        <!-- Flecha central -->
        <div style="display: flex; flex-direction: column; align-items: center; justify-content: center; font-size: 2em; color: #475569;">
            &rarr;
        </div>
        <!-- REDUCE -->
        <div style="flex: 1; background: rgba(74,222,128,0.08); border: 1px solid rgba(74,222,128,0.3); border-radius: 16px; padding: 1em; text-align: center;">
            <h3 style="color: #4ade80; font-size: 0.9em; margin: 0.2em 0;">REDUCE</h3>
            <p style="font-size: 0.48em; color: #e2e8f0; margin: 0.2em 0;">(Reducir)</p>
            <hr style="border-color: rgba(74,222,128,0.3); margin: 0.4em 0;">
            <p style="font-size: 0.5em; color: #cbd5e1; text-align: left;">
                Se combinan todos los valores de la misma clave para obtener el <strong style="color: #4ade80;">resultado final</strong>.
            </p>
            <div style="font-size: 0.45em; color: #94a3b8; margin-top: 0.4em; font-family: monospace; background: rgba(0,0,0,0.3); padding: 0.4em; border-radius: 6px;">
                [clave, [v1,v2,...]] &rarr; resultado
            </div>
        </div>
    </div>
</section>

<!-- SECCIÓN: Analogía de la Cocina -->
<section>
    <!-- SLIDE 4: La Analogía -->
    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h2 style="color: #facc15; font-size: 1.1em;">La Analogía: La Cocina del Banquete</h2>
        <p style="font-size: 0.5em; color: #94a3b8; margin-top: -0.3em;">Imagina una montaña gigante de verduras para un banquete</p>
        <div style="display: flex; gap: 1.5em; margin-top: 0.6em; align-items: center;">
            <div style="flex: 1.2; text-align: center;">
                <img src="{{ site.baseurl }}/images/mapreduce/cocineros.jpg" alt="Equipo de cocineros trabajando en paralelo" style="max-height: 30vh; width: auto; border-radius: 12px; border: 1px solid rgba(250,204,21,0.3);">
            </div>
            <div style="flex: 1; text-align: left;">
                <div style="background: rgba(250,204,21,0.08); border-radius: 12px; padding: 0.6em; margin-bottom: 0.4em;">
                    <p style="font-size: 0.5em; margin: 0; color: #fef08a;">
                        <strong>1 cocinero solo</strong> &rarr; <strong style="color: #ef4444;">Días</strong>
                    </p>
                </div>
                <div style="background: rgba(74,222,128,0.08); border-radius: 12px; padding: 0.6em;">
                    <p style="font-size: 0.5em; margin: 0; color: #bbf7d0;">
                        <strong>Equipo coordinado</strong> &rarr; <strong style="color: #4ade80;">Minutos</strong>
                    </p>
                </div>
                <p style="font-size: 0.45em; color: #94a3b8; margin-top: 0.6em; text-align: center;">
                    Eso es <strong style="color: #facc15;">MapReduce</strong>:<br>dividir el trabajo entre muchos.
                </p>
            </div>
        </div>
    </section>

    <!-- SLIDE 5: Fase 1 — MAP -->
    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #f97316; font-size: 1em;">Fase 1: Mapeo (Map)</h3>
        <p style="font-size: 0.48em; color: #94a3b8; margin-top: -0.3em;">"Cada cocinero pica su saco y grita qué tiene"</p>
        <div style="display: flex; gap: 1em; margin-top: 0.6em;">
            <div style="flex: 1.5;">
                <div class="diagram-box" style="padding: 0.6em; font-size: 1em;">
                    <pre style="background: transparent; box-shadow: none; margin: 0; font-family: monospace; font-size: 0.7em; line-height: 1.3; white-space: pre; color: #e2e8f0;">
   Datos Brutos
   ━━━━━━━━━━━━━━
        |
   ┌────┼────┐
   v    v    v
 ┌───┐┌───┐┌───┐
 │PC1││PC2││PC3│  <- Nodos del cluster
 └─┬─┘└─┬─┘└─┬─┘
   |    |    |
   v    v    v
 [A,1][B,1][A,1]  <- Parejas clave-valor</pre>
                </div>
            </div>
            <div style="flex: 1; text-align: left; display: flex; flex-direction: column; justify-content: center;">
                <div class="highlight-box" style="border-left-color: #f97316; font-size: 0.55em;">
                    Los datos se <strong>dividen en fragmentos</strong> y cada computadora procesa su parte de forma <strong style="color: #f97316;">independiente</strong>.
                </div>
                <p style="font-size: 0.45em; color: #94a3b8; margin-top: 0.4em;">
                    Resultado: millones de parejas<br><code style="color: #f97316;">[clave, valor]</code>
                </p>
            </div>
        </div>
    </section>

    <!-- SLIDE 6: Fase 2 — SHUFFLE -->
    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #a78bfa; font-size: 1em;">Fase 2: Mezcla (Shuffle &amp; Sort)</h3>
        <p style="font-size: 0.48em; color: #94a3b8; margin-top: -0.3em;">"Todos los tomates al Cocinero A, todas las cebollas al Cocinero B"</p>
        <div style="display: flex; gap: 1em; margin-top: 0.6em;">
            <div style="flex: 1.5;">
                <div class="diagram-box" style="padding: 0.6em; font-size: 1em;">
                    <pre style="background: transparent; box-shadow: none; margin: 0; font-family: monospace; font-size: 0.7em; line-height: 1.3; white-space: pre; color: #e2e8f0;">
 [A,1] [B,1] [A,1] [C,1] [B,1]
   |     |     |     |     |
   └──┐  |  ┌──┘     |  ┌──┘
      v  |  v        v  v
   ┌─────┐ ┌─────┐ ┌─────┐
   │ A,A │ │ B,B │ │  C  │
   └─────┘ └─────┘ └─────┘
   Grupo A  Grupo B  Grupo C</pre>
                </div>
            </div>
            <div style="flex: 1; text-align: left; display: flex; flex-direction: column; justify-content: center;">
                <div class="highlight-box" style="border-left-color: #a78bfa; font-size: 0.55em;">
                    El sistema <strong>agrupa automáticamente</strong> todas las claves iguales antes de enviarlas al siguiente paso.
                </div>
                <p style="font-size: 0.45em; color: #94a3b8; margin-top: 0.4em;">
                    Este paso es <strong style="color: #a78bfa;">transparente</strong> para el programador.
                </p>
            </div>
        </div>
    </section>

    <!-- SLIDE 7: Fase 3 — REDUCE -->
    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #4ade80; font-size: 1em;">Fase 3: Reducción (Reduce)</h3>
        <p style="font-size: 0.48em; color: #94a3b8; margin-top: -0.3em;">"Cada cocinero cuenta su grupo y da el total"</p>
        <div style="display: flex; gap: 1em; margin-top: 0.6em;">
            <div style="flex: 1.5;">
                <div class="diagram-box" style="padding: 0.6em; font-size: 1em;">
                    <pre style="background: transparent; box-shadow: none; margin: 0; font-family: monospace; font-size: 0.7em; line-height: 1.3; white-space: pre; color: #e2e8f0;">
  ┌─────┐  ┌─────┐  ┌─────┐
  │ A,A │  │ B,B │  │  C  │
  └──┬──┘  └──┬──┘  └──┬──┘
     | SUM    | SUM    | SUM
     v        v        v
 ┌───────┐┌───────┐┌───────┐
 │ A = 50││ B = 30││ C = 20│
 └───────┘└───────┘└───────┘
         |        |
         └───┬────┘
             v
     Resultado Final</pre>
                </div>
            </div>
            <div style="flex: 1; text-align: left; display: flex; flex-direction: column; justify-content: center;">
                <div class="highlight-box" style="border-left-color: #4ade80; font-size: 0.55em;">
                    Se toman los datos agrupados, se <strong>combinan</strong> (suman, promedian, filtran) y se genera el <strong style="color: #4ade80;">resultado final</strong>.
                </div>
            </div>
        </div>
    </section>
</section>

<!-- SLIDE 8: Flujo completo -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #f97316; font-size: 1em;">Flujo Completo de MapReduce</h2>
    <div style="margin-top: 0.5em; text-align: center;">
        <img src="{{ site.baseurl }}/images/mapreduce/esquema.png" alt="Diagrama de flujo completo de MapReduce: HDFS, Map, Shuffle, Reduce, Output" style="max-height: 42vh; width: auto; border-radius: 10px; border: 1px solid rgba(249,115,22,0.2); background: rgba(255,255,255,0.95); padding: 0.3em;">
    </div>
    <!-- Mini resumen visual de fases -->
    <div style="display: flex; gap: 0.3em; justify-content: center; align-items: center; margin-top: 0.6em;">
        <div style="background: rgba(249,115,22,0.15); border-radius: 10px; padding: 0.3em 0.7em; text-align: center;">
            <p style="font-size: 0.42em; margin: 0; color: #f97316; font-weight: bold;">Input</p>
        </div>
        <span style="color: #475569; font-size: 1em;">&rarr;</span>
        <div style="background: rgba(249,115,22,0.15); border-radius: 10px; padding: 0.3em 0.7em; text-align: center;">
            <p style="font-size: 0.42em; margin: 0; color: #f97316; font-weight: bold;">Split</p>
        </div>
        <span style="color: #475569; font-size: 1em;">&rarr;</span>
        <div style="background: rgba(249,115,22,0.15); border-radius: 10px; padding: 0.3em 0.7em; text-align: center;">
            <p style="font-size: 0.42em; margin: 0; color: #f97316; font-weight: bold;">Map</p>
        </div>
        <span style="color: #475569; font-size: 1em;">&rarr;</span>
        <div style="background: rgba(167,139,250,0.15); border-radius: 10px; padding: 0.3em 0.7em; text-align: center;">
            <p style="font-size: 0.42em; margin: 0; color: #a78bfa; font-weight: bold;">Shuffle</p>
        </div>
        <span style="color: #475569; font-size: 1em;">&rarr;</span>
        <div style="background: rgba(74,222,128,0.15); border-radius: 10px; padding: 0.3em 0.7em; text-align: center;">
            <p style="font-size: 0.42em; margin: 0; color: #4ade80; font-weight: bold;">Reduce</p>
        </div>
        <span style="color: #475569; font-size: 1em;">&rarr;</span>
        <div style="background: rgba(74,222,128,0.15); border-radius: 10px; padding: 0.3em 0.7em; text-align: center;">
            <p style="font-size: 0.42em; margin: 0; color: #4ade80; font-weight: bold;">Output</p>
        </div>
    </div>
</section>

<!-- SECCIÓN: ¿Por qué es importante? -->
<section>
    <!-- SLIDE 9: Tres pilares -->
    <section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
        <h2 style="color: #38bdf8; font-size: 1.1em;">¿Por qué es tan importante?</h2>
        <div style="display: flex; gap: 1.2em; margin-top: 1em;">
            <!-- Escalabilidad -->
            <div style="flex: 1; background: rgba(56,189,248,0.06); border: 1px solid rgba(56,189,248,0.2); border-radius: 16px; padding: 0.8em; text-align: center;">
                <h3 style="color: #38bdf8; font-size: 0.7em; margin: 0.3em 0;">Escalabilidad</h3>
                <hr style="border-color: rgba(56,189,248,0.2); margin: 0.3em 0;">
                <p style="font-size: 0.48em; color: #cbd5e1;">¿Más datos? Solo añade más computadoras al cluster.</p>
                <p style="font-size: 0.4em; color: #64748b;">No necesitas una supercomputadora costosa.</p>
            </div>
            <!-- Tolerancia a fallos -->
            <div style="flex: 1; background: rgba(74,222,128,0.06); border: 1px solid rgba(74,222,128,0.2); border-radius: 16px; padding: 0.8em; text-align: center;">
                <h3 style="color: #4ade80; font-size: 0.7em; margin: 0.3em 0;">Tolerancia a Fallos</h3>
                <hr style="border-color: rgba(74,222,128,0.2); margin: 0.3em 0;">
                <p style="font-size: 0.48em; color: #cbd5e1;">Si un nodo falla, su tarea se reasigna automáticamente.</p>
                <p style="font-size: 0.4em; color: #64748b;">Nadie pierde el trabajo.</p>
            </div>
            <!-- Eficiencia -->
            <div style="flex: 1; background: rgba(250,204,21,0.06); border: 1px solid rgba(250,204,21,0.2); border-radius: 16px; padding: 0.8em; text-align: center;">
                <h3 style="color: #facc15; font-size: 0.7em; margin: 0.3em 0;">Eficiencia</h3>
                <hr style="border-color: rgba(250,204,21,0.2); margin: 0.3em 0;">
                <p style="font-size: 0.48em; color: #cbd5e1;">Mueve el código hacia los datos, no los datos al código.</p>
                <p style="font-size: 0.4em; color: #64748b;">Minimiza tráfico de red.</p>
            </div>
        </div>
    </section>

    <!-- SLIDE 10: Escalabilidad Horizontal -->
    <section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
        <h3 style="color: #38bdf8; font-size: 1em;">Escalabilidad Horizontal</h3>
        <p style="font-size: 0.48em; color: #94a3b8; margin-top: -0.3em;">Añadir nodos, no potencia</p>
        <div style="display: flex; gap: 1.5em; margin-top: 0.6em; align-items: center;">
            <div style="flex: 1; text-align: center;">
                <img src="{{ site.baseurl }}/images/mapreduce/clusters.jpg" alt="Cluster de servidores en escalado horizontal" style="max-height: 28vh; width: auto; border-radius: 12px; border: 1px solid rgba(56,189,248,0.3);">
            </div>
            <div style="flex: 1;">
                <!-- Comparación visual -->
                <div style="background: rgba(239,68,68,0.08); border: 1px solid rgba(239,68,68,0.3); border-radius: 12px; padding: 0.6em; margin-bottom: 0.6em; text-align: center;">
                    <p style="font-size: 0.5em; margin: 0; color: #fca5a5;">
                        <strong>Vertical</strong> — Comprar una sola máquina más potente
                    </p>
                    <p style="font-size: 0.4em; margin: 0.2em 0 0; color: #94a3b8;">Costoso y con límites físicos</p>
                </div>
                <div style="background: rgba(74,222,128,0.08); border: 1px solid rgba(74,222,128,0.3); border-radius: 12px; padding: 0.6em; text-align: center;">
                    <p style="font-size: 0.5em; margin: 0; color: #bbf7d0;">
                        <strong>Horizontal</strong> — Añadir muchas máquinas estándar
                    </p>
                    <p style="font-size: 0.4em; margin: 0.2em 0 0; color: #94a3b8;">Económico e ilimitado en la práctica</p>
                </div>
            </div>
        </div>
    </section>
</section>

<!-- SLIDE 11: Ejemplo con Word Count -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #f97316; font-size: 1em;">Ejemplo Clásico: Conteo de Palabras</h2>
    <div style="margin-top: 0.5em;">
        <div class="diagram-box" style="padding: 0.5em; font-size: 1em;">
            <pre style="background: transparent; box-shadow: none; margin: 0; font-family: monospace; font-size: 0.65em; line-height: 1.4; white-space: pre; color: #e2e8f0;">
 Texto:  "hola mundo hola datos mundo hola"
 ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

 <span style="color: #f97316;">MAP</span>            <span style="color: #a78bfa;">SHUFFLE</span>          <span style="color: #4ade80;">REDUCE</span>

 [hola, 1]      hola  -> [1,1,1]  <span style="color: #4ade80;">hola  = 3</span>
 [mundo, 1]     mundo -> [1,1]    <span style="color: #4ade80;">mundo = 2</span>
 [hola, 1]      datos -> [1]      <span style="color: #4ade80;">datos = 1</span>
 [datos, 1]
 [mundo, 1]          Total: 6 palabras
 [hola, 1]</pre>
        </div>
    </div>
</section>

<!-- SLIDE 12: Ecosistema y Herramientas -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #38bdf8; font-size: 1em;">Ecosistema de Herramientas</h2>
    <p style="font-size: 0.45em; color: #94a3b8; margin-top: -0.3em;">¿Dónde se usa MapReduce?</p>
    <div style="display: flex; gap: 1.2em; margin-top: 0.8em; align-items: stretch;">
        <!-- Hadoop -->
        <div style="flex: 1; background: rgba(250,204,21,0.06); border: 1px solid rgba(250,204,21,0.2); border-radius: 16px; padding: 0.8em; text-align: center;">
            <img src="{{ site.baseurl }}/images/mapreduce/hadoop.jpg" alt="Logo de Apache Hadoop" style="max-height: 10vh; width: auto; border-radius: 8px; margin-bottom: 0.4em;">
            <h3 style="color: #facc15; font-size: 0.65em; margin: 0.2em 0;">Apache Hadoop</h3>
            <p style="font-size: 0.4em; color: #cbd5e1;">Framework original que implementó MapReduce. Procesa datos en <strong>disco</strong>.</p>
            <span class="badge" style="border-color: #facc15; background: rgba(250,204,21,0.15); color: #facc15;">Fundacional</span>
        </div>
        <!-- Spark -->
        <div style="flex: 1; background: rgba(249,115,22,0.06); border: 1px solid rgba(249,115,22,0.2); border-radius: 16px; padding: 0.8em; text-align: center;">
            <img src="{{ site.baseurl }}/images/mapreduce/spark.jpg" alt="Logo de Apache Spark" style="max-height: 10vh; width: auto; border-radius: 8px; margin-bottom: 0.4em;">
            <h3 style="color: #f97316; font-size: 0.65em; margin: 0.2em 0;">Apache Spark</h3>
            <p style="font-size: 0.4em; color: #cbd5e1;">Evolución moderna. Procesa en <strong>memoria RAM</strong>, hasta <strong style="color: #f97316;">100x más rápido</strong>.</p>
            <span class="badge" style="border-color: #f97316; background: rgba(249,115,22,0.15); color: #f97316;">Moderno</span>
        </div>
        <!-- Dataproc -->
        <div style="flex: 1; background: rgba(56,189,248,0.06); border: 1px solid rgba(56,189,248,0.2); border-radius: 16px; padding: 0.8em; text-align: center;">
            <img src="{{ site.baseurl }}/images/mapreduce/dataproc.png" alt="Logo de Google Cloud Dataproc" style="max-height: 10vh; width: auto; border-radius: 8px; margin-bottom: 0.4em;">
            <h3 style="color: #38bdf8; font-size: 0.65em; margin: 0.2em 0;">Google Cloud Dataproc</h3>
            <p style="font-size: 0.4em; color: #cbd5e1;">Hadoop/Spark gestionado en la nube. Clusters en <strong style="color: #38bdf8;">menos de 90 segundos</strong>.</p>
            <span class="badge" style="border-color: #38bdf8; background: rgba(56,189,248,0.15); color: #38bdf8;">Cloud</span>
        </div>
    </div>
</section>

<!-- SLIDE 13: Hadoop vs Spark -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #f97316; font-size: 1em;">Hadoop MapReduce vs Apache Spark</h2>
    <div style="display: flex; gap: 1.5em; margin-top: 0.6em; align-items: center;">
        <div style="flex: 1; text-align: center;">
            <img src="{{ site.baseurl }}/images/mapreduce/grafica.jpeg" alt="Gráfica de rendimiento Hadoop vs Spark" style="max-height: 30vh; width: auto; border-radius: 10px; border: 1px solid rgba(249,115,22,0.3); background: rgba(255,255,255,0.95); padding: 0.3em;">
        </div>
        <div style="flex: 1;">
            <table style="font-size: 0.4em; width: 100%;">
                <thead>
                    <tr>
                        <th>Criterio</th>
                        <th style="color: #facc15;">Hadoop MR</th>
                        <th style="color: #f97316;">Spark</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Almacenamiento</strong></td>
                        <td>Disco (HDFS)</td>
                        <td style="color: #4ade80;">Memoria RAM</td>
                    </tr>
                    <tr>
                        <td><strong>Velocidad</strong></td>
                        <td>Baseline</td>
                        <td style="color: #4ade80;">Hasta 100x más rápido</td>
                    </tr>
                    <tr>
                        <td><strong>Procesamiento</strong></td>
                        <td>Batch</td>
                        <td style="color: #4ade80;">Batch + Streaming</td>
                    </tr>
                    <tr>
                        <td><strong>Facilidad</strong></td>
                        <td>Java / verbose</td>
                        <td style="color: #4ade80;">Python / Scala / SQL</td>
                    </tr>
                    <tr>
                        <td><strong>Iteraciones</strong></td>
                        <td>Lee/escribe disco cada vez</td>
                        <td style="color: #4ade80;">Mantiene datos en RAM</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</section>

<!-- SLIDE 14: Casos de uso reales -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #38bdf8; font-size: 1em;">Casos de Uso en el Mundo Real</h2>
    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.7em; margin-top: 0.8em;">
        <div style="background: rgba(56,189,248,0.06); border: 1px solid rgba(56,189,248,0.15); border-radius: 14px; padding: 0.6em; text-align: left;">
            <p style="font-size: 0.5em; margin: 0; color: #38bdf8;"><strong>Google Search</strong></p>
            <p style="font-size: 0.38em; margin: 0.2em 0 0; color: #94a3b8;">Indexación de billones de páginas web para construir su motor de búsqueda.</p>
        </div>
        <div style="background: rgba(167,139,250,0.06); border: 1px solid rgba(167,139,250,0.15); border-radius: 14px; padding: 0.6em; text-align: left;">
            <p style="font-size: 0.5em; margin: 0; color: #a78bfa;"><strong>Redes Sociales</strong></p>
            <p style="font-size: 0.38em; margin: 0.2em 0 0; color: #94a3b8;">Análisis de grafos sociales, recomendaciones y procesamiento de feeds.</p>
        </div>
        <div style="background: rgba(250,204,21,0.06); border: 1px solid rgba(250,204,21,0.15); border-radius: 14px; padding: 0.6em; text-align: left;">
            <p style="font-size: 0.5em; margin: 0; color: #facc15;"><strong>E-Commerce</strong></p>
            <p style="font-size: 0.38em; margin: 0.2em 0 0; color: #94a3b8;">Sistemas de recomendación de productos basados en historial de compras.</p>
        </div>
        <div style="background: rgba(249,115,22,0.06); border: 1px solid rgba(249,115,22,0.15); border-radius: 14px; padding: 0.6em; text-align: left;">
            <p style="font-size: 0.5em; margin: 0; color: #f97316;"><strong>Análisis de Logs</strong></p>
            <p style="font-size: 0.38em; margin: 0.2em 0 0; color: #94a3b8;">Procesamiento de terabytes de registros de servidores para detectar anomalías.</p>
        </div>
        <div style="background: rgba(74,222,128,0.06); border: 1px solid rgba(74,222,128,0.15); border-radius: 14px; padding: 0.6em; text-align: left;">
            <p style="font-size: 0.5em; margin: 0; color: #4ade80;"><strong>Genómica y Ciencia</strong></p>
            <p style="font-size: 0.38em; margin: 0.2em 0 0; color: #94a3b8;">Análisis de secuencias de ADN y simulaciones científicas a gran escala.</p>
        </div>
        <div style="background: rgba(248,113,113,0.06); border: 1px solid rgba(248,113,113,0.15); border-radius: 14px; padding: 0.6em; text-align: left;">
            <p style="font-size: 0.5em; margin: 0; color: #f87171;"><strong>Servicios Financieros</strong></p>
            <p style="font-size: 0.38em; margin: 0.2em 0 0; color: #94a3b8;">Detección de fraudes en tiempo real analizando millones de transacciones.</p>
        </div>
    </div>
</section>

<!-- SLIDE 15: Línea de tiempo -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #a78bfa; font-size: 1em;">Evolución del Procesamiento de Grandes Datos</h2>
    <div style="text-align: center; margin: 0.5em 0;">
        <img src="{{ site.baseurl }}/images/mapreduce/timeline.png" alt="Línea de tiempo de la evolución del ecosistema Big Data" style="max-height: 22vh; width: auto; border-radius: 10px; border: 1px solid rgba(167,139,250,0.2); background: rgba(255,255,255,0.95); padding: 0.3em;">
    </div>
    <!-- Timeline simplificada con cajas -->
    <div style="display: flex; gap: 0.4em; justify-content: center; align-items: flex-end; margin-top: 0.4em;">
        <div style="text-align: center; flex: 1;">
            <div style="background: rgba(250,204,21,0.1); border: 1px solid rgba(250,204,21,0.3); border-radius: 10px; padding: 0.4em 0.3em;">
                <p style="font-size: 0.38em; margin: 0; color: #facc15;"><strong>2004</strong></p>
                <p style="font-size: 0.3em; margin: 0.1em 0 0; color: #94a3b8;">Google publica el paper de MapReduce</p>
            </div>
        </div>
        <div style="text-align: center; flex: 1;">
            <div style="background: rgba(250,204,21,0.1); border: 1px solid rgba(250,204,21,0.3); border-radius: 10px; padding: 0.4em 0.3em;">
                <p style="font-size: 0.38em; margin: 0; color: #facc15;"><strong>2006</strong></p>
                <p style="font-size: 0.3em; margin: 0.1em 0 0; color: #94a3b8;">Apache Hadoop se lanza como open-source</p>
            </div>
        </div>
        <div style="text-align: center; flex: 1;">
            <div style="background: rgba(249,115,22,0.1); border: 1px solid rgba(249,115,22,0.3); border-radius: 10px; padding: 0.4em 0.3em;">
                <p style="font-size: 0.38em; margin: 0; color: #f97316;"><strong>2014</strong></p>
                <p style="font-size: 0.3em; margin: 0.1em 0 0; color: #94a3b8;">Apache Spark supera a Hadoop en benchmarks</p>
            </div>
        </div>
        <div style="text-align: center; flex: 1;">
            <div style="background: rgba(56,189,248,0.1); border: 1px solid rgba(56,189,248,0.3); border-radius: 10px; padding: 0.4em 0.3em;">
                <p style="font-size: 0.38em; margin: 0; color: #38bdf8;"><strong>Hoy</strong></p>
                <p style="font-size: 0.3em; margin: 0.1em 0 0; color: #94a3b8;">Servicios gestionados en la nube (Dataproc, EMR)</p>
            </div>
        </div>
    </div>
</section>

<!-- SLIDE 16: Resumen visual -->
<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #f97316; font-size: 1em;">Resumen: MapReduce en una Diapositiva</h2>
    <div style="display: flex; gap: 1.5em; margin-top: 0.6em; align-items: center;">
        <!-- Lado izquierdo: Esquema -->
        <div style="flex: 1; text-align: center;">
            <img src="{{ site.baseurl }}/images/mapreduce/esquema.png" alt="Esquema resumen de MapReduce" style="max-height: 34vh; width: auto; border-radius: 10px; border: 1px solid rgba(249,115,22,0.2); background: rgba(255,255,255,0.95); padding: 0.3em;">
        </div>
        <!-- Lado derecho: Puntos clave -->
        <div style="flex: 1; text-align: left;">
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: rgba(249,115,22,0.2); color: #f97316; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">1</span>
                <span style="font-size: 0.5em; color: #e2e8f0;"><strong>Divide</strong> los datos en fragmentos</span>
            </div>
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: rgba(249,115,22,0.2); color: #f97316; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">2</span>
                <span style="font-size: 0.5em; color: #e2e8f0;"><strong>Mapea</strong> cada fragmento en paralelo</span>
            </div>
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: rgba(167,139,250,0.2); color: #a78bfa; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">3</span>
                <span style="font-size: 0.5em; color: #e2e8f0;"><strong>Mezcla</strong> y agrupa por clave</span>
            </div>
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: rgba(74,222,128,0.2); color: #4ade80; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">4</span>
                <span style="font-size: 0.5em; color: #e2e8f0;"><strong>Reduce</strong> a resultados finales</span>
            </div>
            <hr style="border-color: rgba(255,255,255,0.1); margin: 0.6em 0;">
            <p style="font-size: 0.45em; color: #94a3b8; text-align: center;">
                Base del procesamiento de datos masivos moderno
            </p>
        </div>
    </div>
</section>

<!-- SLIDE 17: Conclusiones -->
<section data-background-gradient="linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%)">
    <h2>Conclusiones</h2>
    <div style="display: flex; gap: 1.2em; margin-top: 0.8em;">
        <div style="flex: 1; background: rgba(249,115,22,0.06); border: 1px solid rgba(249,115,22,0.2); border-radius: 14px; padding: 0.8em; text-align: center;">
            <h3 style="color: #f97316; font-size: 0.6em; margin: 0 0 0.3em;">Paradigma Fundamental</h3>
            <p style="font-size: 0.45em; color: #e2e8f0;">MapReduce transformó el procesamiento de datos al demostrar que problemas complejos pueden resolverse dividiéndolos en tareas simples y paralelas.</p>
        </div>
        <div style="flex: 1; background: rgba(74,222,128,0.06); border: 1px solid rgba(74,222,128,0.2); border-radius: 14px; padding: 0.8em; text-align: center;">
            <h3 style="color: #4ade80; font-size: 0.6em; margin: 0 0 0.3em;">Evolución Continua</h3>
            <p style="font-size: 0.45em; color: #e2e8f0;">Aunque tecnologías como Spark lo han superado en velocidad, MapReduce sentó las bases conceptuales del ecosistema Big Data actual.</p>
        </div>
        <div style="flex: 1; background: rgba(56,189,248,0.06); border: 1px solid rgba(56,189,248,0.2); border-radius: 14px; padding: 0.8em; text-align: center;">
            <h3 style="color: #38bdf8; font-size: 0.6em; margin: 0 0 0.3em;">Democratización</h3>
            <p style="font-size: 0.45em; color: #e2e8f0;">Servicios gestionados como Google Cloud Dataproc democratizan el acceso al procesamiento masivo sin necesidad de administrar infraestructura.</p>
        </div>
    </div>
</section>

<!-- SLIDE 18: Referencias -->
<section>
    <section>
        <h3 style="font-size: 1.1em;">Referencias Bibliográficas (1/2)</h3>
        <h4 style="font-size: 0.7em; color: #f97316; margin-top: -0.5em; margin-bottom: 0.5em;">MapReduce: Fundamentos y Paper Original</h4>
        <div class="small-text" style="text-align: left; padding: 0 1em; font-size: 0.42em; line-height: 1.35;">
            <ul>
                <li style="margin-bottom: 0.4em;">Dean, J., &amp; Ghemawat, S. (2004). <em>MapReduce: Simplified Data Processing on Large Clusters</em>. 6th Symposium on Operating System Design and Implementation (OSDI 2004). Google Research. <a href="https://research.google/pubs/mapreduce-simplified-data-processing-on-large-clusters/" target="_blank" style="color: #f97316;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Apache Software Foundation. (2024). <em>Apache Hadoop MapReduce Tutorial</em>. Apache Hadoop Documentation. <a href="https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html" target="_blank" style="color: #f97316;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Apache Software Foundation. (2024). <em>Apache Spark: Unified Analytics Engine for Big Data</em>. Apache Spark Documentation. <a href="https://spark.apache.org/" target="_blank" style="color: #f97316;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Google Cloud. (2024). <em>Dataproc documentation: Managed Hadoop and Spark on Google Cloud</em>. Google Cloud Docs. <a href="https://cloud.google.com/dataproc/docs" target="_blank" style="color: #f97316;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Wikipedia. (2024). <em>MapReduce</em>. Wikipedia, La Enciclopedia Libre. <a href="https://es.wikipedia.org/wiki/MapReduce" target="_blank" style="color: #f97316;">Enlace externo</a></li>
            </ul>
        </div>
    </section>

    <section>
        <h3 style="font-size: 1.1em;">Referencias Bibliográficas (2/2)</h3>
        <h4 style="font-size: 0.7em; color: #38bdf8; margin-top: -0.5em; margin-bottom: 0.5em;">Ecosistema Big Data y Aplicaciones</h4>
        <div class="small-text" style="text-align: left; padding: 0 1em; font-size: 0.42em; line-height: 1.35;">
            <ul>
                <li style="margin-bottom: 0.4em;">White, T. (2015). <em>Hadoop: The Definitive Guide</em> (4th ed.). O'Reilly Media. <a href="https://www.oreilly.com/library/view/hadoop-the-definitive/9781491901687/" target="_blank" style="color: #38bdf8;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Zaharia, M., et al. (2016). <em>Apache Spark: A Unified Engine for Big Data Processing</em>. Communications of the ACM, 59(11), 56-65. <a href="https://dl.acm.org/doi/10.1145/2934664" target="_blank" style="color: #38bdf8;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Google Cloud. (2024). <em>How to submit a Spark job to your Dataproc cluster</em>. Google Codelabs. <a href="https://codelabs.developers.google.com/codelabs/cloud-dataproc-gcloud" target="_blank" style="color: #38bdf8;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Gemini AI. (2026, 17 de junio). <em>MapReduce: Procesamiento de Grandes Datos</em>. Google Gemini. <a href="https://gemini.google.com/share/326173cbda16" target="_blank" style="color: #38bdf8;">Enlace externo</a></li>
                <li style="margin-bottom: 0.4em;">Lam, C. (2010). <em>Hadoop in Action</em>. Manning Publications. <a href="https://www.manning.com/books/hadoop-in-action" target="_blank" style="color: #38bdf8;">Enlace externo</a></li>
            </ul>
        </div>
    </section>
</section>
