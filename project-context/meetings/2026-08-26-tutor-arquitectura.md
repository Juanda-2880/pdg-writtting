# Reunión 2026-08-26 — Arquitectura propuesta, recursos del laboratorio y alcance de PDG1

- **Participantes:** Kevin David Rodríguez Belalcázar (tutor) · Juan José De La Pava Giraldo, Juan David Pacheco Vargas, Juan Camilo Melo López (autores)
- **Tramo cubierto:** [3:05] – [55:50]. Es la **segunda reunión**. La transcripción **se corta a mitad de una pregunta**, así que el cierre de la reunión no está registrado.
- **Fuente:** transcripción pegada en el chat, no versionada (ver [`README.md`](./README.md))

> **Sobre las citas.** La transcripción automática deforma casi todo el vocabulario técnico. Las citas van **literales**, con la lectura entre corchetes: SAAMFI aparece como «ZAMFI», «Sanfi», «Zampi» y «Xamppi»; Ray como «RAIN», «RAID», «Razer» y «array»; ZeroTier como «ZeroTiger»; IAsLab como «IaaS Lab», «ATA» y «EASLAB»; Gabriel Tamura como «Gabriel Tatamura». Además, los hablantes dicen «billones» donde significan *mil millones* (27B parámetros), calco del inglés *billion*.

---

## Decisiones tomadas

- **La infraestructura es obligatoriamente on-premise; nada de nube.** — «claramente que toda la infraestructura tiene que estar instalada de forma on-premise, por lo que no podemos trabajar con infraestructura relacionada a la nube. Y si queremos algo así, tenemos que buscar la versión open source para que se pueda instalar acá» [12:35]
  · confirma: `thesis/chapters/03-hipotesis-restricciones.tex`, restricción `\item[Despliegue estrictamente on-premise]`

- **El núcleo del proyecto es la capa de infraestructura y de servicio, no el módulo de despliegue.** El tutor lo dice como corrección explícita de rumbo, dos veces. — «ese módulo de despliegue es como un caso de uso. Es un módulo que se integraría y que usaría el sistema que está por debajo que ustedes están planteando» [38:22]; «No quisiera que el proyecto tome el camino, como por ejemplo tomó el proyecto de Sara, que pues por naturaleza fue así, de que solamente se enfocó en la parte de despliegue, pero nuevamente nadie está gestionando la capa de, por ejemplo, de cuotas o quién está haciendo a qué, y la observabilidad depende puramente de Ray» [38:22]
  · afecta: `thesis/chapters/04-objetivos.tex` (el orden y el peso de los objetivos), `thesis/chapters/08-contribucion-resultados.tex`

- **El sistema de cuotas no puede quedar limitado a LLM: debe gobernar recursos generales.** — «si el LLM [LiteLLM] no permite más allá de, por ejemplo, los LLM está puramente enfocado a consumo de tokens o algo así, no nos es suficiente» [45:39]; «tiene que soportar cuotas, por ejemplo, metricas en general de todo el cluster, independientemente si está enfocado para desplegar modelos, sino que también, por ejemplo, pueda yo entrenar modelos cualquiera de otro tipo» [44:58]
  · afecta: `thesis/chapters/04-objetivos.tex` `\label{obj:gobernanza}`, `project-context/requirements.md`

- **El AI Gateway se desarrolla, no solo se configura.** — «Sí, probablemente sea un desarrollo que nos toque hacer, aparte de la configuración, también el desarrollo» [49:13]; «Quizá el LightLLM, el AI Gateway, no tengamos que usar LightLLM, toca hacer el LightLLM pero puramente enfocado a cualquier AI Gateway» [49:13]
  · afecta: `thesis/chapters/04-objetivos.tex` `\label{obj:gobernanza}` — ver ADR-015 abajo

- **La plataforma debe ser agnóstica al modelo; el límite de tamaño es aceptable.** — «la plataforma pues tiene que ser agnóstica al modelo que se quiera utilizar. Debería soportar cualquiera, me refiero en versiones o en tipo de modelo. Ya a nivel de tamaño, pues claramente estamos limitados por la capacidad física que tenemos» [14:20]; «si la limitación es que el sistema no es capaz de trabajar con modelos por encima de 50 billones, no es relevante» [12:35]
  · afecta: `thesis/chapters/03-hipotesis-restricciones.tex`

- **El acceso a los equipos será por grupo `docker`, no por root.** — «muchos de los permisos que ustedes necesitarían están relacionados a que tengan precios [permisos] a nivel de grupo de docker» [6:16]; para root «le pediríamos el permiso al profesor Juan Carlos Muñoz […] pero es difícil que les entregue algo de ese estilo» [6:16]

- **Meta de PDG1, para finales de diciembre: infraestructura configurada + AI Gateway + autenticación SAAMFI funcionando de extremo a extremo.** — «Lo principal que esperamos de este, lo que yo esperaría, por ejemplo, de este PDG 1, es que la infraestructura esté configurada y de que el AI Gateway por lo menos esté configurado, ya tengan la autenticación con Xamppi [SAAMFI]» [52:07]; «cuando le doy a ingresar, me redirija al dashboard de la aplicación de ustedes. Que, por ejemplo, no tenga nada, no pasa nada. Pero que por lo menos ya esté el flujo de autenticación instalado en su servicio backend y frontend» [52:07]; «Esperamos para finales de diciembre» [53:57] `[hablante incierto]`
  · ver ADR-008 abajo

- **El soporte posterior lo asume el IAsLab, no los autores.** — «se encarga como ese proyecto está dentro de parte del laboratorio de lab le caerá a mí alejandro o al profesor Juan carlos y a los monitores que tengamos dentro del laboratorio de lab pero usted no debería preocuparse la parte de soporte posterior» [9:27]
  · afecta: `thesis/chapters/07-metodologia.tex`, análisis de riesgos y limitaciones

- **LiteLLM entra al documento como estado de la práctica, no como dependencia.** — «Puede ir en el documento como, por ejemplo, estado de la práctica. Pero pues podemos sacar funcionalidades de esa característica y que sea desarrollado por nosotros» [55:24]
  · afecta: `thesis/chapters/06-estado-del-arte.tex` (hoy `not started`)

- **Las pruebas de carga grandes se ejecutan fuera de horario lectivo.** — «pongamos a prueba por ejemplo un modelo bien grande y pongámoslo ahí entre todos los computadores, muchos, pues claramente tenemos que hacerlo en, no sé, en la noche o en, no sé, en vacaciones, en diciembre o algo así» [29:11]
  · afecta: `thesis/chapters/07-metodologia.tex`, diseño de las pruebas de carga

## Compromisos

- **Autores** — agendar una reunión con el profesor Alejandro y el profesor Juan Carlos Muñoz para elicitación de requerimientos — *sin fecha; el tutor lo pide dos veces* · «recuerden que les solicito que por favor tengan la reunión con el profesor Alejandro y Juan Carlos cuando puedan» [20:57]; «Lo principal es, por favor, si pueden, no sé cuándo será, cuando sientan como ya tienen todos los insumos, agendarse un espacio con ellos» [22:48]
- **Autores** — crear Jira y Bitbucket y ejecutar uno o dos sprints (sprint 1: arquitectura, modelado de datos, mockups; sprint 2: primeras características) — *dentro de PDG1* · «ustedes van a crear un Jira, un Bitbucket, donde ustedes van a guardar ahí todos sus archivos de configuración, proyectos y demás» [52:07]
- **Tutor / laboratorio** — otorgar acceso por VPN cuando los autores lo soliciten — *cuando los autores estén listos* · «ustedes me lo pueden pedir en el punto en que ya estén preparados para ello, el acceso a través de una VPN» [5:31]

## Respuestas a dudas abiertas (ADR)

- **ADR-013 — ¿Cuál es la VRAM real por nodo?** — **24 GB, no 16 GB.** — «las capacidades de los computadores son como de 32 de RAM, 24 de GPU y como son estos i9 no sé cuántos, no sé cuánto, i9 algo» [28:34] (Pacheco), respondido por el tutor con «Perfecto.» [28:47]
  · **pendiente de aplicar** · la entrada la usa en: `project-context/requirements.md`, `project-context/technologies.md`, `thesis/chapters/01-motivacion-antecedentes.tex`, `thesis/chapters/03-hipotesis-restricciones.tex`
  · ⚠️ **La respuesta viene con dos reservas que hay que cerrar antes de escribirla**, ver *Contradicciones* y *Preguntas abiertas*.

- **ADR-014 — ¿Cómo ha sido históricamente el acceso a los equipos?** — **respondida casi por completo**, y coincide con el relato que el tutor pidió en su corrección del documento:
  - No hay política formal: «No hay un aspecto de políticas ahí definidas» [6:16]
  - El acceso era binario y por defecto se negaba: «no tenemos una forma estandarizada de utilizar la infraestructura, porque no hay ninguna plataforma. O es darle las claves de Zero Tier [ZeroTier] y darle claves de Root, que hagan todo lo que quieran, o simplemente no dárselas, **que es la decisión que hemos tomado hasta ahora**» [18:37]
  - Se concedía a título individual y a poquísima gente: «Ha habido estudiantes de maestría y ha habido estudiantes de P.Grado que le han pedido la solicitud para trabajar en los computadores, pero desde manera individual […] han sido contratados máximo yo le pongo 4, 5» [18:37]
  - Y solo a quien ya estaba dentro: «Yo podía hacer eso porque yo tenía acceso a ZeroTiger [ZeroTier], porque fui estudiante de Ingenious 4, o porque hacía parte de ATA [IAsLab], o porque era profesor también» [16:30]
  - Con exclusión práctica del resto, que se iba a la nube: «Pero los estudiantes lo que hacían, trabajaban con este, ¿cómo se llama? ¿Collab? [Colab] […] Ya si necesitaban otra infraestructura, pues no se utilizaba nada de acá» [16:30]
  - Y el resultado, subutilización: «Entonces no se usa masivamente y yo sé que la maestría de IA pues saca mucho pecho de eso, pero realmente no usan la infraestructura de acá» [18:37]; «los estudiantes no utilizan ninguna infraestructura física de acá, ninguna» [15:32]
  - Con el motivo de equidad económica detrás: «sabemos de que muchas personas pueden no pagar, no tienen las capacidades económicas para poder soportar la carga de, por ejemplo, pagar mensualmente un agente» [tramo 7:55–9:02, marca exacta no disponible]
  · **pendiente de aplicar** · la entrada la usa en: `thesis/chapters/01-motivacion-antecedentes.tex`, sección "Antecedentes del problema"
  · Falta solo decidir cómo se cita: nada de esto está publicado, así que sería **comunicación personal** del tutor o un hecho a incorporar antes a `project-context/documentation.md`.

- **ADR-015 — ¿El objetivo de gobernanza solo diseña o también implementa?** — **también implementa.** — «O sea, que el sistema orquestador permita no solamente proveerle los recursos, sino que también, por ejemplo, pueda acotarlos. Yo tal proyecto, por ejemplo, que es el líder, el profesor, puede decirle, no, a este proyecto le vamos a dar tanto de GPUs por tantas horas y después se lo bloqueamos» [45:39]; «Sí, probablemente sea un desarrollo que nos toque hacer» [49:13]
  · **pendiente de aplicar** · la entrada la usa en: `thesis/chapters/04-objetivos.tex` `\label{obj:gobernanza}`, `thesis/chapters/07-metodologia.tex` `\cref{tab:fases-desarrollo}`, `thesis/chapters/08-contribucion-resultados.tex`
  · El verbo "Diseñar" del objetivo se queda corto frente a lo que el tutor espera.

- **ADR-016 — ¿Se sostiene DSR + Scrum?** — **respondida solo la mitad (Scrum).** Los sprints, el backlog y las herramientas son una exigencia real del curso: «en las nuevas iteraciones del proyecto de PDG buscamos de que por lo menos hagan uno a dos sprints» [52:07]; «se espera de que el primer sprint […] está enfocado en arquitecturas, modelamiento de datos, cómo piensan hacer la aplicación, mockups. Y el Spring 2, pues ya hay como algunas características» [52:07]
  · **pendiente de aplicar** · **Design Science Research no se mencionó ni una vez en toda la reunión.** La mitad de la duda sigue abierta, y es justo la que el tutor cuestionó en el documento.

- **ADR-008 — ¿Fechas y duración de las fases?** — **respondida a medias.** Duración total y cortes: «tenemos un plazo de un año para entregarlo» [47:28]; «el anteproyecto que se entrega al final de PDG1 con una exposición» [47:28]; «en PDG2 hacen un documento que es basado en el anteproyecto agregar pues la capa de desarrollo y de resultados. O sea, pasa un documento de 40 páginas a 100 páginas» [47:28]; «Pero contempla todo, contempla el año completo» [48:02]. Corte de PDG1: «Esperamos para finales de diciembre» [53:57] `[hablante incierto]`
  · **pendiente de aplicar** · Sigue faltando la **fecha exacta de inicio** y el **reparto de semanas por fase**, que es lo que el cronograma necesita.

## Contradicciones con `project-context/`

- **VRAM y modelo de GPU** — la reunión dice «24 de GPU» [28:34]; `project-context/requirements.md` dice «NVIDIA GeForce RTX 4080 (16 GB GDDR6X VRAM) per compute node», y `technologies.md` dice «inside the 16 GB VRAM of each RTX 4080»
  · **sin resolver**, y el problema es mayor que la cifra: **una RTX 4080 no existe en versión de 24 GB**. O la VRAM está mal, o el modelo de GPU está mal, o ambos. Confirmar el modelo exacto (`nvidia-smi`) antes de tocar nada.
  · Efecto en cascada: si el dato cambia, hay que revisar los cuatro sitios que citan los 16 GB, incluido el argumento de viabilidad del cap. 01 y la justificación de cuantizar.

- **Qué es el proyecto: ¿extender lo existente o construir la capa de abajo?** — la reunión dice «Es un módulo que se integraría y que usaría el sistema que está por debajo que ustedes están planteando» [38:22] y «yo sí quiero que, personalmente, que este proyecto permita fundamentar las bases, aunque visualmente no haya mucho, técnicamente a nivel de infraestructura hay un montón» [20:57]; `project-context/documentation.md` plantea el proyecto como «Extend the IAsLab's web orchestration system with distributed artificial intelligence model deployment capabilities…», y el objetivo general del cap. 04 arranca con «Extender el sistema web de orquestación del IAsLab»
  · **sin resolver.** El tutor describe una **capa de infraestructura y servicio nueva** sobre la que el sistema web sería un consumidor más, y advierte explícitamente contra repetir el camino del proyecto de Sara. El documento describe una **extensión de la plataforma existente**. No son la misma tesis: cambian el título, el objetivo general y el orden de los objetivos específicos.

- **La fase de estabilización del backlog heredado** — `project-context/documentation.md` afirma que el software «requires stabilization through the resolution of user stories from the backlog», y `thesis/chapters/07-metodologia.tex` abre las fases con «La primera fase corresponde al análisis y la estabilización del backlog heredado»; **en toda la reunión no se mencionó ni una vez**. Lo que sí se discutió es levantar un clúster desde cero: «sería montar un clúster en todo ese salón» [10:08], «lo más difícil, honestamente, es montar el cluster» [40:23]
  · **sin resolver.** Es exactamente la duda **ADR-017**, y la reunión la agrava en vez de cerrarla: la ausencia no prueba que la fase no exista, pero el tutor enumeró lo que espera de PDG1 [52:07] y la estabilización no estaba en la lista.

## Hechos nuevos del proyecto (candidatos a `project-context/`)

- **Sala y equipos:** el laboratorio es el **104M**; los equipos tienen CPU i9 y «32 de RAM, 24 de GPU» [28:34]. El tutor añade «Tienen como 32 núcleos, ¿no?» [26:27], lo que deja ambiguo si el 32 son GB de RAM o núcleos de CPU. · destino: `project-context/requirements.md`
- **Topología posible del clúster:** nodo máster en el equipo 01, o en un servidor aparte, o en un equipo del **205 sin GPU** que está libre casi todo el tiempo — «pueden agarrar un computador del 205 como nodo máster, que no tiene GPU y está libre casi todo el tiempo, como nodo máster, y los demás si se enfoquen como clúster de procesamiento» [50:33] · destino: `project-context/technologies.md`
- **Vías de acceso:** VPN, o presencial por la red del IAsLab — «ustedes también pueden estar cerca de la sala, contactarse por la red de IaaS Lab [IAsLab] y tener acceso a los computadores directamente» [5:31] · destino: `project-context/requirements.md`
- **Actores del laboratorio:** profesor **Juan Carlos Muñoz**, líder del IAsLab, quien reemplazó a «Gabriel Tatamura» [Gabriel Tamura] y trabajó como DevOps y Tech Lead [7:51]; profesor **Alejandro**; los monitores del laboratorio [9:27] · destino: `project-context/documentation.md`
- **Antecedente técnico directo:** ya existe un precedente informal — «estuvieron instalando pues paquetes, elementos con Python y demás, como VLL [vLLM], o LightLLM [LiteLLM] y un modelo de 27 billones [27 mil millones] de parámetros […] Pero fue básicamente como la ejecución de un par de scripts y ya. **No hicieron una plataforma ellos directamente**» [7:55] · destino: `project-context/documentation.md`. Es el mejor argumento disponible para el planteamiento del problema.
- **Escala de modelo de referencia:** un modelo de 27B ocupa casi toda la VRAM de un solo equipo y «tiene características equiparables a por ejemplo lo que hace Gemini Flash» [12:35], según estadísticas del profesor Juan Carlos · destino: `project-context/requirements.md`
- **Inferencia distribuida por red, descartada por los autores:** «creo que la red interna no es lo suficientemente rápida como para hacer inferencia por network» [10:08] (De La Pava). El tutor no la contradijo ni la confirmó. · destino: `project-context/requirements.md`, como supuesto **a verificar**, no como hecho.
- **Restricción operativa nueva:** los equipos deben seguir usables para clases mientras el clúster corre — «Mientras que sea utilizable el computador, no hay problema […] buscamos que sea utilizable el sistema, pero que no esté bloqueado» [29:08] · destino: `project-context/requirements.md`. Hoy no está en las restricciones del cap. 03.
- **Modo de fallo documentado:** «solamente cuando están los modelos en ejecución, ahí sí se bloquean los computadores, porque ocupan toda la memoria VRAM y cuando se desbordan por la ventana de contexto, tienen que usar la memoria RAM y bloquean los computadores» [28:02] · destino: `project-context/requirements.md`, respalda FR-03.4
- **Proceso del curso:** un lector externo, ajeno al tutor y a Alejandro, evalúa el documento en un par de iteraciones — «su documento lo va a leer un lector que no soy yo, ni tampoco Alejandro, sino que también es alguien externo […] Ella dará, ejemplo, feedback sobre el documento, y eso serán como un par de iteraciones» [54:31]. En PDG2 se exige además manual de usuario [48:02].

## Preguntas que quedaron abiertas (candidatas a ADR nueva)

- **¿Cuál es el modelo exacto de GPU y su VRAM?** «24 de GPU» es incompatible con la RTX 4080 que registra `requirements.md`, y la cifra se dijo con vacilación («como de 32 de RAM, 24 de GPU» [28:34]) · a quién corresponde: autores (verificable con `nvidia-smi` cuando tengan acceso) o administrador del laboratorio
- **¿El "32" son GB de RAM o núcleos de CPU?** Los dos hablantes usan el mismo número para cosas distintas [26:27] y [28:34] · a quién corresponde: autores
- **¿Se aborda la cuantización y multiplexación de modelos?** Melo la plantea en la última frase registrada y **la transcripción se corta antes de la respuesta**: «no sé si sea necesario como abarcar esa parte de de cuantizar los modelos para que se puedan desplegar en múltiples como computadores o multiplexación» [55:50] · a quién corresponde: tutor — **retomar en la próxima reunión**
- **¿Dónde vive el nodo máster?** El tutor enumeró tres opciones sin cerrar ninguna: «esas son las posibilidades que yo puedo observar» [50:33] · a quién corresponde: autores / tutor
- **¿Qué es exactamente el "proyecto de Sara"?** Se cita ocho veces como referencia y como antipatrón [21:xx, 38:22], pero nunca se define. `project-context/` no lo menciona · a quién corresponde: tutor

## Discutido sin conclusión

- **Requisitos mínimos de Kubernetes.** Pacheco: «los requerimientos como mínimos por cada son dos CPUs y al menos como dos gigas de RAM, pero pues es que eso termina dependiendo mucho de cada nodo» [25:42]; el tutor zanjó que no es un problema («Realmente no tenemos limitaciones» [26:27]) pero no se dimensionó nada.
- **Qué primitivas de Ray se usan.** Se repasaron RayService, RayJob y RayCluster [30:09] y el tutor preguntó si sirven para algo más que despliegue [34:20]; Pacheco quedó de confirmar dónde están documentadas [33:12] y la conversación se movió a otro tema.
- **Si alguien se quejará del rendimiento de los equipos** al convertirlos en nodos [28:50]. El tutor respondió que mientras sigan usables no hay problema, sin criterio medible.
- **El uso real de la infraestructura por las maestrías** [15:05–18:34]. Contexto valioso para los antecedentes, pero no derivó en ninguna decisión.
