# Citas verificadas

Registro de cada cita indirecta de la tesis comprobada contra el texto completo de su fuente, según [`../skills/reference-writting/source-fidelity.md`](../skills/reference-writting/source-fidelity.md). Una cita que no aparece aquí **no está verificada**.

Cada entrada guarda la versión del documento consultada y, por cada uso en la tesis, la afirmación tal como está escrita, el pasaje literal de la fuente con su ubicación y el estado:

- **verificada:** el pasaje respalda la afirmación, en sus términos.
- **sin respaldo:** la afirmación dice algo que la fuente no dice; queda pendiente de corregir en la revisión de ese apartado.

Los pasajes van en el idioma original y sin traducir. Las páginas son las del PDF consultado, salvo que se indique la paginación impresa.

---

## sculley-hiddentechnicaldebt-2015

- **Versión consultada:** `fuentes/pdf/sculley-hiddentechnicaldebt-2015.pdf`, PDF de NeurIPS 2015, <https://papers.nips.cc/paper_files/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · «su código es solo una pequeña fracción de un sistema real, rodeado de una infraestructura extensa que incluye el servicio y el monitoreo de los modelos»
    - Pasaje: "Figure 1: Only a small fraction of real-world ML systems is composed of the ML code, as shown by the small black box in the middle. The required surrounding infrastructure is vast and complex." (p. 4, Figura 1). La figura incluye los recuadros *Serving Infrastructure* y *Monitoring* (verificado sobre la imagen de la página, porque `pdftotext` no extrae el texto de la figura).
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · **retirada el 2026-09-13** por extensión (el cap. 01 pasaba de 3 páginas) y porque la deuda técnica no aporta al hilo del párrafo. El pasaje sigue verificado para usos futuros: "we argue that ML systems have a special capacity for incurring technical debt […] This debt may be difficult to detect because it exists at the system level rather than the code level." (p. 1, §1 *Introduction*)
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «tratar el modelo entrenado como el sistema completo, sin atender la infraestructura que lo sirve, es la fuente principal de la deuda técnica oculta de estos sistemas»
    - La fuente no presenta ninguna causa como «fuente principal» de la deuda; enumera varios factores de riesgo (*boundary erosion, entanglement, hidden feedback loops, undeclared consumers, data dependencies, configuration issues, changes in the external world*, p. 1, *Abstract*).
    - **Estado:** sin respaldo · pendiente de la revisión del cap. 05

## kreuzberger-mlopsoverview-2023

- **Versión consultada:** `fuentes/pdf/kreuzberger-mlopsoverview-2023.pdf`, preprint de arXiv 2205.02302, <https://arxiv.org/pdf/2205.02302> (2026-09-13). `references.bib` cita la versión publicada en *IEEE Access* 11 (2023). Las páginas de abajo son las del preprint: si alguna vez se cita textualmente, hay que confirmar el pasaje y la página en la versión publicada.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · «definen las operaciones de aprendizaje automático (MLOps) como un paradigma que abarca la conceptualización, implementación, monitoreo, despliegue y escalabilidad de estos productos»
    - Pasaje: "MLOps (Machine Learning Operations) is a paradigm, including aspects like best practices, sets of concepts, as well as a development culture when it comes to the end-to-end conceptualization, implementation, monitoring, deployment, and scalability of machine learning products." (p. 8, §6 *Conceptualization*)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · «e incluyen un componente dedicado a vigilar de forma continua el desempeño en servicio y el estado de la infraestructura»
    - Pasaje: "C9 Monitoring Component (P8, P9). The monitoring component takes care of the continuous monitoring of the model serving performance (e.g., prediction accuracy). Additionally, monitoring of the ML infrastructure, CI/CD, and orchestration are required" (p. 4, §4.2)
    - **Estado:** verificada · 2026-09-13
  - Términos que la fuente **no** usa y no deben atribuírsele: *quota*, *telemetry*, *access governance*. La única aparición de *governance* se refiere a los artefactos: "These repetitive tasks yield a large number of artifacts that require a strong governance" (p. 8, §7).
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «MLOps designa la disciplina que extiende las prácticas de integración y entrega continuas, control de versiones y monitoreo del desarrollo de *software* convencional al ciclo de vida completo»
    - **Estado:** sin verificar · pendiente de la revisión del cap. 05

## eken-mlopsmultivocalreview-2026

- **Versión consultada:** `fuentes/pdf/eken-mlopsmultivocalreview-2026.pdf`, preprint de arXiv 2406.09737v2 (2025-04-16), <https://arxiv.org/pdf/2406.09737> (2026-09-13). `references.bib` cita la versión publicada en *ACM Computing Surveys* 58(2), pp. 1–35 (en línea 2025-09-08, número de 2026). La versión publicada está pendiente de descarga manual (ACM DL devolvió HTTP 403 al agente). El resumen publicado se contrastó en Crossref (`api.crossref.org/works/10.1145/3747346`) y la frase citada coincide palabra por palabra.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · «advierten que un cuerpo de conocimiento integrado sobre MLOps sigue sin lograrse, porque su alcance es amplio y abarca desafíos muy diversos de esa transición»
    - Pasaje: "Despite the utility of MLOps, an integrated body of knowledge regarding MLOps remains elusive because of its extensive scope due to the diversity of ML productionalization challenges it addresses." (p. 1, *Abstract*; idéntico en la versión publicada)
    - Es afirmación propia de la revisión, no atribuida a otro estudio.
    - «Esa transición» retoma la primera oración del párrafo (llevar un modelo a producción) y traduce *productionalization*, que la fuente define así: "Productionalization of ML models refers to the process of transitioning ML models from a laboratory setting to a production environment" (p. 1, §1).
    - **Estado:** verificada · 2026-09-13
  - Aviso de atribución para usos futuros: en §5 (desafíos) muchas afirmaciones concretas se apoyan en un solo estudio primario (por ejemplo, el costo de infraestructura en §5.2.1 se atribuye a [PS129]). Citar a Eken et al. por esas afirmaciones exige decir que la revisión las recoge de un estudio, o ir al estudio original.

## lima-mlopspractices-2022

- **Versión consultada:** `fuentes/pdf/lima-mlopspractices-2022.pdf`, PDF de SciTePress, <https://www.scitepress.org/Papers/2022/109973/109973.pdf> (2026-09-13). Paginación impresa 308–320.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · **retirada el 2026-09-13.** La tesis citaba la conclusión «there is a significant gap in the detailing of activities related to operationalizing machine learning models» (p. 318 impresa, §6). El pasaje respaldaba la frase, pero los autores la retiraron porque describe el estado del campo en 2022 y puede no seguir vigente en 2026 (`skills/reference-writting/recency.md`, «Claims about the state of a field»). La reemplaza `eken-mlopsmultivocalreview-2026`.
  - Términos que la fuente **no** usa: *quota*, *telemetry*, *governance*.
  - Aviso de atribución: la frase de que el monitoreo es «one of the most relevant activities of MLOps practices» está en la sección de antecedentes (p. 310 impresa) y Lima et al. la atribuyen a Cardoso Silva et al. (2020). No es hallazgo propio de la revisión.
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «ubican el despliegue, el monitoreo en producción y la gobernanza de acceso entre las prácticas centrales de ese ciclo»
    - La fuente no menciona la gobernanza de acceso, y el monitoreo aparece como afirmación de antecedentes atribuida a otro estudio.
    - **Estado:** sin respaldo · pendiente de la revisión del cap. 05

## gao-lowgpuutilization-2024

- **Versión consultada:** `fuentes/pdf/gao-lowgpuutilization-2024.pdf`, versión de autor en Microsoft Research, <https://www.microsoft.com/en-us/research/wp-content/uploads/2024/01/gpu-util-icse2024.pdf> (2026-09-13). Publicada en ICSE 2024, DOI 10.1145/3597503.3639232.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶3 · «Incluso en plataformas empresariales multiusuario de aprendizaje profundo, algunos trabajos presentan una utilización notablemente baja de las GPU asignadas, lo que desperdicia recursos valiosos y reduce la productividad del desarrollo»
    - Pasaje: "Enterprise developers submit and run deep learning jobs on shared, multi-tenant platforms to efficiently train and test models. […] However, certain jobs exhibit rather low utilization of the allocated GPUs, resulting in substantial resource waste and reduced development productivity." (p. 1, *Abstract*); "precious platform resources" (p. 2, §1)
    - *Notablemente* traduce *rather low*; *algunos trabajos* traduce *certain jobs*. No se escribe «los trabajos», que generalizaría a todos.
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶3 · «El estudio analizó 400 casos reales en un entorno corporativo de gran tamaño, elegidos entre los que aprovechaban en promedio la mitad o menos de su capacidad, e identificó en ellos 706 problemas de este tipo, originados en el código de cada trabajo por cómputo insuficiente en el acelerador o por interrupciones de tareas ajenas a él»
    - Pasajes: "we retained only those jobs with an average GPU utilization of 50% or less […] Lastly, we randomly selected 400 jobs" (p. 3, §3.2); "we discovered 706 low-GPU-utilization issues across the sampled jobs. These issues were attributed to the code logic of scripts and programs." (p. 2, §1); "Low GPU utilization of deep learning jobs stems from insufficient GPU computations (e.g., using a small batch size or running a non-DL, CPU-centric job) and interruptions caused by non-GPU tasks" (p. 2, §1). Escala: "Platform-X, Microsoft's internal deep learning platform, operates across multiple physical GPU clusters, supporting hundreds of developers" (p. 2, §2).
    - La redacción propuesta por los autores decía que los problemas se derivaban «de la complejidad de gestionar cargas de trabajo concurrentes». La fuente no lo dice: atribuye los problemas al código de los trabajos. Se reemplazó por las causas que la fuente reporta.
    - La frase siguiente («Si el problema aparece a esa escala, es razonable que un laboratorio académico también necesite herramientas para detectarlo y controlarlo») es de los autores y va sin cita. «La mitad o menos de su capacidad» equivale al umbral de ≤ 50 % de utilización promedio de GPU, y «el acelerador» es la GPU.
    - **Estado:** verificada · 2026-09-13
  - Pasajes verificados que la tesis **ya no usa** (salieron del Contexto el 2026-09-13 porque desviaban el párrafo, a pedido de los autores). Quedan disponibles para el Marco teórico:
    - "(4) Most (84.99%) low-GPU-utilization issues could be fixed with a small number of code/script modifications." (p. 1, *Abstract*)
    - "Platform-X employs Prometheus [61] to monitor system status and gather real-time metrics for each DL job at regular intervals. GPU utilization data is retrieved from the NVIDIA Data Center GPU Manager (DCGM)." (p. 3, §2). Platform-X está construida con Kubernetes y Docker (p. 2, §1).

## jeon-philly-2019

- **Versión consultada:** `fuentes/pdf/jeon-philly-2019.pdf`, versión publicada en las actas de USENIX ATC 2019 (acceso abierto), <https://www.usenix.org/system/files/atc19-jeon.pdf> (2026-09-13). Páginas impresas.
- **Retirada del cap. 01 el 2026-09-13** (decisión de los autores). El cambio de escala (clústeres industriales de miles de GPU) rompía el hilo de Antecedentes, y ahí la reemplazan fuentes académicas (`xu-sing-2025`, `weitzel-nrpreservation-2025`). Los pasajes de abajo siguen verificados y quedan como **candidatos para el Estado del arte**, que todavía no se redacta. Los usos del cap. 01 listados abajo ya no están en el texto.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «analizaron una traza de dos meses de Philly, un servicio de Microsoft para entrenar modelos, con cerca de 100 000 trabajos de cientos de usuarios»
    - Pasajes: "we describe Philly, a service in Microsoft for training machine learning models" y "Our analysis spans across two months and uses around 100,000 jobs run by hundreds of users." (p. 947, §1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «aunque la mayoría de las GPU estaban asignadas, las que se usaban tenían en promedio solo cerca del 52 % de utilización, y que cerca del 30 % de los trabajos se cancelaba o terminaba sin éxito por fallas»
    - Pasajes: "Even though most GPUs within a cluster are allocated to users, thus suggesting high cluster utilization, this metric alone is misleading. We show that the hardware utilization of GPUs in use is only around 52% on average." y "Around 30% of jobs are killed or finish unsuccessfully due to failures." (p. 948, §1)
    - **Estado:** verificada · 2026-09-13
  - Uso anterior **corregido** el 2026-09-13: la tesis hablaba de «restricciones de localidad de datos», pero el paper estudia la localidad en la ubicación de las GPU para la sincronización del entrenamiento ("greater locality improves performance due to the availability of faster interconnects for parallel training", p. 948), no la localidad de datos.

## gu-tiresias-2019

- **Versión consultada:** `fuentes/pdf/gu-tiresias-2019.pdf`, versión publicada en las actas de USENIX NSDI 2019 (acceso abierto), <https://www.usenix.org/system/files/nsdi19-gu.pdf> (2026-09-13). Páginas impresas.
- **Retirada del cap. 01 el 2026-09-13** (decisión de los autores). El cambio de escala (clústeres industriales de miles de GPU) rompía el hilo de Antecedentes, y ahí la reemplazan fuentes académicas (`xu-sing-2025`, `weitzel-nrpreservation-2025`). Los pasajes de abajo siguen verificados y quedan como **candidatos para el Estado del arte**, que todavía no se redacta. Los usos del cap. 01 listados abajo ya no están en el texto.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «observaron en un clúster de producción que los planificadores diseñados para el análisis de grandes volúmenes de datos causan largas demoras en cola y un bajo desempeño general con trabajos de entrenamiento de aprendizaje profundo»
    - Pasaje: "Deep learning (DL) training jobs bring some unique challenges to existing cluster managers […] Our analysis of a large GPU cluster in production shows that existing big data schedulers cause long queueing delays and low overall performance." (p. 485, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - Uso anterior **corregido** el 2026-09-13: la tesis concluía, en la misma frase de la cita, que el hallazgo «explica por qué el IAsLab no puede resolver la orquestación de inferencia ni la gobernanza de cuotas». El paper trata el entrenamiento, no la inferencia, y no dice nada sobre el IAsLab.

## weng-mlaasinthewild-2022

- **Versión consultada:** `fuentes/pdf/weng-mlaasinthewild-2022.pdf`, versión publicada en las actas de USENIX NSDI 2022 (acceso abierto), <https://www.usenix.org/system/files/nsdi22-paper-weng.pdf> (2026-09-13). Páginas impresas.
- **Retirada del cap. 01 el 2026-09-13** (decisión de los autores). El cambio de escala (clústeres industriales de miles de GPU) rompía el hilo de Antecedentes, y ahí la reemplazan fuentes académicas (`xu-sing-2025`, `weitzel-nrpreservation-2025`). Los pasajes de abajo siguen verificados y quedan como **candidatos para el Estado del arte**, que todavía no se redacta. Los usos del cap. 01 listados abajo ya no están en el texto.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «identifican retos como la baja utilización de las GPU y las largas demoras en cola en un clúster de Alibaba con más de 6 000 GPU»
    - Pasaje: "we present a characterization study of a two-month workload trace collected from a production MLaaS cluster with over 6,000 GPUs in Alibaba. We explain the challenges posed to cluster scheduling, including the low GPU utilization, the long queueing delays, […]" (p. 945, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - Uso anterior **corregido** el 2026-09-13: la tesis lo agrupaba con Liu et al. para afirmar que «estos estudios confirman que la telemetría *fine-grained* es la condición necesaria». El paper es una caracterización de carga y planificación, no un estudio de telemetría, y no hace esa afirmación.

## liu-gpufailureprediction-2022

- **Versión consultada:** `fuentes/pdf/liu-gpufailureprediction-2022.pdf`, preprint de arXiv 2201.11853v1 (2022-01-27), <https://arxiv.org/pdf/2201.11853> (2026-09-13). `references.bib` también lo cita como preprint de arXiv.
- **Retirada del cap. 01 el 2026-09-13** (decisión de los autores). El cambio de escala (clústeres industriales de miles de GPU) rompía el hilo de Antecedentes, y ahí la reemplazan fuentes académicas (`xu-sing-2025`, `weitzel-nrpreservation-2025`). Los pasajes de abajo siguen verificados y quedan como **candidatos para el Estado del arte**, que todavía no se redacta. Los usos del cap. 01 listados abajo ya no están en el texto.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶4 · «las fallas de GPU interrumpen entrenamientos distribuidos, hacen caer servicios de inferencia y provocan incumplimientos de los acuerdos de nivel de servicio»
    - Pasaje: "GPU failures, which are inevitable, cause severe consequences in DL tasks: they disrupt distributed trainings, crash inference services, and result in service level agreement violations." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶4 · «proponen predecirlas con modelos entrenados sobre datos recolectados de GPU en producción, y sus técnicas elevan la precisión de la predicción del 46.3 % al 84.0 % en un conjunto de 350 millones de registros de cuatro meses»
    - Pasaje: "we propose to predict failures by using ML models. […] We evaluate the performances of our various techniques on a four-month production dataset including 350 million entries. The results show that our proposed techniques improve the prediction precision from 46.3% to 84.0%." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - Uso anterior **corregido** el 2026-09-13: la tesis decía que «trescientos cincuenta millones de registros de telemetría […] elevan la precisión». La mejora la producen las técnicas que proponen los autores (ensambles de modelos y entrenamiento deslizante), no el volumen de datos.

## sevilla-computetrends-2022

- **Versión consultada:** `fuentes/pdf/sevilla-computetrends-2022.pdf`, preprint de arXiv 2202.05924v2 (2022-03-09), <https://arxiv.org/pdf/2202.05924> (2026-09-13). `references.bib` cita la versión publicada en IJCNN 2022 (IEEE, doi:10.1109/IJCNN55064.2022.9891914), cuyo orden de autores se tomó de Crossref.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶2 · «Desde la llegada del aprendizaje profundo a comienzos de la década de 2010, el cómputo necesario para entrenar los sistemas más avanzados se ha duplicado aproximadamente cada seis meses»
    - Pasaje: "Since the advent of Deep Learning in the early 2010s, the scaling of training compute has accelerated, doubling approximately every 6 months. […] Overall, our work highlights the fast-growing compute requirements for training advanced ML systems." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-13

## ahmed-industryinfluence-2023

- **Versión consultada:** `fuentes/pdf/ahmed-industryinfluence-2023.pdf`, copia del *Policy Forum* publicada por el MIT Initiative on the Digital Economy, <https://ide.mit.edu/wp-content/uploads/2023/03/0303PolicyForum_Ai_FF-2.pdf> (2026-09-13). Trae la maquetación de *Science* 379(6635), p. 884, con la fecha aún como marcador («3 MONTH 2023»), así que es anterior a la impresión final. Metadatos de la versión publicada confirmados en Crossref.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶2 · «La industria domina una porción cada vez mayor de ese poder de cálculo, mientras la academia cuenta con menos del que necesita para investigar, sobre todo en unidades de procesamiento gráfico (GPU)»
    - Pasajes: "industry increasingly dominates the three key ingredients of modern AI research: computing power, large datasets, and highly skilled researchers." y "This is not just a difference in approach but a shortfall in computing available to academics. For example, data from Canada's National Advanced Research Computing Platform reveals that academic demand for graphics processing units (GPUs; the most common chips used in AI) on their platform has increased 25-fold since 2013 (see SM), but supply has only been able to meet 20% of this demand in recent years." (p. 884)
    - La tesis generaliza sin nombrar el caso de Canadá, a pedido de los autores, y se apoya en la afirmación general del artículo («a shortfall in computing available to academics»), no en extrapolar el dato canadiense.
    - **Estado:** verificada · 2026-09-13

## xu-sing-2025

- **Versión consultada:** `fuentes/pdf/xu-sing-2025.pdf`, preprint de arXiv 2110.01556v2 (2025-05-14), que ya lleva el encabezado de ASPLOS '25, <https://arxiv.org/pdf/2110.01556> (2026-09-13). `references.bib` cita la versión publicada (doi:10.1145/3669940.3707266). Páginas del PDF consultado.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «a partir de la operación de un clúster de más de 160 GPU al servicio de más de 480 usuarios de su universidad»
    - Pasaje: "Launched in early 2021, SING has become a cornerstone of our institution's AI research infrastructure, managing over 160 GPUs and serving over 480 active users." (p. 2, §1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «señalan que compartir estos recursos es esencial para aprovecharlos y ampliar el acceso, aunque gestionarlos plantea desafíos que van desde la configuración del sistema hasta el reparto equitativo entre usuarios, con personal limitado para operarlos»
    - Pasaje: "The rapid advancement of large machine learning (ML) models has driven universities worldwide to invest heavily in GPU clusters. Effectively sharing these resources among multiple users is essential for maximizing both utilization and accessibility. However, managing shared GPU clusters presents significant challenges, ranging from system configuration to fair resource allocation among users. […] Aimed at addressing the pressing need for efficient resource sharing with limited staffing" (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «muchas universidades adoptan una herramienta conocida con configuraciones subóptimas y terminan subutilizando recursos ya limitados»
    - Pasaje: "many universities do not have the expertise to make the best use of shared GPU clusters. In most cases, campus IT (or graduate students) pick a tool that they are familiar with (e.g., Slurm) and use it as-is with sub-optimal settings. Consequently, they end up underutilizing the already limited resources" (p. 1, §1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «Un esquema simple y común, que entrega a los usuarios acceso directo por consola a las máquinas con GPU, carece de mecanismos de aislamiento y de gestión, obliga a cada usuario a configurar su entorno y a coordinar a mano el uso de las GPU, y dificulta que el reparto sea equitativo»
    - Pasajes: "A simple and common approach to GPU sharing is to provide direct shell access to users" (p. 2, §1); "A common approach is to grant users native shell access to GPU-equipped machines through SSH […] due to the lack of resource isolation and management mechanisms, this method raises concerns about system stability and security. Without careful coordination, it can result in conflicts between competing user sessions, degrading system performance and making it difficult to ensure fair resource allocation." y "Step 2. Manual Environment Setup: Users are responsible for manually configuring their runtime environments […] Step 3. Resource Allocation: Users must manually coordinate GPU resources through other channels" (p. 3, §2.1.1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* ¶3 · «el consumo base de los equipos, que incluye la potencia en reposo de sus componentes, se mantiene relativamente constante sin importar cuántas GPU estén ocupadas, y la GPU representa la mayor parte de la potencia demandada»
    - Pasajes: "the base power draw, which includes the idle power of the CPU, GPU, and other components, is relatively constant and independent of the GPU occupancy rate" y "Figure 9. Cluster-wide power draw over the same time period as in Figure 8, showing the GPU power is dominant." (p. 11, §5.2)
    - La frase siguiente («Un acelerador asignado que no se usa gasta energía sin producir resultados…») es de los autores y va sin cita.
    - **Estado:** verificada · 2026-09-13
  - La fuente no usa «monopolización». Habla de reparto equitativo y de límites para evitar la ocupación excesiva ("to prevent excessive occupation during peak hours", p. 12, §5.2). En la tesis, el riesgo de monopolización aparece solo en la frase de los autores, respaldada por `project-context/documentation.md` (*Problem Description*).

## weitzel-nrpreservation-2025

- **Versión consultada:** `fuentes/pdf/weitzel-nrpreservation-2025.pdf`, preprint de arXiv 2505.22864v1 (2025-05-28), que ya lleva la referencia de PEARC '25 (doi:10.1145/3708035.3736060, añadido a `references.bib` el 2026-09-13), <https://arxiv.org/pdf/2505.22864> (2026-09-13). Páginas del PDF consultado.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶4 · «un clúster Kubernetes multiusuario que en 2024 atendió a investigadores de 50 campus»
    - Pasajes: "a distributed, multi-tenant Kubernetes-based cyberinfrastructure" (p. 1, *Abstract*); "In calendar year 2024, there were 670 NRP Nautilus Namespaces […] Individual campus researchers (525). These latter 525 Namespaces consumed >3/4 of the GPU-Hrs […] The individual PIs of these 525 researcher Namespaces came from 50 campuses" (p. 2, §1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶4 · «la introducción de un sistema de reservas para las GPU de mayor demanda elevó la utilización promedio de las GPU del clúster del 21.49 % al 31.37 %, aunque sus operadores reconocen que aún hay margen de mejora»
    - Pasaje: "With the rising demand for high-end GPUs, […] the NRP implemented an allocation system aimed at optimizing GPU utilization. Following the introduction of the reservation system for A100 GPUs, average GPU utilization across the cluster improved significantly from 21.49% to 31.37%. Although there is still room for further enhancement, this marked improvement underscores the effectiveness of the reservation system." (p. 4, §3.1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «introducir reservas sobre GPU elevó sustancialmente la utilización promedio del clúster»
    - **Estado:** sin verificar · pendiente de la revisión del cap. 05 (el pasaje de arriba es el candidato)

## frantar-gptq-2023

- **Versión consultada:** `fuentes/pdf/frantar-gptq-2023.pdf`, preprint de arXiv 2210.17323v2 (2023-03-22), marcado «Published as a conference paper at ICLR 2023», <https://arxiv.org/pdf/2210.17323> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13** (decisión de los autores): el párrafo sobre cuantización tenía un nivel de detalle de implementación y trataba una capacidad fuera del alcance. La frase decía que reducen un modelo de 175 mil millones de parámetros a 3–4 bits por peso en unas cuatro horas con degradación despreciable. Es fiel a: "GPTQ can quantize GPT models with 175 billion parameters in approximately four GPU hours, reducing the bitwidth down to 3 or 4 bits per weight, with negligible accuracy degradation relative to the uncompressed baseline." (p. 1, *Abstract*)
  - `chapters/05-marco-teorico.tex` · `\label{sec:servicio-inferencia-motores}` · **sin verificar** · pendiente de la revisión del cap. 05

## lin-awq-2024

- **Versión consultada:** `fuentes/pdf/lin-awq-2024.pdf`, versión publicada en las actas de MLSys 2024 (acceso abierto), <https://proceedings.mlsys.org/paper_files/paper/2024/file/42a452cbafa9dd64e9ba4aa95cc1ef21-Paper-Conference.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13** junto con el párrafo de cuantización. La frase decía «reportan una aceleración superior a 3 veces frente a la implementación de referencia» y atribuía la aceleración a AWQ, cuando la fuente se la atribuye a **TinyChat**, el *framework* de inferencia que presentan junto a AWQ: "Alongside AWQ, we implement TinyChat, an efficient and flexible inference framework tailored for on-device LLM/VLMs, offering more than 3× speedup over the Huggingface FP16 implementation on both desktop and mobile GPUs." (p. 1, *Abstract*)
  - `chapters/05-marco-teorico.tex` · `\label{sec:servicio-inferencia-motores}` · **sin verificar** · pendiente de la revisión del cap. 05 (revisar la misma atribución)

## dettmers-llmint8-2022

- **Versión consultada:** `fuentes/pdf/dettmers-llmint8-2022.pdf`, versión publicada en las actas de NeurIPS 2022 (acceso abierto), <https://proceedings.neurips.cc/paper_files/paper/2022/file/c3ba4962c05c49636d4c6206a97e9c8a-Paper-Conference.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13** junto con el párrafo de cuantización. La frase («LLM.int8() reduce a la mitad la memoria necesaria para la inferencia sin pérdida perceptible de precisión») es fiel a: "We develop a procedure for Int8 matrix multiplication for feed-forward and attention projection layers in transformers, which cut the memory needed for inference by half while retaining full precision performance." (p. 1, *Abstract*)
  - `chapters/05-marco-teorico.tex` · `\label{sec:servicio-inferencia-motores}` · **sin verificar** · pendiente de la revisión del cap. 05
- **Aviso general para los tres:** la afirmación de la tesis «Esta evidencia respalda que existen modelos precuantizados que caben en la VRAM disponible» no tenía respaldo en ninguno de ellos, porque proponen métodos de cuantización y no hablan de modelos precuantizados de terceros. Salió con el párrafo.

## wiest-privacypreservingllm-2024

- **Versión consultada:** `fuentes/pdf/wiest-privacypreservingllm-2024.pdf`, versión publicada en *npj Digital Medicine* 7, 257 (acceso abierto), <https://www.nature.com/articles/s41746-024-01233-2.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13**: los autores decidieron omitir el impacto en el manejo de datos. Pasajes verificados por si se retoma: "these LLMs run as cloud services and using them requires the transfer of privileged information to remote servers. This brings along immense legal and ethical challenges, especially in the European Union (EU), where the export of personal health data is not legally permitted. Ideally, LLMs should run on-premise of healthcare institutions" y "Quantized models have lower numerical precision of the model parameters and have lower graphics processing unit (GPU) memory consumption than unquantized models, allowing for easier integration with existing hospital hardware." (p. 2). La tesis decía «riesgos»; la fuente dice *challenges*.
