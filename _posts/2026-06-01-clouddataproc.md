---
title: Fundamentos de Cloud y Procesamiento de Datos
layout: post
permalink: /clouddataproc/
---

<section>
    <h1>Unidad 1: Fundamentos</h1>
    <h3>Cloud Computing y Procesamiento de Datos</h3>
    <p>
        <small>Creado por <a href="http://tuxtter.net">Ismael Jimenez</a></small>
    </p>
</section>

<section>
    <section>
        <h2>1.1 Solución estratificada de problemas en TIC</h2>
        <p>
            La solución estratificada de problemas en Tecnologías de la Información y Comunicación divide un reto complejo en capas o niveles de abstracción. Cada capa aborda una parte específica del sistema, desde el hardware y la virtualización hasta las plataformas y servicios finales.
        </p>
    </section>
    <section>
        <h2>1.1.a Virtualización por interpretación pura</h2>
        <p>
            La virtualización por interpretación pura se basa en un software que traduce instrucciones de una máquina invitada a la arquitectura física en tiempo real. Esta técnica permite ejecutar sistemas operativos diferentes al hardware subyacente, aunque con menor rendimiento debido a la sobrecarga del intérprete.
        </p>
    </section>
    <section>
        <h2>1.1.b Virtualización por recompilación dinámica</h2>
        <p>
            La recompilación dinámica convierte bloques de código de la máquina invitada en código nativo de la plataforma anfitrión durante la ejecución. Este enfoque mejora el rendimiento frente a la interpretación pura y permite aplicar optimizaciones sobre la marcha, manteniendo compatibilidad con arquitecturas heterogéneas.
        </p>
    </section>
    <section>
        <h2>1.1.c Virtualización por hipervisión (bare metal)</h2>
        <p>
            La virtualización por hipervisión, también llamada bare metal, instala el hipervisor directamente sobre el hardware. Esto ofrece un control directo de recursos, mejor aislamiento y mayor eficiencia, y es común en servidores de centros de datos que alojan múltiples máquinas virtuales.
        </p>
    </section>
</section>

<section>
    <section>
        <h2>1.2 Definiciones básicas</h2>
        <p>
            Los modelos de servicio en la nube describen cómo se entregan los recursos a los usuarios. Cada modelo define niveles distintos de responsabilidad entre el proveedor y el cliente.
        </p>
    </section>
    <section>
        <h2>1.2.a El software como servicio (SaaS)</h2>
        <p>
            SaaS ofrece aplicaciones listas para usar a través de internet. El proveedor administra todo el software, la infraestructura y el mantenimiento, mientras que el usuario solo consume el servicio, como correo electrónico, herramientas de oficina o plataformas de gestión.
        </p>
    </section>
    <section>
        <h2>1.2.b Plataforma como servicio (PaaS)</h2>
        <p>
            PaaS proporciona un entorno de desarrollo completo en la nube, con servidores, almacenamiento y herramientas de despliegue. Los desarrolladores construyen y gestionan sus aplicaciones sin ocuparse de la infraestructura subyacente.
        </p>
    </section>
    <section>
        <h2>1.2.c Infraestructura como servicio (IaaS)</h2>
        <p>
            IaaS entrega recursos de infraestructura como servidores virtuales, redes y almacenamiento bajo demanda. El usuario controla el sistema operativo, las aplicaciones y la configuración, mientras que el proveedor mantiene el hardware y la virtualización.
        </p>
    </section>
</section>

<section>
    <section>
        <h2>1.3 Tipos de nubes</h2>
        <p>
            Los modelos de despliegue en la nube determinan quién tiene acceso a los recursos y cómo se gestionan. Existen nubes pública, privada, comunitaria e híbrida.
        </p>
    </section>
    <section>
        <h2>Nube pública</h2>
        <p>
            La nube pública está disponible para cualquier usuario a través de internet, ofrecida por proveedores como AWS, Azure o Google Cloud. Comparte recursos entre clientes y suele ser la opción más flexible y escalable.
        </p>
    </section>
    <section>
        <h2>Nube privada</h2>
        <p>
            Una nube privada está dedicada a una sola organización y puede estar alojada en sus propias instalaciones o en un centro de datos externo. Proporciona mayor control, seguridad y cumplimiento normativo.
        </p>
    </section>
    <section>
        <h2>Nube comunitaria</h2>
        <p>
            La nube comunitaria es compartida por varias organizaciones con intereses o requisitos similares, como entidades gubernamentales o instituciones educativas. Se enfoca en colaboración y uso común de recursos controlados.
        </p>
    </section>
    <section>
        <h2>Nube híbrida</h2>
        <p>
            La nube híbrida combina nubes públicas y privadas, permitiendo distribuir cargas de trabajo entre ambas. Esto ayuda a balancear costos, rendimiento y privacidad según la naturaleza de las aplicaciones.
        </p>
    </section>
</section>

<section>
    <section>
        <h2>1.4 Arquitecturas</h2>
        <p>
            Las arquitecturas en la nube describen cómo se organizan los componentes, datos y servicios. Incluyen modelos como microservicios, arquitecturas orientadas a eventos y sistemas distribuidos para escalar y optimizar la gestión de datos.
        </p>
    </section>
    <section>
        <h2>Arquitectura de microservicios</h2>
        <p>
            La arquitectura de microservicios divide una aplicación en servicios independientes y desplegables por separado. Cada servicio es responsable de una función específica, lo que facilita la evolución, el desarrollo paralelo y la escalabilidad.
        </p>
    </section>
    <section>
        <h2>Arquitectura orientada a eventos</h2>
        <p>
            Este modelo se basa en productores y consumidores de eventos, permitiendo respuestas asíncronas y desacopladas. Es útil para sistemas de procesamiento de datos en tiempo real y arquitecturas de integración distribuidas.
        </p>
    </section>
    <section>
        <h2>Sistemas distribuidos</h2>
        <p>
            Los sistemas distribuidos combinan múltiples nodos que cooperan para ofrecer servicios. En la nube, esto permite tolerancia a fallos, balanceo de carga y procesamiento paralelo de grandes volúmenes de datos.
        </p>
    </section>
</section>
