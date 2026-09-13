# Escalera de alcance (MoSCoW) · IAsLab ORCHID

> [!IMPORTANT]
> **Propuesta para discutir, todavía no es alcance.** La línea de corte la fijan el equipo y el tutor ([ADR-032](./ADR.md)). Mientras no quede escrita en la sección *Línea de corte* de este archivo, ninguna fila es compromiso del proyecto, y la columna MoSCoW es solo un punto de partida.

## Para qué sirve

El tutor pidió dos cosas el 2026-09-09. La primera, ordenar los requerimientos con MoSCoW antes de seguir escribiendo: «Hay un patrón que se llama must have, should have y puede estar en un futuro» [10:01]. La segunda, que el equipo proponga hasta dónde llega y él decida: «ustedes me proponen hasta qué punto quieren llegar y yo les digo si hasta ahí o no, un poco más, un poco menos» [55:28].

Esta tabla reúne lo que se ha pedido en las tres reuniones y lo que ya exige `requirements.md`. Lo ordena de lo mínimo indispensable a lo que podría añadirse en el futuro, para que el corte sea una sola decisión.

## Cómo leer la escalera

- **Orden.** Las filas van de los cimientos hacia arriba, y cada una depende solo de filas anteriores (columna *Depende de*). Por eso el alcance se corta con **una sola línea horizontal**: lo que queda por encima es compromiso del PDG y lo de abajo se documenta como trabajo futuro.
- **MoSCoW (propuesta inicial).**
  - **Must:** sin esto la plataforma no existe o no responde al problema.
  - **Should:** esperado y valioso, pero el proyecto se sostiene sin ello.
  - **Could:** deseable si sobra tiempo.
  - **Won't:** fuera de este PDG.
  
  La propuesta se armó con la evidencia citada en cada fila. El equipo puede mover cualquier fila.
- **Origen.**
  - **hecho:** está en `project-context/` y es citable en la tesis.
  - **acta:** solo consta en una reunión (`meetings/`). Es evidencia propuesta y no se cita en la tesis hasta promoverse (regla 9 de `CLAUDE.md`).
- **Objetivo hoy.** El objetivo específico del cap. 04 que hoy compromete la fila. Si la línea deja fuera una fila que un objetivo compromete, ese objetivo tiene que reescribirse.

Las actas se citan por fecha y marca de tiempo: `[08-26 52:07]` es la reunión del 2026-08-26, minuto 52:07.

---

## La escalera

### Nivel 0 · Cimientos de infraestructura

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-01 | Clúster Kubernetes operando sobre las 31 estaciones de la sala 104M, con el nodo máster ubicado en una de las opciones posibles | ninguna | **Must** | Es la base de todo lo demás. Tutor: «lo más difícil, honestamente, es montar el cluster» [08-26 40:23]; «que este proyecto permita fundamentar las bases» [08-26 20:57]. hecho: `requirements.md` §4 (sala, 31 equipos), `technologies.md` §A.1 (opciones de máster) | general |
| A-02 | GPU RTX 4090 expuestas al clúster (NVIDIA GPU Operator) y pesos de modelos en una partición de disco dedicada | A-01 | **Must** | Sin GPU visibles no hay inferencia. hecho: `requirements.md` NFR-02, NFR-03; `technologies.md` §A.3 | general |
| A-03 | El clúster convive con las clases: los equipos siguen usables, y las pruebas que degradan rendimiento van fuera de horario | A-01 | **Must** | Restricción operativa de la sala, no negociable. hecho: `requirements.md` §4 «Shared use with classes». El reparto «infraestructura en CPU y RAM, motor en GPU» es acta [09-04 22:18] | ninguno |
| A-04 | Infraestructura como código, documentada y automatizada (GitOps), redesplegable en otra sala | A-01 | **Must** | Fue la contrapartida acordada al descartar OpenStack: «algo que sí podemos comprometernos es que sí esté bien documentado y como bien automatizado» [09-09 39:50]. Responde a la mayor preocupación del tutor [09-09 32:51]. acta | ninguno |

### Nivel 1 · Primer flujo de extremo a extremo

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-05 | Inicio de sesión con SAAMFI en frontend y backend, con dos roles: administrador y usuario | A-01 | **Must** | Primer entregable visible que esperaba el tutor: «que por lo menos ya esté el flujo de autenticación instalado en su servicio backend y frontend» [08-26 52:07]; roles «administrador y usuario, de momento» [09-09 22:48]. hecho: `requirements.md` NFR-05, FR-02.4 | obj 2 |
| A-06 | Desplegar desde la plataforma un modelo ya entrenado en un nodo, empaquetado como imagen de contenedor sobre KubeRay, con un primer motor (llama.cpp) | A-02, A-05 | **Must** | Es el caso de uso que consume la capa inferior. hecho: `documentation.md` *Scope* «Architectural core»; `requirements.md` FR-01.1, FR-01.3, FR-01.4 | obj 3 |
| A-07 | Punto de entrada único (AI Gateway) con API compatible con OpenAI y *API key* por usuario para consumir el modelo desplegado | A-06 | **Must** | El tutor lo esperaba al cierre de PDG1: «que el AI Gateway por lo menos esté configurado» [08-26 52:07]. Es también donde se aplicarán las cuotas. hecho: `requirements.md` FR-01.5; `technologies.md` §B.1 | obj 3 |
| A-08 | El mismo flujo sirve al menos un modelo que no es de lenguaje (por ejemplo, un modelo PyTorch) | A-06 | **Must** | «Quítense eso de la mente de que el proyecto está enfocado a modelos largos de lenguaje» [09-09 25:18]. hecho: `requirements.md` FR-01.4 (cargas no LLM) | obj 3 |

### Nivel 2 · Observabilidad

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-09 | Panel con telemetría de *hardware* por nodo (temperatura, VRAM, potencia de GPU, CPU, RAM), sin importar qué carga corra | A-02 | **Must** | El tutor puso como antipatrón un proyecto donde «la observabilidad depende puramente de Ray» [08-26 38:22]. hecho: `requirements.md` FR-03.1 | obj 1 |
| A-10 | Telemetría de la carga servida: *tokens* por segundo, latencia, tiempo en cola | A-06, A-09 | **Must** | «tanto de modelo como de hardware» [09-09 28:39]. hecho: `requirements.md` FR-03.2 | obj 1 |

### Nivel 3 · Gobernanza mínima

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-11 | Cuota de recursos por usuario aplicada en el clúster, con un panel donde el administrador ve cuánto consume cada uno | A-05, A-07, A-09 | **Must** | Es el hueco que el tutor no quiere repetir: «nadie está gestionando la capa de, por ejemplo, de cuotas» [08-26 38:22]; pidió un panel, no solo *backend* [09-09 24:29]. hecho: `requirements.md` FR-02.4 | obj 2 |
| A-12 | El administrador ve todos los modelos en ejecución y puede apagarlos, encenderlos o deshabilitarlos | A-06, A-11 | **Must** | Funciones del administrador descritas por el tutor [09-09 22:48]. hecho: `requirements.md` FR-02.4 | obj 2 |
| A-13 | Reserva de cupos por adelantado, con inicio y fin automáticos | A-11 | **Must** | Es el mecanismo del modelo de gobernanza. hecho: `requirements.md` FR-02.1 | obj 2 |

### Nivel 4 · Evaluación mínima

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-14 | Prueba de carga con 20 usuarios simultáneos sobre la plataforma, fuera del horario de clases | A-07, A-10, A-11 | **Must** | Es el único criterio de aceptación cuantitativo decidido. hecho: `documentation.md` *Formulation of Objectives* ítem 4 (ADR-004); `requirements.md` §4 (horario) | obj 4 |

> Hasta aquí llega la propuesta de **mínimo indispensable**: una plataforma que existe, autentica, despliega y sirve modelos, se observa, reparte recursos por usuario y se prueba con la concurrencia objetivo.

### Nivel 5 · Lo esperado que completa los objetivos actuales

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-15 | Cuestionario *System Usability Scale* aplicado a usuarios del laboratorio | A-12, A-13 | **Should** | Mide aceptación con poco costo. Sin él, la evaluación queda solo en desempeño. hecho: `documentation.md` ítem 4 | obj 4 |
| A-16 | La telemetría separa el consumo de entrenamiento del de inferencia, según el plano de control por el que entró el trabajo | A-09 | **Should** | ⚠ Depende de que el proyecto hermano conecte su plano de control al clúster, lo que el equipo no controla. hecho: `requirements.md` FR-03.5, FR-02.6 | obj 1 (en parte) |
| A-17 | Las cuotas y reservas cuentan también los trabajos de entrenamiento del proyecto hermano | A-13, A-16 | **Should** | El tutor lo pidió: «pueda yo entrenar modelos cualquiera de otro tipo» [08-26 44:58]. ⚠ Misma dependencia externa que A-16. hecho: `requirements.md` FR-02.6 | obj 2 |
| A-18 | Prioridad de profesores sobre estudiantes para reclamar recursos y repartir la capacidad de la sala | A-13 | **Should** | ⚠ Tensión. El 08-26 el tutor describió a un profesor que asigna «tanto de GPUs por tantas horas» a un proyecto [45:39]; el 09-09 dejó estudiante y profesor para después: «Si a futuro sí estudiante y profesor, bueno, chévere» [22:48]. Los autores lo confirmaron en FR-02.7. hecho: `requirements.md` FR-02.7 | obj 2 |
| A-19 | Logs centralizados (Loki) para diagnosticar congelamientos y falta de memoria | A-09 | **Should** | Alejandro: «Porque eso nos pasa mucho» [09-04 22:18]. hecho: `requirements.md` FR-03.3 | ninguno |
| A-20 | Detección automática de nodo caído o congelado, con alerta al administrador | A-09, A-19 | **Should** | Modo de fallo conocido de la sala. hecho: `requirements.md` FR-03.4 | ninguno |
| A-21 | Corte automático de la sesión al vencer la reserva, con aviso y guardado de estado | A-13 | **Should** | Sin corte, una reserva vencida sigue ocupando la GPU. hecho: `requirements.md` FR-02.5 | ninguno |
| A-22 | *Benchmarking* automatizado con especificaciones YAML, reutilizando el harness del laboratorio | A-06 | **Should** | ⚠ Sin decidir si se reutiliza o se construye (ADR-031). Alejandro lo dejó para el tutor [09-04 20:32]. hecho: `requirements.md` FR-04.1; `documentation.md` «Institutional antecedents» | cap. 07 y 08 |

### Nivel 6 · Extensiones deseables

| ID | Capacidad al terminar | Depende de | MoSCoW | Por qué y de dónde sale | Objetivo hoy |
| :--- | :--- | :--- | :---: | :--- | :--- |
| A-23 | Sobreasignación controlada del 10 % al 20 % sobre las reservas | A-13 | **Could** | Optimiza el uso, pero la gobernanza funciona sin ella. hecho: `requirements.md` FR-02.3 | ninguno |
| A-24 | Comparación formal de motores de inferencia bajo cargas idénticas | A-22 | **Could** | Alejandro pidió comparar los motores [09-04 7:34]. hecho: `requirements.md` FR-04.3 | ninguno |
| A-25 | Evaluación de la calidad del código que generan los modelos | A-22 | **Could** | Contraprestación que pidió Alejandro [09-04 14:59, 20:32]. hecho: `requirements.md` FR-04.2 | ninguno |
| A-26 | Selector gráfico del nodo o tipo de *hardware* al desplegar | A-06 | **Could** | Comodidad de uso. hecho: `requirements.md` FR-01.2 | ninguno |
| A-27 | Acceso a los modelos desde el IDE o por sesiones remotas seguras, además de la API | A-07 | **Could** | hecho: `requirements.md` FR-01.5 (segunda mitad) | ninguno |
| A-28 | Enrutamiento por perfil: unas máquinas con modelos potentes y otras con modelos rápidos | A-07, A-10 | **Could** | Petición de Alejandro [09-04 7:34]. acta | ninguno |
| A-29 | Alta de un modelo desde repositorio o archivo con búsqueda automática de parámetros de ejecución | A-06, A-22 | **Could** | Petición de Alejandro [09-04 4:37]. La carga desde repositorio ya es FR-01.1; la búsqueda de parámetros es acta | ninguno |
| A-30 | Encendido remoto por red de nodos apagados, con alerta si no responden | A-20 | **Could** | Alejandro lo pidió y lo considera barato; nadie dijo si entra [09-04 4:37]. acta | ninguno |

### Nivel 7 · Fuera de este PDG

| ID | Capacidad | MoSCoW | Por qué y de dónde sale |
| :--- | :--- | :---: | :--- |
| A-31 | Prioridad de reserva por curso académico y cuotas ligadas a horarios de clase | **Won't** | El tutor la dejó fuera: «yo no tenía planeado que en este PDG el sistema de, por ejemplo, de cursos» [09-09 19:22]. ⚠ `requirements.md` FR-02.2 todavía la exige (ADR-029) |
| A-32 | Inferencia distribuida entre nodos por red | **Won't** | hecho: `requirements.md` §4 (la red de 10 Gbit/s no la sostiene; un modelo por máquina) |
| A-33 | Cuantización de modelos como proceso propio | **Won't** | hecho: `requirements.md` FR-01.3 |
| A-34 | Nube privada con OpenStack debajo de la plataforma | **Won't** | «siento que eso es un PDG chiquito por sí solo» [09-09 39:12]; el tutor lo aceptó [39:49]. acta |
| A-35 | Máquinas virtuales para que los estudiantes hagan pruebas remotas | **Won't** | Planteado por el tutor como necesidad futura [09-09 31:55]. acta |
| A-36 | Proyectos de consultoría como usuarios de la plataforma | **Won't** | Mencionado por Alejandro [09-04 4:37]; no está en los roles de FR-02.4. acta |
| A-37 | Funcionalidades de entrenamiento de modelos | **Won't** | Las cubre el proyecto hermano. hecho: `documentation.md` *Scope* «Exclusions» |
| A-38 | Soporte y mantenimiento después del cierre | **Won't** | Lo asume el IAsLab. hecho: `documentation.md` *Scope* «Post-project support» |

---

## Tensiones que conviene resolver al fijar la línea

1. **Prioridad de profesores (A-18).** Hoy la compromete el objetivo 2, pero el tutor la dejó para el futuro el 09-09. Si queda debajo de la línea, el objetivo 2 pierde «con prioridad de los profesores».
2. **Cargas de entrenamiento (A-16, A-17).** El objetivo 2 promete reservar cupos «para cargas de inferencia y de entrenamiento», pero eso depende de otro proyecto de grado. Comprometerlo como Must ata el resultado de este PDG a un trabajo ajeno.
3. **Prioridad por curso (A-31).** La propuesta la deja fuera, como pidió el tutor; FR-02.2 la mantiene. Cerrar ADR-029 en la misma decisión.
4. **Benchmarking (A-22).** Reutilizar o construir cambia el peso de la fase de evaluación. Cerrar ADR-031 en la misma decisión.
5. **Evaluación de usabilidad (A-15).** El objetivo 4 incluye el *System Usability Scale*. Si la línea lo deja debajo, el objetivo 4 queda solo con la prueba de carga.
6. **GitOps (A-04).** La propuesta lo pone como Must porque fue lo acordado a cambio de descartar OpenStack, pero hoy solo consta en el acta del 09-09: conviene promoverlo o retirarlo (ADR-030).

## Lo que el tutor esperaba al cierre de PDG1

Dato de contexto para ADR-033, no compromiso: el 2026-08-26 el tutor esperaba para el final de PDG1 la infraestructura configurada (A-01, A-02), el AI Gateway configurado (A-07) y la autenticación con SAAMFI funcionando (A-05) [08-26 52:07]. Según el calendario de `README.md`, PDG1 termina en los primeros días de diciembre de 2026 y PDG2 va de febrero a mayo de 2027.

---

## Línea de corte

> **Pendiente (ADR-032).** Cuando el equipo y el tutor la fijen, anotar aquí:
>
> - **Fecha y participantes:**
> - **Última fila dentro del alcance:** (por ejemplo, «hasta A-22, sin A-18»)
> - **Filas que cambian de categoría respecto a la propuesta:**
> - **Objetivos del cap. 04 que hay que reescribir:**

## Qué hay que actualizar cuando se fije

- `thesis/chapters/04-objetivos.tex`: cada objetivo compromete solo filas por encima de la línea.
- `thesis/chapters/07-metodologia.tex`: fases y cronograma reconstruidos desde las filas dentro del alcance, repartidos entre PDG1 y PDG2 (ADR-033).
- `thesis/chapters/08-contribucion-resultados.tex`: tabla de resultados y entregables.
- `project-context/requirements.md`: marcar como fuera de alcance los FR de las filas que queden debajo.
- `project-context/ADR.md`: cerrar ADR-029, ADR-031 y ADR-032.
