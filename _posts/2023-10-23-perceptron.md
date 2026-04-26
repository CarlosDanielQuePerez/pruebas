---
title: Arquitectura del perceptron
layout: post
permalink: /
---

<section>
    <h1>Seminario de redes neuronales</h1>
    <h3>Arquitectura del perceptron</h3>
    <p>
        <small>Creado por <a href="http://tuxtter.net">Ismael Jimenez</a></small>
    </p>
</section>

<section>
    <section>
        <h2>Perceptron</h2>
        <p>
            Un perceptrón es un modelo matemático inspirado en una estructura y función simplificadas de una única neurona biológica. Es una sección de Machine Learning que se utiliza para entender el concepto de clasificadores binarios.
        </p>
    </section>
    <section>
        <h2>Perceptron</h2>
        <p>Forma parte del sistema de redes neuronales. De hecho, se puede decir que el perceptrón y las redes neuronales están interconectados. El perceptrón constituye el fundamento básico de la red neuronal que forma parte de Deep Learning. Se considera como bloques de construcción de una sola capa de la red neuronal.
        </p>
    </section>
    <section>
        <h2>Perceptron</h2>
        <p>Una red neuronal formada por el perceptrón puede definirse como un enunciado complejo con una comprensión muy profunda de las ecuaciones lógicas. Un enunciado neuronal que sigue al perceptrón es verdadero o falso, pero nunca puede ser ambas cosas a la vez.</p>
    </section>
</section>

<section>
    <section>
        <h2>Arquitectura del perceptron</h2>
    </section>
    <section>
        <h2>Elementos de una neurona artificial</h2>
        <ul>
            <li>Elemento receptor</li>
            <li>Elemento sumador</li>
            <li>Elemento de funcion activadora</li>
            <li>Elemento de salida</li>
        </ul>
    </section>
    <section>
        <h2>Elemento receptor</h2>
        <p>Es a donde llegan las señales de entrada, cuyo origen puede mayormente provenir del elemento de salida de otras neuronas, para ser manipuladas de acuerdo a la definicion de peso que se le haya asignado de acuerdo a la relacion que exista con la neurona de la que provenga la entrada, y la neurona a la que vaya a enviarse la salida.</p>
    </section>
        <section>
        <h2>Elemento sumador</h2>
        <p>Es el elemento que realiza la suma algebraica de las entradas, considerando el peso, aplicando la formula:</p>
    </section>
        <section>
        <h2>Elemento de funcion activadora</h2>
        <p>Este elemento determina si la neurona devolvera una salida, mediante la aplicacion de una funcion no lineal de umbral al resultado del elemento sumador.</p>
    </section>
        <section>
        <h2>Elemento de salida</h2>
        <p>Este elemento permite que la neurona emita una salida que sera captada ayormente por otra neuronas de la red comenzando el ciclo nuevamente.</p>
    </section>
</section>

<section>
    <section>
        <h2>¿Como funciona?</h2>
        <p>desarrollado por Rosenblatt (1958), consiste en una neurona procesadora, con sus elementos de entrada, sumador, activador y de salida.</p>
    </section>
    <section>
        <h2>Suma ponderada</h2>
        <p>El elemento sumador efectúa entonces una suma ponderada de las entradas, en tanto que el activador emplea una función escalón de umbral: si la suma ponderada es mayor o igual a un valor de umbral , da una salida de tal manera que:</p>
    </section>
    <section>
        <h2>Red neuronal simple</h2>
        <p>La red neuronal más simple construida con perceptrones tiene dos capas: una en la que la salida de cada neurona reproduce simplemente su entrada y una formada por perceptrones como los descritos, totalmente conectados con la capa de entrada, a través de líneas de comunicación con **conductividades o pesos ajustables**.</p>
    </section>
    <section>
        <h2>Entrada y salida</h2>
        <p>Cada neurona de entrada está conectada con cada neurona de salida a través de una línea de comunicación con una conductividad o peso ajustable.</p>
    </section>
    <section>
        <h2>Ley de aprendizaje</h2>
        <p>La ley de aprendizaje del perceptrón ajusta estos pesos, de manera que se obtenga con mayor probabilidad la salida deseable correspondiente a un cierto conjunto de entradas.</p>
    </section>
    <section>
        <h2>Entrenamiento</h2>
        <p>El perceptrón es entrenado presentándole un conjunto de patrones de entrenamiento en forma repetida. Cada patrón de entrenamiento es una pareja formada por un vector de entrada X y su vector de salida Y deseable.</p>
    </section>
    <section>
        <h2>Dimension del vector</h2>
        <p>La dimensión del vector de entrada es igual al número de neuronas de la capa de entrada, en tanto que la dimensión del vector de salida es igual al número de neuronas de la capa de salida.</p>
    </section>
    <section>
        <h2>Reajuste de valores</h2>
        <p>Al presentarle el vector de entrada al perceptrón, sus neuronas de entrada lo asumen. Las salidas de la red se comparan con el vector de salida y la diferencia obtenida se utiliza para reajustar los valores de los pesos W de las interconexiones.</p>
    </section>
    <section>
        <h2>Reajuste de valores</h2>
        <p>Este reajuste se hace de modo que sea más probable que la red dé la respuesta apropiada la siguiente vez. El entrenamiento prosigue hasta que todas las respuestas de la red se aproximan en forma aceptable a las deseadas.</p>
    </section>
    <section>
        <h2>Reajuste de pesos</h2>
        <p>Para el reajuste de los pesos, existen diferentes reglas propuestas posteriormente por diferentes autores (Duda & Hart 1973; Rosenblatt 1962), basadas en la Regla Delta de Widrof y Hoff (1960).</p>
    </section>
        <section>
        <h2>Reajuste de pesos</h2>
        <p>En una de las más sencillas, el nuevo peso w1 es igual al peso anterior w0 más una cantidad proporcional a la diferencia entre la salida deseada t y la salida real y: donde n es una constante de proporcionalidad menor que la unidad que se llama razon de aprendizaje</p>
    </section>
    <section>
        <h2>Razon de aprendizaje</h2>
        <p>Si el vector de entradas es de ceros y unos, hay una fórmula derivada en la que la razón de aprendizaje se multiplica por la entrada correspondiente x. De este modo, el peso se modifica solo cuando la entrada vale 1, es decir, cuando está activa. Así,la fórmula anterior queda en la forma:</p>
    </section>
    <section>
        <h2>Convergencia</h2>
        <p>Antes de comenzar el entrenamiento, los pesos se fijan aleatoriamente. Durante el entrenamiento, los patrones de entrenamiento se presentan a la red una y otra vez (a veces cientos y hasta miles de veces), hasta que los pesos ya no se modifican.</p>
    </section>
        <section>
        <h2>Convergencia</h2>
        <p>En este caso se dice que la red ha convergido, en cuyo caso o ha aprendido con éxito o se declara incapaz de aprender todas las respuestas correctas.</p>
    </section>
    <section>
        <h2>Limitantes</h2>
        <p>Las limitantes más grandes del perceptrón es que, aunque pueden construirse Redes Neuronales de varias capas con él, no permite más que una sola capa de pesos adaptativos.</p>
    </section>
</section>