# Reunión 2026-09-09 — Delimitación del alcance y revisión en vivo del anteproyecto

- **Participantes:** Kevin David Rodríguez Belalcázar (tutor) · Juan José De La Pava Giraldo, Juan David Pacheco Vargas, Juan Camilo Melo López (autores)
- **Tramo cubierto:** [0:00] – [57:39]. Tercera reunión con el tutor. La transcripción **se corta a mitad de una frase** sobre los riesgos.
- **Fuente:** transcripción pegada en el chat, no versionada (ver [`README.md`](./README.md))

> **Reunión de dos mitades.** La primera [0:00]–[41:15] delimita el alcance tras las entrevistas con Juan Carlos Muñoz y Alejandro. La segunda [41:15]–[57:39] es el tutor **releyendo en voz alta sus propios comentarios `\todo{}`** del commit `fb9ee6b`, lo que convierte esta acta en la validación directa del triaje.

> **Sobre las citas.** SAAMFI aparece como «Sanfi», «Zafi», «Zamfi», «Xamppi», «Savanfi», «Xadamfi» y «SAAM»; KubeRay como «Kubrick» y «Kubernetes concurre»; Ray Serve como «RaySurf»; DSR como «BDSR»; IAsLab como «EASLAB», «JazzLab», «IaaS Lab», «SLAB», «Yastla» y «Yahoo»; guiones largos como «GNS largos» y «Yolen Largos»; NVIDIA DGX Spark, probablemente, como «Envías Park».

---

## Decisiones tomadas

- **Antes de escribir nada más, se organizan los requerimientos con MoSCoW y se propone el corte de alcance al tutor.** Es la instrucción principal de la reunión, repetida cuatro veces. — «Hay un patrón que se llama must have, should have y puede estar en un futuro» [10:01]; «lo principal que ustedes deben tener en cuenta en este momento hacer la parte de requerimientos, definirlos y poder definir correctamente el alcance. Y eso les ayuda a ustedes también para **reescribir los objetivos** que ustedes tienen en este momento, porque puede que se modifiquen un poco» [40:42]
  · afecta: `thesis/chapters/04-objetivos.tex`, `thesis/chapters/07-metodologia.tex`, `project-context/requirements.md`

- **El tutor es el único árbitro del alcance; los demás profesores piden, él corta.** — «Los profesores pueden pedir lo que quieran, ya, pero **yo soy quien les digo hasta qué punto llegamos**, hasta qué punto no» [55:28]; «ustedes me proponen hasta qué punto quieren llegar y yo les digo si hasta ahí o no, un poco más, un poco menos» [55:28]

- **Se descarta montar una nube privada con OpenStack por debajo de la plataforma.** El tutor lo propone, el equipo argumenta y el tutor lo acepta. — De La Pava: «sería hacer AWS y encima [de] AWS, crear las máquinas virtuales, configurar un clúster, o sea, ahí sí yo creo que ya el trabajo se nos agranda muchísimo» [34:03]; «siento que eso es un PDG chiquito por sí solo» [39:12]; Kevin: «No, está bien, muchachos» [39:49]
  · **Contrapartida acordada:** GitOps, documentación y automatización para que la infraestructura sea portable — «algo que sí podemos comprometernos es que sí esté bien documentado y como bien automatizado de manera que si por ejemplo decimos queremos desplegar esa infraestructura pero en el Salón 205M» [39:50]

- **Las cuotas por curso y horario quedan fuera de este PDG.** Lo pidió Juan Carlos Muñoz; el tutor lo descarta. — «yo no tenía planeado que en este PDG el sistema de, por ejemplo, de cursos y cuándo el curso se va a dar y que esté conectado como con ICESI» [19:22]; De La Pava: «no nos tenemos que comprometer a eso» [21:08]

- **La cuantización y la inferencia distribuida quedan fuera de alcance.** — «la parte de cuantización y todo eso no iba a entrar, o sea, la disminución de los modelos no podíamos hacerlo. Distribución de modelos quedaba complicada también porque las conexiones entre los computadores no daban para distribuir los modelos» [15:36] (Melo, reportando a Juan Carlos y Alejandro); el tutor no lo contradice y añade la cifra de red [16:02]
  · **Cierra la pregunta que quedó truncada el 2026-08-26** (`[55:50]` de aquella acta)
  · afecta: `project-context/requirements.md` FR-01.3, `thesis/chapters/01-motivacion-antecedentes.tex` — ver *Contradicciones*

- **Roles iniciales: administrador y usuario común. Nada de pregrado, electiva o semilleros por ahora.** — «uno configura dentro de [SAAMFI] cuáles son los roles, por ejemplo, administrador y usuario, **de momento**. Si a futuro sí estudiante y profesor, bueno, chévere» [22:48]; el administrador «puede observar todos los modelos que se estén ejecutando, no importa de cuál sea el usuario, poderlos apagar, encender o deshabilitar […] y observar cuánta cuota están consumiendo cada uno de los usuarios» [22:48]

- **Se espera un dashboard de cuotas y recursos, no solo un backend.** — «podríamos esperar de este proyecto que tenga por lo menos un dashboard donde pueda haber el sistema de cuotas […] que no quede a nivel solamente como una aplicación de [back], sino que visualmente pueda ver cuántas cuotas están consumiendo tal modelo» [24:29]; «Un dashboard de recursos, sí lo pensamos tener» [24:29]

- **La plataforma no se enfoca en LLM.** — «**Quítense eso de la mente** de que el proyecto está enfocado a modelos largos de lenguaje, no. ¿Su caso de uso principal es ese? Pues probablemente sí, pero busca ser un sistema que permita registrar telemetría, [enrutamiento] de cuotas […] para cualquier tipo de modelos de IA, ya gracias a Ray» [25:18]. Ejemplo concreto: un modelo de Parkinson de los proyectos de Andrés Navarro, «un archivo .pytorch y un servidor con Python» [25:18]
  · Confirma lo mismo que dijo Alejandro el 2026-09-04

- **KubeRay queda aprobado y resuelve el problema del motor de inferencia**, porque es agnóstico al motor. — «si bien el Kubernetes ya no lo aprobaron, [KubeRay] nos dijeron que está bien […] por ahí vamos bien encaminados» [13:37]; «podría configurarse […] es agnóstico al motor entonces le podemos meter [llama.cpp]» [13:37]; «[KubeRay] permite entrenar a cualquiera. O sea, vos literalmente le entregas un archivo a python que puede hacer cualquier cosa y él lo ejecuta […] de forma distribuida si vos se lo especificas así» [26:57]; «[Ray Serve] no está enfocado solamente a servir modelos LLM» [26:57]

- **Terminología: se escribe \emph{Large Language Models} en cursiva, o «modelos de lenguaje».** — «ninguno de nosotros habla llamados a los LLM como modelos de lenguaje extenso» [46:02]; «pueden llamarlo en inglés, Large Language Models y ponerlo como en cursiva para que cada una de las palabras que ustedes ponen, que son de otro idioma, lo pongan en cursiva» [47:25]
  · **Cierra el punto A7 del triaje**

- **El riesgo de reclutamiento de usuarios se elimina; el de ancho de banda se acota a la sala.** — «Eso es que dificulta para reclutar usuarios finales en la validación de usabilidad. ¿Eso es un riesgo?» [56:48]; «enfoquen sus riesgos de su proyecto a nivel entre técnico y de proceso» [57:10]; «límites de ancho de banda del campus. ¿De la sala? Eso está bien, de la sala, de la sala, **del campus no**» [57:10]

## Compromisos

- **Autores** — organizar los requerimientos de los tres profesores en must / should / could y proponerle al tutor el punto de corte — *lo antes posible; bloquea la reescritura de objetivos* · «por favor, organiza nuevamente los requerimientos, da la propuesta al profe, queremos llegar hasta el punto 10 que mencionamos en este documento» [55:28]
- **Autores** — entregar el documento al profesor Navarro — **lunes 2026-09-14** · «para el lunes es el documento» [41:24]
- **Autores** — redactar marco teórico y estado del arte — *fin de semana del 2026-09-12* · «este finde también es de marco teórico y de estado del arte» [41:37]
- **Autores** — evaluar una entrevista con la profesora Ángela Villota sobre la historia del IAsLab — *sin fecha* · «la idea de Navarro es que hablemos con Villota[] para que nos cuente como el lore de [IAsLab] para la parte del contexto» [5:39]; el tutor la avala: «no vería por qué le daría mala información. Quizá no le dé mucha información, pero la que le dé puede ser de ayuda» [5:23]
- **Tutor** — revisar la propuesta de alcance y fijar el corte · [55:28]
- **Tutor** — dejar comentarios sobre la formulación de los objetivos · «ahí yo puedo hacer comentarios, pero por favor tengan en cuenta cómo es que esperamos de que los objetivos sean escritos» [50:36]

## Respuestas a dudas abiertas (ADR)

- **ADR-015 — ¿El objetivo de gobernanza diseña o implementa?** — **implementa. Resuelta.** — «en una parte también hablan sobre diseñar un esquema lógico de cuotas, pero **no solamente lo van a diseñar, plano. Ustedes van a hacer el sistema de cuotas**. Entonces quizás hay que reformular el objetivo para que involucre ambas cosas» [50:36]
  · **pendiente de aplicar** · se usa en: `thesis/chapters/04-objetivos.tex` `\label{obj:gobernanza}`, `thesis/chapters/07-metodologia.tex` `\cref{tab:fases-desarrollo}`, `thesis/chapters/08-contribucion-resultados.tex`

- **ADR-016 — ¿Se sostiene DSR + Scrum?** — **DSR se retira; queda Scrum o «enfoque iterativo». Resuelta.** — «En la estrategia metodológica sí se fueron a la locura. Yo no sé de dónde sacaron esa vaina o quién les dijo. ¿Ustedes saben qué es esa vaina de [DSR]?» [52:26]; «¿cuál es su metodología? Scrum, ¿no?» [53:28]; «O enfoque iterativo, también puede llamarse así» [53:39]; y la razón: «cuando ustedes dicen vamos a usar el marco de referencia Design Science Research es porque ustedes van a seguir unos lineamientos muy claros que vienen de una metodología en un paper de no sé dónde y **ustedes probablemente no saben ese paper dónde existe ni que existe**» [53:39]
  · **pendiente de aplicar** · se usa en: `thesis/chapters/07-metodologia.tex` `\label{sec:estrategia-metodologica}`
  · Arrastra la cita `hevner-designscienceis-2004`, que sale del documento con DSR.

- **ADR-018 — ¿"Hipótesis y restricciones" va o no va?** — **se queda. Resuelta.** El tutor preguntó de dónde salió y aceptó la respuesta del formato. — «¿quién les pidió ese capítulo que llama hipótesis y restricciones?» [47:46]; De La Pava: «yo me basé para escribirlo en el documento que nos pasaron en el Moodle, que es un PDF de formato PDG» [48:06]; Kevin: «**si los piden pues los piden, yo no tengo problema**, solo que me pareció un poco extraño porque no lo había visto hasta el momento» [48:43]
  · **pendiente de aplicar** · queda por decidir solo si el detalle de hardware se mueve a anexos.

- **ADR-011 — ¿Qué es SAAMFI?** — **la sigla sigue sin expandirse, pero su función queda definida y cambia la arquitectura.** SAAMFI es **únicamente un proveedor de identidad**, comparable a Auth0 o Keycloak. — «[SAAMFI] solamente va a funcionar como un Identity Provider y ya está» [18:30] (De La Pava, confirmado por el tutor con «Exactamente» [18:39]); «ahí yo proveo, registro a los usuarios, registro quizá un esquema de roles y permisos, pero solamente los provee» [19:22]; «[SAAMFI] provee los permisos, pues un token, básicamente, y **cada sistema es responsable de cómo quiere utilizar ese token**» [22:48]
  · **ADR-011 sigue abierta** para las palabras exactas de la sigla. Tres reuniones sin obtenerlas.
  · Consecuencia de alcance: la gestión de cursos, salones y roles académicos **no vive en SAAMFI**, así que o la construye el proyecto o queda fuera. Se decidió que queda fuera [19:22].

- **ADR-013 — ¿VRAM real?** — **tercer testimonio, tercera vacilación.** — «Son 16 gigas, creo que son 24, por el estilo» [47:25]
  · **sigue abierta.** El tutor duda en la misma frase. Ya van tres fuentes y ninguna afirma con seguridad. Se cierra con `nvidia-smi`, no preguntando.

- **ADR-014 — antecedente institucional de acceso** — **no se respondió, pero apareció la vía para cerrarla.** El tutor confirma que falta y nombra a quién preguntar. — «Falta un poco de contexto en antecedentes de[l] problema […] sí faltan los antecedentes» [46:02]; «con lo que le va a decir la profesora Ángela de cómo pueden acceder los usuarios en ese momento a los computadores, cómo pueden interactuar con ellos, qué tipo de limitaciones existen, quiénes pueden acceder, quiénes no» [46:02]; y la fuente ideal ya no está: «al que le [hubieran] puesto la preguntada [hubiera] sido a Gabriel, pero ya no está» [6:32]

- **ADR-017 — fases y backlog heredado** — **las fases se rehacen a partir de los requerimientos.** — «las fases de desarrollo del proyecto están desorganizadas o realmente pueden cambiar un montón por lo que les mencioné» [55:28]. Sobre el riesgo del backlog heredado, el tutor empieza a objetarlo y **la transcripción se corta**: «Esfuerzo del backlog heredado mayor al previsto. Pero usted no lo diga…» [57:36]
  · **sigue abierta**, ahora dependiente del ejercicio de requerimientos.

- **ADR-008 — fechas** — **dos hitos nuevos**: entrega a Navarro el **lunes 2026-09-14** [41:24] y marco teórico + estado del arte el fin de semana previo [41:37]. Siguen faltando inicio, fin y reparto por fase.

- **ADR-001, ADR-004, ADR-010, ADR-012** — no se tocaron.

## Contradicciones con `project-context/`

- **Cuantización** — la reunión la deja **fuera de alcance** [15:36]; `project-context/requirements.md` la exige como **FR-01.3 (Quantization Support)** con AWQ, GPTQ, GGUF y bitsandbytes, la repite en «Model Size Constraints», y `technologies.md` la desarrolla
  · **sin resolver, y es la contradicción más cara del documento.** El capítulo 01 sostiene la viabilidad del despliegue on-premise **sobre la cuantización**, citando a `frantar-gptq-2023`, `lin-awq-2024` y `dettmers-llmint8-2022`. Si la cuantización sale del alcance, ese argumento pierde su función y esas tres citas pasan a ser exactamente lo que el tutor llama citas forzadas.
  · Ojo con el matiz: «no podíamos hacerlo» [15:36] puede significar *no lo implementamos nosotros* y no *no se usa*. Confirmarlo antes de borrar nada.

- **Roles de la gobernanza** — la reunión fija **administrador y usuario común** [22:48]; `thesis/chapters/04-objetivos.tex` `\label{obj:gobernanza}` promete cuotas «acoplado a los atributos de rol de SAAMFI (pregrado, electiva, semilleros y profesores)», y `requirements.md` mapea esos cuatro roles académicos
  · **sin resolver.** El objetivo compromete un modelo de roles que el tutor acaba de sacar del alcance.

- **«Extender el sistema web de orquestación»** — el tutor cuestiona el verbo del objetivo general: «dice como que ustedes quieren extender el sistema web de orquestación, o sea que eso supone que ya existe un sistema […] y **puede que ustedes no hagan eso, sino que ustedes van a directamente levantar la base** del sistema web de orquestación. Hay como unas ligerezas en verbos que ustedes utilicen y tengan cuidado porque va a haber quejas respecto a ello» [48:43]; `project-context/documentation.md` plantea el proyecto como «Extend the IAsLab's web orchestration system…»
  · **Resuelve la contradicción abierta el 2026-08-26 en la misma dirección**: el proyecto construye la base. Falta que alguien lo escriba en `documentation.md` y reformule el objetivo general.

- **Velocidad de red** — el tutor da **10 Gbit/s actuales** y «para modelos creo que se necesitan como 200 gigabits para hacer una buena tasa de token» [16:02]; Alejandro había dicho que querían switches «de al menos 25 gigas por segundo» [2026-09-04, 7:34]
  · **sin resolver**: 25 y 200 Gbit/s no son el mismo requisito. Ninguna cifra tiene fuente escrita todavía.

## Hechos nuevos del proyecto (candidatos a `project-context/`)

- **Red actual: 10 Gbit/s.** — «la tasa de transmisión de datos es como de 10 gigabits» [16:02] · destino: `project-context/requirements.md`. Primera cifra de red que aparece.
- **Renovación de hardware en curso:** Juan Carlos Muñoz gestiona cambiar los equipos del 206 por NVIDIA DGX Spark. — «el profesor Juan Carlos está intentando ver si la sala del 206 la cambian […] por esos que se llaman [DGX] Spark, que son como esos pedazos chiquitos […] porque ellos tienen como tarjetas de alta velocidad» [16:02]. El tutor lo desliga del proyecto: «eso es independientemente del proyecto» [16:02]
- **El alcance creció ~100 % tras las entrevistas.** — «el PDG se extendió un 100% por el tema de requerimientos» [7:00]
- **El sistema no tiene nombre.** — «Ustedes tendrán que ponerle un nombre a esa vaina porque **no tenemos nombre para toda esta infraestructura y aplicación**» [21:22] · se enlaza con ADR-001
- **Cadena de revisión del documento:** tutor → lector externo que califica → tutor otra vez. — «Primero lo leo yo como tutor, luego lee un lector externo que lo califica y luego otra vez lo leo yo» [54:37]; el profesor Navarro hace «un barrido súper rápido» en clase [54:37]
- **Se puede corregir en cualquier momento antes del lector externo.** — «Claro, en cualquier momento, corríjanlo todo en el momento que ustedes quieran» [55:02]
- **El proyecto de Sara ya expone telemetría de Ray vía Prometheus** para el modelo en entrenamiento [27:54]. El de este PDG debe cubrir además **los nodos**: «no sería solo así, sino también de los nodos […] métricas de todo, del sistema en general, tanto de modelo como de hardware» [28:39]
- **Preocupación de diseño del tutor, para el documento:** «mi mayor preocupación es que su proyecto, cuando lo terminen, lleguen nuevas necesidades y toque tumbar todo lo que ustedes hicieron, colocar algo por debajo y luego ponerlo ustedes» [32:51]. Es el argumento a favor del compromiso GitOps.
- **Valoración del documento por el tutor:** «lo que tenemos en este momento no está tan bien, la verdad» [42:06]; «hay buena forma y mal fondo» [42:16]; el formato sí le gusta: «me parece muy bien el formato, qué chévere que lo hayan seguido» [45:13]

## Preguntas que quedaron abiertas (candidatas a ADR nueva)

- **¿Cómo se llama el sistema?** Sin nombre para la infraestructura ni la aplicación [21:22] · a quién corresponde: autores + tutor · **bloquea ADR-001**, porque el título del PDG debería nombrarlo
- **¿Qué tecnología para el AI Gateway?** — «tendremos que investigar esa parte como para mirar qué tecnología exactamente vamos a usar. O si no vamos a usar una tecnología […] sería definirla nosotros» [12:51] · a quién corresponde: autores · sigue sin cerrar desde el 2026-08-26
- **¿Se entrevista a la profesora Ángela Villota?** El tutor lo avala pero no lo decide [5:23] · a quién corresponde: autores
- **¿Hasta qué punto llega el alcance?** La pregunta que ordena todas las demás; se responde con el ejercicio MoSCoW [55:28] · a quién corresponde: autores proponen, tutor decide
- **¿"No podíamos hacer" cuantización significa que no se implementa, o que no se usa?** [15:36] · a quién corresponde: tutor · determina si se borran tres citas del cap. 01

## Discutido sin conclusión

- **Convertir el análisis de requerimientos en un objetivo específico.** — «si es muy grande esta reorganización de todos los elementos, podríamos extender el proyecto o modificar uno de los objetivos para que el primero sea, por ejemplo, un análisis […] de los requerimientos o algo similar» [10:01]. Depende del tamaño del ejercicio MoSCoW.
- **Qué se quitaría del alcance actual para meter la nube privada.** El tutor lo preguntó explícitamente [34:17]; los tres respondieron que no hay nada intercambiable, solo cosas que sumar [34:43, 36:11, 36:58], y el tema se cerró descartando OpenStack.
- **Acceso remoto de estudiantes a máquinas virtuales para pruebas.** El tutor lo planteó como necesidad futura [31:55]; quedó fuera, apoyado en el compromiso GitOps.
- **Los antecedentes del capítulo 2.** — «Me pareció un poco raro que ustedes tenían antecedentes y planteamientos […] en el planteamiento solamente ponen la pregunta de investigación. Pues no tengo problema. Pero sí faltan los antecedentes» [46:02]. Se sugiere el PDG de Sara como referencia.
- **El flujo de compilación del LaTeX** [42:54]–[44:45]. El tutor recomienda la vista previa de VS Code en vez de `make`; los autores explican que compilan por lotes. Sin consecuencias para el documento.
