# Reunión 2026-09-04 — Elicitación con Alejandro: uso real de la sala, motor de inferencia y benchmarks

- **Participantes:** Alejandro Muñoz Bravo (laboratorio IAsLab) · Juan José De La Pava Giraldo, Juan Camilo Melo López (autores). **Ausente:** Juan David Pacheco Vargas — «él no va a poder estar el día de hoy, pues, porque tiene clase» [1:05]. **El tutor (Kevin) no participó.**
- **Tramo cubierto:** [0:00] – [26:12]
- **Fuente:** transcripción pegada en el chat, no versionada (ver [`README.md`](./README.md)). Generada por Read.AI [25:20].

> **Contexto.** Esta es la reunión de elicitación de requerimientos que el tutor pidió el 2026-08-26 (ver [`2026-08-26-tutor-arquitectura.md`](./2026-08-26-tutor-arquitectura.md), *Compromisos*). **Compromiso cumplido.** La reunión con el profesor Juan Carlos Muñoz ya había ocurrido antes — «el día miércoles que tuvimos la reunión con el profesor Juan Carlos» [6:23] — y **no hay transcripción de esa**: lo que se sabe de ella llega de segunda mano por De La Pava.

> **Sobre las citas.** La transcripción deforma casi todo el vocabulario técnico. Citas literales, lectura entre corchetes: llama.cpp aparece como «LAMA», «llama a CP», «llama FPP», «YAMACP, CPP»; vLLM como «VLM», «BLM», «VLLM»; Ollama como «OLAMA»; LiteLLM como «Light LLM»; RTX 4080 como «ARTX 4080»; tokens como «toques»; Antigravity como «antigravity»; Claude como «Cloud CLI» y «cloud»; ChatGPT como «JPPT». Nombres: Kevin aparece como «Kenny» y posiblemente como «IKEA»; el proyecto de Sara como «Zara».

> **Naturaleza de la reunión.** Fue **elicitación, no toma de decisiones**: Alejandro describe cómo opera hoy el laboratorio y pide características. Por eso la sección de decisiones es corta y las de hechos y peticiones son largas. No se ascendió ninguna petición a decisión.

---

## Decisiones tomadas

- **El laboratorio ya descartó vLLM en la práctica; el motor en uso es llama.cpp compilado a medida.** Decisión tomada antes de la reunión y comunicada aquí. — «en un principio IKEA [¿Kevin?] nos recomendó utilizar VLM [vLLM], pero el día miércoles que tuvimos la reunión con el profesor Juan Carlos nos dijo que ustedes no habían logrado tener buenos resultados con ese motor de inferencia, que sería mejor llegar a utilizar uno LAMA o un LLM» [6:23]; Alejandro confirma: «Llama a CP, llama a CP» [6:47]; «se hizo una compilación específica de YAMACP, CPP [llama.cpp], para basar las características del hardware que tienen esas máquinas» [7:34]
  · afecta: `project-context/technologies.md`, `thesis/chapters/01-motivacion-antecedentes.tex` — ver *Contradicciones*

- **La inferencia distribuida queda fuera de alcance por falta de hardware de red.** — «quisiéramos ejecutarlos por una red de al menos **25 gigas por segundo, pero esos switches no los tenemos aún**» [7:34]; «van a ser modelos que quizás sean más grandes, pero van a ser más lentos porque están limitados por la velocidad de la red» [7:34]; y ya lo había dicho Juan Carlos: «el profesor Juan Carlos nos dijo que no era viable debido a las limitaciones de hardware» [13:52]
  · afecta: `thesis/chapters/03-hipotesis-restricciones.tex` `\item[Límites de red y capacidad física del laboratorio]`, que hoy lo enuncia sin cifra
  · Alejandro deja abierto si el PDG lo aborda igualmente: «no sabemos si en el alcance de su PDG podría llegar a abordarse esa parte» [7:34]

- **Un modelo por máquina; el paralelismo entre tarjetas no se persigue.** — «Con el profesor Juan Carlos quedamos en que las limitaciones de hardware nos dan para desplegar un modelo en un computador» [2:09]

## Compromisos

- **Alejandro** — dar acceso al repositorio con el harness de benchmarks (Bitbucket o GitHub) — *al recibir el correo* · «mandame un correo consultorio [con el usuario] de GitHub y yo le doy acceso al repositorio» [20:04]; «Sé que lo metí en un repositorio, pero no recuerdo exactamente en qué repositorio» [18:59]
- **Autores** — enviarle a Alejandro el usuario de GitHub para el acceso — *sin fecha* · «Obtener acceso al repositorio» [20:25]
- **Autores** — consultar con Kevin si el harness de benchmarks entra en el alcance del PDG — *sin fecha* · «Ahí lo hablan con Kenny [Kevin], si algo, si lo van a colocar dentro del scope» [20:32]; «no sé si eso entra en nuestro scope, tendríamos que hablarlo con Kevin» [17:58]
- **Autores** — armar un documento para la semana siguiente — *semana del 2026-09-07* · «Tenemos que armar un pequeño documento para la próxima semana y eso ya lo discutimos con Kevin» [25:55]
- **Autores (contraprestación pedida por Alejandro)** — ayudar a revisar la calidad del código que producen los modelos evaluados · «me sirve para que me ayuden a revisar los códigos que votan esos modelos» [20:32]

## Respuestas a dudas abiertas (ADR)

**Ninguna duda abierta quedó respondida.** Una quedó peor de lo que estaba:

- **ADR-013 — ¿Cuál es la VRAM real por nodo?** — **la reunión la contradice en vez de cerrarla.** Alejandro identifica la tarjeta como **RTX 4080** (16 GB), que es lo que ya dice `project-context/requirements.md` y lo contrario de lo que se dijo el 26-ago: «la gráfica, pues, ARTX 4080 [RTX 4080], creo que no recuerdo exactamente la referencia» [7:34]
  · **sigue abierta**, y ahora con **testimonio contradictorio de dos fuentes**, ambas vacilantes: Pacheco dijo «como de 32 de RAM, **24** de GPU» [2026-08-26, 28:34] y Alejandro dice RTX 4080 «creo que no recuerdo exactamente la referencia» [7:34].
  · Hay una tercera cifra, en una frase que la transcripción destroza: «uno puede decir yo puedo modelo y ocupa **23 GB** de RAM y resulta que está RAM 124» [22:18]. No es utilizable como evidencia.
  · **No se resuelve por testimonio.** Cerrarla exige `nvidia-smi` en una máquina de la sala.

- **ADR-004 — criterio cuantitativo de aceptación operacional** — **sigue abierta, pero ya hay línea base medida** (ver *Hechos nuevos*). Alejandro explícitamente no fija umbral: «10, 15 minutos, Es bastante, pero hay que revisar» [7:34].

- **ADR-017 — fase de estabilización del backlog heredado** — **segunda reunión consecutiva en la que no se menciona.** Todo lo discutido es infraestructura desde cero. Ver *Contradicciones*.

- **ADR-011 (SAAMFI), ADR-016 (DSR+Scrum), ADR-001, ADR-010, ADR-012** — no se tocaron.

## Contradicciones con `project-context/`

- **El motor de inferencia** — la reunión dice que el laboratorio **no obtuvo buenos resultados con vLLM** y usa llama.cpp [6:23, 6:47, 7:34]; `project-context/technologies.md` registra vLLM en la pila tecnológica, y `thesis/chapters/01-motivacion-antecedentes.tex` construye **el argumento central de viabilidad** sobre él, citando a `kwon-pagedattention-2023` (PagedAttention, mejora de 2 a 4 veces)
  · **sin resolver.** Es la contradicción más cara de las tres: el capítulo 1 justifica que el despliegue on-premise es viable apoyándose en un motor que el propio laboratorio descartó por resultados. O se documenta por qué no funcionó ahí y se reencuadra el argumento, o el argumento queda desmentido por la evidencia local.
  · Alejandro pide justamente eso, y lo pide como trabajo formal: «lo que también me gustaría es que podrían llegar a ser como una investigación formal» [7:34], sobre el trade-off vLLM / llama.cpp / Ollama: «sabemos que OLAMA [Ollama] es una capa más arriba que LLAMA [llama.cpp] y que ya configura ciertas cosas que uno en LLAMA no puede configurar más […] hay que revisar como esos trade-offs» [7:34]

- **VRAM y modelo de GPU** — ver ADR-013 arriba. La contradicción reportada el 26-ago **no se confirma**: esta reunión respalda los 16 GB de `requirements.md`. Queda un empate entre dos testimonios vacilantes.

- **El AI Gateway: ¿se desarrolla o se usa LiteLLM?** — la reunión dice que **LiteLLM ya está en uso**: «por ahí también estaba como el proxy que estamos usando también, que se llama Light LLM [LiteLLM] […] compatible pues con el API de OpenAI y que permite pues un simple punto, un solo punto de entrada» [7:34]; el tutor había decidido lo contrario el 26-ago: «no tengamos que usar LightLLM, toca hacer el LightLLM pero puramente enfocado a cualquier AI Gateway» [2026-08-26, 49:13]
  · **sin resolver.** No es contradicción con `project-context/` sino **entre el tutor y el laboratorio**, y decide si el objetivo de gobernanza es desarrollo desde cero o integración sobre algo ya desplegado. Toca ADR-015.

- **La fase de estabilización del backlog heredado** — `project-context/documentation.md` la exige y `thesis/chapters/07-metodologia.tex` abre las fases con ella; **en esta reunión tampoco aparece**, y De La Pava describe el proyecto como greenfield: «lo que se quiere realizar con este PDG es volver utilizables y medibles los computadores del 104M […] instalar dentro de todos esos computadores un clúster de Kubernetes» [2:09]
  · **sin resolver** — refuerza ADR-017 con una segunda ausencia, esta vez en boca de los propios autores.

## Hechos nuevos del proyecto (candidatos a `project-context/`)

- **La sala tiene 31 máquinas.** — «En la sala hay 31 máquinas» [7:34] · destino: `project-context/requirements.md`. Es la primera cifra de inventario que aparece en cualquier reunión.
- **Línea base de desempeño real, medida:** ~20 tokens/s con el modelo en uso; 10–15 minutos por respuesta frente a 30 s–1 min de un modelo de frontera. — «tiene una velocidad de toques [tokens] como de 20 toques por segundo, entonces es bastante lenta» [7:34]; «este modelo de nosotros nos está demorando entre 10 y 15 minutos» [7:34] · destino: `project-context/requirements.md`. **Insumo directo para ADR-004.**
- **Resultados concretos del harness:** una calculadora básica tarda ~5 min (Antigravity: 20–30 s); una API completa tarda ~20 min (Antigravity: 3–4 min). — [14:59] · destino: `project-context/requirements.md`
- **El harness de benchmarks ya existe** y es un script de Python guiado por especificaciones YAML que simula un agente, ejecuta llamadas a herramientas y mide tokens/s de entrada y salida, tiempos y si pasan las pruebas. — «Actualmente, lo que tengo es un benchmark automatizado con un script de Python. Entonces, básicamente, tengo un esquema donde tengo unas especificaciones» [14:59]; «hay métricas que saco como […] tokens por segundo de entrada y también tokens por segundo de salida, los tiempos que se han demorado» [14:59] · destino: `project-context/requirements.md`. Afecta al requisito de *benchmark harness*: no hay que construirlo de cero.
- **Métrica que el harness todavía no cubre:** la calidad del código generado. — «hay que revisar si lo que está entregando, pues, qué tan de buena calidad llegan a ser […] esas serían otras métricas que entrarían dentro de la evaluación» [14:59]
- **Almacenamiento de modelos:** partición de disco dedicada, montada aparte del sistema de archivos principal; 10 modelos ocupan 150–200 GB. — «hacer una partición del disco y montarla sobre un directorio dedicado a almacenar los modelos […] descargué 10 modelos y eso básicamente son como 150 o 200 gigas» [7:34] · destino: `project-context/technologies.md`
- **Uso actual: experimentación, no explotación.** — «como ahorita estamos simplemente es como haciendo experimentos, no en un uso continuo o explotación directa, sino más a nivel de experimentación» [7:34] · destino: `project-context/documentation.md`. **Refuerza ADR-014** (subutilización) con un testigo operativo.
- **Modo de fallo confirmado con umbral:** la GPU al 90–95 % de uso sostenido congela la máquina. — «qué pasa cuando uno tiene la gráfica como al 90 por ciento, 95 por ciento de uso. Después de ciertos tiempos llegan y se congelan y entonces ya dejan de responder» [22:18]; «hay unas máquinas que se congelan» [22:18] · **confirma FR-03.4 de `requirements.md`** con evidencia de campo, no supuesta.
- **Causa física del congelamiento, no registrada hasta ahora:** la fuente de poder de la torre. — «si la fuente que tiene configurada la torre no soporta la cantidad de potencia que se está consumiendo […] pues el computador se va a congelar» [22:18] · **da razón operativa al FR-03.1** (`power draw in Watts`), que hoy figura sin justificación.
- **Motivo institucional nuevo para el proyecto:** demostrar uso para justificar inversión. — «si con esta plataforma se puede llegar a mostrarle pues a los ejecutivos cierto que la sala está siendo utilizada pues puede que sea como una buena prueba para hacer que ellos inviertan más y poder conseguir estos equipos» [13:52] (De La Pava, reportando a Juan Carlos) · destino: `thesis/chapters/01-motivacion-antecedentes.tex`, justificación
- **Usuario no contemplado: proyectos de consultoría.** — «como mirar la posibilidad de poderlos hacer para proyectos de consultoría que así solemos tener» [4:37] · destino: `project-context/documentation.md`. No aparece entre los roles de `requirements.md` (pregrado, electiva, semilleros, profesores).
- **Los modelos se descargan de un repositorio externo** — «nosotros los descargamos directamente de una cuenta de GDFS [¿Hugging Face?]. Es como que se descarga los repositorios donde tenemos los modelos» [7:34] · lectura incierta, verificar antes de escribirlo.
- **Cambió el monitor de sala**, lo que afecta la logística de acceso — «creo que Ricardo cambió, ¿cierto? Ya no es el mismo monitor de sala» [20:42]

### Requisitos que pidió Alejandro y no están en `requirements.md`

- **Encendido remoto por red y alerta de nodo caído.** — «uno a través del cable de red, uno podría llegar a configurarlos para que se puedan llegar a prender, de tal forma que automáticamente el clúster debería poder detectarse alguno que está apagado, intentarlo prender. Y el caso de que no lo pueda prender […] que lance una alerta a la administradora» [4:37]. Alejandro lo considera barato: «creo que no está complicado, o sea, es simplemente un tema de configuración» [4:37]
- **Alta de modelos nuevos desde repositorio o archivo, con autoconfiguración.** — «pueda vincularse con algún repositorio o colocarle directamente el archivo .book [¿.gguf?] y que él sea capaz de correrlo y configurarlo y tratar de buscar como las mejores optimizaciones de parámetros para poderlo ejecutar» [4:37]
- **Enrutamiento por perfil de modelo:** máquinas distintas sirviendo modelos distintos, y la petición se dirige al que corresponda según si necesita razonar o solo responder rápido. — «no todas las máquinas desplegando el mismo modelo, sino unas ciertas máquinas, unos modelos más potentes, otras no tan potentes […] si necesitas un servicio más soft […] quizás necesitamos un modelo que no sea tan potente, pero que sí sea más rápido» [7:34]
- **Logs de diagnóstico de congelamiento.** — «poder también como meter algún mecanismo de diagnóstico, ¿cierto? Como que guarden logs para ver si se están congelando las máquinas. Porque eso nos pasa mucho» [22:18]
- **Separar el presupuesto de recursos:** que la infraestructura consuma CPU y RAM, y el motor de inferencia la GPU. — «tienen que revisar que estén bien configurados para que esos recursos de la infraestructura sean recursos de CPU y de RAM. Que los recursos del motor de inteligencia [inferencia] de la gráfica» [22:18]

## Preguntas que quedaron abiertas (candidatas a ADR nueva)

- **¿Qué motor de inferencia adopta la plataforma: vLLM, llama.cpp u Ollama?** El laboratorio descartó vLLM, `technologies.md` lo registra y el cap. 01 argumenta sobre él. Alejandro pide una comparación formal de los tres [7:34] · a quién corresponde: autores + tutor + laboratorio · **la más urgente: bloquea el cap. 01 y el estado del arte**
- **¿El harness de benchmarks de Alejandro entra en el alcance del PDG?** Quedó explícitamente aplazado para consultarlo con Kevin [17:58, 20:32] · a quién corresponde: tutor
- **¿Se adopta LiteLLM o se desarrolla el AI Gateway?** El tutor dijo desarrollarlo [2026-08-26, 49:13]; el laboratorio ya lo tiene desplegado [7:34] · a quién corresponde: tutor + laboratorio
- **¿Entra el encendido remoto de nodos (Wake-on-LAN) en el alcance?** Alejandro lo pide y lo considera barato; nadie dijo si se acepta [4:37] · a quién corresponde: tutor
- **¿Qué modelo se está usando realmente?** La transcripción da «Cuent 3.8» [1:05] y «gamma 3.8» [7:34], y la reunión del 26-ago hablaba de uno de 27 mil millones de parámetros. Son escalas distintas · a quién corresponde: laboratorio
- **¿Los proyectos de consultoría son usuarios de la plataforma?** Aparece por primera vez y no está en los roles de `requirements.md` [4:37] · a quién corresponde: tutor + laboratorio

## Discutido sin conclusión

- **Los objetivos del PDG.** Alejandro preguntó de entrada «no sé cómo se están relacionando ustedes con el PDG de Zara [Sara]» y «como qué objetivos han sacado» [1:52]; De La Pava respondió que aún no hay objetivos propios: «no le hemos empezado a trabajar en objetivos específicos. O bueno, tenemos los que se nos llega el documento, pero no tenemos unos que eran nosotros formalmente» [2:09]. No se avanzó en definirlos.
- **La arquitectura propuesta.** De La Pava la resumió, pero la transcripción destroza el nombre del operador: «montar en todos esos nodos un clúster de Kubernetes. Encima de ese clúster, montarle un operador que se llama Kubernetes. Sí, que se llama Kubernetes» [20:42] — casi con seguridad **KubeRay**, coherente con el diagrama del 26-ago. Alejandro no comentó la arquitectura; respondió con advertencias de recursos [22:18].
- **El acceso a las notas de Read.AI** que genera las transcripciones [25:20]. La respuesta quedó ininteligible («es automático»).
