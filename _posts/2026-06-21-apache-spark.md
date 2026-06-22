---
title: "Apache Spark: Procesamiento de Datos a Gran Escala"
layout: post
permalink: /spark/
theme: moon
number: 996
label: "Presentación"
---

<section data-background-gradient="linear-gradient(135deg, #1B456C 0%, #0f172a 50%, #E25A1C 100%)">
    <h2>Presentación</h2>
    <h3 style="font-size: 1.1em; line-height: 1.2;">Apache Spark: Procesamiento de Datos a Gran Escala</h3>
    <p style="font-size: 0.65em; color: #f9a8d4;">Motor Unificado de Analítica de Datos</p>
    <br>
    <p style="font-size: 0.5em; color: #94a3b8;">
        Cloud Data Processing — Verano 2026<br>
        Tu Nombre Aquí<br>
        Universidad del Caribe<br>
    </p>
</section>

<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #E25A1C; font-size: 1.1em;">¿Qué es Apache Spark?</h2>
    <div style="display: flex; align-items: center; justify-content: center; gap: 1.5em; margin-top: 0.5em;">
        <div style="flex: 1; text-align: center;">
            <img src="{{ site.baseurl }}/images/spark/logo_spark.png" alt="Logo de Apache Spark" style="max-height: 32vh; width: auto; border-radius: 12px; border: 2px solid #E25A1C; background: rgba(255,255,255,0.05); padding: 10px;">
        </div>
        <div style="flex: 1; text-align: left;">
            <div class="highlight-box" style="border-left-color: #E25A1C; font-size: 0.6em;">
                Framework líder de <strong>computación distribuida</strong> que procesa datos en <strong>RAM</strong> para máxima velocidad.
            </div>
            <p style="font-size: 0.55em; margin-top: 0.6em; color: #cbd5e1;">
                Diseñado para ser:<br><strong style="color: #38bdf8; font-size: 1.3em;">100x más rápido</strong><br>que Hadoop MapReduce.
            </p>
            <p style="font-size: 0.42em; color: #64748b; margin-top: 0.3em;">La evolución lógica del procesamiento en clúster.</p>
        </div>
    </div>
</section>

<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #38bdf8; font-size: 1.1em;">¿Por qué destaca Spark?</h2>
    <div style="display: flex; gap: 1.2em; margin-top: 1em;">
        <div style="flex: 1; background: rgba(226, 90, 28, 0.08); border: 1px solid #E25A1C; border-radius: 16px; padding: 0.8em; text-align: center;">
            <h3 style="color: #E25A1C; font-size: 0.7em; margin: 0.3em 0;">In-Memory</h3>
            <hr style="border-color: rgba(226, 90, 28, 0.3); margin: 0.3em 0;">
            <p style="font-size: 0.45em; color: #cbd5e1;">Mantiene los datos en RAM entre pasos, eliminando el cuello de botella del disco.</p>
        </div>
        <div style="flex: 1; background: rgba(27, 69, 108, 0.2); border: 1px solid #1B456C; border-radius: 16px; padding: 0.8em; text-align: center;">
            <h3 style="color: #38bdf8; font-size: 0.7em; margin: 0.3em 0;">Lazy Eval</h3>
            <hr style="border-color: rgba(56, 189, 248, 0.3); margin: 0.3em 0;">
            <p style="font-size: 0.45em; color: #cbd5e1;">No ejecuta nada hasta que es estrictamente necesario, optimizando el plan lógico.</p>
        </div>
        <div style="flex: 1; background: rgba(74, 222, 128, 0.06); border: 1px solid #4ade80; border-radius: 16px; padding: 0.8em; text-align: center;">
            <h3 style="color: #4ade80; font-size: 0.7em; margin: 0.3em 0;">Resiliencia</h3>
            <hr style="border-color: rgba(74, 222, 128, 0.3); margin: 0.3em 0;">
            <p style="font-size: 0.45em; color: #cbd5e1;">Usa Linajes (DAG) para reconstruir datos en caso de fallo de algún nodo.</p>
        </div>
    </div>
</section>

<section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
    <h3 style="color: #E25A1C; font-size: 1.1em;">Arquitectura del Cluster</h3>
    <div style="display: flex; gap: 1em; margin-top: 0.6em;">
        <div style="flex: 1.5;">
            <div class="diagram-box" style="padding: 0.6em; font-size: 1em;">
                <pre style="background: transparent; box-shadow: none; margin: 0; font-family: monospace; font-size: 0.75em; line-height: 1.2; color: #e2e8f0;">
   <span style="color: #E25A1C;">[ Driver Program ]</span> <-- Master
           |
    { DAG Scheduler }
           |
   ┌───────┴───────┐
   v               v
<span style="color: #38bdf8;">[ Executor ]    [ Executor ]</span> <-- RAM
  (Tasks)         (Tasks)
   └───────┬───────┘
     [ Cluster Manager ] (YARN/K8s)</pre>
            </div>
        </div>
        <div style="flex: 1; text-align: left; display: flex; flex-direction: column; justify-content: center;">
            <div class="highlight-box" style="border-left-color: #E25A1C; font-size: 0.55em;">
                El <strong>Driver</strong> convierte el código en tareas y el <strong>Cluster Manager</strong> las reparte entre los <strong>Executors</strong>.
            </div>
        </div>
    </div>
</section>

<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #E25A1C; font-size: 1em;">Caso Práctico: Laboratorio PySpark</h2>
    <div style="display: flex; gap: 1em; margin-top: 0.5em; align-items: flex-start;">
        <div style="flex: 1;">
            <p style="font-size: 0.4em; color: #E25A1C; margin-bottom: 0.3em; font-weight: bold;">Código: script.py</p>
            <img src="{{ site.baseurl }}/images/spark/script.png" alt="Captura del código Spark" style="max-height: 38vh; width: auto; border-radius: 8px; border: 1px solid #E25A1C; background: rgba(0,0,0,0.3);">
        </div>
        <div style="flex: 1;">
            <p style="font-size: 0.4em; color: #38bdf8; margin-bottom: 0.3em; font-weight: bold;">Resultado en Terminal</p>
            <img src="{{ site.baseurl }}/images/spark/resultado.png" alt="Captura del resultado" style="max-height: 38vh; width: auto; border-radius: 8px; border: 1px solid #38bdf8;">
            <p style="font-size: 0.32em; color: #94a3b8; margin-top: 0.5em; line-height: 1.2;">
                <strong>Infraestructura:</strong> <br>
                Ubuntu (WSL2) + Docker <br>
                Imagen: <code>apache/spark:3.5.1</code>
            </p>
        </div>
    </div>
</section>

<section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
    <h2 style="color: #38bdf8; font-size: 1.1em;">Ecosistema Unificado</h2>
    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.7em; margin-top: 0.8em;">
        <div style="background: rgba(27, 69, 108, 0.2); border: 1px solid #1B456C; border-radius: 14px; padding: 0.6em;">
            <p style="font-size: 0.45em; margin: 0; color: #38bdf8;"><strong>Spark SQL</strong></p>
            <p style="font-size: 0.35em; color: #94a3b8;">Datos estructurados y DataFrames.</p>
            <span class="badge" style="border-color: #38bdf8; color: #38bdf8; font-size: 0.25em;">RECOMENDADO</span>
        </div>
        <div style="background: rgba(226, 90, 28, 0.08); border: 1px solid #E25A1C; border-radius: 14px; padding: 0.6em;">
            <p style="font-size: 0.45em; margin: 0; color: #E25A1C;"><strong>MLlib</strong></p>
            <p style="font-size: 0.35em; color: #94a3b8;">Machine Learning Distribuido.</p>
            <span class="badge" style="border-color: #E25A1C; color: #E25A1C; font-size: 0.25em;">IA / DATA SCIENCE</span>
        </div>
        <div style="background: rgba(167, 139, 250, 0.06); border: 1px solid #a78bfa; border-radius: 14px; padding: 0.6em;">
            <p style="font-size: 0.45em; margin: 0; color: #a78bfa;"><strong>Streaming</strong></p>
            <p style="font-size: 0.35em; color: #94a3b8;">Análisis en tiempo real.</p>
            <span class="badge" style="border-color: #a78bfa; color: #a78bfa; font-size: 0.25em;">STREAMS</span>
        </div>
        <div style="background: rgba(74, 222, 128, 0.06); border: 1px solid #4ade80; border-radius: 14px; padding: 0.6em;">
            <p style="font-size: 0.45em; margin: 0; color: #4ade80;"><strong>GraphX</strong></p>
            <p style="font-size: 0.35em; color: #94a3b8;">Procesamiento de grafos.</p>
            <span class="badge" style="border-color: #4ade80; color: #4ade80; font-size: 0.25em;">REDES</span>
        </div>
    </div>
</section>

<section data-background-gradient="linear-gradient(160deg, #1B456C 0%, #0f172a 100%)">
    <h2 style="color: #E25A1C; font-size: 1.1em;">Resumen: Spark en una Diapositiva</h2>
    <div style="display: flex; gap: 1.5em; margin-top: 0.6em; align-items: center;">
        <div style="flex: 1; text-align: center;">
            <div style="background: rgba(226, 90, 28, 0.1); border-radius: 50%; padding: 2.5em; border: 3px dashed #E25A1C;">
                <strong style="font-size: 1.8em; color: #E25A1C;">RAM</strong>
                <p style="font-size: 0.5em; color: #38bdf8; font-weight: bold;">Power</p>
            </div>
        </div>
        <div style="flex: 1.5; text-align: left;">
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: #E25A1C; color: #fff; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">1</span>
                <span style="font-size: 0.55em; color: #e2e8f0;"><strong>Elimina</strong> la dependencia del disco</span>
            </div>
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: #E25A1C; color: #fff; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">2</span>
                <span style="font-size: 0.55em; color: #e2e8f0;"><strong>Unifica</strong> SQL, Streaming y ML</span>
            </div>
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: #38bdf8; color: #000; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">3</span>
                <span style="font-size: 0.55em; color: #e2e8f0;"><strong>Optimiza</strong> consultas con Catalyst</span>
            </div>
            <div style="margin-bottom: 0.5em;">
                <span style="display: inline-block; background: #4ade80; color: #000; border-radius: 50%; width: 1.5em; height: 1.5em; text-align: center; line-height: 1.5em; font-size: 0.6em; font-weight: bold; margin-right: 0.3em;">4</span>
                <span style="font-size: 0.55em; color: #e2e8f0;"><strong>Escala</strong> de 1 a miles de nodos</span>
            </div>
            <hr style="border-color: rgba(255,255,255,0.1); margin: 0.6em 0;">
            <p style="font-size: 0.45em; color: #94a3b8; text-align: center;">Dudas: TuCorreo@uqrroo.mx</p>
        </div>
    </div>
</section>