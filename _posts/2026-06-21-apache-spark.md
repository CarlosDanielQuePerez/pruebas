---
title: "Apache Spark: Procesamiento de Datos a Gran Escala"
layout: post
permalink: /spark/
theme: moon
number: 996
label: "Presentación"
---

<section data-background-gradient="linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #E25A1C 100%)">
    <h3 style="color: #38bdf8; letter-spacing: 3px; font-size: 0.8em; margin-bottom: 20px;">CLOUD DATA PROCESSING</h3>
    <h2 style="font-size: 1.8em; line-height: 1.1;">Apache <span style="color: #E25A1C;">Spark</span></h2>
    <p style="font-size: 0.6em; color: #cbd5e1;">El motor de procesamiento distribuido más rápido del ecosistema</p>
    <br>
    <p style="font-size: 0.45em; color: #94a3b8;">
        Verano 2026<br>
        <strong>Carlos Daniel Que Perez</strong><br>
        <strong>Edgar Antonio Perez Flores</strong><br>
        <br>
        Universidad del Caribe
    </p>
    <p style="font-size: 0.35em; color: #38bdf8; margin-top: 40px;">➡️ Para avanzar de tema | ⬇️ Para profundizar</p>
</section>

<section>
    <section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
        <h2 style="color: #E25A1C; font-size: 1.1em;">¿Qué es Spark?</h2>
        <div style="display: flex; align-items: center; justify-content: center; gap: 1.5em; margin-top: 0.5em;">
            <div style="flex: 1; text-align: left;">
                <div class="highlight-box" style="border-left: 8px solid #E25A1C; padding-left: 15px; font-size: 0.6em;">
                    Framework open-source de <strong>computación distribuida</strong> diseñado para procesar volúmenes masivos de datos sobre clústeres.
                </div>
                <p style="font-size: 0.55em; margin-top: 0.6em; color: #cbd5e1;">
                    Diseñado para ser hasta:<br><strong style="color: #38bdf8; font-size: 1.3em;">100x más rápido</strong><br>que Hadoop MapReduce tradicional.
                </p>
            </div>
            <div style="flex: 1; text-align: center;">
                <img src="{{ site.baseurl }}/images/spark/logo_spark.png" alt="Logo Spark" style="max-height: 30vh; width: auto; border: 2px solid #E25A1C; border-radius: 12px; padding: 10px;">
            </div>
        </div>
        <p style="font-size: 0.4em; color: #94a3b8; margin-top: 20px;">⬇️ Presiona abajo para ver por qué es tan rápido</p>
    </section>

    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #38bdf8; font-size: 1em;">La Revolución: RAM vs Disco</h3>
        <div style="display: flex; gap: 1.2em; margin-top: 1em;">
            <div style="flex: 1; background: rgba(239, 68, 68, 0.05); border: 1px solid rgba(239, 68, 68, 0.3); border-radius: 16px; padding: 0.8em; text-align: center;">
                <h4 style="color: #fca5a5; font-size: 0.7em; margin-bottom: 0.3em;">Hadoop MapReduce</h4>
                <p style="font-size: 0.45em; color: #cbd5e1;">Depende de lecturas/escrituras en <strong>disco (HDFS)</strong> después de cada paso. Genera latencia masiva.</p>
            </div>
            <div style="flex: 1; background: rgba(56, 189, 248, 0.05); border: 1px solid rgba(56, 189, 248, 0.3); border-radius: 16px; padding: 0.8em; text-align: center;">
                <h4 style="color: #38bdf8; font-size: 0.7em; margin-bottom: 0.3em;">Apache Spark</h4>
                <p style="font-size: 0.45em; color: #cbd5e1;">Procesa directamente en <strong>memoria RAM</strong>. Mantiene los datos vivos para un acceso instantáneo.</p>
            </div>
        </div>
    </section>
</section>

<section>
    <section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
        <h2 style="color: #E25A1C; font-size: 1.1em;">Arquitectura del Sistema</h2>
        <div style="display: flex; gap: 1em; margin-top: 0.6em; align-items: center;">
            <div style="flex: 1.5;">
                <div style="padding: 0.6em; border: 1px solid #E25A1C; border-radius: 10px; background: rgba(0,0,0,0.2); text-align: left;">
                    <pre style="background: transparent; box-shadow: none; margin: 0; font-family: monospace; font-size: 0.7em; line-height: 1.3; color: #e2e8f0;">
   [ Driver Program ] <-- El Cerebro
           |
    { DAG Optimizer }
           |
   ┌───────┴───────┐
   v               v
[ Executor ]    [ Executor ] <-- RAM
  (Tasks)         (Tasks)
   └───────┬───────┘
     [ Cluster Manager ] (YARN/K8s)</pre>
                </div>
            </div>
            <div style="flex: 1; text-align: left;">
                <p style="font-size: 0.45em;"><strong style="color: #E25A1C;">Driver:</strong> Coordina la ejecución y reparte tareas.</p>
                <p style="font-size: 0.45em;"><strong style="color: #E25A1C;">Executors:</strong> Nodos que realizan el cálculo real.</p>
                <p style="font-size: 0.45em;"><strong style="color: #E25A1C;">Cluster Manager:</strong> Gestor de recursos del hardware.</p>
            </div>
        </div>
        <p style="font-size: 0.4em; color: #94a3b8; margin-top: 20px;">⬇️ Presiona abajo para ver el concepto de DAG</p>
    </section>

    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #38bdf8; font-size: 1em;">DAG y Tolerancia a Fallos</h3>
        <div style="display: flex; gap: 1.5em; margin-top: 1em; align-items: center;">
            <div style="flex: 1; text-align: left;">
                <div style="border-left: 8px solid #38bdf8; padding-left: 15px; font-size: 0.55em;">
                    Spark crea un <strong>Grafo Acíclico Dirigido (DAG)</strong> de todas las transformaciones.
                </div>
                <p style="font-size: 0.45em; margin-top: 15px; color: #cbd5e1;">
                    Si un nodo falla, Spark consulta el DAG y <strong>reconstruye</strong> automáticamente solo la parte de los datos que se perdió sin necesidad de reiniciar todo el proceso desde cero.
                </p>
            </div>
        </div>
    </section>
</section>

<section>
    <section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
        <h2 style="color: #38bdf8; font-size: 1.1em;">Ecosistema Unificado</h2>
        <p style="font-size: 0.45em; color: #94a3b8; margin-top: -0.3em;">Un solo motor para todas las necesidades analíticas</p>
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 0.7em; margin-top: 0.8em; text-align: left;">
            <div style="background: rgba(56, 189, 248, 0.06); border: 1px solid #38bdf8; border-radius: 14px; padding: 0.6em;">
                <p style="font-size: 0.5em; margin: 0; color: #38bdf8;"><strong>Spark SQL</strong></p>
                <p style="font-size: 0.38em; color: #cbd5e1;">Análisis de datos estructurados con DataFrames.</p>
            </div>
            <div style="background: rgba(226, 90, 28, 0.06); border: 1px solid #E25A1C; border-radius: 14px; padding: 0.6em;">
                <p style="font-size: 0.5em; margin: 0; color: #E25A1C;"><strong>MLlib</strong></p>
                <p style="font-size: 0.38em; color: #cbd5e1;">Librería de Machine Learning distribuido a escala.</p>
            </div>
            <div style="background: rgba(167, 139, 250, 0.06); border: 1px solid #a78bfa; border-radius: 14px; padding: 0.6em;">
                <p style="font-size: 0.5em; margin: 0; color: #a78bfa;"><strong>Streaming</strong></p>
                <p style="font-size: 0.38em; color: #cbd5e1;">Procesamiento de flujos de datos en tiempo real.</p>
            </div>
            <div style="background: rgba(74, 222, 128, 0.06); border: 1px solid #4ade80; border-radius: 14px; padding: 0.6em;">
                <p style="font-size: 0.5em; margin: 0; color: #4ade80;"><strong>GraphX</strong></p>
                <p style="font-size: 0.38em; color: #cbd5e1;">Analítica avanzada de redes y grafos.</p>
            </div>
        </div>
        <p style="font-size: 0.4em; color: #94a3b8; margin-top: 20px;">⬇️ Presiona abajo para ver lenguajes soportados</p>
    </section>

    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #E25A1C; font-size: 1em;">Flexibilidad Multilenguaje</h3>
        <div style="margin-top: 1em;">
            <table style="font-size: 0.45em; width: 100%; border-collapse: collapse; text-align: left;">
                <thead>
                    <tr style="border-bottom: 2px solid #E25A1C;">
                        <th style="padding: 10px;">Lenguaje</th>
                        <th style="padding: 10px;">API</th>
                        <th style="padding: 10px;">Uso Principal</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td style="padding: 10px;"><strong>Python</strong></td>
                        <td style="color: #38bdf8; padding: 10px;">PySpark</td>
                        <td style="padding: 10px;">Data Science / Machine Learning.</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;"><strong>Scala</strong></td>
                        <td style="color: #38bdf8; padding: 10px;">Nativa</td>
                        <td style="padding: 10px;">Máximo rendimiento (lenguaje nativo).</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;"><strong>SQL</strong></td>
                        <td style="color: #38bdf8; padding: 10px;">Spark SQL</td>
                        <td style="padding: 10px;">Consultas relacionales sobre Big Data.</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;"><strong>Java</strong></td>
                        <td style="color: #38bdf8; padding: 10px;">Java API</td>
                        <td style="padding: 10px;">Desarrollo empresarial robusto.</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </section>
</section>

<section>
    <section data-background-gradient="linear-gradient(160deg, #0f172a 0%, #1a1a2e 100%)">
        <h2 style="color: #E25A1C; font-size: 1.1em;">Caso Práctico: Word Count</h2>
        <p style="font-size: 0.45em; color: #94a3b8; margin-top: -0.3em;">Implementación técnica (script.py)</p>
        <div style="margin-top: 1em;">
            <img src="{{ site.baseurl }}/images/spark/script.png" alt="Script PySpark" style="max-height: 45vh; border-radius: 12px; border: 2px solid #E25A1C;">
        </div>
        <p style="font-size: 0.4em; color: #cbd5e1; margin-top: 15px;">Infraestructura: Ubuntu (WSL2) + Docker + Spark 3.5.1</p>
        <p style="font-size: 0.4em; color: #94a3b8;">⬇️ Presiona abajo para ver el resultado</p>
    </section>

    <section data-background-gradient="linear-gradient(160deg, #1a1a2e 0%, #16213e 100%)">
        <h3 style="color: #38bdf8; font-size: 1em;">Evidencia de Ejecución</h3>
        <div style="margin-top: 1em;">
            <img src="{{ site.baseurl }}/images/spark/resultado.png" alt="Resultado Spark" style="max-height: 45vh; border-radius: 12px; border: 2px solid #38bdf8;">
        </div>
        <div style="margin-top: 20px; border-left: 8px solid #38bdf8; padding-left: 15px; font-size: 0.5em; max-width: 80%; margin-left: auto; margin-right: auto; text-align: left;">
            Salida consolidada devuelta por el motor distribuido procesando el texto estructurado.
        </div>
    </section>
</section>

<section data-background-gradient="linear-gradient(135deg, #E25A1C 0%, #0f172a 100%)">
    <h2 style="font-size: 2.5em; margin-bottom: 20px;">¿Preguntas?</h2>
    <div style="margin-top: 40px;">
        <p style="font-size: 0.7em; color: #f3f0df;">Muchas gracias por su atención.</p>
        <hr style="width: 25%; border-color: #38bdf8; margin: 30px auto;">
        <p style="font-size: 0.5em; color: #cbd5e1;">
            <strong>Carlos Daniel Que Perez</strong><br>
            <strong>Edgar Antonio Perez Flores</strong>
        </p>
        <p style="font-size: 0.4em; margin-top: 20px; opacity: 0.7;">Ingeniería en Datos | Cloud Computing 2026</p>
    </div>
</section>
