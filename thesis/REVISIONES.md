# Revisiones humanas

Registro de cada pasada de la skill [`revision-humana`](../skills/revision-humana/README.md): quién revisó qué apartado, qué pidió con sus propias palabras y qué se hizo con cada punto.

Cada cambio al texto que aparece aquí tiene un origen humano: **F** es feedback escrito por una persona en el chat y **S** es una sugerencia de la IA que una persona aprobó por su id. Las sugerencias que nadie aprobó también se anotan, para que quede claro que no se aplicaron.

Las entradas van en orden cronológico, la más reciente al final. No se editan una vez escritas; si algo se revierte, se registra en una entrada nueva.

---

### 2026-09-13 · cap01 · Contexto (sección 1.1)

- **Revisó:** Melo088 (feedback dado en el chat, antes de invocar la skill con `/revision-humana`)
- **F1** (humano, ¶1): «Mezcla afirmaciones correctas con conceptos y términos que no existen en las fuentes […] Ninguno de los documentos de Kreuzberger et al. o Lima et al. menciona el uso de "cuotas" (quotas), "telemetría" (telemetry) o "gobernanza de acceso" (access governance) como prácticas centrales» → aplicado · ¶1 reescrito con lo que dicen las fuentes: Figura 1 y deuda en el nivel del sistema (Sculley et al.), definición de MLOps y componente de monitoreo (Kreuzberger et al.), vacío en el detalle de las actividades para operacionalizar modelos (Lima et al.). Verificado contra el texto completo; ver `CITAS-VERIFICADAS.md`.
- **F2** (humano, regla general): «es importante de aquí en adelante que las citas si son indirectas no involucren terminos o cosas que no se hayan dicho en el documento como tal» → aplicado · regla nueva `skills/reference-writting/source-fidelity.md`, registro `thesis/CITAS-VERIFICADAS.md`, y enlaces en `CLAUDE.md` regla 6 y en los roles Investigador y Revisor.
- **Hallazgos al aplicar F1** (misma sección, mismo problema):
  - ¶3, Gao et al. (2024): la tesis presentaba el umbral de selección (≤ 50 % de utilización) como hallazgo, hablaba de «casos» cuando la fuente cuenta *issues*, y atribuía a la literatura «mecanismos de gobernanza» que la fuente no documenta → corregido.
  - ¶2: «Sus usuarios» se refería al sistema de la fase previa, pero el hecho de `project-context/documentation.md` habla de la plataforma de este proyecto → corregido.
- **Extensión:** el cap. 01 llegó a 4 páginas con la primera reescritura. Se condensaron ¶1 a ¶3 sin quitar afirmaciones verificadas; vuelve a 3 páginas (cap. 02 empieza en p. 4).
- **Pendiente fuera del apartado:** `chapters/05-marco-teorico.tex` `\label{sec:mlops-ciclo-vida}` usa las mismas citas de Sculley et al. y Lima et al. con afirmaciones sin respaldo (registradas en `CITAS-VERIFICADAS.md`). No se tocó.

### 2026-09-13 · cap01 · Contexto (sección 1.1), segunda pasada

- **Revisó:** Melo088 (feedback dado en el chat)
- **F1** (humano, ¶1): «lo de lima en el primer parrafo no me suena, debido a que es 2026 y esa conclusion de el vacio significativo puede llegar a haber cambiado en estos años» → aplicado · la cita de Lima et al. (2022) sale del cap. 01 y la reemplaza Eken et al. (2026, *ACM Computing Surveys*, revisión multivocal de 150 estudios revisados por pares y 48 de literatura gris): «un cuerpo de conocimiento integrado sobre MLOps sigue sin lograrse». Verificada contra el preprint y contra el resumen publicado (Crossref). Regla nueva en `skills/reference-writting/recency.md`, «Claims about the state of a field».
- **F2** (humano, fuentes): «la universidad permite la busqueda en los siguientes portales […] se les permite a los agentes buscar algo de ahi y si esta bloqueado, se puede compartir el pdf manualmente en alguna carpeta […] incluye en el repositorio una carpeta que mapee las fuentes con pdfs, es importante» → aplicado · carpeta `fuentes/` con `README.md` (portales de Icesi y su pertinencia, orden de búsqueda, qué hacer cuando un portal bloquea la descarga), `INDEX.md` (las 42 entradas de `references.bib` con su PDF, versión, forma de obtenerla, verificación y SHA-256) y `pdf/` con los 5 PDF leídos hasta ahora.
- **Decisión técnica a confirmar por los autores:** los PDF quedan **fuera de git** (`fuentes/.gitignore`) porque el repositorio es público en GitHub y la mayoría de los artículos tiene derechos del editor o licencia de la universidad. Se versionan el índice y las huellas SHA-256.
- **Extensión:** el cap. 01 sigue en 3 páginas.

### 2026-09-13 · cap01 · Contexto (sección 1.1), tercera pasada

- **Revisó:** Melo088 (feedback dado en el chat)
- **F1** (humano, ¶3): «siento que el 3er parrafo corta completamente lo que se habla en los otros 2, nos vamos a microsoft, hablamos de nvidia, de prometheus... no siento que este haciendo logica con el contexto, corrigelo» → aplicado · el Contexto se reordenó de lo general a lo particular. ¶1 trata MLOps (sin cambios). ¶2 trata el reto de aprovechar GPU **compartidas**, con Gao et al. reducido a lo que sostiene esa idea: advierten sobre la baja utilización en plataformas multiusuario, y se mantienen los 400 trabajos y los 706 problemas. Salen el 84.99 %, Prometheus y DCGM. ¶3 presenta al IAsLab como el caso concreto («Ese reto aparece, a menor escala…»), y ahora incluye la sala 104M con sus 31 estaciones con GPU RTX 4090 que también se usan para clases (`requirements.md` §4), algo que el formato pide en el Contexto (escenario físico).
- **Confirmación de los autores:** los PDF de `fuentes/pdf/` quedan fuera de git (respuesta «si», 2026-09-13).
- **Extensión:** el cap. 01 sigue en 3 páginas, tras condensar ¶2 y ¶3.
- **Pendiente para la revisión de Antecedentes:** el segundo párrafo de esa sección repite «sala 104M» y «31 máquinas», que ahora se presentan en el Contexto.

### 2026-09-13 · cap01 · Contexto (sección 1.1), cuarta pasada

- **Revisó:** Melo088 (feedback dado en el chat)
- **F1** (humano, ¶1): «El pronombre "que abarca" al final de tu frase genera un poco de ambigüedad» → aplicado · «porque su alcance es amplio: MLOps aborda retos muy diversos para llevar modelos a producción». El sujeto queda explícito.
- **F2** (humano, ¶2): «"aprovechar bien": Es un término un poco coloquial» → aplicado · «optimizar el uso de sus unidades de procesamiento gráfico (GPU)».
- **F3** (humano, ¶2): «"bastante baja": Suena subjetivo. Queda mejor "significativamente baja" o "notablemente baja"» → aplicado con la segunda opción, «notablemente baja». La fuente dice *rather low*, y «significativamente» sugeriría una prueba estadística que el estudio no reporta (`skills/reference-writting/source-fidelity.md`, modalidad).
- **F4** (humano, ¶2): «se genera una pequeña ambigüedad sobre el sujeto de la oración […] Es mejor reestructurarlo para que la acción recaiga claramente en los investigadores» → aplicado · «Los autores analizaron 400 trabajos reales de la plataforma interna de aprendizaje profundo de Microsoft…».
- **F5** (humano, ¶3): «No es el IASLAB el que se enmarca en el macro proyecto, es nuestro pdg en si» → aplicado · «Este proyecto de grado se enmarca en el macroproyecto…», dentro del cual «un proyecto de grado previo» construyó el plano de control (`project-context/documentation.md`: el macroproyecto se dividió en proyectos de grado separados).
- **F6** (humano, ¶3): «el último párrafo debe centrarse más en la arquitectura e infraestructura del problema y menos en el inventario del salón. Mencionar la "sala 104M" interrumpe el flujo técnico» → aplicado · sale el inventario (sala 104M, 31 estaciones, RTX 4090, uso en clases). El párrafo describe ahora la infraestructura del problema: el plano de control existente (configuración, ejecución y seguimiento del entrenamiento distribuido, aprovisionamiento de nodos, SAAMFI como proveedor de identidad) y la plataforma de este proyecto operando sobre los mismos nodos con GPU que el entrenamiento (`documentation.md`, *Introduction* y *Scope clarification*).
- **Recorte por extensión (decisión de la IA, a confirmar):** para volver a 3 páginas se quitó de ¶1 la cláusula de Sculley et al. sobre la deuda técnica difícil de detectar. El pasaje sigue verificado en `CITAS-VERIFICADAS.md` por si se quiere recuperar recortando otra cosa.
- **Queda sin efecto** la nota de la tercera pasada sobre la repetición de «sala 104M» en Antecedentes: el Contexto ya no la menciona.
- **Pendiente para Antecedentes:** esa sección abre con «Antes de esta primera fase» y habla de «la brecha que deja la primera fase», pero el Contexto ya no usa «fase»: ahora dice «proyecto de grado previo».

### 2026-09-13 · cap01 · Antecedentes del problema (sección 1.2), y ajuste del Contexto

- **Revisó:** Melo088 (feedback dado en el chat)
- **F1** (humano, ¶2): «Lo que se menciona de harness de benchmarking no siento que este bien puesto, primero porque dice "construyó", quien? […] no creo que se deba mencionar lo de YAML y en general cosas especificas […] el segundo párrafo desciende abruptamente a un nivel de "bitácora de laboratorio" […] el objetivo es documentar las carencias sistémicas y los esfuerzos previos, no detallar la minucia de las pruebas exploratorias […] distrayendo al lector del verdadero dolor: que los despliegues son manuales» → aplicado · ¶2 reescrito en torno al despliegue manual («Poner un modelo en operación también era un proceso manual…»). Salen el *harness*, YAML, vLLM, llama.cpp, los 20 *tokens* por segundo y los 10 a 15 minutos; esos datos siguen en `project-context/documentation.md`. En el mismo párrafo se integró la brecha del proyecto previo, antes un párrafo aparte.
- **F2** (humano, regla general): «estoy viendo un patron que no me gusta en muchos parrafos, el usar : dos puntos […] es mejor evitarlo y seguir una secuencia lógica que conecte las ideas» → aplicado · cero dos puntos en Contexto y Antecedentes. Regla nueva en `skills/writting-tools/puntuation.md` §4.3, con su `grep`, y en `CLAUDE.md` regla 8. La tabla de §4.1, que recomendaba reemplazar el guion largo por dos puntos, se corrigió.
- **F3** (humano, «corregir en la skill de escritura»): los criterios de F1 quedaron como regla en `skills/writting-tools/nivel-de-detalle.md` (nivel de detalle por sección, hilo entre párrafos, sujeto explícito, antecedente único y registro formal, con los ejemplos de esta revisión y la anterior).
- **Verificación de citas al aplicar F1** (misma sección, `source-fidelity.md`):
  - Jeon et al. (2019): la tesis decía «localidad de datos», pero el paper estudia la localidad en la ubicación de las GPU → corregido. El párrafo usa ahora sus cifras propias: 52 % de utilización promedio de las GPU en uso y 30 % de trabajos fallidos.
  - Gu et al. (2019): la tesis sacaba de esa cita una conclusión sobre «orquestación de inferencia» en el IAsLab, cuando el paper trata el entrenamiento → corregido.
  - Weng et al. (2022): se le atribuía, junto con Liu, que «la telemetría *fine-grained* es la condición necesaria», y no lo dice → corregido a los retos que sí identifica.
  - Liu et al. (2022): la tesis atribuía la mejora de precisión a los 350 millones de registros, cuando la logran las técnicas propuestas → corregido. Se añade lo que la fuente dice sobre las fallas que hacen caer servicios de inferencia.
  - Frase retirada por exagerar lo que dice `project-context/`: «el riesgo de monopolización que ya se observa en el laboratorio». `documentation.md` lo describe como riesgo latente.
- **Contexto (ajuste por F2):** «porque su alcance es amplio: MLOps aborda…» pasa a «porque MLOps tiene un alcance amplio y aborda…», y «del entrenamiento distribuido: centraliza…» se parte en dos oraciones.
- **Sugerencias de la IA (no aplicadas):**
  - **S1** (¶1): «Esa restricción respondía, además, a un criterio de equidad económica, dado que no todos los estudiantes pueden sostener una suscripción comercial de cómputo en la nube». La lógica está invertida: la dificultad de pagar la nube explica por qué el laboratorio debería **abrir** su infraestructura, no por qué la restringía. La cita del tutor en el acta del 2026-08-26 va en ese sentido («muchas personas […] no tienen las capacidades económicas para […] pagar mensualmente un agente»). Además, la Justificación ya desarrolla la equidad económica. Propuesta: quitar la frase de Antecedentes y corregir la redacción en `documentation.md` («Behind the restriction sat…»). Pendiente de aprobación.
- **Extensión:** el cap. 01 sigue en 3 páginas.

### 2026-09-13 · cap01 · Contexto (sección 1.1), quinta pasada

- **Revisó:** Melo088 (feedback dado en el chat, sobre propuestas presentadas antes de aplicar nada)
- **F1** (humano): «no quiero que nos limitemos por paginas» → aplicado · decisión registrada en `STATUS.md`. La skill `revision-humana` ya no pide recortar por extensión.
- **F2** (humano, macroproyecto): «no hay link funcional, quedate con el proposito que marcaron en el anteroir proyecto y adecualo a este pdg» → aplicado · propósito tomado del anteproyecto TRAINI (2026-1) y escrito primero en `project-context/documentation.md` como hecho adoptado por los autores. En la tesis, ¶4 presenta el propósito del macroproyecto y ¶5 lo adecua a este PDG: el proyecto previo cubrió el entrenamiento y este aporta la etapa siguiente (despliegue y servicio, gobernanza, observabilidad).
- **F3** (humano): «no pongas lo de la revista» → aplicado · no se incluye el editorial de *Nature Computational Science*.
- **F4** (humano, ¶2 nuevo): «un parafraseo mas general puede servir […] no nombrar especificamente lo de canada o cosas por el estilo, usar el estilo de referencia parafraseo y al final entre parentesis el nombre» → aplicado · ¶2 con citas parentéticas (Sevilla et al., 2022; Ahmed et al., 2023) y sin el dato de Canadá. La generalización se apoya en la afirmación general de Ahmed et al. («a shortfall in computing available to academics»), no en extrapolar el dato canadiense.
- **F5** (humano): «si sientes que se da un buen contexto, que si se esta organizando a modo de filtro la informacion […] que si sea un buen contexto» → aplicado · orden de embudo en seis párrafos: MLOps → cómputo cada vez más escaso para la academia → reto de las GPU compartidas → IAsLab y macroproyecto → proyecto previo y este proyecto → involucrados. La primera frase del párrafo de Gao pasa a «Cuando esa capacidad se comparte entre muchos usuarios…» para enlazar con ¶2.
- **Decisión de la IA sobre una pregunta sin respuesta:** el párrafo de involucrados (¶6) presenta a los actores **sin** la carencia de visibilidad de los administradores, que ya está en Antecedentes ¶2 (aprobado). Así no se toca lo aprobado ni se repite.
- **Extensión:** el cap. 01 ocupa 4 páginas (cap. 02 empieza en p. 5), sin límite por F1.

### 2026-09-13 · cap01 · Contexto (sección 1.1), párrafo de Gao et al.

- **Revisó:** Melo088 (feedback dado en el chat)
- **F1** (humano, ¶3): «pasar de hablar de Microsoft a hablar de la sala 104M puede sentirse como un salto muy brusco […] el truco es quitarle el foco a la marca comercial (Microsoft) y ponérselo a la escala y naturaleza del problema» → aplicado junto con F2.
- **F2** (humano, ¶3): «junta tu aporte con el mio "Cuando esa capacidad se comparte entre muchos usuarios, optimizar su uso se vuelve un reto estructural. Gao et al. (2024) advierten que, incluso en plataformas industriales de aprendizaje profundo, los trabajos presentan una utilización notablemente baja de las GPU asignadas, lo que desperdicia recursos críticos y reduce la productividad de los equipos. Al evaluar 400 trabajos reales en un entorno corporativo a gran escala —elegidos entre aquellos que usaban en promedio el 50 % o menos de su capacidad—, los autores identificaron 706 problemas asociados a la baja utilización, derivados de la complejidad de gestionar cargas de trabajo concurrentes." obviamente cambiando el estilo con nuestras reglas, lo que si me gusta es el estilo de la cita el criterio de seccion la frase final y sin la mara» → aplicado. Del texto humano se conservan «reto estructural», «incluso en plataformas…», «entorno corporativo a gran escala» y el criterio de selección. De la propuesta de la IA, la cita parentética, la frase final y la ausencia de la marca. Ajustes por las reglas del proyecto:
  - Guiones largos → comas (`puntuation.md` §4.1).
  - «los trabajos» → «algunos trabajos», porque la fuente dice *certain jobs* (`source-fidelity.md`, modalidad).
  - «recursos críticos» → «recursos valiosos» (*precious*); «productividad de los equipos» → «productividad del desarrollo» (*development productivity*).
  - «derivados de la complejidad de gestionar cargas de trabajo concurrentes» → «originados en el código de los propios trabajos por cómputo insuficiente en la GPU o por interrupciones de tareas ajenas a ella». La fuente atribuye los 706 problemas al código de los trabajos, no a la gestión de cargas concurrentes.
  - Con la cita parentética al final de la segunda oración, la tercera abre con «Ese mismo estudio…» para que el sujeto quede claro (`nivel-de-detalle.md` §2).

### 2026-09-13 · cap01 · Contexto (sección 1.1), repeticiones

- **Revisó:** Melo088 (feedback dado en el chat; la propuesta se mostró y se aprobó antes de aplicarla)
- **F1** (humano, todo el Contexto): «se repiten muchas cosas, por ejemplo computo en el segundo parrafo se dice muchas veces, verifica que en general todo el contexto no pase eso con saamfi u otras cosas» → aplicado tras aprobación · se contó la frecuencia de cada término por párrafo y en total. Antes, en todo el Contexto: entrenar/entrenamiento 8 (5 en ¶5), cómputo 7 (4 en ¶2), infraestructura 7, proyecto 7, sistema 6; SAAMFI en dos párrafos seguidos. Después: entrenar/entrenamiento 4, cómputo 3, infraestructura 4, proyecto 3, sistema 3; SAAMFI una sola vez. Ningún término técnico se repite más de dos veces dentro de un párrafo. Las oraciones con cita se reformularon conservando lo que dice cada fuente, y `CITAS-VERIFICADAS.md` se actualizó con la redacción nueva.
- **F2** (humano, ¶2): «quiero que el segundo parrafo comience asi: sobre la infraestructura mencionada se exige, ademas, una capacidad de procesamiento creciente. o algo por el estilo, infraestructura quedo un poco lejos» → aplicado · «La infraestructura mencionada exige, además, una capacidad de procesamiento creciente.» La sintaxis se ajustó: «sobre… se exige» cambia a sujeto y verbo directos.

### 2026-09-13 · cap01 · Antecedentes del problema (sección 1.2), párrafos 3 y 4

- **Revisó:** Melo088 (feedback dado en el chat; la propuesta se mostró y se aprobó antes de aplicarla)
- **F1** (humano, ¶3-4): «s un error muy común en los anteproyectos de ingeniería citar problemas de hiperescala (como los clústeres de Microsoft o Alibaba con miles de GPUs) para justificar un problema en un laboratorio universitario (31 GPUs) […] el enfoque (approach) no debe centrarse en "cómo las grandes tecnológicas manejan el Big Data", sino en los desafíos de los clústeres GPU multiusuario (multi-tenant) en entornos académicos e institucionales» → aplicado tras aprobar la propuesta («apruebo») · ¶3 con Xu et al. (2025): clúster universitario compartido de más de 160 GPU, desafíos de gestión, subutilización con herramientas mal configuradas y el esquema de acceso directo por consola, el mismo del IAsLab. ¶4 con Weitzel et al. (2025): reservas en una plataforma académica Kubernetes, utilización del 21.49 % al 31.37 %. Cierra con una frase de los autores que conecta con el IAsLab y con el riesgo de monopolización de `documentation.md`.
- **F2** (humano): «dejamos pero no se hace estado del arte todavia» → aplicado · Jeon, Gu, Weng y Liu salen del cap. 01. Sus pasajes verificados quedan en `CITAS-VERIFICADAS.md` y figuran como candidatos en la fila del Estado del arte de `STATUS.md`. `fuentes/INDEX.md` se recalculó: Jeon y Gu pasan a «sin citar»; Weng y Liu siguen citados en los cap. 05 y 07.
- **S1** (IA, aprobada por Melo088 con «si»): se quita de ¶1 «Esa restricción respondía, además, a un criterio de equidad económica…», y se corrige la redacción de origen en `project-context/documentation.md`, que invertía el argumento del tutor.
- **Otros:** se añade a `references.bib` el DOI de Weitzel et al. (PEARC '25), tomado del propio PDF.

### 2026-09-13 · cap01 · Justificación (sección 1.3)

- **Revisó:** Melo088 (feedback dado en el chat; la propuesta se mostró antes de aplicarla)
- **F1** (humano): «menciona todo menos el manejo de datos, ese nos lo podemos saltar» → aplicado · entran la pertinencia, el acceso con retorno de inversión, el efecto ambiental (nuevo, con Xu et al., 2025) y la relevancia. Sale el párrafo de Wiest et al. También sale el párrafo de cuantización (Frantar, Lin, Dettmers): tenía detalle de implementación de una capacidad fuera del alcance y afirmaciones sin respaldo («esta evidencia respalda que existen modelos precuantizados»; la aceleración de Lin et al. es de TinyChat, no de AWQ).
- **F2** (humano): «que no sea subtitulo desarrollo sino un flujo natural» → aplicado · los párrafos se enlazan con transiciones («Ese cambio amplía…», «Ese mejor aprovechamiento tiene, además…», «Por último…») y no con aperturas tipo rótulo.
- **F3** (humano): «no hables mucho de los proyectos de esalud ni los proyectos que el macroproyecto desarrolla, basta con decir se fortalecen otros proyectos que requieren de los recursos» → aplicado · «y se fortalecen otros proyectos que requieren esos recursos».
- **Ajustes de la IA:** se quitaron tres repeticiones al aplicar («consumo» 3→1, «acceso» 2→1, «plataforma» 2→1). «La GPU domina el consumo de todo el clúster» pasa a «la GPU representa la mayor parte de la potencia demandada», fiel a *"the GPU power is dominant"*. Sin dos puntos ni guiones largos.

### 2026-09-13 · cap02 · Identificación del problema (sección 2.1)

- **Revisó:** Melo088 (feedback dado en el chat; la propuesta se mostró y se aprobó antes de aplicarla)
- **Diagnóstico presentado por la IA:** las causas estaban escritas como ausencia de la solución (motor de orquestación, reserva de cupos con prioridad por rol, telemetría), contra la regla del encabezado del capítulo. La jerarquía mezclaba síntomas, causas y efectos. El efecto principal («competencia desordenada») no coincidía con los hechos del cap. 01, que documentan subutilización y exclusión. Quedaban «fase previa» y un uso de dos puntos, y no se identificaba a los involucrados.
- **F1** (humano): «perfecto. apruebo» → aplicado · nueva estructura: problema central (infraestructura de GPU que no puede aprovecharse de forma compartida, controlada y observable), tres síntomas, causa principal y tres secundarias, efecto principal y efectos secundarios por involucrado. Todo se deriva del cap. 01 y de `project-context/` (*Institutional antecedents*, Glosario, *Scope clarification*, §4, *Problem Description*, FR-03.4). Sin citas nuevas.
- **Pregunta sin responder, resuelta en conservador:** la IA preguntó si promover a `project-context/` que restringir el acceso era la única forma de evitar la saturación de los equipos (idea del `\todo` del tutor). No hubo respuesta y el texto aprobado no la incluye.

### 2026-09-13 · cap02 · Formulación del problema (sección 2.2)

- **Revisó:** Melo088 (feedback dado en el chat)
- **F1** (humano): «si la pregunta afecta los objetivos entonces no. se deja la pregunta como antes y solo se modifica lo anterior» → aplicado · el enunciado que precede a la pregunta se reescribió siguiendo la identificación aprobada en 2.1 (causa principal y secundarias en la primera oración, efectos en la segunda). La pregunta del proyecto y la oración final («Responderla consolida…») se conservan palabra por palabra.
- **Ajustes de la IA para no tocar la pregunta:** «la pregunta del proyecto: ¿cómo construir…» pasa a «la pregunta del proyecto. ¿Cómo construir…», con la regla de dos puntos (`puntuation.md` §4.3) aplicada a la introducción y no a la pregunta. El enunciado nombra «las cargas de inferencia y de entrenamiento» para que «ambos tipos de carga», dentro de la pregunta, tenga referente.
- **Pendiente señalado, no aplicado:** la pregunta conserva «reserva de cupos con prioridad por rol» (tensión abierta en ADR-032) y «observabilidad avanzada» (adjetivo que las reglas de objetivos marcan como ambiguo). La pertinencia y la relevancia siguen resumidas en la oración final. Se retoma cuando se fije el alcance y se revisen los objetivos.
- **F2** (humano, misma sección): «cambia prioridad por rol por reglas de reparto» → aplicado · la pregunta dice ahora «reserva de cupos con reglas de reparto y observabilidad avanzada». Con esto deja de depender de la tensión de ADR-032 sobre la prioridad de profesores.

### 2026-09-13 · cap04, cap01, cap02, cap05, cap07, cap08 · Exclusión del soporte a entrenamiento e integración del trabajo de JDLP

- **Revisó:** Melo088 (instrucción dada en el chat; aplicada sin propuesta previa porque la instrucción fue explícita)
- **F1** (humano, cap. 02 §2.2): «a que se refiere ambos tipos de carga» → la IA explicó que la frase remitía a inferencia y entrenamiento.
- **F2** (humano): «no se incluye la parte de soportar entrenamiento. con eso corregido en los objetivos y donde mas haga falta» → aplicado · objetivo 1 sin «sin importar si ejecutan inferencia o entrenamiento»; objetivo 2 reserva cupos «para las cargas de inferencia»; cap. 02 sin «que gobierne ambos tipos de carga» en la pregunta, sin cargas de entrenamiento en el enunciado de 2.2 y con la causa secundaria de los nodos compartidos referida a las clases; cap. 01 Justificación ¶4 sin «gobernar y observar esas cargas en conjunto»; cap. 05 sin el párrafo del criterio de punto de envío, sin la fila «Carga de entrenamiento» y sin el rotulado de métricas por clase de carga; cap. 07 sin etiquetado por clase de carga ni «gobierno de las cargas de entrenamiento»; cap. 08 con las filas de los objetivos 1 y 2 alineadas. En `project-context/`: FR-02.6 y FR-03.5 fuera de alcance, A-16 y A-17 a *Won't*, espejo de objetivos y aclaración de alcance en `documentation.md`, avance en ADR-032.
- **F3** (humano): «JDLP hizo push con correciones al marco teorico, esta bien y no afecta lo que hicimos, lo que si: haz que cumpla con las reglas nuevas de escritura que pusimos» → aplicado · en los conflictos de los caps. 05 y 07 se tomó la versión de JDLP. Luego, sobre su texto: dos puntos de empalme reescritos con el conector que ocultaban (caps. 05, 07 y 08), antítesis retiradas («es de capacidad y no de construcción», «y no un resultado establecido», «no pertenece al dominio de…», «y no de ninguna de estas fuentes»), *model serving* y *el servido* retirados, *huella* → *footprint*, *los primitivos* → *las primitivas*, *macro-proyecto* → *macroproyecto*, *de grano fino* → *fine-grained*, y cursiva en *hardware*, *software*, *token(s)*, *throughput*, *kernels*, *runtime*, *framework*, *script*, *firmware*, *sprint(s)* y *backlog*.
- **Ajustes de la IA al integrar:** en cap. 05 §2.1 se reescribieron las citas de Kreuzberger, Lima y Sculley contra el texto completo (dos usos estaban registrados como sin respaldo); en cap. 07 se quitó «y los que respaldan las actas del proyecto» (regla 9), se restituyeron el marcador ADR-030 de Jira y Bitbucket y la exigencia de PDG I, se movió el marcador ADR-031 al *Sprint* 10, se dejó un solo marcador ADR-033 y se corrigió «El \cref{cha:objetivos} exige…», que atribuía al capítulo de objetivos una exigencia del formato. Rutas a `agent-roles/` corregidas en `skills/latex/` y `skills/revision-humana/` tras el traslado que hizo JDLP.
- **Pendiente señalado, no aplicado:** el cronograma de JDLP termina el *Sprint* 4 el 13 de diciembre y ubica el *Sprint* 5 en enero, y el cap. 07 dice «PDG2, entre enero y mayo de 2027» mientras `project-context/README.md` fija PDG2 de febrero a mayo (ADR-033). La decisión de JDLP de un tope de 8 páginas para el Marco teórico convive con la de no aplicar extensiones; queda por confirmar si el Estado del arte conserva 4 páginas.

### 2026-09-17 · cap01 · Antecedentes del problema (sección 1.2) y Justificación (sección 1.3)

- **Revisó:** Tutor del proyecto (feedback entregado como `\todo`)
- **F1** (tutor, §1.2 ¶1): «Cuidado con el lenguaje, mantienen un lenguaje formal previo a este capitulo y empieza este mencioanndo " a un máximo de 4 o 5 personas de su círculo, o no entregaba nada. Esta información es falsa, los estudiantes sí tenían acceso a través de la VPN, (ej curso ingesoft 4) o participantes del laboratorio IasLab, si un estudiante o profesor solicitaba acceso se le daba, no obstante el proceso era manual y en ocasiones tomaba un tiempo extenso para aceptarse la solicitud, entonces no es que toda la comunidad no pudiera acceder y era monopolizado por un conjunto de personas.» → aplicado · §1.2 ¶1 reescrito con registro académico formal: se retiran las expresiones coloquiales e inexactas («a un máximo de cuatro o cinco personas de su círculo, o no entregaba nada») y se establece con precisión que el acceso se otorgaba mediante VPN y credenciales a solicitud (estudiantes de cursos como Ingeniería de Software IV, integrantes del laboratorio, docentes o estudiantes), pero el proceso era manual y conllevaba tiempos de espera prolongados que desincentivaban el aprovechamiento continuo. En §1.3 ¶2 se ajustó la justificación para sustituir «el uso restringido a unas pocas personas» por «un esquema de asignación manual y tiempos de espera prolongados». Reflejado también en `project-context/documentation.md`.
- **F2** (tutor, §1.2 ¶2): «La conclusión no se deriva directamente de la premisa: se pasa de afirmar que el proceso era manual a concluir que solo quienes tenían acceso a los equipos podían hacerlo, sin explicar la relación entre ambas ideas.» → aplicado · §1.2 ¶2 reescrito para hacer explícito el vínculo técnico y causal: la ejecución manual de *scripts* directamente sobre el sistema operativo, en ausencia de una plataforma de autoservicio o API que abstraiga el *hardware*, obligaba a interactuar por consola y requería privilegios locales en las máquinas físicas, lo que supeditaba la puesta en servicio a disponer de credenciales directas en los nodos.

### 2026-09-17 · cap02 · Identificación del problema (sección 2.1) y Formulación del problema (sección 2.2)

- **Revisó:** Tutor del proyecto (feedback entregado como `\todo`)
- **F1** (tutor, §2.1 ¶1): «"El problema central es que..." es un lenguaje muy básico. La formulación del problema resulta demasiado coloquial; convendría emplear una construcción más académica que introduzca la situación problemática.» → aplicado · se reemplazó la fraseología coloquial e introductoria por un planteamiento formal del problema estructural de la infraestructura multiusuario.
- **F2** (tutor, §2.1 ¶2): «"La causa principal es que..."» y «algunas “causas secundarias” parecen más bien limitaciones o condiciones del contexto... Conviene revisar que cada causa explique directamente un síntoma» → aplicado · se reemplazó el inicio básico por una introducción técnica; se eliminaron las condiciones de contexto ajenas (como el uso de la sala para clases) y se alinearon estrictamente las tres causas secundarias para que expliquen de forma directa los tres síntomas identificados (falta de plano de servicio $\rightarrow$ despliegue manual; falta de motor de cuotas acoplado a SAAMFI $\rightarrow$ asignación manual de accesos; falta de agentes de telemetría de aceleradores $\rightarrow$ falta de visibilidad en tiempo real).
- **F3** (tutor, §2.1 ¶3): «mientras que los “efectos secundarios” provienen de problemas distintos (acceso, gobernanza y monitoreo). Conviene revisar... que cada efecto se derive claramente del problema o de sus síntomas.» → aplicado · se reestructuraron los efectos secundarios derivándolos claramente de los síntomas y agrupándolos por su impacto en los estudiantes e investigadores (dificultades de validación y costos en la nube), administradores (sobrecarga operativa) y la estabilidad de la infraestructura compartida (riesgos de saturación desordenada y fallas no detectadas).
- **F4** (tutor, §2.2): «La formulación es coherente con el planteamiento general, pero la pregunta incorpora directamente la solución propuesta. Revisar si se busca formular una pregunta de investigación sobre el problema o una pregunta de desarrollo tecnológico orientada a construir la plataforma. También conviene mantener consistencia entre los conceptos de roles, cupos y reglas de reparto» → aplicado · se explicitó que el proyecto responde a una pregunta de desarrollo tecnológico para una solución de software propia; se retiró la enumeración detallada de módulos que prefiguraba la solución en la pregunta; y se mantuvo estricta consistencia conceptual articulando «cupos asignados según las reglas de reparto asociadas a los roles institucionales».

### 2026-09-17 · cap07 · Fases de desarrollo (sección 7.2), Cronograma (sección 7.3) y Análisis de riesgos (sección 7.4)

- **Revisó:** Tutor del proyecto (feedback entregado como `\todo`)
- **F1** (tutor, §7.2): «Revisar, si la informacion que da la tabla y el texto es muyh parecida, mejor resuman el texto del apartado y presentan la tabla.» → aplicado · se condensaron los párrafos redundantes en un único párrafo conciso que resume la lógica de dependencias técnicas entre fases y da paso directo a `\cref{tab:fases-desarrollo}`.
- **F2** (tutor, §7.3): «Me parece adecuado lo que mencionan, pero recomiendo narrar los aspectos del cronograma sin mencionar las materias de pdg, sino mas bien como el proyecto en si mismo. No relacionarlo a las materias, sus nombres y semestres academicos.» → aplicado · se reescribió la narración del cronograma estructurándola en dos etapas de trabajo consecutivas del propio proyecto (agosto-diciembre 2026 y enero-mayo 2027), eliminando términos como «dos cursos consecutivos», «PDG1» y «PDG2». En `\cref{tab:cronograma}` se actualizaron los hitos a «Entrega y formalización del documento de anteproyecto» e «Informe final del proyecto».
- **F3** (tutor, §7.4 intro): «Esa primera frase, qué?» → aplicado · se retiró el metacomentario sobre el formato de anteproyecto de la facultad y se introdujo una motivación formal y técnica sobre la gestión de incertidumbres en entornos multiusuario compartidos.
- **F4** (tutor, §7.4 ítems): «Si hacen referencia al objetivo especifico 2, que eso me lleve a la seccion, poner hipervinculo. En un apartado habla sobre FR03.4, pero no especifica qué es eso o a qué hace referencia.» → aplicado · se configuró `colorlinks=true` en `skills/latex/preamble.tex` para enlaces visibles; se añadió `\label{sec:objetivos-especificos}` en `04-objetivos.tex`; se referenciaron explícitamente el objetivo y la sección en los ítems de riesgo; y se sustituyó el identificador interno «FR-03.4» por una descripción explícita de las alertas tempranas y el diagnóstico de salud ante saturación crítica de VRAM (> 90 %).


### 2026-09-19 · caps. 01, 02, 07 (+ preamble) · Verificación de las correcciones de Juanda-2880 al feedback del tutor (2026-09-16)

- **Revisó:** Melo088 (veredictos dados en el chat, ítem por ítem, sobre cada corrección de Juanda-2880 a los `\todo` de `e31d654`)
- **K1** (tutor, cap01 §1.2 ¶1): corrección de Juanda-2880 **aprobada** con pulido (sugerencia aprobada por Melo): «se gestionaba de forma manual» → «se realizaba mediante credenciales de VPN y permisos otorgados a solicitud individual» (el «manual» ya aparece en la oración siguiente) y «integrantes del laboratorio y docentes o estudiantes que tramitaran su requerimiento» → «a integrantes del laboratorio y, en general, a docentes o estudiantes que tramitaran su requerimiento». La reescritura colateral de `project-context/documentation.md` (cita «tutor feedback, 2026-09-17») queda cubierta por esta aprobación.
- **K2** (tutor, cap01 §1.2 ¶2): corrección de Juanda-2880 **aprobada con cambio de Melo**: la frase «exigía conectarse por consola mediante una sesión remota y disponer de privilegios de ejecución en las máquinas físicas» era una inferencia sin origen en `project-context/` (regla 6); los extremos de la cadena causal sí están registrados (acta 2026-08-26 y feedback del tutor 09-17, promovidos a `documentation.md`). Melo dictó: «La puesta en servicio exigía operar directamente sobre los nodos con credenciales de acceso a las máquinas, otorgadas vía VPN y permisos administrativos, condición técnica que supeditaba el despliegue a contar previamente con dicho acceso.» Pulido adicional aprobado: segunda mención de «sistema operativo» → «del anfitrión».
- **K3-K5** (tutor, cap02 §2.1): corrección de Juanda-2880 **aprobada** con ajustes de Melo: «estado operativo de los aceleradores» → «estado de los nodos» y «nodos físicos» → «máquinas físicas» (evitar el eco), «tres síntomas concretos» → «tres síntomas», «tres factores causales directos» → «tres factores causales», «cupos normados» → «cupos sujetos a normas», «gestión artesanal de credenciales» → «gestión individual de credenciales» y «atención individualizada de solicitudes» → «atención particular de cada solicitud», «ni distribución equitativa de capacidad» eliminada del síntoma 2, y enumeración mecánica reducida («Por último» → «Además» en ¶2; «Finalmente» → «Sobre la infraestructura compartida, además,» en ¶3, conservando «En primer/segundo/tercer lugar» solo en ¶1).
- **K6** (tutor, cap02 §2.2): corrección de Juanda-2880 **aprobada** con ajustes de Melo: «queda truncado tras el entrenamiento» → «se interrumpe tras el entrenamiento», «orientado a dotar al laboratorio de una solución de \emph{software} propia» → «que construye una solución de \emph{software} propia» (verbo «construir», coherente con ADR-027).
- **K8** (tutor, cap07 §7.2): condensación de Juanda-2880 **aprobada** con ajuste de Melo: «los motores de inferencia base» → «los motores de inferencia». Los matices perdidos en la condensación (clúster desde cero, sin fase de *mockups*, cuotas dentro del clúster) no se recuperaron, por decisión de Melo.
- **K9** (tutor, cap07 §7.3): reescritura de Juanda-2880 en dos etapas del proyecto, sin PDG1/PDG2, **aprobada** con ajuste de Melo: «culminando con la consolidación del informe final y la entrega de la solución terminada» → «culminando con el informe final del proyecto». El marcador `% [verify: ADR-033]` (texto nuevo de Juanda) se deja como está; ADR-033 sigue abierta en `project-context/ADR.md`.
- **K10** (tutor, cap07 §7.4 intro): corrección de Juanda-2880 **aprobada** sin cambios.
- **K11** (tutor, cap07 §7.4 ítems): corrección de Juanda-2880 **aprobada con cambios de Melo**: (a) `colorlinks=true` **revertido** en `skills/latex/preamble.tex` a `colorlinks=false, pdfborder={0 0 0}` (los enlaces quedan como cajas invisibles clicables, que es lo que pidió el tutor); (b) la mención a «FR-03.4», ID interno de `requirements.md`, sale de la prosa; (c) el umbral «superiores al 90 %» no se afirma como decisión: la mitigación queda «ante niveles de saturación críticos de la VRAM, cuyo umbral de disparo se calibrará durante la implementación con base en la telemetría observada, a fin de anticiparse a fallas que comprometan el funcionamiento del equipo». El hecho observado (90-95 %, fuente de poder) se conserva con su marcador ADR-030.
- **K7** (tutor, cap05 intro, `\todo` en línea 41): **no abordada en esta pasada**; la decisión sobre figuras en el documento no correspondía a este revisor. El `\todo` permanece en el archivo.
- **Verificación:** `make build` OK (38 págs.), cero `Citation/Reference undefined`, greps de `puntuation.md` §5 y `ortografia-rae.md` sin hallazgos en los archivos editados. Extensión: cap. 02 sigue en 1-4, cap. 07 en 17-22.

### 2026-09-20 · caps. 04, 05, 07, 08 · Correcciones del tutor: concurrencia sin número, títulos de capítulo y restricción de hardware NVIDIA

- **Revisó:** JuanJDlp (Juan José De La Pava), transmitiendo correcciones del tutor
- **F1** (humano, transversal): «En el documento no se puede mencionar un numero de usuario a soportar, se menciona en 3 partes lo de 20 usuarios, esto es erroneo. Por ahora simplemente lo vamos a mencionar como usuarios conurrentes si poner un numero de cuantos vamos a soportar.» → **aplicado en cinco de seis ubicaciones** (eran seis, no tres): `05-marco-teorico.tex` l. 149 (`tab:marco-conceptual`, fila «Aceptación operacional»), `07-metodologia.tex` l. 37 (`sec:estrategia-metodologica`), l. 74 (`tab:fases-desarrollo`) y l. 156 (`tab:cronograma`, *Sprint* 10), y `08-contribucion-resultados.tex` l. 63 (`tab:objetivos-entregables`). **Pendiente** la sexta, `04-objetivos.tex` l. 37 (`obj:evaluacion`): quitar el número choca con la regla 6 de `objectives-project-rules.md`, que exige criterio medible en el objetivo y cita ese mismo número como ejemplo. Consultado al autor.
- **F2** (humano): «En los titulos: Quitar la parte de Capítulo , simplemente numerar el título. EJ: 6. Metodología» → **pendiente**: el cambio vive en `skills/latex/preamble.tex`, fuera del apartado y fuera de `thesis/`. Consultado al autor.
- **F3** (humano): «Hay que dejar claro en el documento como restricción que el proyecto funciona para los computadores de NVIDIA... la plataforma a desarrollar solo esta pensada para este tipo de arquitecutra» → **pendiente**: el hecho no está registrado como restricción en `project-context/` (regla 5 de la skill). Consultado al autor.
- **F1 · cierre** (humano): «nada, quita esa mencion del obejtivo. Me gusta tu opcion A» → **aplicado** en `04-objetivos.tex` l. 37 (`obj:evaluacion`): «pruebas de carga con veinte usuarios simultáneos… determinar si la plataforma sostiene esa concurrencia» → «pruebas de carga con usuarios concurrentes… determinar hasta qué nivel de concurrencia sostiene el servicio». Espejo aplicado en `project-context/documentation.md` («Formulation of Objectives», punto 4) y ancla de texto literal de ADR-031 actualizada en `project-context/ADR.md`. Quedan cero menciones numéricas en el documento.
- **F2 · cierre** (humano): «Esta bien que se mencionen capitulo a lo largo del documento, solo no como titulo, algo puramente estetico» → **aplicado** en `skills/latex/preamble.tex` con `titlesec`: el encabezado imprime «6. Metodología». Las referencias cruzadas de la prosa se dejan intactas, siguen diciendo «Capítulo 6». Los anexos pasan a numerarse «A.», sin la palabra delante, por coherencia con la misma instrucción; se revierte con una regla aparte si los autores prefieren «Anexo A.».
- **F3 · cierre** (humano): «Estoy de acuerdo que modifiques el project context y de ahi modifica los cap 7 y 5» → **aplicado**. Hecho registrado primero en `project-context/documentation.md` (*Scope → Constraints*) y en `project-context/requirements.md` §1.3; escrito después en `07-metodologia.tex` (ítem nuevo «Dependencia de la arquitectura de aceleración de NVIDIA» en el análisis de riesgos) y en `05-marco-teorico.tex` §`sec:crd-operadores`, donde ya se presentaba el NVIDIA GPU Operator.
- **F4** (humano): «El capítulo 06 se redactó y commiteó hoy (5a4a782), pero thesis/STATUS.md todavía lo marca not started […] Tambien aplica eso» → **aplicado** en `thesis/STATUS.md`: la fila del Estado del arte pasa a `drafted` con sus siete secciones y sus tres pendientes anotados, se advierte que el capítulo no está cubierto por las verificaciones de la lista, y «Lo que sigue» punto 1 pasa de redactarlo a revisarlo.
- **F5** (humano): «Si, modifica las skills necesarias del harness para que todo tenga sentido» → **aplicado** en tres archivos del harness. (a) `skills/objectives-writting/objectives-project-rules.md` regla 6: usaba «soportar 20 usuarios simultáneos» como ejemplo de criterio medible, que la corrección del tutor ahora prohíbe; queda enmendada distinguiendo capacidad comprometida de resultado medido, con una casilla nueva en su checklist. (b) `skills/latex/references/packages.md`: fila de `titlesec`. (c) `skills/latex/SKILL.md`: la presentación del título de capítulo queda fijada, al mismo nivel que las opciones de `hyperref`. Decisiones espejadas en las «Decisiones estructurales vigentes» de `thesis/STATUS.md`.
- **Estado del arte:** no se tocó, por decisión del autor («El estado del arte no lo toques, no nos corresponde»). Las sugerencias S1, S2 y S3 de esta pasada quedan **no aprobadas**; se anotaron como pendientes en la fila del cap. 06 de `STATUS.md` para quien lo revise.
- **Verificación:** `make build` OK, cero `Citation/Reference undefined`, 44 páginas. Greps de `puntuation.md` §5, `ortografia-rae.md` §4 y de identificadores internos sin hallazgos en los archivos editados. Encabezados renderizados «4. Marco teórico», «6. Metodología». Cap. 05 en p. 8, cap. 06 en p. 16, cap. 07 en p. 23, cap. 08 en p. 29.

### 2026-09-27 · cap01 · Antecedentes del problema (sección 1.2) · revisión completa del documento

- **Revisó:** Melo088 (instrucción dada en el chat; cada cambio se propone por capítulo y se aplica solo tras su aprobación)
- **F1** (humano, todo el documento): «quiero que me ayudes verificando todo el documento citas fuentes escritura cosas que pidio el tutor etc de todas las partes» y, tras ver el diagnóstico, «vamos capitulo por capitulo» → en curso. El diagnóstico completo, con los pasajes de cada fuente, quedó en `compiled-output/revision-completa-2026-09-27.md` (documento de trabajo, fuera de git).
- **Verificación del cap. 01:** sus siete citas siguen respaldadas por los pasajes registrados en `CITAS-VERIFICADAS.md`; sin guiones largos, antítesis ni dos puntos de empalme. Los caps. 02 y 04 no tienen hallazgos (el objetivo 2 sigue pendiente de ADR-034).
- **S1** (IA, ¶1, aprobada por Melo088 con «si, aplica la recomendada»): la sigla VPN no se definía en su primer uso, como exige el formato → aplicado · «credenciales de red privada virtual (VPN, *Virtual Private Network*)» en §1.2 ¶1 y entrada nueva en la lista de acrónimos de `main.tex`.

### 2026-09-27 · cap05 · Marco teórico completo · revisión completa del documento

- **Revisó:** Melo088 (veredictos dados en el chat, ítem por ítem, sobre 17 propuestas de la IA presentadas antes de aplicar nada)
- **Contexto:** todas las citas del capítulo se comprobaron contra el texto completo. Los PDF que faltaban se descargaron a `fuentes/pdf/`, y los autores bajaron con su cuenta de Icesi los que Springer y Wiley bloqueaban (Carrión, Li et al. 2015, Chen, Muiruri). Pasajes y páginas en `CITAS-VERIFICADAS.md`.
- **F1** (humano, regla para todo el capítulo): «no digas cifras exactas» → aplicado · el texto nuevo no copia cifras de las fuentes («alrededor de la mitad», «miles de GPU», «más de un centenar de estudios»).
- **S1 / C5-1** (§5.1 ¶2, aprobada con «si»): Muiruri et al. no respaldaba los objetivos atribuidos a cada fase → aplicado con Gao et al. (2022): entrenamiento fuera de línea contra inferencia en línea con exigencia de latencia, y planificadores estudiados por separado.
- **S2 / C5-2** (§5.2 ¶1, aprobada con «si»): «el punto donde se concentran las decisiones de rendimiento» (Muiruri) no estaba en la fuente → aplicado con Miao et al. (latencia y *throughput*, objetivos en conflicto) y Gao et al. (lote contra latencia). Primera definición de LLM, en inglés y cursiva como pidió el tutor el 2026-09-09.
- **S3 / C5-3** (§5.2 ¶2): **no aprobada** («c5-3 no»). Se conservan «capacidad instalada» y «espectro continuo»; el registro anota el matiz frente a la fuente.
- **S4 / C5-4** (§5.2 ¶4, aprobada con «si»): se retira la atribución a Kwon et al. de que vLLM «paga el *throughput* con mayor latencia» (la fuente reporta la misma latencia) y la comparación con *llama.cpp*, que ya vive en el cap. 06, al que ahora remite.
- **S5 / C5-5** (§5.3 ¶1): aprobada con cambio del humano, «sin decir estandar de facto sino solo estandar» → Carrión (estándar; programación de recursos, microservicios e IA) y Shamim et al. (falta de herramientas de diagnóstico).
- **S6 / C5-6** (§5.4): aprobada con cambio del humano, «no pongas porcentajes para xu, la de gao esta bien» → Xu et al. sin porcentajes; Gao et al. como *gang scheduling*.
- **S7 a S15 / C5-7 a C5-15**, aprobadas con «el resto tambien esta bien pero no digas cifras exactas»:
  - §5.5 ¶1–¶2: Borg (Verma et al.) pasa a la familia de prioridad y expropiación, porque la fuente lo dice así; Gavel ya no se agrupa bajo «mismo derecho»; la taxonomía de Gao et al. se cita por lo que clasifica (eficiencia, equidad y plazos); se añade George (2020) con lo que sí dice (profesores con prioridad algo mayor). Salen «sin ambigüedad» y «precedencia institucional», sin respaldo.
  - §5.5 ¶3: Weitzel et al. sin el mecanismo inventado; Cortez et al. con sus términos; el margen del 10 % al 20 % queda como «decisión de diseño del proyecto que estas fuentes no fijan» (opción a).
  - §5.5 ¶4: George (2020) con el uso simultáneo durante las clases.
  - §5.6: Li et al. (RBAC) con sus términos; Fett et al. con la condición de la versión corregida; el *API gateway* queda como patrón (Montesi y Weber) y deja de comprometer un punto único de entrada, que es RSC-10 y RSC-13 de `requirements.md` §3 (*Sin compromiso*).
  - §5.7 ¶1–¶2: Li et al. (2021) con la cita de segunda mano marcada (Sridharan, 2018); Jeon, Weng, Gao y Liu reescritos con lo que dicen (el error de Liu ya corregido en el cap. 01 había reaparecido aquí). DCGM y PCIe definidas en su primer uso.
  - §5.7 ¶3: «que ningún otro componente puede obtener» → «que los demás componentes del conjunto no exponen».
  - §5.8: Lewis y Sauro sin las cifras erróneas («446 estudios y más de cinco mil respuestas»; la fuente dice 166 estudios y 11 855 cuestionarios).
- **S16 / C5-16** (pedido del tutor, `\todo` del 2026-09-16): aplicado · tres figuras en TikZ, cada una referida en el texto: `fig:ciclo-vida-alcance` (§5.1), `fig:bucle-reconciliacion` (§5.4, adaptada de Xu et al. y Burns et al.) y `fig:flujo-observabilidad` (§5.7).
- **S17 / C5-17**: `\todo` del tutor borrado. El documento queda sin `\todo`.
- **Verificación:** `make build` OK, 46 páginas, sin citas ni referencias indefinidas; cero guiones largos, antítesis, dos puntos de empalme y calcos en el capítulo. `fuentes/INDEX.md` recalculado (43 citadas, 3 sin citar).

### 2026-09-27 · cap06 · Estado del arte completo · revisión completa del documento

- **Revisó:** Melo088 (veredictos dados en el chat, ítem por ítem, sobre 16 propuestas de la IA)
- **Contexto:** primera revisión del capítulo desde que lo redactó Juanda-2880 (2026-09-20). Todas sus citas se comprobaron contra el texto completo; pasajes y páginas en `CITAS-VERIFICADAS.md`, donde además se rehicieron las entradas del cap. 06 que no seguían el formato (Themis, Gavel, Kwon, Orca, Miao, Montesi, Muiruri, Chen) y se corrigieron dos citas textuales que no eran literales (Gavel, y la página de Themis).
- **S1 / C6-1** (aprobada con «si»): se borraron las ~170 líneas de la guía de normasapa.in copiadas en comentarios y se actualizó el comentario de cabecera. Sin efecto en el PDF.
- **S2 / C6-2** (§6.1): **no aprobada**. Se conservan la descripción de la búsqueda, las exclusiones y las citas de Eken y Muiruri para el criterio de 2015, registradas como «sin respaldo, conservadas por decisión de los autores».
- **S3 a S7 / C6-3 a C6-7** (aprobadas con «si»): Jeon et al. sin la conclusión sobre la «reserva estática»; Weng et al. con los retos que enumera la fuente; Gao et al. sin «fallas lógicas… exportador DCGM»; Tiresias precisado; «procesadores homogéneos» → «aceleradores» y «maximizar» → «minimizar» el tiempo de finalización; personal especializado apoyado en Xu et al. (personal limitado); SING sin intensificadores que la fuente no usa y con la premisa de compartir recursos como premisa, no como resultado; la frase de consumo energético sale (repetía la Justificación del cap. 01); NRP sin «confirma experimentalmente»; HPC y SSH definidas en su primer uso.
- **F1 / C6-8** (humano, §6.3 ¶3): «no, obviamente ninguna va a integrarse con saamfi porque es de la universidad, eso es obvio, restructuralo a lo que dices pero entendiendo bien esto» → aplicado · el párrafo reconoce lo que cada solución sí resuelve (identidad federada y espacios de nombres en la NRP, cuotas por usuario en SING, prioridad de profesores en el clúster de George) y ubica el vacío en la combinación: despliegue de servicios de inferencia, reserva de cupos con prioridad según los roles del proveedor de identidad de cada institución y convivencia con las clases en las mismas estaciones. La integración con SAAMFI deja de presentarse como vacío.
- **Aplicación de F1 fuera de C6-8, por coherencia** (informada al aplicar): la columna de la tabla pasa de «Gobernanza por rol (SAAMFI)» a «Gobernanza por rol» (la fila de la propuesta conserva SAAMFI), el cierre de §6.4 ¶3 habla de reserva de cupos con prioridad por rol sin mencionar SAAMFI, y el segundo vacío de §6.7 ya no lo usa como argumento.
- **S9 a S15 / C6-9 a C6-15** (aprobadas con «si»): plataformas en la nube con Kreuzberger et al. y Eken et al. (sale el comentario de pendiente); se retira la afirmación legal sobre normativas de datos y se añade la pérdida de control *fine-grained* (Eken et al.); Kubeflow y TensorFlow Serving con Kreuzberger et al. y Eken et al. en lugar de Sculley et al. (anterior a ambos); sale el marcador de ADR-024, ya cerrada; «arquitectura del IAsLab» → «de la plataforma»; LLM con la sigla; vLLM y *llama.cpp* apoyados en el hecho del laboratorio (`documentation.md`) y Frantar/Chen ya no citados para GGUF; tabla sin citas por fila, con la nota de valoración de los autores, la fila de Slurm en «Parcial», celdas alineadas a la izquierda y dentro del margen; vacíos de §6.7 acotados y «resuelve» → «busca resolver».
- **C6-16** (humano): «dejalas» → se conservan las cifras exactas ya verificadas del capítulo.
- **Pendiente detectado al compilar, fuera del apartado:** `\cref` imprime las secciones como «Apartado» y los cuadros como «Cuadro», de modo que el texto dice «la Apartado 4.7» y «las Apartados 5.2 a 5.6», y los rótulos de tabla dicen «Cuadro» mientras la prosa dice «Tabla». Se corrige en `skills/latex/preamble.tex`; se propone en el paso de preliminares.
- **Verificación:** `make build` OK, 45 páginas, sin citas ni referencias indefinidas; cero guiones largos, antítesis, dos puntos de empalme y calcos en el capítulo; la tabla ya no desborda el margen.

### 2026-09-27 · cap07 · Metodología completa · revisión completa del documento

- **Revisó:** Melo088 (veredictos dados en el chat, ítem por ítem)
- **S1 / C7-1** (§7.1 ¶1, Scrum): **no aprobada**. Se conserva «de tipo Scrum, siguiendo la *Scrum Guide*»; el registro anota que la guía dice que implementar solo partes de Scrum no es Scrum.
- **S2 / C7-2** (§7.1 ¶3, aprobada con «si», opción a): salen «los que exige el curso de proyecto de grado» y «El curso de Proyecto de Grado I exige, como mínimo, el anteproyecto y dos *sprints*», en línea con el pedido del tutor de no relacionar el proyecto con las materias (2026-09-16); «un repositorio Jira» → «un tablero en Jira». El marcador de ADR-030 sigue en su lugar.
- **F1 / C7-3** (humano, §7.1 ¶5): «no. el texto se explaya y no era necesario las cosas de evaluaciones desempeño ya se explicaran despues en fases o algo asi revisa el documento de requerimientos o alcances donde esas cosas habian cambiado y el profe dijo que era mejor dejar el scope con scripts de python o algo asi mas simple» → aplicado · la IA encontró el comentario del tutor en `requirements_c.pdf` (2026-09-21), sobre R4-01 a R4-03: «Aunque sería genial que el sistema se autoevalúe y genere su enjambre de solicitudes, es posible que esto sea realizando scripts sencillos en python para no complejizar la aplicación y también su desarrollo», ya promovido a `requirements.md` R4-03 («harness externo a la aplicación… sin complejizar la plataforma»). El párrafo quedó en dos oraciones (pruebas de carga con *scripts* de Python externos a la plataforma y *System Usability Scale*, con remisión a las fases y al Marco teórico) y dejó de citar a Jiang y Hassan y a Lewis y Sauro, que siguen en el cap. 05. Con la misma base, «el motor de *benchmarking* automatizado» pasó a *scripts* de Python en §7.1 ¶4, en la fila «Evaluación empírica» de `tab:fases-desarrollo` (que ahora menciona también los modelos que no son de lenguaje, otro comentario del tutor en la misma página) y en el *Sprint* 10 de `tab:cronograma`. El marcador de ADR-031 (construir o reutilizar el harness del laboratorio) sigue abierto.
- **S4 / C7-4** (riesgo de VRAM, aprobada con «si»): Liu et al. con la redacción verificada; ya no se extiende su hallazgo al congelamiento por la fuente de poder.
- **S5 / C7-5** (§7.3 ¶1, aprobada con «si»): sale el metacomentario «El formato de anteproyecto de la facultad exige…».
- **F2 / C7-6** (humano): «si pero revisa bien el documento que te mencione anteriormente» → aplicado · diagrama de Gantt en TikZ (`fig:gantt`) con las fechas de `tab:cronograma` ya alineadas con `requirements.md` (el *Sprint* 10 con *scripts* de Python) y frase de ruta crítica, que el formato exige.
- **S7 / C7-7**: anchos de `tab:fases-desarrollo` ajustados; la tabla ya no desborda el margen.
- **Pendiente para el cap. 08:** dos menciones al «motor de *benchmarking* automatizado» con la misma alineación a `requirements.md` R4-03.
- **Pendiente de bookkeeping (project-context):** los literales de ADR-031 en `project-context/ADR.md` citan el texto anterior («Ejecución del motor de \emph{benchmarking} automatizado…»); se proponen en el paso final.
- **Verificación:** `make build` OK, 45 páginas, sin citas ni referencias indefinidas y sin cajas desbordadas; cero guiones largos, antítesis y dos puntos de empalme en el capítulo.

### 2026-09-27 · cap08 · Contribución y resultados completo · revisión completa del documento

- **Revisó:** Melo088 (aprobó las seis propuestas con «todas»)
- **S1 / C8-1:** «en particular \emph{Large Language Models}» → «en particular los LLM», sigla definida en el cap. 05.
- **S2 / C8-2:** «habilitación del despliegue de modelos» → «implementación…», coherente con el verbo del objetivo 3.
- **S3 / C8-3:** «motor de *benchmarking* automatizado» → *scripts* de Python en capacidades del investigador y en el entregable del objetivo 4, con la misma base que en el cap. 07 (`requirements.md` R4-03 y comentario del tutor del 2026-09-21).
- **S4 / C8-4:** «propias del programa de Ingeniería Telemática» → «propias de la ingeniería telemática y de sistemas», porque De La Pava es de ambos programas.
- **S5 / C8-5:** artículo ante tres `\cref` a capítulos («en el Capítulo 2»).
- **S6 / C8-6:** el resumen del problema en ¶1 se alinea con el cap. 02 aprobado (interrupción del ciclo de vida tras el entrenamiento y gestión manual de una infraestructura compartida que no se gobierna ni se observa).
- **Verificación:** `make build` OK, 45 páginas; cero guiones largos y dos puntos de empalme en prosa (los de la tabla son rótulos).

### 2026-09-27 · preliminares, preámbulo, bibliografía y registros · revisión completa del documento

- **Revisó:** Melo088 (aprobó P-1 a P-6 con «si»)
- **S1 / P-1** (`skills/latex/preamble.tex`): `\cref` nombraba las secciones «Apartado» (el PDF decía «la Apartado 4.7») y babel rotulaba las tablas «Cuadro» mientras la prosa decía «Tabla» → ahora «Sección» y «Tabla». Documentado en `skills/latex/references/troubleshooting.md`.
- **S2 / P-2** (`main.tex` y capítulos): lista de acrónimos con API, CUDA, HPC, HTTP, IA, KV, ML, PCIe y SSH añadidas, y sin SSO, SUS ni PDG, que no aparecen en el texto. Definidas en su primer uso API y CUDA (cap. 05 §5.3–§5.4), VRAM (cap. 05 §5.7), HTTP (cap. 06 §6.5) y CPU (cap. 08).
- **S3 / P-3** (portada): «Santiago de Cali», como pide el formato.
- **S4 / P-4** (`references.bib`): sale una `}` suelta; autores de `li-rbaccloudsurvey-2015` y `chen-llmquantizationsurvey-2026` corregidos contra los PDF (Chen tenía además tres autores de menos).
- **S5 / P-5** (`project-context/ADR.md`): literales de ADR-031 y ADR-033 al día con el texto actual; ADR-034 lista también el cap. 05 §5.5, la fila «Reserva con prioridad de rol» de `tab:marco-conceptual` y el segundo vacío del cap. 06; ADR-030 anota que el compromiso GitOps ya está en `requirements.md` R3-10. Ninguna ADR se cerró.
- **S6 / P-6** (`project-context/requirements.md`): §1.2 y R4-01 a R4-03 hablan de *scripts* sencillos de Python externos a la plataforma, conforme al comentario del tutor del 2026-09-21 que ya se había aplicado a R4-03.
- **Verificación final del documento:** `make build` OK, 45 páginas, sin advertencias de citas, referencias ni cajas desbordadas; ninguna «Apartado», «Cuadro», `??` ni `\todo` en el PDF; cero guiones largos, antítesis, dos puntos de empalme, prefijos con guion, calcos e identificadores internos en la prosa.

### 2026-09-27 · caps. 04 a 08 · alineación con `requirements.md`

- **Revisó:** Melo088
- **F1** (humano): «revisa entonces si todo el documento coincide con lo que se espera hacer en requirements md en caso de que si commit y push» → la IA cruzó objetivos, alcance (§1), requerimientos por objetivo (§2) y requerimientos *Sin compromiso* (§3). Encontró cuatro diferencias y las propuso antes de aplicar nada.
- **F2** (humano): «1 opción a, aprueba 2 3 y 4» → aplicado:
  - **1 (opción a):** el objetivo 2 ya no dice «con prioridad de los profesores sobre la asignación de la capacidad de la sala» y queda igual al de `requirements.md` §2.2. Sus ecos pasan a prioridad por rol (R2-19, R2-20): cap. 05 §5.5 ¶2 y fila «Reserva con prioridad de rol» de `tab:marco-conceptual`; cap. 06 §6.7; cap. 07 `tab:fases-desarrollo` y *Sprint* 6; cap. 08 ¶1 y `tab:objetivos-entregables`. ADR-034 queda cerrada con su opción (b): se borró de `project-context/ADR.md`, sale el marcador de R2-20 y se actualizaron `documentation.md` y `technologies.md`. El ejemplo de George (2020), que da a los profesores de su clúster una prioridad algo mayor, se conserva porque describe la fuente.
  - **2:** Thanos (R1-03, R1-05) entra al texto: cap. 05 §5.7 ¶3 y `fig:flujo-observabilidad`, cap. 06 §6.7, cap. 07 (fila de observabilidad y *Sprint* 3) y cap. 08 (capacidades y entregable).
  - **3:** en el riesgo de VRAM del cap. 07, «genere alertas tempranas y active el diagnóstico automatizado de salud de los nodos» → reglas de alerta configuradas en el propio conjunto de observabilidad y conservación de la telemetría previa a una falla (R1-30, R1-33), en línea con el comentario del tutor en `requirements_c.pdf` (p. 7).
  - **4:** cap. 05 §5.1 ya no afirma que la plataforma «no lo ejecuta, no lo gobierna ni lo clasifica» (el soporte de entrenamiento se construye como requerimiento *Sin compromiso*, §3.1); ahora dice que el entrenamiento «queda fuera del alcance de este documento». «Proyecto hermano» → «proyecto de grado previo», como en el cap. 01.
- **Verificación:** `make build` OK, 45 páginas, sin advertencias; objetivos 1 a 3 idénticos a `requirements.md` §2 y el 4 con la misma sustancia; ningún texto de la tesis depende de un requerimiento de la §3.

### 2026-09-27 · caps. 04, 05, 07, 08 · requerimientos en la Metodología y salida del SUS

- **Revisó:** JuanJDlp (Juan José De La Pava), en el chat, actuando la IA como Coordinador (Redactor y Revisor como subagentes)
- **F1** (humano): «lo que quiero hacer es en la metodologia escribir estos requerimientos amarrados por cada objetivo, sin necesidad de la columna de prioridad o de ID» y «Los requerimienmtos no tienen que ser entregables, simplemente tienen que ser mencionados, como para que un evaluador que quiera comprobar si los objetivos se cumplieron puera verificarlo» → aplicado · sección nueva `sec:requerimientos-objetivo` en el cap. 07, antes de las fases, con una subsección por objetivo (`sec:req-telemetria`, `sec:req-gobernanza`, `sec:req-orquestacion`, `sec:req-evaluacion`), grupos en negrita y requerimientos en viñetas, sin ID ni prioridad. El Revisor comprobó uno por uno los 110 contra `project-context/requirements.md` §2.
- **F2** (humano): «Solamente entonces incluye los de prioridad ala o media» → aplicado · salen R1-31, R1-32, R2-18, R3-24, R3-30 y R4-09, y nada de la §3.
- **F3** (humano): «para el objetivo especifcio 4, simplemente quita la parte del SUS […] que no mencione un framework en general. Tambien tendriamos que quitarlo donde aparezca en el texto», y ante la falta de requerimientos que midieran aceptación, «Quita la parte de aceptacion» y «Quita todo lo relacionado a SUS» → aplicado · `obj:evaluacion` queda «Evaluar el desempeño de la plataforma mediante pruebas de carga con usuarios concurrentes, con el fin de determinar hasta qué nivel de concurrencia sostiene el servicio». Sale el SUS de los caps. 05 (fila «Aceptación operacional» → «Desempeño del servicio bajo carga concurrente», y último párrafo solo con Jiang y Hassan), 07 y 08. `lewis-susbenchmarks-2018` sale de `references.bib`, `CITAS-VERIFICADAS.md` y `fuentes/INDEX.md`. Espejo en `requirements.md` §2.4, `documentation.md`, ADR-032 y la regla 6 de `objectives-project-rules.md`.
- **F4** (humano): «prefiero tablas en una nueva seccion, que vaya antes de fases de desarrollo y cronograma. De hecho estas partes debes de re escribirlas teniendo ahora en cuenta los requerimientos» y «La parte del cronograma es un borrador que hizo un companiero asi que lo podemos tomar como base y ponerle encima los requerimientos» → aplicado · la tabla de fases nombra los grupos de requerimientos de cada fase; los *sprints* conservan fechas y orden (ADR-033 sigue abierta) y cada uno nombra los grupos que realiza.
- **F5** (humano): «podemos tambien eliminar la tabla 6.2 y quedarnos solo cn la figura 6.1, pero que este bien hecha» → aplicado · sale `tab:cronograma`; `fig:gantt` en página apaisada con grupos por *sprint*, fechas por barra, bandas por fase y ruta crítica en el pie.
- **F6** (humano, sobre la primera versión en tablas): «La tabla de los requerimientos no es realmente legiuble, asi que probablemente hay que buscar otra forma de presentar» → aplicado · tablas reemplazadas por subsecciones con listas. «Las siglas en ingles UI estan bien» → se conserva «UI» en el Gantt.
- **F7** (humano): «Sube elk tope a 9, esta bien porque tiene diagramas» → aplicado · tope propio del Marco teórico en 9 páginas (cabecera del cap. 05, `thesis/README.md`, `STATUS.md`). El capítulo ya ocupaba 9 páginas antes de este cambio (lo comprobó el Revisor compilando la versión anterior).
- **Correcciones del Revisor aplicadas:** antítesis «No son entregables, sino…» reescrita; la fila «Gobernanza de cuotas» de `tab:fases-desarrollo` nombraba cuatro grupos y el módulo administrativo pertenece a la fase de plataforma; `fig:gantt` desbordaba la página. El Coordinador corrigió «del Sección» → «de la Sección» en cinco referencias.
- **Siglas:** CNI, E/S, OAuth, OIDC y RAM nuevas en la lista; CPU se define ahora en el cap. 07, su primer uso.
- **Verificación:** `make build` OK, 51 páginas, sin citas ni referencias indefinidas, sin cajas desbordadas ni flotantes demasiado grandes; cero guiones largos, antítesis y dos puntos de empalme en prosa; ningún identificador R*-** visible ni mención al SUS.

### 2026-10-09 · cap01 · Contexto ¶3

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **F1** (tutor, `\todo` l. 32): «'El estudio analizó...' Cual estudio? No es claro a cual hace referencia» → aplicado · «El estudio analizó 400 casos reales…» → «Dicho estudio analizó 400 casos reales…». La cita parentética se conserva al final del parafraseo, en la oración anterior, y el demostrativo «dicho» ata la oración siguiente a la fuente recién citada. `CITAS-VERIFICADAS.md` actualizado con la redacción nueva.
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; el `\todo` de la l. 32 ya no aparece en el PDF.

### 2026-10-09 · cap01 · Contexto ¶4–¶5 · ítems 2–4 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C1-2** (tutor, `\todo` l. 35): «En este apartado… evitar introducir explícitamente el proyecto de grado. En su lugar, podría presentarse el macroproyecto como parte de las iniciativas de la Universidad Icesi o del IAsLab…» → aplicado · ¶4: «Este proyecto de grado se enmarca en el macroproyecto X, cuyo propósito es…» → «El macroproyecto X, una iniciativa de la universidad, tiene como propósito…»; «la iniciativa busca» → «el macroproyecto busca». Opción A aprobada por el autor.
- **C1-3** (tutor, `\todo` l. 38): «El comentario anterior modifica como empieza este parrafo o como se describe.» → aplicado · ¶5 pierde la oración final («La presente propuesta aporta al propósito común…»); el vínculo con este PDG queda en la Justificación y en el cap. 02, como pidió el tutor. Sin pérdida de contenido: la etapa siguiente ya está en Antecedentes ¶2.
- **C1-4** (tutor, `\todo` l. 46): «…llamar al nombre del otro proyecto por su nombre, busquenlo, se llama TrainIA y hace parte del glosario.» → aplicado · el nombre se verificó contra el anteproyecto del proyecto anterior (`workspace/PDG/Anteproyecto-PdG-I-2026-1.docx`, «la plataforma TRAINI»), que corrige la grafía del comentario. ¶5 nombra «la plataforma TRAINI» y el Glosario de `main.tex` la define. Quedan como «el proyecto de grado previo» las menciones de Antecedentes ¶1–¶2 y del cap. 05, pendientes de decisión del autor.
- **Repeticiones:** conteo por párrafo del Contexto (sin `\todo`): ningún término se repite tres o más veces dentro de un párrafo; «software» bajó de 3 a 2 en ¶4 al caer «de \emph{software}» de la enumeración.
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; los `\todo` de las líneas 35, 38 y 46 ya no aparecen en el PDF.

### 2026-10-09 · cap01 · Justificación ¶1 · ítems 5–6 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C1-5** (tutor, `\todo` l. 53): «Este proyecto responde a...» → aplicado · la Justificación abre con «Este proyecto responde a una necesidad compartida por el IAsLab, el Departamento de Computación y Sistemas Inteligentes y la universidad.» (antes: «Construir esta plataforma es pertinente porque responde a necesidades concretas del IAsLab»).
- **C1-6** (tutor, `\todo` l. 54): «No solamente responde a la necesidad del Iaslab, sino del departamento y la universidad, debe justificar por que, este es un proyecto que puede impactar mas areas.» → aplicado · el alcance se amplía al departamento (nombre confirmado por los autores) y a la universidad, y cierra con «Con esa capacidad, la plataforma puede sostener proyectos de otras áreas, como los de Industria 4.0 y e-Salud.» Se evitó la construcción «no solo… sino» (`puntuation.md` §4.2). El hecho del departamento se registró primero en `project-context/documentation.md` (*Introduction*, 2026-10-09).
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; sin repeticiones de 3+ en la Justificación; cero guiones largos en el capítulo; los `\todo` de las líneas 53 y 54 ya no aparecen en el PDF.

### 2026-10-09 · cap01 · Justificación ¶3–¶4 · ítems 7–8 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C1-7** (tutor, `\todo` l. 57): «'Ese mejor aprovechamiento tiene, ademas, un efecto ambiental.' Es una forma extrana de narrar el hecho, poner ese ademas.» → aplicado · «tiene, además,» → «tiene también».
- **C1-8** (tutor, `\todo` l. 60): «El proyecto o la plataforma?.» → aplicado · el sujeto sigue siendo «el proyecto» y el posesivo ambiguo se reemplaza por «el escenario en el que se desarrolla».
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; cero `\todo` en el capítulo; greps de estilo sin hallazgos en prosa.

### 2026-10-09 · cap02 · Identificación del problema ¶2 · ítem 9 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C2-9** (tutor, `\todo` l. 26): «No todos los elementos deben de ser parrafos, existe la posibilidad de que cuando nombren los 3 factores, pueda ser una enumeracion, unos bullets.» → aplicado · los tres factores causales pasan a `itemize` bajo la frase «De esta causa principal se desprenden tres factores causales.»; salen los conectores «Asimismo» y «Además» (`puntuation.md` §4.4).
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; el capítulo ocupa ahora 2 páginas impresas (el `\todo` pendiente del ítem 10 sigue dentro).

### 2026-10-09 · cap04 · Objetivos · ítem 11 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C4-11** (tutor, `\todo` l. 27): «Es posible que un objetivo previo a todo esto se enfoque en diseñar la arquitectura. Pueden decirdir esto si el proceso de diseño fue extenso y detallado. O si es mas bien un objetivo intrinseco.» → aplicado sin cambio en el texto: el diseño queda como intrínseco al objetivo general (*Construir la plataforma…*) y documentado en la etapa previa del cap. 07. Se descarta un quinto objetivo específico (máximo de 4 del formato; reglas 1 y 8 de `objectives-project-rules.md`). Decisión del autor; no se responde al tutor.
- **Verificación:** `make build` OK; cero `\todo` en el capítulo.

### 2026-10-09 · cap05 · Despliegue e inferencia de modelos · ítem 12 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C5-12** (tutor, `\todo` l. 85): «Podria separarse estas explicaciones cuando desplegamos modelos de IA tradicionales y modelos LLM, claramente el de LLM se puede extender mas, pero los otros modelos tambien son importantes» → aplicado · §5.2 queda en tres párrafos: general (definición y compromiso latencia/aprovechamiento, Ye), LLM (Miao, Kwon, Orca y las métricas de lenguaje) y modelos que no son de lenguaje (nuevo: artefacto propio, marcos como TensorFlow Serving y Seldon, métricas sin \emph{tokens}). Kreuzberger pasa a citarse también en §5.2 ¶3; `CITAS-VERIFICADAS.md` actualizado. El capítulo se mantiene en 9 páginas.
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; cero guiones largos en el capítulo.

### 2026-10-09 · cap05 · Lista de acrónimos · ítem 13 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C5-13** (tutor, `\todo` l. 88): «LLM puedee hacer parte de los acronimos o glosario» → aplicado sin cambio en el texto: «LLM» ya figura en la Lista de acrónimos de `main.tex` desde el 2026-09-27 y se define en su primer uso en §5.2 ¶2. Solo se retira el `\todo`.
- **Verificación:** `make build` OK; el capítulo queda con tres `\todo` (ítems 14 a 16).

### 2026-10-09 · cap05 · Extensibilidad declarativa · ítems 14–15 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C5-14** (tutor, `\todo` l. 105): «'La figura 4.2 representa ese bucle.' La lectura del texto se diifculta con tanta puntuacion y pausas. revisar eso en todo el documento, tantas comas y puntos...» → aplicado · §5.4 ¶1 pasa de las oraciones encadenadas originales a seis con conectores explícitos (y sin embargo, cuyo, Según, Como, y esa propiedad, porque). La revisión de la puntuación en el resto del documento queda como barrido aparte (80 oraciones candidatas medidas).
- **C5-15** (tutor, `\todo` l. 106): «Observa va a observar? Es raro. Pueden omitir la palabra observa.» → aplicado · sale el rótulo «observa» de la flecha «Estado actual del clúster → Observar» en `fig:bucle-reconciliacion`; el nodo «Observar» se conserva. En la prosa, «compara ese estado con el observado» pasa a «compara el estado declarado con el actual».
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; cap. 05 sigue en 9 páginas; cero guiones largos.

### 2026-10-09 · cap05 · Identidad federada y control de acceso · ítem 16 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C5-16** (tutor, `\todo` l. 149): «Pueden especificar aqui un diagrama sencillo de como saamfi u otros proveedores de autenticacion se usan y se conectan a las aplicaciones.» → aplicado · figura nueva `fig:identidad-federada` en §5.6, referida en el texto, con el flujo Usuario (autenticación OAuth 2.0 / OIDC) → proveedor institucional SAAMFI → \emph{token} con roles → plataforma (traducción y asignación de roles) → permisos → recursos del clúster. Elaboración propia, sin fuente nueva. Ajustes pedidos por el autor antes de aprobar: el rótulo del protocolo salió de la caja de SAAMFI y quedó sobre la flecha del intercambio, y las etiquetas se separaron en dos filas para no montarse sobre los cuadros.
- **Tope del capítulo:** subido de 9 a 10 páginas por decisión de los autores el 2026-10-09, porque la cuarta figura deja el capítulo en 10. Actualizados la cabecera de `chapters/05-marco-teorico.tex`, `thesis/README.md` y `STATUS.md`.
- **Verificación:** `make build` OK, sin citas ni referencias indefinidas; figura sin desbordes ni solapamientos.

### 2026-10-09 · cap06 · Gestión y planificación en clústeres · ítem 17 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C6-17** (tutor, `\todo` l. 102): «Cuestionarse si deberian de mencionar la sala 104M, si lo consideran necesario, en algun apartado deben de explicar que es el salon y que hay en el que les interese en su proyecto.» → aplicado · la primera mención de la sala 104M (§6.2) ahora explica qué es y qué aloja: «El IAsLab, en cambio, dispone de 31 estaciones de trabajo con GPU en la sala 104M, un aula de docencia que comparte esos equipos con la investigación, conectadas por una red de área local estándar.» Las menciones posteriores (cap. 06, cap. 07 y anexos) se conservan.
- **Verificación:** `make build` OK; cap. 06 sigue en 7 páginas; cero `\todo` en el capítulo.

### 2026-10-09 · cap07 · Requerimientos por objetivo · ítem 18 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C7-18** (tutor, `\todo` l. 49): «Este apartado de requerimientos porque hace parte de la metodologia? Esto ya es algo del desarrollo de su proyecto, la metodologia deberia de presentar principalmente como piensan trabajar el proyecto como equipo. Podria ir posterior en un capitulo aparte, pero debe de explicarse como obtuvieron esos requerimientos, que tecnicas utilizaron.» → aplicado · la sección se queda en Metodología (decisión de los autores del 2026-09-27) y su introducción explica el proceso: los requerimientos se levantaron a partir de las sesiones de elicitación, que sirvieron como insumo; se revisaron y ajustaron; se cruzaron con los objetivos específicos para validar y definir el alcance propuesto, y el equipo los refinó y priorizó con la revisión del tutor. Se consultaron el formato de la facultad y el anteproyecto de TRAINI (2026-1), que sitúa sus requerimientos en anexos y explica la elicitación dentro de las fases.
- **Verificación:** `make build` OK; cap. 07 sigue en 13 páginas.

### 2026-10-09 · cap07 · Requerimientos por objetivo · ítem 19 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C7-19** (tutor, `\todo` l. 50): «Podrian crear un codigo tipo REQ-01 para identificarlo con facilidad... Puede ser RQ-01» → aplicado · los 110 requerimientos de §7.2 muestran el código `Rk-nn` de `requirements.md` (el mismo identificador, sin doble numeración): R1-01 a R4-11, omitiendo los de prioridad Baja. Las listas pasan de `itemize` a `description` para que el código encabece cada ítem, y la introducción de la sección explica la forma del código. Decisión del autor sobre el esquema («el más entendible y limpio»). Se enmiendan la decisión del 2026-09-27 en `STATUS.md` y la regla §5 de `skills/writting-tools/nivel-de-detalle.md` para admitir los códigos en esa sección.
- **Verificación:** `make build` OK; cap. 07 sigue en 13 páginas; los códigos se renderizan de R1-01 a R4-11.

### 2026-10-09 · cap07 · ubicación de subsecciones · ítems 20–21 del tutor (aparcados)

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C7-20** (tutor, `\todo` l. 279): «El cronograma y fases del proyecto pueden estar en un capitulo aparte, no como una seccion de metodologia.» → **aparcado por decisión del autor**: el formato ubica fases y cronograma en Metodología; se conserva el `\todo` del tutor y se añade un `\todo` de verificación.
- **C7-21** (tutor, `\todo` l. 387): «Esto hace parte del capitulo? O es mas como anexos en la fase de analisis y diseño...?» → **aparcado**: el formato ubica el análisis de riesgos y limitaciones en Metodología; queda el `\todo` del tutor para revisión.
- **C7-18 · addendum** (autor): §7.2 conserva el listado de requerimientos, con un `\todo` de verificación sobre su ubicación. La duda de las tres subsecciones queda registrada en **ADR-036** (`project-context/ADR.md`).
- **Verificación:** `make build` OK; los `\todo` de verificación quedan visibles en el PDF.

### 2026-10-09 · portada · título del profesor acompañante · ítem 22 del tutor

- **Revisó:** Melo088 (veredictos en el chat, ítem por ítem, sobre los `\todo` del tutor del 2026-10-07)
- **C22** (tutor, `\todo` en `main.tex` l. 38): «Antecederle al profesor alejandro el acronimo de maestria, Msc creo que es» → aplicado · «Profesor acompañante: Mgtr. Alejandro Muñoz Bravo». El profesor confirmó que tiene el título de maestría (transmitido por los autores); la abreviatura sigue la recomendación de FundéuRAE para *máster/magíster* («Mtr., Mag. o Mgtr.»), y descarta «M.Sc./MSc» por ser la forma inglesa. El hecho queda registrado en `project-context/documentation.md`.
- **Verificación:** `make build` OK; la portada ya no muestra `\todo`.

### 2026-10-09 · caps. 01, 05 y anexos · normalización a TRAINI · ítem 4 (segunda parte)

- **Revisó:** Melo088 (decisión del autor, 2026-10-09)
- **C1-4 · cierre:** las menciones restantes al proyecto anterior pasan a nombrar la plataforma: «Quienes usan el plano de control anterior» → «Quienes usan TRAINI» (cap. 01 ¶7); «Antes del proyecto de grado previo» → «Antes de TRAINI» y «El proyecto de grado previo automatizó…» → «TRAINI automatizó…» (cap. 01, Antecedentes ¶1–¶2); «corresponde al proyecto de grado previo del mismo macroproyecto» → «corresponde a TRAINI, el proyecto de grado previo del mismo macroproyecto» (§5.1 y su figura); «sistema web del proyecto anterior» → «sistema web de TRAINI» (Anexo A). Se conservan las descripciones que definen qué es TRAINI (glosario y primera mención en el Contexto).
- **Verificación:** `make build` OK; sin citas ni referencias indefinidas.

### 2026-10-12 · cap02 · Identificación del problema · ítem 10 del tutor (C2-10)

- **Revisó:** feedback del tutor del 2026-10-07 aplicado con datos oficiales de matrícula provistos por los autores en el chat (2026-10-12)
- **C2-10** (tutor, `\todo` l. 33): «Podrian nombrar estadisticas de cuantos estudiantes hay aproximadamente en el programa de ing de sistemas, cuantos hay en maestria, para denotar el impacto que tiene la subutilizacion de estos recursos frente a la posible demanda que podria tener.» → aplicado · se incorporan las estadísticas de matrícula institucional de la Universidad Icesi para programas de tecnologías de la información: 667 estudiantes de pregrado y 190 de posgrado (Maestría en IA: 89; Maestría en Ciencia de Datos: 74; Doctorado en Ingeniería: 13; Especialización en Ingeniería de Datos: 8; Especialización en IA Aplicada: 6), totalizando una comunidad potencial de 857 estudiantes. Se contrasta esta demanda con la subutilización y la falta de autoservicio y gobernanza. Cero guiones largos, sin construcciones antitéticas y sin dos puntos en prosa. Los datos quedan registrados en `project-context/documentation.md`. Se retira el `\todo`.
- **Verificación:** `make build` OK; cap. 02 compila en 2 páginas; cero `\todo` en el capítulo.

### 2026-10-12 · cap07 y anexos · Reubicación de requerimientos y riesgos a anexos · Ítems 18 y 21 del tutor

- **Revisó:** feedback del tutor del 2026-10-07 y decisión explícita de los autores en el chat (2026-10-12)
- **C7-18 · resolución:** «Verificar si este listado de requerimientos va en la Metodología o pasa a un anexo (decisión pendiente).» → aplicado por decisión de los autores · el catálogo exhaustivo de 110 requerimientos (R1-01 a R4-11) con sus agrupaciones funcionales por objetivo se traslada a `thesis/chapters/99-anexos.tex` como nuevo Anexo D (`\chapter{Requerimientos del sistema por objetivo}\label{anx:requerimientos}`). En `07-metodologia.tex`, la sección 7.2 pasa a titularse «Elicitación y especificación de requerimientos» (`\label{sec:requerimientos-objetivo}`) y conserva la justificación metodológica de las sesiones con el laboratorio, el cruce con los objetivos específicos, el refinamiento y validación con el tutor, y la codificación Rk-nn, remitiendo al Anexo D y enlazando los cuatro subsistemas. Se retira el `\todo`.
- **C7-21 · resolución:** (tutor, `\todo` l. 388): «Esto hace parte del capitulo? O es mas como anexos en la fase de analisis y diseño...?» → aplicado por decisión de los autores · el análisis detallado de los 7 riesgos y sus mitigaciones se traslada íntegramente a `thesis/chapters/99-anexos.tex` como nuevo Anexo E (`\chapter{Análisis de riesgos y limitaciones}\label{anx:riesgos}`). En `07-metodologia.tex`, la sección final («Riesgos y limitaciones del proyecto», `\label{sec:riesgos-limitaciones}`) resume la caracterización preventiva y remite al Anexo E. Se retira el `\todo`.
- **ADR-036:** se actualiza para reflejar la resolución y cierre de los puntos de requerimientos y riesgos; queda abierta únicamente la duda sobre si fases y cronograma permanecen en Metodología o pasan a un capítulo aparte.
- **Verificación:** `make build` OK (62 páginas en total); cero citas indefinidas, cero referencias cruzadas rotas (`??`), cero em dashes (`—`), cero antítesis y cero dos puntos en prosa.

### 2026-10-14 · caps. 07, 08 y 09 · Separación de fases y cronograma en capítulo independiente · Ítem 20 del tutor (C7-20)

- **Revisó:** feedback del tutor del 2026-10-07 y decisión explícita de los autores en el chat (2026-10-14)
- **C7-20 · resolución:** «El cronograma y fases del proyecto pueden estar en un capitulo aparte, no como una seccion de metodologia.» y «Verificar si las fases y el cronograma van como sección de la Metodología o como capítulo aparte (decisión pendiente).» → aplicado por decisión de los autores · «Fases de desarrollo del proyecto» y «Cronograma» se trasladan desde `thesis/chapters/07-metodologia.tex` a un nuevo capítulo independiente: `thesis/chapters/08-fases-desarrollo-cronograma.tex`, bajo el título «Fases de desarrollo y cronograma» (`\label{cha:fases-cronograma}`). El capítulo de contribución y resultados se renumera secuencialmente como `thesis/chapters/09-contribucion-resultados.tex`. Se conserva el 100 % de la información original: la correspondencia y duración de fases en `tab:fases-desarrollo`, el texto explicativo de *sprints* de tres semanas e hitos, y el diagrama de Gantt en formato apaisado (`fig:gantt`). En Metodología, la introducción y la estrategia metodológica enlazan al nuevo capítulo y a sus secciones correspondientes. Se retiran ambos marcadores `\todo` y se cierra y elimina definitivamente **ADR-036** de `project-context/ADR.md`.
- **Verificación:** `make build` OK (61 páginas); cero citas indefinidas, cero referencias cruzadas rotas (`??`), cero em dashes (`—`), cero antítesis y cero dos puntos como empalme en prosa.

### 2026-11-07 · caps. 07, 08 y 09, Anexos A y D, `main.tex` · Alineación con la implementación y retiro de dudas abiertas

- **Revisó:** JuanJDlp (Juan José De La Pava), en el chat, sobre un cruce de la tesis con el repositorio de implementación hecho por la IA (Coordinador, Investigador, Redactor y Revisor).
- **F1** (humano): «Sobre los Pendientes que siguen abiertos que me mencionaste, puedes eliminarlos, el proyecto esta bien en el estado en que esta y no tenemos nada que hacer con esas desiciones, simplemente borralos tienes el permiso.» → aplicado · ADR-010, 030, 031, 032, 033 y 035 retiradas de `project-context/ADR.md`; sus ocho marcadores `% [verify: ADR-...]` salieron de los caps. 07 y 08 y de los anexos. El texto impreso no cambia.
- **F2** (humano, punto 5 del cruce): «aqui si cambia el numero a 3 nodos de control, solamente eso, nada mas» → aplicado · R3-01 (Anexo D) y cap. 07.
- **F3** (humano, punto 13): «ACtualiza el cronograma, se desplegara en la sala en dicimebre, por ahora lo que es octubre y noviembre se trabaja en el POC, pero igual las fases del desarrollo siguen siendo las mimas» → aplicado · caps. 07 y 08.
- **F4** (humano, punto 16): «Ajusta esa parte en la thesis tambien» → aplicado · R3-27 habla solo de archivo de pesos, sin servidor propio.
- **F5** (humano, punto 17): «la tesis debe mencionar que el administrador es quien otorga el permiso para que los usuarios desplieguen modelos, y el es el unico que da de alta cargas LLM, esto se hizo para proteger los recursos de las salas» → aplicado · Anexo A y R3-29.
- **F6** (humano, punto 8): «Actualiza como lo menciona la tesis, la forma que la tenemos en el poc es la correcto, es solo de expresion» y «Sobre el punto 7 me equivoque, es el 8 el que menciono» → aplicado · R3-23 y cap. 09 hablan de la imagen oficial de llama.cpp.
- **No aplicado, por decisión del autor:** el resto de puntos del cruce. «Lo que no te mencione o te dije que lo dejaras asi, simplement eno toques nada relacionado a eso, esta bien como esta y no lo queremos romper».
- **Verificación:** `make build` OK (61 páginas). La ausencia de referencias indefinidas se confirmó después con `grep -a` (ver la tercera entrada de este día).

### 2026-11-07 · cap. 10 (nuevo) · Avances del proyecto

- **Revisó:** JuanJDlp, en el chat. El plan del capítulo se aprobó antes de redactar.
- **F1** (humano): «la nueva seccion es avances del proyecto que va despues de los apartados principales, este apartado tiene que decir que hemos hecho, retos, como hemos avanzado y como lo hemos solucionado, basicamente es describir lo que hemos hehco en el POC» → aplicado · `chapters/10-avances-proyecto.tex`, incluido después del cap. 09.
- **F2** (humano): «Tiene que quedar claro en este apartado que esto es un POC, prueba del PDG en un solo nodo, que puede que sucedan cambios en la implementacion de vvverdad y que tambien nos vimos limitados por el hardware por lo que tuvimos que ajustar la arquitectura» → aplicado.
- **F3** (humano): «No digas que hay cosas bloqueadas, simplemente di que hay cosas que se estan implementado» → aplicado.
- **F4** (humano): «Si, el POC corre en un unico servidor fisico, y que tambien cada modelo se sirve en cada modelo» → aplicado como «cada modelo se sirve en un solo nodo de cómputo».
- **F5** (humano): «Si, agrega como mediciones, pero no seria un parrafo ya que aun no se ejecutan pruebas» → aplicado · `tab:mediciones-poc`.
- **F6** (humano): «Tambien menciona en este de avances del proyecto que se han tenido varias reuniones con el tutor, con el profesor Alejandro y Juan Carlos» → aplicado · sección «Reuniones de seguimiento», solo con hechos de las actas ya promovidos a `project-context/`.
- **Capturas de pantalla:** pedidas por el autor, no se tomaron. Chromium headless funciona, pero la interfaz del POC no responde desde la máquina de trabajo.
- **Verificación:** `make build` OK (65 páginas).

### 2026-11-07 · cap. 10, cap. 08 y Anexos A y D · Revisión cruzada del trabajo del día

- **Revisó:** JuanJDlp, sobre una revisión de la IA del trabajo de las dos entradas anteriores. Hallazgos **S1 a S12** aprobados con «Estoy de acuerdo con lo que dices», con estos ajustes:
- **F1** (humano): «Yo si quiero tener 3 nodos de control en el cluster final, la thesis deberia de decir eso, actualmente en el poc todo corre en 1 ervidor y tiene 3 maquinas virtuales.» → aplicado · R3-02 en plural (Anexo D y `requirements.md`); el cap. 10 distingue el clúster final del POC.
- **F2** (humano): «Los equipos si se encienden y apagan sin aviso, eso esta bien» → se conserva, sin nombrar la sala 205; registrado en `project-context/documentation.md`.
- **F3** (humano): «IMportante eliminar eso, la thesis deberia ser self contained, o sea que el lector la debe de entender si necesidar de ver el repositorio o tener contexto adicional externo» → aplicado · el cap. 10 ya no remite al plan de las specs; la regla queda en la cabecera del capítulo y en `STATUS.md`.
- **F4** (humano): «si puedes agregar mas imagenes, por ejemplo 1 explicando como es el flujo del despliegue esta bien» → aplicado · `fig:flujo-despliegue`, en TikZ.
- **S1 a S12 aplicados:** etapas del prototipo en lugar de *sprints* propios, ubicadas dentro de los *sprints* 2 y 3 del cronograma; el adaptador de medición solo en la variante de Ray; los retos de los *taints* y de la interfaz de configuración avanzada y energía, descritos según el hallazgo; el Anexo A sin contradicción entre el rol por defecto y el permiso de despliegue; «un modelo por equipo»; cursivas de *hardware*, *tokens* y *llama.cpp*; «+2,4 %» sin doble espacio; la sigla POC expandida en su primer uso (cap. 08).
- **Figura del POC:** regenerada con draw.io desde una copia del generador, sin em dash ni códigos internos (ADR, specs, dudas, rutas), fechada al 26 de octubre de 2026 y apaisada al final del capítulo para no dejar páginas a medias. Tabla de mediciones con columnas alineadas a la izquierda.
- **`project-context`:** R3-02; fecha correcta del diagrama; retos reescritos; flujo de despliegue documentado; `meetings/INDEX.md` marca ADR-030 y ADR-031 como retiradas.
- **Verificación:** `make build` OK (66 páginas); con `grep -a`, cero citas y referencias indefinidas y cero cajas desbordadas; revisión visual de las páginas del capítulo; cero em dash, antítesis y dos puntos de empalme en la prosa nueva; cero referencias al repositorio de implementación en el cap. 10.

### 2026-11-07 · cap. 10 · Despliegue de un modelo desde la vista del usuario

- **Revisó:** JuanJDlp, en el chat.
- **F1** (humano): «Si pueds en el cap 10, explicar un poco como es el despliegue de un modelo, seria perfecto» → aplicado · párrafo nuevo en la sección de la segunda etapa, antes de `fig:flujo-despliegue`, con el recorrido desde la vista del usuario: alta del modelo por el administrador, permiso de despliegue, elección de modelo, motor y nodo, fases visibles, dirección publicada y acciones sobre el despliegue. El párrafo de la figura pasa a describir lo que ocurre internamente. Hechos registrados antes en `project-context/documentation.md` («How a user deploys a model in the POC»).
- **Verificación:** `make build` OK (66 páginas); con `grep -a`, cero referencias indefinidas y cero cajas desbordadas; revisión visual de las páginas afectadas; cero em dash, dos puntos de empalme y referencias al repositorio de implementación en el capítulo.


### 2026-11-14 · cap. 01 · §Contexto ¶1 · Referente de «su código» (corrección del tutor)

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); aplicado por Melo088 tras aprobación en el chat.
- **F1** (tutor): «Precisen el referente de "su código". Por el contexto, parece referirse al código del modelo dentro del sistema completo.» → aplicado · «señalan que su código es solo una pequeña fracción de un sistema real» → «señalan que el código que lo implementa es solo una pequeña fracción de un sistema real». Se eligió la opción A, que evita repetir «modelo» y mantiene el referente inequívoco.
- **Verificación:** `make build` OK; cero citas y referencias indefinidas, cero cajas desbordadas; quedan 11 `\todo` en el capítulo.

### 2026-11-14 · cap. 01 · §Contexto ¶3 · Cierre del párrafo sobre Gao et al. (corrección del tutor)

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); aplicado por Melo088 tras aprobación en el chat.
- **F1** (tutor): «Revisen el cierre de este párrafo. Que el problema exista en un entorno corporativo de gran tamaño no implica por sí solo que ocurra en un laboratorio académico pequeño. Apoyen la conexión con evidencia del propio laboratorio o preséntenla como una suposición.» → aplicado · «Si el problema aparece a esa escala, es razonable que un laboratorio académico también necesite herramientas para detectarlo y controlarlo» → «Si bien el IAsLab no alcanza esa escala, ese estudio permite suponer que un entorno de menor tamaño también puede necesitar herramientas para detectar y controlar el mismo problema». La conexión se presenta como suposición, no como conclusión.
- **Verificación:** `make build` OK; cero citas y referencias indefinidas, cero cajas desbordadas; quedan 10 `\todo` en el capítulo.

### 2026-11-14 · cap. 01 · ¶4–¶5 · Cita del anteproyecto de TRAINI (corrección del tutor)

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); aplicado por Melo088 tras aprobación en el chat.
- **F1** (tutor): «El propósito del macroproyecto proviene del anteproyecto del proyecto de grado anterior, pero el texto no lo cita. Referencien ese documento y, en general, el trabajo de sus compañeros de proyectos de grado previos. Es válido citar documentos institucionales o trabajos de grado aunque no sean artículos publicados.» → aplicado · se añadió `\citep{tobar-sistemaentrenamiento-2026}` al cierre del párrafo del macroproyecto (¶4) y en la primera mención de TRAINI (¶5). Se eligió la opción A, que cita el anteproyecto en los dos puntos donde se usa.
- **Fuente:** `workspace/PDG/Anteproyecto-PdG-I-2026-1.docx` (Tobar, Diaz, Quigua y Diaz, 2026; Universidad Icesi), SHA-256 `c9a347b3d8b872fd9ad43e7652d815573e71985a62efcafff910507742f41cbe`. Entrada `tobar-sistemaentrenamiento-2026` en `references.bib`, fila en `fuentes/INDEX.md` y verificación en `CITAS-VERIFICADAS.md`.
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; la entrada aparece en la bibliografía como «Tobar et al., 2026»; quedan 9 `\todo` en el capítulo.

### 2026-11-14 · caps. 01 y 05, Anexo A y glosario · Renombrado de TRAINI a TrainLab (corrección del tutor)

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); aplicado por Melo088 tras aprobación en el chat.
- **F1** (tutor): «El proyecto TRAINI ahora se denomina TrainLab. Actualicen el nombre en todo el documento, incluidos el glosario, los capítulos 1 y 4 (también la Figura 4.1) y los anexos.» → aplicado · nueve menciones reemplazadas por «TrainLab»: cap. 01 ¶5, ¶7 y Antecedentes ¶1–¶2; cap. 05 §4.1, nodo y rótulo de la Figura 4.1; Anexo A; glosario de `main.tex`. Se actualizaron también `project-context/documentation.md` y la fila del glosario en `STATUS.md`, con una decisión nueva que prohíbe reintroducir «TRAINI» en la prosa. Los registros históricos de `REVISIONES.md` y la cita literal de `CITAS-VERIFICADAS.md` conservan «TRAINI», porque documentan lo que decía la fuente o el texto en su momento.
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; cero «TRAINI» en la prosa de `chapters/` y `main.tex`; quedan 8 `\todo` en el capítulo 01.

### 2026-11-14 · cap. 01 · §Contexto ¶5 · Función de TrainLab y definición de SAAMFI (corrección del tutor)

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); aplicado por Melo088 tras aprobación en el chat.
- **F1** (tutor): «En este párrafo aparecen "plano de control (\emph{control plane})" y SAAMFI sin explicación, y el lector solo los entiende si consulta el glosario. Expliquen brevemente qué es SAAMFI en su primera mención y describan la función de la plataforma anterior en lugar de usar "plano de control".» → aplicado · «que actúa como plano de control (\emph{control plane}) del entrenamiento distribuido» → «que centraliza la configuración, ejecución y seguimiento de los entrenamientos distribuidos y aprovisiona los nodos de procesamiento»; «e integra SAAMFI como proveedor institucional de identidad» → «La plataforma integra SAAMFI, el servicio institucional de identidad de la Universidad Icesi, que registra a los usuarios y su esquema de roles y permisos y emite el \emph{token} con el que estos se autentican».
- **Fuente de la definición:** el anteproyecto de Tobar et al. (2026) describe SAAMFI como «Sistema de Autenticación y Autorización Multi-Institucional […] una plataforma centralizada desarrollada en el contexto de ICESI que permite gestionar identidad, autenticación y autorización para múltiples aplicaciones (sistemas) desde un solo punto». La prosa adopta la definición operativa del glosario, que trata SAAMFI como nombre propio y proveedor de identidad.
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 7 `\todo` en el capítulo 01.

### 2026-11-14 · Definición de SAAMFI · Corrección de la apreciación institucional

- **Revisó:** Melo088, aclaración en el chat (2026-11-14).
- **F1** (humano): «SAAMFI es Sistema de Autenticación y Autorización Multi-Institucional, es una plataforma centralizada desarrollada en el contexto de ICESI que permite gestionar identidad, autenticación y autorización para múltiples aplicaciones (sistemas) desde un solo punto. No es que sea de la Universidad Icesi. Hay una apreciación que corregir ahi.» → aplicado · se reemplazó «servicio institucional de identidad de la Universidad Icesi» por la definición completa en el cap. 01 ¶5 y en el glosario; se añadió SAAMFI a la lista de acrónimos; se corrigieron las atribuciones en los caps. 02, 05 (incluida la Figura 4.2 y su rótulo), 06, 09 y 10, y en los anexos A y E. En `project-context/` se añadió la definición corregida a `documentation.md` y se ajustaron `requirements.md` y `technologies.md`.
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; no quedan «servicio institucional de identidad» ni «proveedor institucional de identidad» en la prosa.

### 2026-11-14 · caps. 05 y anexos A y E · No repetir la definición de SAAMFI

- **Revisó:** Melo088, aclaración en el chat (2026-11-14).
- **F1** (humano): «esta bien lo de saamfi, pero no tienes que repetir que es cada que se menciona, ni de la misma manera: "en el contexto de ICESI". Eso corrigelo en los capitulos en los que se mencona» → aplicado · la definición completa queda solo en la primera mención del cap. 01, en el glosario y en la lista de acrónimos. El cap. 05 pasa a «SAAMFI cumple ese papel y es comparable en su función con productos como Keycloak o Auth0»; el Anexo A usa solo «SAAMFI» en las tablas; el Anexo E dice «SAAMFI emite un \emph{token} con los roles y permisos del usuario».
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; «en el contexto de ICESI» queda solo en la primera mención y en el glosario.

### 2026-11-14 · cap. 01, cap. 05, cap. 06 y Anexo D · Sala 104M y datos de hardware

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); propuesta A aprobada por Melo088 en el chat.
- **F1** (tutor): «Revisen el orden en que se describen las estaciones de trabajo de la sala 104M. Hoy se presentan por primera vez en el capítulo 5, mientras que el capítulo 4 ya se refiere a "las estaciones de trabajo de la sala" como si el lector las conociera. Definan y describan primero la sala, con el número de estaciones, sus GPU, la red y el uso compartido con las clases, preferiblemente en este Contexto, y después referéncienla en los demás capítulos.» → aplicado · el Contexto del cap. 01 describe la sala (31 estaciones de trabajo, 30 con una GPU NVIDIA RTX 4500 Ada Generation de 24 GB, red de 10 Gbit/s y uso compartido con las clases); el cap. 05 la referencia como «sala 104M»; el cap. 06 conserva solo los datos que necesita el contraste con los clústeres de hiperescala (31 estaciones, uso docente y red de 10 Gbit/s).
- **F2** (tutor, cap. 06): «Aquí se habla de una "red de área local estándar", mientras que el Anexo E indica que la red de la sala es de 10 Gbit/s. Usen el mismo dato en ambos lugares.» → aplicado · el cap. 06 dice «red de 10 Gbit/s».
- **Datos:** se adoptó la observación del 2026-10-22 registrada en `project-context/documentation.md` (RTX 4500 Ada Generation de 24 GB en 30 de los 31 equipos; el `104m30` no tiene GPU NVIDIA; red de 10 Gbit/s). Se actualizaron las menciones a RTX 4090 del cap. 05, el cap. 06, el Anexo D, `requirements.md` y `technologies.md`.
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 6 `\todo` en el capítulo 01.

### 2026-11-14 · cap. 01 · Antecedentes ¶1 · «Explotación continua»

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «"Explotación continua" es un término poco claro para el lector general. Consideren una expresión como "uso productivo continuo".» → aplicado · «y todavía no en explotación continua» → «y todavía no en uso productivo continuo».
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 5 `\todo` en el capítulo 01.

### 2026-11-14 · cap. 01 · Antecedentes ¶2 · «Despliegue manual»

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Revisen la redacción de este párrafo. "Poner un modelo en operación" y "el laboratorio desplegaba modelos ejecutando a mano" usan un registro coloquial y repiten la idea. Reformúlenlo en un lenguaje técnico y más preciso, por ejemplo con el término "despliegue manual" definido una sola vez y usado de forma consistente.» → aplicado · el párrafo abre con «El despliegue manual era el único procedimiento disponible» y usa «despliegue» de forma consistente; salen «poner un modelo en operación», «desplegaba modelos ejecutando a mano» y «puesta en servicio».
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 4 `\todo` en el capítulo 01.

### 2026-11-14 · cap. 01 · Antecedentes ¶3 · Nombrar Slurm

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «"Una herramienta conocida" es vago. Revisen la fuente para identificar a qué herramienta se refieren los autores, nómbrenla y evalúen si deberían tenerla en consideración como alternativa en el estado del arte.» → aplicado · «muchas universidades adoptan una herramienta conocida con configuraciones subóptimas» → «muchas universidades adoptan un planificador de colas como Slurm con configuraciones subóptimas». La fuente (Xu et al., 2025) dice «pick a tool that they are familiar with (e.g., Slurm [41]) and use it as-is with sub-optimal settings». Slurm ya se analiza como alternativa en el cap. 06, §5.3 y en la tabla comparativa.
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 3 `\todo` en el capítulo 01.

### 2026-11-14 · cap. 01 y cap. 06 · Separador decimal

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); aplicado por Melo088 tras aprobación en el chat.
- **F1** (tutor): «Unifiquen el separador decimal. Aquí se usa el punto (21.49 y 31.37), mientras que en otros apartados se usa la coma (2,4 en la Tabla 9.1 y 1,5 en el capítulo 5). En español se recomienda la coma decimal.» → aplicado · «21.49» y «31.37» → «21,49» y «31,37» en el cap. 01 y en la misma cifra del cap. 06. No quedan puntos decimales en la prosa de los capítulos.
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 2 `\todo` en el capítulo 01.

### 2026-11-14 · caps. 01, 05 y 06 · Evidencias repetidas

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); propuesta A aprobada por Melo088 en el chat.
- **F1** (tutor): «Varias evidencias se repiten casi con las mismas palabras en distintos capítulos. El estudio de Xu et al. (2025) sobre el acceso directo por consola aparece en la sección 1.2 y en la 5.2, las cifras de la National Research Platform aparecen en las secciones 1.2, 4.5 y 5.2, y el estudio de Gao et al. (2024) en las secciones 1.1, 4.7 y 5.1. Desarrollen cada evidencia una sola vez, en el capítulo que le corresponde, y en los demás remitan a ella.» → aplicado · el desarrollo detallado queda en el cap. 06 (Estado del arte): Gao et al. con los 400 casos y los 706 problemas, Xu et al. con las 160 GPU, los 480 usuarios, Slurm y el acceso por consola, y la National Research Platform con las cifras 21,49 % → 31,37 %. El cap. 01 conserva el hallazgo y remite al cap. 06; el cap. 05 conserva el punto propio de observabilidad (DCGM/Prometheus) y la definición de reserva anticipada, con remisión al cap. 06. Se actualizaron las entradas correspondientes de `CITAS-VERIFICADAS.md`.
- **Verificación:** `make build` OK (77 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; queda 1 `\todo` en el capítulo 01.

### 2026-11-14 · cap. 01 · Justificación ¶2 · Costo de los servicios externos

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La afirmación de que los usuarios "dejan de depender de suscripciones comerciales que no todos pueden costear" no tiene respaldo. Matícenla o susténtenla, por ejemplo con el uso de Google Colab que mencionan en la sección 1.2.» → aplicado · «que dejan de depender de suscripciones comerciales que no todos pueden costear» → «que pueden prescindir de servicios externos como Google Colab, a los que parte de la comunidad recurría ante la falta de acceso». La frase se apoya en el dato ya presente en los Antecedentes y retira la generalización sin respaldo.
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el capítulo 01 queda sin `\todo`.

### 2026-11-14 · cap. 02 · §2.1 · Presentación de síntomas y causas

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «El capítulo repite la estructura de "tres síntomas" y "tres factores causales". Varíen la forma de presentar estos elementos para que la lectura no resulte mecánica.» → aplicado · los síntomas quedan en prosa continua, sin el conteo «tres síntomas» ni los marcadores «En primer lugar / En segundo lugar / En tercer lugar»; la introducción de las causas pasa de «De esta causa principal se desprenden tres factores causales» a «Esa ausencia se concreta en las siguientes carencias», y la lista se conserva.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 4 `\todo` en el capítulo 02.

### 2026-11-14 · cap. 02 y Anexo B · Causas del problema como carencias

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Las causas del problema nombran componentes de la solución, como un "plano de servicio que gestione motores de inferencia" o un "motor de políticas de cuotas". Este capítulo debe describir el problema sin anticipar la solución. Redacten las causas como carencias, sin nombrar los componentes que las resuelven.» → aplicado · la causa principal pasa a «la etapa de inferencia no cuenta con mecanismos integrados de administración»; las tres carencias se redactan como falta de automatización, falta de un mecanismo que traduzca los roles en cupos y falta de visibilidad en tiempo real. Se ajustaron los tres nodos de causas del Anexo B para que no contradigan el capítulo.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 3 `\todo` en el capítulo 02.

### 2026-11-14 · cap. 02 · Fuente de las cifras de matrícula

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Las cifras de matrícula no tienen fuente. Citen el documento o portal del que provienen e indiquen el año o periodo académico de corte.» → aplicado · la frase pasa a «De acuerdo con las estadísticas de matrícula de la Universidad Icesi para 2026 \citep{icesi-matricula-2026}». Se añadió la entrada `icesi-matricula-2026` a `references.bib` (panel institucional de analítica académica en Power BI, datos de 2026, consultado el 2026-10-12), la fila en `fuentes/INDEX.md` y la verificación en `CITAS-VERIFICADAS.md`.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 2 `\todo` en el capítulo 02.

### 2026-11-14 · cap. 02 · Doctorado en Ingeniería y demanda potencial

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «El Doctorado en Ingeniería se incluye entre los programas avanzados de computación e inteligencia artificial, aunque su alcance es más amplio. Justifiquen su inclusión o aclaren que solo una parte de esa población constituye demanda potencial.» → aplicado · se añade «Del Doctorado en Ingeniería, solo una parte de sus estudiantes desarrolla proyectos de computación e inteligencia artificial, de modo que no toda esa población constituye demanda potencial para la plataforma» y «más de 850 estudiantes» pasa a «cerca de 850 estudiantes».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; queda 1 `\todo` en el capítulo 02.

### 2026-11-14 · caps. 02 y 04 · Objetivo general y pregunta de ingeniería

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor, cap. 04): «El objetivo general contiene dos verbos, "construir" la plataforma y "consolidar" el ciclo de vida de MLOps. Definan cuál es el propósito principal del proyecto. Si construir la plataforma es un medio para consolidar el ciclo de vida, el verbo del objetivo debería ser el segundo, y la plataforma pasaría al "mediante". Mantengan un solo verbo y verifiquen que los objetivos específicos, en conjunto, permitan alcanzarlo.» → aplicado · el objetivo general pasa a «Consolidar el ciclo de vida de MLOps \emph{on-premise} en la Universidad Icesi, mediante la construcción de la plataforma...». Los objetivos específicos construyen los módulos y evalúan la plataforma, que es el medio para consolidar el ciclo.
- **F2** (tutor, cap. 02): «La pregunta de ingeniería incluye la solución ("diseñar y construir una plataforma") y un compromiso que el proyecto no medirá ("garantizando la estabilidad"). Además, sus verbos no coinciden con el del objetivo general. Alineen la pregunta con el objetivo general una vez lo ajusten y eviten verbos como "garantizar".» → aplicado · la pregunta pasa a «¿De qué manera se puede consolidar el ciclo de vida de MLOps \emph{on-premise} en el IAsLab, de modo que el despliegue de modelos de inferencia, la gobernanza de las GPU según los roles institucionales y la observabilidad del \emph{hardware} operen de forma articulada sobre su infraestructura de cómputo compartida?». Salen «diseñar y construir una plataforma» y «garantizando la estabilidad».
- **Propagación:** `project-context/documentation.md` (objetivo general en inglés), `thesis/STATUS.md` y el objetivo central del Anexo C.
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el capítulo 02 queda sin `\todo` y quedan 3 en el capítulo 04.

### 2026-11-14 · cap. 04 · Orden de los objetivos específicos

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «El orden de los objetivos específicos (observabilidad, gobernanza, despliegue y evaluación) no coincide con el orden de ejecución del capítulo 7 ni con el del diagrama de Gantt, que empiezan por el despliegue del clúster. Ordénenlos según la cadena de dependencias o expliquen por qué se presentan en otro orden.» → aplicado · se conserva el orden y se añade: «Los objetivos se presentan en el orden de los módulos y de los requerimientos que los sustentan (R1 a R4), no en el orden de ejecución del cronograma, que empieza por el clúster porque es la infraestructura que soporta a los demás módulos.» Se evita renumerar los códigos Rk-nn del Anexo D.
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 2 `\todo` en el capítulo 04.

### 2026-11-14 · cap. 04 · Resultado verificable del objetivo específico 3

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La expresión "fase de servicio consumible" es imprecisa. Expresen el resultado de forma verificable, por ejemplo, modelos accesibles mediante una API desde la plataforma.» → aplicado · «con el fin de llevar los modelos del laboratorio a una fase de servicio consumible» → «con el fin de que los modelos del laboratorio queden accesibles mediante una API desde la plataforma».
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; queda 1 `\todo` en el capítulo 04.

### 2026-11-14 · cap. 04 · Criterio de sostenibilidad del servicio

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «El objetivo no define qué significa que el servicio "se sostenga". Fijen el criterio, por ejemplo un umbral de latencia o de tasa de error, o remitan al capítulo donde se define.» → aplicado · el objetivo específico 4 añade «según los criterios de latencia, \emph{throughput} y tasa de error definidos en el \cref{sec:marco-conceptual}».
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el capítulo 04 queda sin `\todo`.

### 2026-11-14 · cap. 05 · Primera oración del capítulo

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La primera oración del capítulo tiene cerca de noventa palabras y enumera cinco dominios. Divídanla para facilitar la lectura.» → aplicado · la oración se divide en dos: «...exige integrar conocimiento de cinco dominios de la ingeniería de sistemas. Esos dominios son el ciclo de vida...».
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 12 `\todo` en el capítulo 05.

### 2026-11-14 · cap. 05 · Alcance de la distinción entrenamiento/inferencia

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La afirmación de que la distinción entre entrenamiento e inferencia se aplica a cualquier tipo de modelo (clasificadores, visión por computador, modelos generativos) no tiene cita. Respáldenla con una fuente o preséntenla como una posición de los autores.» → aplicado · «La distinción se aplica a cualquier tipo de modelo» → «Para este proyecto, la distinción se aplica a cualquier tipo de modelo». La afirmación queda declarada como posición de los autores.
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 11 `\todo` en el capítulo 05.

### 2026-11-14 · Anglicismos y glosario

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); decisiones de Melo088 en el chat: traducir *fine-grained*, *runtime* y *batch*; conservar *proxy*, *framework*, *kernels*, *backlog*, *throughput* y *token*.
- **F1** (tutor): «Revisen los anglicismos del documento... Tradúzcanlos cuando exista un equivalente claro en español. Si el concepto se entiende mejor en inglés, consérvenlo, defínanlo en su primer uso y añádanlo al glosario. Aprovechen para ampliar el glosario con los términos propios del proyecto...» → aplicado · *fine-grained* pasa a «detallado»; *runtime* a «entorno de ejecución»; *batch* a «lotes». Se conservan *proxy*, *framework*, *kernels*, *backlog*, *throughput* y *token*, definidos en su primer uso. El glosario incorpora operador, recurso personalizado, cuota, reserva, expropiación, motor de inferencia, *backlog*, *framework*, *kernels*, *proxy*, *throughput* y *token*.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 10 `\todo` en el capítulo 05.

### 2026-11-14 · cap. 05 · Orden de los párrafos de §4.2

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Revisen el orden de los párrafos de esta sección. "Dentro de ese espectro" remite al espectro de optimización de los LLM descrito dos párrafos antes, pero entre ambos se ubicó el párrafo sobre los modelos que no son de lenguaje, y lo mismo ocurre en el párrafo siguiente. Dejen juntos los párrafos sobre LLM y ubiquen el de los demás modelos al final de la sección.» → aplicado · el párrafo de los modelos que no son de lenguaje se trasladó al final de §4.2, después del párrafo de los motores, y abre con «También los modelos que no son de lenguaje reciben el mismo tratamiento».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 9 `\todo` en el capítulo 05.

### 2026-11-14 · cap. 05 · Cálculo de memoria para modelos cuantizados

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Respalden con una cita o con un cálculo de memoria la afirmación de que los modelos de 7000 a 14000 millones de parámetros caben en 24 GB de memoria de video.» → aplicado · se añade el cálculo: «Con pesos de 8 bits por parámetro, un modelo de 14 000 millones ocupa alrededor de 14 GB y uno de 7 000 millones, alrededor de 7 GB; con 4 bits, ocupan la mitad. Esos valores dejan margen dentro de los 24 GB para la caché de atención y el entorno de ejecución.»
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 8 `\todo` en el capítulo 05.

### 2026-11-14 · cap. 05 y cap. 10 · Términos de Kubernetes

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Den el término original en el primer uso de "marcas y tolerancias" (\emph{taints} y \emph{tolerations}) y de "espacios de nombres" (\emph{namespaces}), y usen los mismos nombres en el capítulo 9, donde aparecen como "marcas de reserva" y "un espacio con su límite".» → aplicado · el cap. 05 dice «marcas y tolerancias (\emph{taints} y \emph{tolerations})» y «espacios de nombres (\emph{namespaces})»; el cap. 10 pasa a «marcas (\emph{taints})» y «un espacio de nombres con su límite».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 7 `\todo` en el capítulo 05.

### 2026-11-14 · cap. 05 · Cita del diseño de Kubernetes

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción B aprobada por Melo088 en el chat.
- **F1** (tutor): «La afirmación inicial sobre el diseño de Kubernetes no tiene cita. Además, la sección termina con "las estaciones de trabajo de la sala", que en este punto el lector aún no conoce (ver el comentario sobre la sala 104M en el capítulo 1).» → aplicado · la oración pasa a «Kubernetes se diseñó para servicios de internet y, sin embargo, hoy hospeda cargas de inteligencia artificial \citep{xu-sing-2025}». La sala 104M ya se describe en el Contexto del cap. 01. Se retiró «sin que su núcleo haya sido rediseñado» porque Xu et al. no lo afirman.
- **Fuente:** Xu et al. (2025), p. 2, §1 («Originally designed for internet backend services…»; «…applied to ML model training jobs in campus ML clusters») y p. 3, §2.1.3 («Recently, Kubernetes has also been used to manage shared ML clusters»). Registrado en `CITAS-VERIFICADAS.md`.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 6 `\todo` en el capítulo 05.

### 2026-11-15 · caps. 05, 09 y 10 · Mecanismo de despliegue de modelos (KubeRay frente a *Deployment*)

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A+ aprobada por Melo088 en el chat.
- **F1** (tutor, cap. 05 §4.4): «Este párrafo presenta a KubeRay como el mecanismo con el que se despliegan los modelos, y el capítulo 8 lo menciona como una integración central del proyecto. Sin embargo, en el capítulo 9 la línea base del prototipo es un \emph{Deployment} de Kubernetes y Ray Serve aparece solo como una variante comparada. Alineen los capítulos 4, 8 y 9 con la decisión vigente o expliquen por qué cambió.» → aplicado · la oración de KubeRay pasa a presentar el recurso personalizado y el operador propios, el *Deployment* de Kubernetes como forma base para servir un modelo en un solo nodo, y KubeRay (*RayService*) como forma alternativa y vía prevista para repartir un modelo entre varios nodos.
- **F2** (tutor, cap. 09): «Este párrafo presenta la integración de KubeRay como una competencia central, aunque en el prototipo Ray quedó como una variante comparada. Ajústenlo según lo que decidan en el comentario de la sección 4.4.» → aplicado · «la integración de KubeRay y del NVIDIA GPU Operator» → «la integración del NVIDIA GPU Operator, el desarrollo de un operador propio que traduce cada despliegue en objetos nativos de Kubernetes, con KubeRay como vía para el servicio distribuido».
- **Cap. 10** (parte de la opción A+): se añade por qué cambió la decisión, «El diseño inicial servía cada despliegue con Ray Serve. La línea base pasó a un \emph{Deployment} porque el ejemplo oficial de KubeRay reserva cerca de 4 GiB por despliegue y porque Ray Serve no integra \emph{llama.cpp}, de modo que servirlo con Ray exige un adaptador propio. Ray Serve se conserva como variante porque es la vía para repartir un modelo entre varios nodos.»
- **Propagación:** `project-context/documentation.md`, §POC, viñeta *Architectural adjustments* (b), recibe las razones del ADR 0029 del repositorio de implementación (aceptado por los autores el 2026-10-26).
- **No incluido:** la elección de la forma de servir por parte del usuario (D-10), porque el operador todavía no genera `RayService`, y la mención a la línea base E0 pedida por el tutor.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 5 `\todo` en el capítulo 05 y 6 en el capítulo 09.

### 2026-11-15 · cap. 05 §4.5 y cap. 10 · Figura de gobernanza y concepto de fondo común

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción F1 aprobada por Melo088 en el chat.
- **F1** (tutor, cap. 05 §4.5): «Esta sección es muy densa y no tiene apoyo gráfico. Explica dos familias de planificación, la prioridad, la expropiación, las reservas, la sobreasignación y las cuotas solo con texto, y es el núcleo del objetivo 2. Añadan una figura que muestre cómo se relacionan la cuota por usuario, el fondo común de la sala, la prioridad por rol y la expropiación. Presenten aquí también el concepto de fondo común, que el capítulo 9 usa sin haberlo introducido.» → aplicado · el último párrafo de §4.5 introduce el fondo común, la cohorte de Kueue, la recuperación de la capacidad prestada y la carga expropiada, con cita a la documentación de Kueue; se añade la \cref{fig:gobernanza-cuotas}, un flujo de decisión de la admisión con flechas ortogonales. Se retiró el comentario LaTeX que pedía no nombrar Kueue, porque ya figura en `project-context/documentation.md`.
- **F2** (tutor, cap. 10): «Conceptos como el «fondo común» de cuota, «recuperar cuota» y «carga expropiada» no se presentan en el marco teórico. Introdúzcanlos en la sección 4.5 o explíquenlos aquí.» → aplicado · quedan introducidos en §4.5; se retiró el `\todo`.
- **Fuente:** `kueue-clusterqueue-2026`, página *Cluster Queue* (§Cohort, §Resources, §Preemption). Registrada en `CITAS-VERIFICADAS.md` y `fuentes/INDEX.md`.
- **Propagación:** `project-context/documentation.md`, viñeta *Governance and workloads*, recibe cómo funciona el fondo común en el POC (`Cohort`, `nominalQuota: 0`, `borrowingLimit` igual a la cuota efectiva, `reclaimWithinCohort: Any`), tomado de `backend/MANUAL-CRDS.md` §3.2–3.3.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el Marco teórico sigue entre las pp. 7 y 17; quedan 4 `\todo` en el capítulo 05 y 10 en el capítulo 10.

### 2026-11-15 · cap. 05 · Flechas ortogonales en las figuras 4.2 y 4.5

- **Revisó:** Melo088 (autor), en el chat.
- **F1** (humano): «aprovechemos a mejorar o corregir las otras figuras, donde, si bien el contenido puede estar bien, las flechas hacen que se vea desordenado, no quiero que hayan flechas diagonales, prefiero ortogonales.» → aplicado · en la \cref{fig:bucle-reconciliacion}, «Reconciliar» pasa debajo de «Analizar cambios» y «Estado actual» a su altura, de modo que el bucle forma un rectángulo y la flecha hacia «Observar» sube en ángulo recto; en la \cref{fig:flujo-observabilidad}, Prometheus y Thanos bajan a la fila de los servicios y la flecha del exportador DCGM llega con un codo. El contenido de ambas figuras no cambia.
- **Revisadas sin cambios:** figuras 4.1, 4.3 (gobernanza, nueva), 4.4 (identidad), 9.1, A.1, B.1 y C.1, que ya eran ortogonales. La 9.2 es una imagen de draw.io y queda para su propio comentario del tutor.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas.

### 2026-11-15 · cap. 05 · Tabla 4.1, fila «Recurso personalizado y operador»

- **Revisó:** Melo088 (autor); sugerencia de la IA aprobada en el chat («ajustalo»).
- **S1** (IA, aprobada por Melo088): la fila conservaba el encuadre de KubeRay corregido en §4.4 → aplicado · «Es el mecanismo por el que la plataforma declara clústeres de cómputo, trabajos y servicios de inferencia como objetos nativos del orquestador» → «Es el mecanismo por el que la plataforma describe cada despliegue como un objeto propio y lo traduce en objetos nativos del orquestador».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas.

### 2026-11-15 · caps. 01, 02, 05, 06 y 10 · Unificación de la terminología

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat, con la condición de no repetir un mismo término varias veces en un párrafo.
- **F1** (tutor, cap. 05 §4.5): «Unifiquen la terminología. Para un mismo concepto se usan varios términos, por ejemplo «sobreaprovisionamiento», «sobreasignación» y «sobresuscribir» en esta sección, «planificador» y «programador del clúster», «capa de admisión y encolamiento», «gestor de colas de cómputo» y «cola de cómputo», y «poner en operación», «puesta en servicio», «servir» y «desplegar». Elijan un término por concepto, defínanlo una vez y úsenlo igual en todo el documento.» → aplicado · términos elegidos: **sobreasignación**, **planificador** («planificador del clúster» para el de Kubernetes), **gestor de colas**, **desplegar** (llevar un modelo a ejecución) y **servir** (atender las solicitudes de un modelo desplegado, definido en §4.2). Desaparecen «sobreaprovisionamiento», «sobresuscribir», «programador del clúster», «capa de admisión (y encolamiento)», «cola de cómputo», «puesta en operación», «puesta en servicio» y «poner en servicio». La fila «Admisión y encolamiento» de la Tabla 4.1 pasa a «Gestor de colas», y el paso 4 de la Figura 9.1 a «Gestor de colas». El glosario incorpora Desplegar, Gestor de colas, Planificador, Servir y Sobreasignación.
- **Condición del autor** (Melo088): «lo que no quiero es que la palabra se repita varias veces en un mismo párrafo». Se revisó cada párrafo editado y se reformularon los que quedaban con tres o más apariciones: §4.4 (párrafo de las extensiones), §4.3 (primitivas del orquestador) y cap. 10 §Segunda etapa ¶1. Quedan dos apariciones en cap. 02 ¶ de la formulación, porque una de ellas está en la pregunta de ingeniería.
- **Citas:** se actualizaron en `CITAS-VERIFICADAS.md` las afirmaciones de Kreuzberger et al. (caps. 01 y 06) y de Cortez et al. (cap. 05); los pasajes siguen respaldándolas.
- **No incluido:** «desplegar» aplicado al clúster o a la plataforma (caps. 08 y 10) y «políticas de admisión» (cap. 10), que nombran otros conceptos.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; sin variantes residuales de los términos retirados; quedan 3 `\todo` en el capítulo 05.

### 2026-11-15 · caps. 01 y 10 · Repetición de «despliegue» en dos párrafos

- **Revisó:** Melo088 (autor); sugerencias de la IA aprobadas en el chat («aplica las dos propuestas»).
- **S1** (IA, aprobada por Melo088, cap. 01 ¶ «El despliegue manual…»): «despliegue»/«desplegar» aparecía 4 veces → aplicado · «el despliegue no podía gestionarse de forma desacoplada del anfitrión. Cada despliegue exigía…» → «ese proceso no podía gestionarse de forma desacoplada del anfitrión, y cada instalación exigía…». Quedan 2 apariciones.
- **S2** (IA, aprobada por Melo088, cap. 10 §Segunda etapa ¶2): «despliegue»/«desplegar» aparecía 6 veces → aplicado · «El estado del despliegue avanza por en cola…» → «La solicitud avanza por los estados en cola…»; «los registros de su despliegue» → «los registros de ejecución». Se conservó «el permiso para desplegar», porque «ese permiso», como se había propuesto, remitía a un permiso no mencionado antes. Quedan 4 apariciones.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas.

### 2026-11-15 · cap. 05 · §4.6 · Cita de las variantes del API gateway

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Las afirmaciones sobre las variantes del \emph{API gateway} para modelos de lenguaje y sobre la ausencia de variantes con cuotas unificadas no tienen cita, y no se explica cómo se hizo esa búsqueda. Citen las fuentes, por ejemplo la documentación de LiteLLM del capítulo 5, y remitan a la estrategia de búsqueda de la sección 5.1.» → aplicado · se añadió `\citep{litellm-proxyusers-2026}` a la frase sobre los límites por \emph{tokens}, y «La revisión de esta literatura no localizó» pasó a «La revisión documental descrita en la \cref{sec:estrategia-revision} no localizó». Se actualizó `CITAS-VERIFICADAS.md`.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 2 `\todo` en el capítulo 05.

### 2026-11-15 · cap. 05 · Documentación de la pila de observabilidad

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat, con verificación previa de las fuentes.
- **F1** (tutor): «Prometheus, Thanos, Loki, Grafana y el exportador DCGM se describen sin ninguna referencia. Citen su documentación oficial, como hacen en el capítulo 5.» → aplicado · se añadieron `prometheus-overview-2026`, `thanos-quick-tutorial-2026`, `loki-overview-2026`, `grafana-overview-2026` y `dcgm-exporter-2026` a `references.bib`, con su cita en la frase correspondiente. Se registraron en `fuentes/INDEX.md` y `CITAS-VERIFICADAS.md`, con los pasajes literales verificados.
- **Ajuste de fidelidad:** la documentación de DCGM no afirma que las métricas «residan en el \emph{firmware} del dispositivo»; esa cláusula se retiró.
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; queda 1 `\todo` en el capítulo 05.

### 2026-11-15 · cap. 05 · Explicación literal de las etiquetas de Loki

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «"Sin cambiar de sistema de coordenadas" es una metáfora poco clara. Expliquen literalmente qué permite, por ejemplo, consultar métricas y registros con las mismas etiquetas.» → aplicado · la frase pasa a «Loki agrega los registros que emiten los contenedores y los indexa por las mismas etiquetas, de modo que las métricas y los registros se pueden consultar con un mismo conjunto de etiquetas y es posible pasar de una anomalía observada en una gráfica a los registros que la produjeron».
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el capítulo 05 queda sin `\todo`.

### 2026-11-15 · cap. 06 · Siglas definidas de nuevo

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «En este capítulo se definen de nuevo siglas que ya se definieron antes, como GPU, MLOps e IAsLab. Definan cada sigla una sola vez, en su primer uso.» → aplicado · se retiraron las expansiones de GPU, MLOps, IAsLab y API en el cap. 06. Quedan solo las siglas, ya definidas en los capítulos 01 y 05.
- **Verificación:** `make build` OK (76 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 5 `\todo` en el capítulo 06.

### 2026-11-15 · cap. 06 · «Entre las que destaca LiteLLM»

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «"Entre las que destaca LiteLLM" no indica un criterio que justifique "destaca". Consideren "como LiteLLM".» → aplicado · «entre las que destaca LiteLLM» → «como LiteLLM».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 4 `\todo` en el capítulo 06.

### 2026-11-15 · cap. 06 · «Estas son lecturas de los autores»

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La última oración del párrafo ("Estas son lecturas de los autores…") es poco clara. Reformúlenla, por ejemplo, como "Esta valoración es de los autores y se basa en la documentación disponible".» → aplicado · «Estas son lecturas de los autores a partir de lo que la documentación describe y de lo que no describe» → «Esta valoración es de los autores y se basa en la documentación disponible».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 3 `\todo` en el capítulo 06.

### 2026-11-15 · cap. 06 · Prueba de vLLM en el laboratorio

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La afirmación de que vLLM "no produjo buenos resultados" es informal y no describe la prueba. Indiquen con qué modelo, con qué métrica y qué valores se obtuvieron, o citen la prueba como comunicación del laboratorio con su fecha.» → aplicado · la frase remite al banco de pruebas del laboratorio, describe la métrica («\emph{tokens} de entrada y salida por segundo y el tiempo de respuesta extremo a extremo») y cita la comunicación del laboratorio del 4 de septiembre de 2026. No se inventan el modelo ni los valores de vLLM, que no constan en `project-context/`.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 2 `\todo` en el capítulo 06.

### 2026-11-15 · cap. 06 · Rendimiento de llama.cpp

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La baja latencia y el consumo reducido de \emph{llama.cpp} se afirman sin evidencia en esta sección. Respáldenlos con una cita o remitan a las mediciones de la Tabla 9.1.» → aplicado · se retiran «baja latencia» y «consumo reducido», que la tabla no mide, y se remite a las mediciones preliminares: «\emph{llama.cpp} superó a vLLM en CPU para el modelo probado (\cref{tab:mediciones-poc})».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; queda 1 `\todo` en el capítulo 06.

### 2026-11-15 · cap. 06 · Tercer vacío redactado como carencia

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «De los tres vacíos, el tercero ("El tercero es acercar la telemetría…") está redactado como una meta y no como un vacío. Redáctenlo como una carencia.» → aplicado · «El tercero es acercar la telemetría…» → «El tercero es la ausencia de una interfaz de autoservicio que exponga a los administradores de una sala académica la telemetría…».
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el capítulo 06 queda sin `\todo`.

### 2026-11-15 · cap. 07 · Primer párrafo del capítulo

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «El primer párrafo del capítulo es una sola oración que enumera cinco contenidos. Divídanla para facilitar la lectura.» → aplicado · el párrafo se divide en tres oraciones: metodología y justificación; estructura lógica y elicitación de requerimientos; fases, cronograma y riesgos.
- **Verificación:** `make build` OK (75 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 5 `\todo` en el capítulo 07.

### 2026-11-15 · cap. 09 · Afirmaciones que el proyecto no mide

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088, con la condición de no repetir «contribuye a» tres veces.
- **F1** (tutor): «Expresiones como "maximiza el retorno de la inversión" y "reducen la carga cognitiva" (párrafo siguiente) son afirmaciones que el proyecto no medirá. Usen formulaciones como "contribuye a" y retiren o sustenten la referencia a la carga cognitiva.» → aplicado · «maximiza el retorno de la inversión» → «contribuye a aprovechar mejor la inversión»; «reduce la necesidad» → «ayuda a reducir la necesidad»; «reducen la carga cognitiva y administrativa» → «reducen la carga administrativa». Se varían los verbos para no repetir «contribuye a».
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 5 `\todo` en el capítulo 09.

### 2026-11-15 · cap. 09 · Modelos ya entrenados, no solo LLM

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La frase sobre "arquitecturas de gran escala, en particular los LLM" que pasan del entrenamiento al servicio de inferencia sugiere que el laboratorio entrena LLM, lo cual no está sustentado, y restringe el aporte a los modelos de lenguaje. Reformúlenla en términos de modelos de IA ya entrenados, propios o descargados.» → aplicado · «arquitecturas de gran escala, en particular los LLM» → «modelos de inteligencia artificial ya entrenados, propios o descargados».
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 4 `\todo` en el capítulo 09.

### 2026-11-15 · cap. 09 · Imagen de llama.cpp presentada antes de nombrarla

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «Revisen que todo elemento que se nombra haya sido presentado antes o tenga una referencia explícita. Por ejemplo, este párrafo menciona "la imagen oficial de \emph{llama.cpp}" como si el lector ya la conociera, y el capítulo 9 usa conceptos como el "fondo común" de cuota que no aparecen en el marco teórico. Hagan esta revisión en todos los capítulos.» → aplicado · «la imagen oficial de \emph{llama.cpp}» → «la imagen de contenedor que publica el proyecto \emph{llama.cpp}». El «fondo común» ya quedó definido en el cap. 05 §4.5 con su figura (commit `5704686`).
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 3 `\todo` en el capítulo 09.

### 2026-11-15 · caps. 05, 06 y 09 · Siglas CPU y RBAC en su primer uso

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «La sigla CPU (párrafo anterior) se usa sin definir, pues solo se define en el Anexo D, y RBAC se define aquí aunque el control de acceso basado en roles ya aparece en la sección 4.6. Definan cada sigla en su primer uso dentro del texto.» → aplicado · CPU se define en su primer uso real (cap. 06 §6.5): «unidad central de procesamiento (CPU)»; RBAC se introduce en el cap. 05 §4.6: «control de acceso basado en roles (RBAC)»; el cap. 09 pasa a «integración con sistemas RBAC», sin volver a expandir la sigla.
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; quedan 2 `\todo` en el capítulo 09.

### 2026-11-15 · cap. 09 · Métricas del objetivo 1 en la Tabla 8.1

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «En la Tabla 8.1, el resultado del objetivo 1 solo incluye métricas de modelos de lenguaje (\emph{tokens} por segundo). Añadan las métricas de los demás modelos, como la latencia y la tasa de peticiones atendidas (R1-24).» → aplicado · la fila del objetivo 1 añade «tasa de peticiones atendidas» a las métricas de carga de trabajo.
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; queda 1 `\todo` en el capítulo 09.

### 2026-11-15 · cap. 09 · Resultado del objetivo 4 en la Tabla 8.1

- **Revisó:** tutor del proyecto (correcciones de 2026-11-14); opción A aprobada por Melo088 en el chat.
- **F1** (tutor): «En la Tabla 8.1, el resultado del objetivo 4 incluye "el crecimiento de la capacidad por nodo", que no forma parte del objetivo tal como está redactado. Alineen la tabla con el objetivo o el objetivo con la tabla.» → aplicado · se retiró «y el crecimiento de la capacidad por nodo» de la fila del objetivo 4. El resultado queda alineado con el objetivo: pruebas de carga con usuarios concurrentes, incluidos los modelos que no son de lenguaje.
- **Verificación:** `make build` OK (74 páginas); cero citas y referencias indefinidas, cero cajas desbordadas; el capítulo 09 queda sin `\todo`.
