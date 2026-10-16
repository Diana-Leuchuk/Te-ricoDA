<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Diagramas de Actividades UML</title>

<style>
:root {
    --azul: #123c83;
    --azul-oscuro: #102d65;
    --celeste: #38bdf8;
    --fondo: #f3f7ff;
    --texto: #172554;
    --blanco: #ffffff;
    --borde: #dbe5f5;
    --violeta: #7954d6;
    --verde: #15803d;
    --rojo: #dc2626;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: "Segoe UI", Arial, sans-serif;
    background: var(--fondo);
    color: var(--texto);
    line-height: 1.6;
}

header {
    background: linear-gradient(120deg, #102d65, #1764b1);
    color: white;
}

nav {
    padding: 20px 6%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 15px;
}

.logo {
    font-size: 1.1rem;
    font-weight: 800;
    letter-spacing: 1px;
}

nav .enlaces {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

nav a {
    color: white;
    text-decoration: none;
    font-weight: 700;
}

nav a:hover {
    color: #7dd3fc;
}

.hero {
    text-align: center;
    padding: 65px 22px 75px;
    max-width: 1000px;
    margin: auto;
}

.etiqueta {
    display: inline-block;
    background: #dbeafe;
    color: #123c83;
    padding: 6px 15px;
    border-radius: 30px;
    font-weight: 800;
    margin-bottom: 20px;
}

.hero h1 {
    font-size: clamp(2.4rem, 5vw, 4rem);
    line-height: 1.15;
    margin-bottom: 22px;
}

.hero p {
    font-size: 1.2rem;
    color: #e0edff;
    max-width: 760px;
    margin: auto;
}

.boton {
    display: inline-block;
    margin-top: 28px;
    background: #7dd3fc;
    color: #082f49;
    padding: 13px 24px;
    border-radius: 10px;
    font-weight: 800;
    text-decoration: none;
}

.boton:hover {
    background: white;
}

main {
    max-width: 1200px;
    padding: 40px 24px 65px;
    margin: auto;
}

section {
    margin-bottom: 55px;
    scroll-margin-top: 20px;
}

.titulo-seccion {
    font-size: clamp(1.8rem, 3vw, 2.4rem);
    color: var(--azul);
    margin-bottom: 12px;
}

.intro {
    font-size: 1.1rem;
    margin-bottom: 25px;
    max-width: 900px;
}

.card {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 18px;
    padding: 26px;
    box-shadow: 0 6px 20px rgba(18, 60, 131, 0.07);
}

.destacado {
    border-left: 6px solid var(--celeste);
}

.destacado h3 {
    color: var(--azul);
    margin-bottom: 10px;
    font-size: 1.25rem;
}

.lista {
    padding-left: 25px;
    margin-top: 12px;
}

.lista li {
    margin-bottom: 8px;
}

.grid-simbolos {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 18px;
}

.simbolo {
    text-align: center;
    background: white;
    padding: 22px 16px;
    border: 1px solid var(--borde);
    border-radius: 16px;
}

.figura {
    height: 85px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.inicio {
    height: 27px;
    width: 27px;
    background: #111827;
    border-radius: 50%;
}

.accion {
    padding: 10px 16px;
    min-width: 145px;
    background: #eff6ff;
    border: 3px solid #2563eb;
    border-radius: 15px;
    font-weight: 800;
}

.rombo {
    width: 48px;
    height: 48px;
    background: #f3e8ff;
    border: 3px solid #7c3aed;
    transform: rotate(45deg);
}

.flecha {
    font-size: 3rem;
    color: #2563eb;
    font-weight: 900;
}

.final {
    height: 34px;
    width: 34px;
    background: #111827;
    border: 6px solid white;
    outline: 3px solid #111827;
    border-radius: 50%;
}

.simbolo h3 {
    color: var(--azul);
    font-size: 1.2rem;
    margin: 12px 0 7px;
}

.simbolo p {
    font-size: 1rem;
}

.nota {
    margin-top: 20px;
    padding: 16px 20px;
    border-left: 5px solid #2563eb;
    background: #e8f1ff;
    border-radius: 10px;
}

/* CARD DEL EJEMPLO */

.ejemplo-card {
    display: grid;
    grid-template-columns: 0.85fr 1.15fr;
    align-items: start;
    gap: 28px;
    padding: 28px;
}

.ejemplo-texto h3 {
    color: var(--azul);
    font-size: 1.45rem;
    margin-bottom: 14px;
}

.ejemplo-texto p {
    margin-bottom: 15px;
}

.paso {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    margin-bottom: 15px;
}

.numero {
    flex-shrink: 0;
    width: 32px;
    height: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    background: #dbeafe;
    color: #123c83;
    font-weight: 900;
}

.paso strong {
    display: block;
    color: #123c83;
}

.diagrama-panel {
    min-width: 0;
    background: #f8faff;
    border: 1px solid var(--borde);
    border-radius: 14px;
    padding: 16px;
}

.diagrama-panel h3 {
    text-align: center;
    font-size: 1.15rem;
    color: var(--azul);
    margin-bottom: 10px;
}

.diagrama {
    display: block;
    width: 100%;
    height: auto;
    max-width: 470px;
    margin: auto;
}

.diagrama text {
    font-family: "Segoe UI", Arial, sans-serif;
    fill: #172554;
    font-size: 13px;
    font-weight: 700;
}

.diagrama .flujo {
    stroke: #334155;
    stroke-width: 2.3;
    fill: none;
    marker-end: url(#punta);
}

.diagrama .nodo-accion {
    fill: #eff6ff;
    stroke: #2563eb;
    stroke-width: 2;
}

.diagrama .nodo-decision {
    fill: #f3e8ff;
    stroke: #7c3aed;
    stroke-width: 2;
}

.diagrama .si {
    fill: #15803d;
    font-size: 13px;
    font-weight: 900;
}

.diagrama .no {
    fill: #dc2626;
    font-size: 13px;
    font-weight: 900;
}

.pie-diagrama {
    text-align: center;
    color: #334155;
    font-size: .92rem;
    margin-top: 8px;
}

footer {
    background: var(--azul-oscuro);
    color: white;
    text-align: center;
    padding: 25px 18px;
}

footer p + p {
    margin-top: 5px;
    color: #dbeafe;
}

@media (max-width: 850px) {
    .ejemplo-card {
        grid-template-columns: 1fr;
    }

    .diagrama-panel {
        width: 100%;
    }

    .grid-simbolos {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }
}

@media (max-width: 520px) {
    nav {
        justify-content: center;
    }

    nav .enlaces {
        justify-content: center;
        gap: 12px;
    }

    .grid-simbolos {
        grid-template-columns: 1fr;
    }

    main {
        padding-left: 14px;
        padding-right: 14px;
    }

    .card,
    .ejemplo-card {
        padding: 18px;
    }
}
</style>
</head>

<body>

<header>
    <nav>
        <div class="logo">UML | INGENIERÍA DE SOFTWARE</div>

        <div class="enlaces">
            <a href="#concepto">Concepto</a>
            <a href="#simbolos">Símbolos</a>
            <a href="#ejemplo">Ejemplo</a>
        </div>
    </nav>

    <div class="hero">
        <span class="etiqueta">MODELADO DE SISTEMAS</span>

        <h1>Diagramas de<br>Actividades UML</h1>

        <p>
            Representá visualmente los pasos, las acciones
            y las decisiones que forman parte de un proceso.
        </p>

        <a class="boton" href="#concepto">Comenzar la clase ↓</a>
    </div>
</header>

<main>

    <!-- CONCEPTO -->

    <section id="concepto">
        <h2 class="titulo-seccion">
            01. ¿Qué es un diagrama de actividades?
        </h2>

        <div class="card destacado">
            <h3>Representar un proceso visualmente</h3>

            <p>
                Es un diagrama de comportamiento de UML que permite
                mostrar gráficamente cómo se desarrolla un proceso,
                desde su inicio hasta su finalización.
            </p>

            <h3 style="margin-top:20px;">¿Para qué sirve?</h3>

            <ul class="lista">
                <li>Representar los pasos de un proceso en orden.</li>
                <li>Mostrar decisiones y diferentes caminos.</li>
                <li>Comprender cómo funciona un sistema.</li>
            </ul>
        </div>
    </section>

    <!-- SIMBOLOS -->

    <section id="simbolos">
        <h2 class="titulo-seccion">
            02. Los símbolos principales
        </h2>

        <p class="intro">
            Cada símbolo tiene un significado específico.
            Las flechas muestran cómo continúa el proceso.
        </p>

        <div class="grid-simbolos">

            <article class="simbolo">
                <div class="figura">
                    <div class="inicio"></div>
                </div>

                <h3>Nodo inicial</h3>

                <p>
                    Un círculo negro indica dónde comienza el proceso.
                </p>
            </article>

            <article class="simbolo">
                <div class="figura">
                    <div class="accion">Ingresar datos</div>
                </div>

                <h3>Acción</h3>

                <p>
                    Un rectángulo con esquinas redondeadas
                    representa una tarea.
                </p>
            </article>

            <article class="simbolo">
                <div class="figura">
                    <div class="rombo"></div>
                </div>

                <h3>Decisión</h3>

                <p>
                    Un rombo representa una condición que permite
                    elegir entre distintos caminos.
                </p>
            </article>

            <article class="simbolo">
                <div class="figura">
                    <div class="flecha">→</div>
                </div>

                <h3>Flujo de control</h3>

                <p>
                    Una flecha indica el orden en que se ejecutan
                    las acciones.
                </p>
            </article>

            <article class="simbolo">
                <div class="figura">
                    <div class="final"></div>
                </div>

                <h3>Nodo final</h3>

                <p>
                    Un círculo negro rodeado por otro círculo
                    indica que finaliza toda la actividad.
                </p>
            </article>

        </div>

        <div class="nota">
            <strong>Recordá:</strong> el inicio indica dónde comienza
            el proceso, las acciones representan tareas, el rombo
            representa una decisión y el nodo final indica dónde termina.
        </div>
    </section>

    <!-- EJEMPLO EN UNA CARD -->

    <section id="ejemplo">
        <h2 class="titulo-seccion">
            03. Ejemplo: iniciar sesión
        </h2>

        <p class="intro">
            Observá cómo se utilizan los símbolos para representar
            un proceso sencillo dentro de un sistema informático.
        </p>

        <div class="card ejemplo-card">

            <!-- EXPLICACIÓN A LA IZQUIERDA -->

            <div class="ejemplo-texto">
                <h3>¿Cómo funciona?</h3>

                <p>
                    Una persona intenta ingresar a un sistema
                    utilizando su usuario y contraseña.
                </p>

                <div class="paso">
                    <span class="numero">1</span>
                    <div>
                        <strong>Inicio</strong>
                        Comienza el proceso de acceso.
                    </div>
                </div>

                <div class="paso">
                    <span class="numero">2</span>
                    <div>
                        <strong>Ingresar datos</strong>
                        La persona escribe su usuario y contraseña.
                    </div>
                </div>

                <div class="paso">
                    <span class="numero">3</span>
                    <div>
                        <strong>Verificar datos</strong>
                        El sistema comprueba la información ingresada.
                    </div>
                </div>

                <div class="paso">
                    <span class="numero">4</span>
                    <div>
                        <strong>Tomar una decisión</strong>
                        Si los datos son válidos, permite el acceso.
                        Si no son válidos, muestra un error.
                    </div>
                </div>

                <div class="paso">
                    <span class="numero">5</span>
                    <div>
                        <strong>Finalizar</strong>
                        El proceso termina cuando se accede al sistema.
                        Si los datos son incorrectos, se pueden ingresar
                        nuevamente.
                    </div>
                </div>

                <div class="nota">
                    <strong>Pregunta clave:</strong>
                    ¿Qué camino sigue el sistema si la contraseña
                    es incorrecta?
                </div>
            </div>

            <!-- DIAGRAMA A LA DERECHA -->

            <div class="diagrama-panel">
                <h3>Representación UML</h3>

                <svg class="diagrama"
                     viewBox="0 0 390 590"
                     role="img"
                     aria-labelledby="titulo-svg descripcion-svg">

                    <title id="titulo-svg">
                        Diagrama UML de inicio de sesión
                    </title>

                    <desc id="descripcion-svg">
                        El proceso comienza, se ingresan los datos
                        y se verifican. Si son válidos, se accede
                        al sistema. Si no, se muestra un error y
                        se puede volver a ingresar los datos.
                    </desc>

                    <defs>
                        <marker id="punta"
                                markerWidth="8"
                                markerHeight="8"
                                refX="7"
                                refY="3"
                                orient="auto">
                            <path d="M0,0 L0,6 L8,3 Z"
                                  fill="#334155"/>
                        </marker>
                    </defs>

                    <!-- INICIO -->
                    <circle cx="190" cy="24" r="10" fill="#111827"/>

                    <path class="flujo" d="M190 34 V57"/>

                    <!-- INGRESAR DATOS -->
                    <rect class="nodo-accion"
                          x="95" y="59"
                          width="190" height="49"
                          rx="14"/>

                    <text x="190" y="79" text-anchor="middle">
                        <tspan x="190">Ingresar usuario</tspan>
                        <tspan x="190" dy="17">y contraseña</tspan>
                    </text>

                    <path class="flujo" d="M190 108 V132"/>

                    <!-- VERIFICAR -->
                    <rect class="nodo-accion"
                          x="95" y="134"
                          width="190" height="43"
                          rx="14"/>

                    <text x="190" y="160" text-anchor="middle">
                        Verificar datos
                    </text>

                    <path class="flujo" d="M190 177 V201"/>

                    <!-- DECISION -->
                    <polygon class="nodo-decision"
                             points="190,201 243,239 190,277 137,239"/>

                    <text x="190" y="243" text-anchor="middle">
                        ¿Son válidos?
                    </text>

                    <!-- CAMINO SI -->
                    <path class="flujo" d="M243 239 H300 V306"/>

                    <text class="si" x="263" y="227">Sí</text>

                    <rect x="238" y="308"
                          width="130" height="47"
                          rx="13"
                          fill="#dcfce7"
                          stroke="#15803d"
                          stroke-width="2"/>

                    <text x="303" y="327" text-anchor="middle">
                        <tspan x="303">Acceder al</tspan>
                        <tspan x="303" dy="17">sistema</tspan>
                    </text>

                    <path class="flujo" d="M303 355 V382"/>

                    <!-- FINAL -->
                    <circle cx="303" cy="397" r="11"
                            fill="#111827"
                            stroke="white"
                            stroke-width="3"/>

                    <circle cx="303" cy="397" r="14"
                            fill="none"
                            stroke="#111827"
                            stroke-width="2"/>

                    <!-- CAMINO NO -->
                    <path class="flujo" d="M137 239 H78 V306"/>

                    <text class="no" x="91" y="227">No</text>

                    <rect x="13" y="308"
                          width="130" height="47"
                          rx="13"
                          fill="#fee2e2"
                          stroke="#dc2626"
                          stroke-width="2"/>

                    <text x="78" y="327" text-anchor="middle">
                        <tspan x="78">Mostrar</tspan>
                        <tspan x="78" dy="17">mensaje de error</tspan>
                    </text>

                    <!-- RETORNO PARA REINTENTAR -->
                    <path class="flujo"
                          d="M78 355 V450 H12 V83 H92"/>

                    <text x="16" y="437"
                          style="font-size:11px; fill:#dc2626;">
                        Reintentar
                    </text>

                </svg>

                <p class="pie-diagrama">
                    Las flechas indican el recorrido del proceso.
                    El rombo divide el flujo según la condición.
                </p>
            </div>

        </div>
    </section>

    <!-- FUENTES -->

    <section>
        <h2 class="titulo-seccion">Para seguir aprendiendo</h2>

        <div class="card">
            <p>
                <strong>Video de referencia:</strong>
            </p>

            <p style="margin-top:8px;">
                <a href="https://www.youtube.com/watch?v=GoYdpOVhDRc&t=336s"
                   target="_blank"
                   rel="noopener">
                    Ver el video sobre diagramas de actividades UML
                </a>
            </p>

            <p style="margin-top:18px;">
                <strong>Material complementario:</strong>
            </p>

            <p style="margin-top:8px;">
                <a href="https://lucid.co/es/diagrama/uml/tutorial-diagrama-de-actividad"
                   target="_blank"
                   rel="noopener">
                    Tutorial de diagramas de actividades UML — Lucidchart
                </a>
            </p>
        </div>
    </section>

</main>

<footer>
    <p><strong>Ingeniería de Software | Diagramas de Actividades UML</strong></p>
    <p>Aprender a modelar es aprender a representar cómo funciona un proceso.</p>
</footer>

</body>
</html>
