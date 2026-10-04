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
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · **versión de JDLP retirada el 2026-09-13.** Decía que tratar el modelo entrenado como producto terminado «genera una deuda técnica que permanece invisible durante el desarrollo y emerge cuando el sistema debe operar». La fuente no presenta ninguna causa como fuente principal de la deuda ni describe ese momento de aparición; enumera varios factores de riesgo (p. 1, *Abstract*).
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «el código del modelo ocupa una fracción pequeña del conjunto, y la infraestructura que lo rodea, que incluye la configuración, la infraestructura de servicio, la gestión de los recursos de cómputo y el monitoreo, es extensa y compleja»
    - Pasaje: el mismo de la Figura 1 (p. 4), cuyos recuadros incluyen *Configuration*, *Machine Resource Management*, *Serving Infrastructure* y *Monitoring*.
    - **Estado:** verificada · 2026-09-13
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «estos sistemas tienen una capacidad especial para acumular deuda técnica, difícil de detectar porque se sitúa en el nivel del sistema completo, fuera del código del modelo»
    - Pasaje: "we argue that ML systems have a special capacity for incurring technical debt […] This debt may be difficult to detect because it exists at the system level rather than the code level." (p. 1, §1 *Introduction*)
    - **Estado:** verificada · 2026-09-13
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶1 · «la identificación de los costos ocultos de mantener sistemas de aprendizaje automático en producción»
    - Pasaje: "we find it is common to incur massive ongoing maintenance costs in real-world ML systems" (p. 1, *Abstract*). La versión anterior decía que esa identificación «motivó» la formalización de MLOps; Kreuzberger et al. no citan a Sculley et al., y la frase quedó como secuencia («tras la identificación…»).
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶3 · **uso retirado el 2026-09-27**: se citaba para afirmar que Kubeflow y TensorFlow Serving son «las alternativas más citadas»; la fuente es de 2015 y no los menciona.

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
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «MLOps designa un paradigma que reúne buenas prácticas, conceptos y una cultura de desarrollo para la conceptualización, implementación, monitoreo, despliegue y escalabilidad de extremo a extremo de los productos de aprendizaje automático, y que se apoya en tres disciplinas, el aprendizaje automático, la ingeniería de *software* (en particular DevOps) y la ingeniería de datos» (reescrita el 2026-09-13; la versión anterior le atribuía una lista de prácticas que el pasaje de definición no enumera así)
    - Pasaje: el de p. 8, §6 citado arriba, que continúa: "Most of all, it is an engineering practice that leverages three contributing disciplines: machine learning, software engineering (especially DevOps), and data engineering."
    - **Estado:** verificada · 2026-09-13
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶1 · «la literatura propuso el paradigma de MLOps para el ciclo de vida de estos sistemas […], aunque [Eken et al.] advierten que su conceptualización unificada sigue sin lograrse»
    - Pasaje: "The paradigm of Machine Learning Operations (MLOps) addresses this issue. MLOps includes several aspects, such as best practices, sets of concepts, and development culture. However, MLOps is still a vague term" (*Abstract*); y, en Eken et al., "an evidence-based body of knowledge regarding MLOps practices and tools grounded in a unified conceptualization of the MLOps concept remains elusive" (introducción)
    - **Estado:** verificada · 2026-10-04. «Formalizó el ciclo de vida» se cambió porque las fuentes no dicen que lo formalizaran; ambas hablan de un paradigma todavía sin conceptualización unificada.
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶1 · «recogen, entre los servicios en la nube para poner modelos en servicio, Microsoft Azure ML, AWS SageMaker, IBM Watson Studio y Google Vertex AI»
    - Pasaje: "Examples of cloud services include Microsoft Azure ML REST API [ε], AWS SageMaker Endpoints [α, β], IBM Watson Studio [γ], and Google Vertex AI prediction service [δ]." (p. 4, §4.2, C8)
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶3 · «mencionan KServing de Kubeflow, TensorFlow Serving y Seldon como marcos de servicio de modelos compatibles con Kubernetes, y describen Kubeflow como una plataforma de aprendizaje automático de extremo a extremo basada en Kubernetes, en la que cada componente se empaqueta en un contenedor»
    - Pasaje: "Other Kubernetes supported frameworks are KServing of Kubeflow [α], TensorFlow Serving, and Seldion.io serving [40]." (p. 4) y "Kubeflow is a Kubernetes-based end-to-end ML platform. Each Kubeflow component is wrapped into a container and orchestrated by Kubernetes." (p. 11, tabla de herramientas)
    - **Estado:** verificada · 2026-09-27

## eken-mlopsmultivocalreview-2026

- **Versión consultada:** `fuentes/pdf/eken-mlopsmultivocalreview-2026.pdf`, preprint de arXiv 2406.09737v2 (2025-04-16), <https://arxiv.org/pdf/2406.09737> (2026-09-13). `references.bib` cita la versión publicada en *ACM Computing Surveys* 58(2), pp. 1–35 (en línea 2025-09-08, número de 2026). La versión publicada está pendiente de descarga manual (ACM DL devolvió HTTP 403 al agente). El resumen publicado se contrastó en Crossref (`api.crossref.org/works/10.1145/3747346`) y la frase citada coincide palabra por palabra.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · «advierten que un cuerpo de conocimiento integrado sobre MLOps sigue sin lograrse, porque su alcance es amplio y abarca desafíos muy diversos de esa transición»
    - Pasaje: "Despite the utility of MLOps, an integrated body of knowledge regarding MLOps remains elusive because of its extensive scope due to the diversity of ML productionalization challenges it addresses." (p. 1, *Abstract*; idéntico en la versión publicada)
    - Es afirmación propia de la revisión, no atribuida a otro estudio.
    - «Esa transición» retoma la primera oración del párrafo (llevar un modelo a producción) y traduce *productionalization*, que la fuente define así: "Productionalization of ML models refers to the process of transitioning ML models from a laboratory setting to a production environment" (p. 1, §1).
    - **Estado:** verificada · 2026-09-13
  - Aviso de atribución para usos futuros: en §5 (desafíos) muchas afirmaciones concretas se apoyan en un solo estudio primario (por ejemplo, el costo de infraestructura en §5.2.1 se atribuye a [PS129]). Citar a Eken et al. por esas afirmaciones exige decir que la revisión las recoge de un estudio, o ir al estudio original.
  - `chapters/06-estado-del-arte.tex` · `\label{sec:estrategia-revision}` ¶2 · «(criterio de selección desde 2015) \citep{eken, muiruri}»
    - Pasaje: ninguno; la revisión no respalda el criterio de este capítulo.
    - **Estado:** uso retirado el 2026-10-04 (revisión del cap. 06 pedida por un autor). La frase conserva el criterio de selección y quedó sin cita. El 2026-09-27 los autores habían decidido conservar la cita (C6-2 no aprobada).
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶1 · «señalan, con base en uno de los estudios que revisan, que las plataformas gestionadas en la nube, como Amazon SageMaker, dan soporte a la preparación de datos, el entrenamiento y el seguimiento de experimentos, el despliegue automatizado sobre infraestructura gestionada y el monitoreo durante todo el ciclo de vida»
    - Pasaje: "Managed cloud-based platforms such as Amazon SageMaker [PS108] and IBM Watson [PS115] provide support for data preparation, model training and experiment tracking, automated deployment on managed infrastructure and monitoring throughout the life cycle." (p. 24, §4.7). Atribuida a estudios primarios, como lo dice la frase.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶2 · «recogen, además, que usar plataformas completamente gestionadas implica perder control *fine-grained* sobre la pila tecnológica, y que sus servicios pueden no cubrir los requisitos especializados de muchas empresas»
    - Pasaje: "using fully managed MLOps platforms means the practitioners would lose fine-grained control over the technology stack and the services supported by the platform may not meet specialized requirements of many businesses [PS108]." (p. 28, §5.3.1)
    - **Estado:** verificada · 2026-10-04. «Organizaciones» pasó a «empresas», como dice la fuente (*many businesses*).
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶3 · «pese a la potencia de herramientas como Kubeflow, el alto costo de infraestructura, la experiencia que exige operar sus canalizaciones y la sobrecarga de instalación y mantenimiento frenan su adopción, en especial en las etapas iniciales de los proyectos y en proyectos impulsados por empresas pequeñas»
    - Pasaje: "While there are many powerful tools such as Kubeflow, FedML, Polyaxon for creating MLOps pipelines, high infrastructure cost, high expertise required for pipelines operation, high setup and maintenance overhead of the pipelines slows down their adoptions [PS129]. This is prevalent especially during the initial stages of ML projects or during ML projects driven by small companies." (p. 27, §5.2.1). Recogida de un estudio primario, como lo dice la frase («recogen»).
    - **Estado:** verificada · 2026-10-04. «Organizaciones pequeñas» pasó a «proyectos impulsados por empresas pequeñas» (*projects driven by small companies*).

## lima-mlopspractices-2022

- **Versión consultada:** `fuentes/pdf/lima-mlopspractices-2022.pdf`, PDF de SciTePress, <https://www.scitepress.org/Papers/2022/109973/109973.pdf> (2026-09-13). Paginación impresa 308–320.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Contexto* ¶1 · **retirada el 2026-09-13.** La tesis citaba la conclusión «there is a significant gap in the detailing of activities related to operationalizing machine learning models» (p. 318 impresa, §6). El pasaje respaldaba la frase, pero los autores la retiraron porque describe el estado del campo en 2022 y puede no seguir vigente en 2026 (`skills/reference-writting/recency.md`, «Claims about the state of a field»). La reemplaza `eken-mlopsmultivocalreview-2026`.
  - Términos que la fuente **no** usa: *quota*, *telemetry*, *governance*.
  - Aviso de atribución: la frase de que el monitoreo es «one of the most relevant activities of MLOps practices» está en la sección de antecedentes (p. 310 impresa) y Lima et al. la atribuyen a Cardoso Silva et al. (2020). No es hallazgo propio de la revisión.
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · **versión anterior retirada el 2026-09-13.** Decía que la fuente ubica «el despliegue, el monitoreo en producción y la gobernanza de acceso» entre las prácticas centrales. La fuente no menciona la gobernanza de acceso, y el monitoreo aparece como afirmación de antecedentes atribuida a otro estudio.
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶1 · «El enfoque surgió para reducir el esfuerzo y mejorar la integración entre quienes llevan los modelos al entorno de producción»
    - Pasaje: "MLOps have emerged as an approach to minimizing efforts and improving integration between those who are in the process of deploying the models in the production environment." (p. 308 impresa, *Abstract*)
    - **Estado:** verificada · 2026-09-13

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
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶2 · «la mayoría de los problemas de baja utilización que estudiaron podía corregirse con pocas modificaciones al código, en una plataforma que obtiene la utilización de cada GPU del gestor DCGM de NVIDIA a través de Prometheus»
    - Pasaje: "Most (84.99%) low-GPU-utilization issues could be fixed with a small number of code/script modifications." (p. 1, *Abstract*); "Platform-X employs Prometheus [61] to monitor system status and gather real-time metrics for each DL job at regular intervals. GPU utilization data is retrieved from the NVIDIA Data Center GPU Manager (DCGM)." (p. 3, §2). Sustituye «causas corregibles identificables a partir de la telemetría», sin respaldo.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶2 · «los problemas de baja utilización de las GPU se originan en la lógica del código de los trabajos, por cómputo insuficiente en la GPU o por interrupciones de tareas ajenas a ella, en una plataforma que obtiene la utilización de cada GPU del gestor DCGM de NVIDIA a través de Prometheus»
    - Pasaje: los pasajes de pp. 2–3 registrados arriba ("attributed to the code logic of scripts and programs"; "insufficient GPU computations […] and interruptions caused by non-GPU tasks"; Prometheus y DCGM). La versión anterior hablaba de «fallas lógicas… detectables mediante el exportador DCGM»; la fuente no menciona el exportador.
    - **Estado:** verificada · 2026-09-27

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
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶2 · «aunque la mayoría de las GPU de un clúster figuren asignadas, esa métrica por sí sola es engañosa, porque las GPU en uso alcanzaban en promedio solo alrededor de la mitad de su utilización»
    - Pasaje: "Even though most GPUs within a cluster are allocated to users, thus suggesting high cluster utilization, this metric alone is misleading. We show that the hardware utilization of GPUs in use is only around 52% on average." (p. 948 impresa, §1). Los autores pidieron no escribir cifras exactas (2026-09-27). Sustituye la versión anterior («visible únicamente cuando se instrumentan las colas»), sin respaldo.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶1 · «analizaron una traza de dos meses de Philly, la plataforma de Microsoft para el entrenamiento de modelos de aprendizaje profundo, que procesó cerca de 100 000 trabajos de cientos de usuarios […] la utilización real del *hardware* en uso alcanzaba únicamente cerca del 52 % en promedio, al tiempo que cerca del 30 % de las tareas se cancelaba o terminaba de forma anómala debido a fallos»
    - Pasaje: los pasajes de pp. 947–948 registrados arriba. La conclusión anterior («demuestra que la reserva estática… induce una subutilización severa») no estaba en la fuente y se reemplazó por una frase de los autores sin cita.
    - **Estado:** verificada · 2026-09-27

## gu-tiresias-2019

- **Versión consultada:** `fuentes/pdf/gu-tiresias-2019.pdf`, versión publicada en las actas de USENIX NSDI 2019 (acceso abierto), <https://www.usenix.org/system/files/nsdi19-gu.pdf> (2026-09-13). Páginas impresas.
- **Retirada del cap. 01 el 2026-09-13** (decisión de los autores). El cambio de escala (clústeres industriales de miles de GPU) rompía el hilo de Antecedentes, y ahí la reemplazan fuentes académicas (`xu-sing-2025`, `weitzel-nrpreservation-2025`). Los pasajes de abajo siguen verificados y quedan como **candidatos para el Estado del arte**, que todavía no se redacta. Los usos del cap. 01 listados abajo ya no están en el texto.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «observaron en un clúster de producción que los planificadores diseñados para el análisis de grandes volúmenes de datos causan largas demoras en cola y un bajo desempeño general con trabajos de entrenamiento de aprendizaje profundo»
    - Pasaje: "Deep learning (DL) training jobs bring some unique challenges to existing cluster managers […] Our analysis of a large GPU cluster in production shows that existing big data schedulers cause long queueing delays and low overall performance." (p. 485, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - Uso anterior **corregido** el 2026-09-13: la tesis concluía, en la misma frase de la cita, que el hallazgo «explica por qué el IAsLab no puede resolver la orquestación de inferencia ni la gobernanza de cuotas». El paper trata el entrenamiento, no la inferencia, y no dice nada sobre el IAsLab.
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «reducen el tiempo de finalización de los trabajos sin conocer de antemano su duración»
    - Pasaje: "Given that a DL job's execution time is often unpredictable, we propose two scheduling algorithms – Discretized Two-Dimensional Gittins index relies on partial information and Discretized Two-Dimensional LAS is information-agnostic – that aim to minimize the average JCT." (p. 485 impresa, *Abstract*)
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶2 · «los planificadores tradicionales concebidos para el procesamiento de grandes volúmenes de datos provocan prolongadas demoras en cola y un bajo desempeño global […]; Tiresias reduce el tiempo de finalización con dos algoritmos bidimensionales, uno basado en el índice de Gittins cuando se dispone de información parcial y otro que no requiere información alguna»
    - Pasaje: los pasajes del *Abstract* (p. 485 impresa) registrados arriba y en el uso del cap. 05
    - **Estado:** verificada · 2026-09-27

## weng-mlaasinthewild-2022

- **Versión consultada:** `fuentes/pdf/weng-mlaasinthewild-2022.pdf`, versión publicada en las actas de USENIX NSDI 2022 (acceso abierto), <https://www.usenix.org/system/files/nsdi22-paper-weng.pdf> (2026-09-13). Páginas impresas.
- **Retirada del cap. 01 el 2026-09-13** (decisión de los autores). El cambio de escala (clústeres industriales de miles de GPU) rompía el hilo de Antecedentes, y ahí la reemplazan fuentes académicas (`xu-sing-2025`, `weitzel-nrpreservation-2025`). Los pasajes de abajo siguen verificados y quedan como **candidatos para el Estado del arte**, que todavía no se redacta. Los usos del cap. 01 listados abajo ya no están en el texto.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶3 · «identifican retos como la baja utilización de las GPU y las largas demoras en cola en un clúster de Alibaba con más de 6 000 GPU»
    - Pasaje: "we present a characterization study of a two-month workload trace collected from a production MLaaS cluster with over 6,000 GPUs in Alibaba. We explain the challenges posed to cluster scheduling, including the low GPU utilization, the long queueing delays, […]" (p. 945, *Abstract*)
    - **Estado:** verificada · 2026-09-13
  - Uso anterior **corregido** el 2026-09-13: la tesis lo agrupaba con Liu et al. para afirmar que «estos estudios confirman que la telemetría *fine-grained* es la condición necesaria». El paper es una caracterización de carga y planificación, no un estudio de telemetría, y no hace esa afirmación.
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶2 · «identifican la baja utilización de las GPU y las largas demoras en cola entre los retos de un clúster de producción con miles de GPU»
    - Pasaje: el mismo pasaje del *Abstract* registrado arriba (p. 945 impresa). Sustituye la versión anterior («patrones sostenidos de subutilización que solo la instrumentación por nodo permite detectar»), sin respaldo.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶2 · «traza de dos meses en un clúster de producción con más de 6 000 GPU heterogéneas en Alibaba, y explicaron los desafíos […] la baja utilización de las GPU, los largos retardos en cola, las tareas difíciles de ubicar por exigir GPU de gama alta, el desbalance de carga entre máquinas heterogéneas y un posible cuello de botella en los procesadores»
    - Pasaje: "a two-month workload trace collected from a production MLaaS cluster with over 6,000 GPUs in Alibaba. We explain the challenges posed to cluster scheduling, including the low GPU utilization, the long queueing delays, the presence of hard-to-schedule tasks demanding high-end GPUs with picky scheduling requirements, the imbalance load across heterogeneous machines, and the potential bottleneck on CPUs." (p. 945 impresa, *Abstract*). La versión anterior decía «baja utilización del procesador» y «fragmentación sustancial de la memoria del acelerador», que no están en la fuente.
    - **Estado:** verificada · 2026-09-27

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
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶2 · «proponen predecirlas con modelos entrenados sobre datos recolectados de GPU en producción, entre ellos la temperatura, el consumo de potencia y la utilización de la GPU y de su memoria»
    - Pasaje: "we propose to predict failures by using ML models" (p. 1, *Abstract*) y la Tabla 1 (p. 3), cuyos datos dinámicos son *temperature*, *power consumption*, *GPU SM utilization* y *GPU mem utilization*, tomados de `nvidia-smi`. Sustituye la versión anterior («un volumen extenso de telemetría… eleva la precisión»), el mismo error ya corregido en el cap. 01.
    - **Estado:** verificada · 2026-09-27
  - `chapters/07-metodologia.tex` · §«Análisis de riesgos y limitaciones», ítem «Saturación de VRAM y congelamiento de nodos GPU» · «muestran que las fallas de GPU bajo cargas de aprendizaje profundo pueden predecirse con modelos entrenados sobre datos recolectados en producción»
    - Pasaje: el título ("Prediction of GPU Failures Under Deep Learning Workloads") y el *Abstract* registrados arriba (p. 1). La versión anterior («este tipo de fallos es predecible con telemetría suficiente») extendía el hallazgo al congelamiento por la fuente de poder, que la fuente no estudia.
    - **Estado:** verificada · 2026-09-27

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
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶3 · «operar estas arquitecturas requiere personal especializado, un recurso escaso en los laboratorios universitarios, que suelen administrar sus clústeres compartidos con personal limitado»
    - Pasaje: "Aimed at addressing the pressing need for efficient resource sharing with limited staffing" (p. 1, *Abstract*) y "many universities do not have the expertise to make the best use of shared GPU clusters" (p. 1, §1). La primera mitad de la frase es de los autores.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶1 · «Un esquema simple y común […] acceso directo por consola […] a través de SSH, y otro, en administrar las máquinas con un planificador de colas como Slurm […] muchas universidades carecen de la experiencia necesaria […] terminan subutilizando recursos ya limitados […] el acceso directo por consola carece de mecanismos de aislamiento y gestión de recursos […]»
    - Pasaje: los pasajes de pp. 1–3 registrados arriba para el cap. 01. Se retiraron «el esquema más extendido», «subutilización marcada», «canales informales» y «conflictos recurrentes», que la fuente no usa.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶2 · «SING, un clúster de aprendizaje automático en campus que gestiona más de 160 GPU para más de 480 usuarios activos, y señalan que compartir estos recursos de forma efectiva es esencial para maximizar tanto su utilización como su accesibilidad»
    - Pasaje: "managing over 160 GPUs and serving over 480 active users" (p. 2, §1) y "Effectively sharing these resources among multiple users is essential for maximizing both utilization and accessibility." (p. 1, *Abstract*). La versión anterior lo presentaba como resultado de la evaluación; en la fuente es una premisa.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶3 · «SING aplica cuotas de recursos por usuario»
    - Pasaje: "while SING enforces user resource quotas" (p. 9)
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶3 · «Slurm […] ofrece encolamiento y planificación de trabajos, y [Xu et al.] señalan que carece de soporte para aprovisionar los entornos de dependencias que exigen los trabajos de aprendizaje automático, que su nodo de acceso puede convertirse en un punto único de falla y que su asignación de recursos de grano grueso puede fragmentarlos»
    - Pasaje: "Slurm provides job queueing and scheduling capabilities in clusters." y "Slurm lacks support for provisioning the complex dependency environments required by ML jobs […] the login node often becomes a single point of failure […] Slurm's coarse-grained resource allocation mechanisms may lead to resource fragmentations and underutilization under certain submission orders and job characteristics" (§2.1.2, *Traditional HPC Solution*, *Analysis*)
    - **Estado:** verificada · 2026-10-04
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶3 · «Kubernetes carece de soporte nativo para el control de acceso por usuario y el encolamiento de trabajos, que exigen herramientas adicionales»
    - Pasaje: "Kubernetes lacks native support for user-level access control and job queuing essential for shared ML clusters, each requiring a separate set of tools and configurations [30] to be added on top of Kubernetes." (§2.1.3, *Container Platforms*, *Analysis*)
    - **Estado:** verificada · 2026-10-04
  - `fuentes/` · tabla comparativa · «Clústeres de campus: monitoreo de utilización de GPU» · Pasaje: "GPU Utilization Monitoring. We closely monitor GPU utilization in SING to identify cases of underutilized resources" (§5). **Estado:** verificada · 2026-10-04

## weitzel-nrpreservation-2025

- **Versión consultada:** `fuentes/pdf/weitzel-nrpreservation-2025.pdf`, preprint de arXiv 2505.22864v1 (2025-05-28), que ya lleva la referencia de PEARC '25 (doi:10.1145/3708035.3736060, añadido a `references.bib` el 2026-09-13), <https://arxiv.org/pdf/2505.22864> (2026-09-13). Páginas del PDF consultado.
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶4 · «un clúster Kubernetes multiusuario que en 2024 atendió a investigadores de 50 campus»
    - Pasajes: "a distributed, multi-tenant Kubernetes-based cyberinfrastructure" (p. 1, *Abstract*); "In calendar year 2024, there were 670 NRP Nautilus Namespaces […] Individual campus researchers (525). These latter 525 Namespaces consumed >3/4 of the GPU-Hrs […] The individual PIs of these 525 researcher Namespaces came from 50 campuses" (p. 2, §1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/01-motivacion-antecedentes.tex` · *Antecedentes* ¶4 · «la introducción de un sistema de reservas para las GPU de mayor demanda elevó la utilización promedio de las GPU del clúster del 21.49 % al 31.37 %, aunque sus operadores reconocen que aún hay margen de mejora»
    - Pasaje: "With the rising demand for high-end GPUs, […] the NRP implemented an allocation system aimed at optimizing GPU utilization. Following the introduction of the reservation system for A100 GPUs, average GPU utilization across the cluster improved significantly from 21.49% to 31.37%. Although there is still room for further enhancement, this marked improvement underscores the effectiveness of the reservation system." (p. 4, §3.1)
    - **Estado:** verificada · 2026-09-13
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶3 · «documentan su introducción para las GPU de mayor demanda de un clúster Kubernetes multiusuario de escala nacional, y reportan una mejora marcada de la utilización promedio de las GPU, que sus operadores presentan como evidencia de la efectividad del sistema de reservas»
    - Pasaje: "With the rising demand for high-end GPUs, […] Following the introduction of the reservation system for A100 GPUs, average GPU utilization across the cluster improved significantly […] this marked improvement underscores the effectiveness of the reservation system." (p. 4, §3.1). La versión anterior («al reducir el tiempo que los recursos pasan ociosos entre usos no coordinados») atribuía un mecanismo que la fuente no describe; se retiró.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶2 · «atiende a investigadores de 50 campus universitarios […] la incorporación de un sistema de reservas sobre las tarjetas de alta gama elevó la utilización promedio de las GPU del 21.49 % al 31.37 %, mejora que sus operadores presentan como evidencia de la efectividad del sistema de reservas»
    - Pasaje: los pasajes de pp. 2 y 4 registrados arriba. Sustituye «confirma experimentalmente que… aventaja a los esquemas de acceso libre», sin respaldo.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶3 · «autentica a sus usuarios con identidad federada y los restringe a los espacios de nombres de sus grupos de investigación»
    - Pasaje: "users log into the NRP portal to download a personalized Kubernetes configuration file containing Kubernetes RBAC-compliant OIDC tokens issued via CILogon federated authentication. Users are restricted to Kubernetes namespaces specific to their research groups" (p. 4)
    - **Estado:** verificada · 2026-09-27

## frantar-gptq-2023

- **Versión consultada:** `fuentes/pdf/frantar-gptq-2023.pdf`, preprint de arXiv 2210.17323v2 (2023-03-22), marcado «Published as a conference paper at ICLR 2023», <https://arxiv.org/pdf/2210.17323> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13** (decisión de los autores): el párrafo sobre cuantización tenía un nivel de detalle de implementación y trataba una capacidad fuera del alcance. La frase decía que reducen un modelo de 175 mil millones de parámetros a 3–4 bits por peso en unas cuatro horas con degradación despreciable. Es fiel a: "GPTQ can quantize GPT models with 175 billion parameters in approximately four GPU hours, reducing the bitwidth down to 3 or 4 bits per weight, with negligible accuracy degradation relative to the uncompressed baseline." (p. 1, *Abstract*)
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶3 · «La técnica reduce la precisión numérica con la que se representan los pesos, con una degradación de calidad acotada y medida experimentalmente»
    - Pasaje: "reducing the bitwidth down to 3 or 4 bits per weight, with negligible accuracy degradation relative to the uncompressed baseline" (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:motores-inferencia}` ¶2 · «La cuantización posentrenamiento […] reduce la precisión numérica de los pesos procurando mantener una pérdida mínima de rendimiento»
    - Pasaje: el pasaje del *Abstract* (p. 1) registrado arriba. La versión anterior lo citaba para GGUF, que la fuente no trata; GPTQ es otro método.
    - **Estado:** verificada · 2026-10-04. «Pérdida acotada» pasó a «procurando mantener una pérdida mínima de rendimiento» (Chen et al.: «while striving to maintain minimal performance loss»). La frase sobre *llama.cpp* que la antecede no lleva cita.

## lin-awq-2024

- **Versión consultada:** `fuentes/pdf/lin-awq-2024.pdf`, versión publicada en las actas de MLSys 2024 (acceso abierto), <https://proceedings.mlsys.org/paper_files/paper/2024/file/42a452cbafa9dd64e9ba4aa95cc1ef21-Paper-Conference.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13** junto con el párrafo de cuantización. La frase decía «reportan una aceleración superior a 3 veces frente a la implementación de referencia» y atribuía la aceleración a AWQ, cuando la fuente se la atribuye a **TinyChat**, el *framework* de inferencia que presentan junto a AWQ: "Alongside AWQ, we implement TinyChat, an efficient and flexible inference framework tailored for on-device LLM/VLMs, offering more than 3× speedup over the Huggingface FP16 implementation on both desktop and mobile GPUs." (p. 1, *Abstract*)
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶3 · «(misma frase que Frantar et al.)»
    - Pasaje: "AWQ, a hardware-friendly approach for LLM low-bit weight-only quantization […] it can well preserve LLMs' generalization ability on different domains and modalities" (p. 1, *Abstract*). No se le atribuye aquí la aceleración de TinyChat.
    - **Estado:** verificada · 2026-09-27

## dettmers-llmint8-2022

- **Versión consultada:** `fuentes/pdf/dettmers-llmint8-2022.pdf`, versión publicada en las actas de NeurIPS 2022 (acceso abierto), <https://proceedings.neurips.cc/paper_files/paper/2022/file/c3ba4962c05c49636d4c6206a97e9c8a-Paper-Conference.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13** junto con el párrafo de cuantización. La frase («LLM.int8() reduce a la mitad la memoria necesaria para la inferencia sin pérdida perceptible de precisión») es fiel a: "We develop a procedure for Int8 matrix multiplication for feed-forward and attention projection layers in transformers, which cut the memory needed for inference by half while retaining full precision performance." (p. 1, *Abstract*)
- **Aviso general para los tres:** la afirmación de la tesis «Esta evidencia respalda que existen modelos precuantizados que caben en la VRAM disponible» no tenía respaldo en ninguno de ellos, porque proponen métodos de cuantización y no hablan de modelos precuantizados de terceros. Salió con el párrafo.
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶3 · «(misma frase que Frantar et al.)»
    - Pasaje: "which cut the memory needed for inference by half while retaining full precision performance" (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-27

## wiest-privacypreservingllm-2024

- **Versión consultada:** `fuentes/pdf/wiest-privacypreservingllm-2024.pdf`, versión publicada en *npj Digital Medicine* 7, 257 (acceso abierto), <https://www.nature.com/articles/s41746-024-01233-2.pdf> (2026-09-13).
- **Usos:**
  - `chapters/01-motivacion-antecedentes.tex` · *Justificación* · **retirada el 2026-09-13**: los autores decidieron omitir el impacto en el manejo de datos. Pasajes verificados por si se retoma: "these LLMs run as cloud services and using them requires the transfer of privileged information to remote servers. This brings along immense legal and ethical challenges, especially in the European Union (EU), where the export of personal health data is not legally permitted. Ideally, LLMs should run on-premise of healthcare institutions" y "Quantized models have lower numerical precision of the model parameters and have lower graphics processing unit (GPU) memory consumption than unquantized models, allowing for easier integration with existing hospital hardware." (p. 2). La tesis decía «riesgos»; la fuente dice *challenges*.

## mahajan-themis-2020

- **Versión consultada:** `fuentes/pdf/mahajan-themis-2020.pdf`, actas de USENIX NSDI 2020.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «incorporan la equidad entre trabajos o usuarios, con una noción de equidad en el tiempo de finalización»
    - Pasaje: "Its GPU allocation policy enforces that ML workloads complete in a finish-time fair manner, a new notion we introduce." (p. 2, *Abstract*). PDF: `fuentes/pdf/mahajan-themis-2020.pdf`, actas de USENIX NSDI 2020.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶2 · «Themis, un esquema de subastas que busca asegurar a largo plazo la equidad en el tiempo de finalización de las cargas de aprendizaje automático»
    - Pasaje: "Our auction design allocates GPUs to winning bids by trading off fairness for efficiency in the short term, but ensuring finish-time fairness in the long term." (p. 2, *Abstract*; la p. 1 del PDF es la portada de USENIX)
    - **Estado:** verificada · 2026-10-04. Redactada de nuevo con los términos del pasaje (*auction*, *finish-time fairness*, *long term*).

## narayanan-gavel-2020

- **Versión consultada:** `fuentes/pdf/narayanan-gavel-2020.pdf`, actas de USENIX OSDI 2020.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «(equidad) con políticas adaptadas a aceleradores heterogéneos»
    - Pasaje: "Gavel expresses these policies as optimization problems and then systematically transforms these problems into heterogeneity-aware versions" (p. 2) y "heterogeneity-aware versions of fair sharing / least attained service" (p. 3). Gavel también admite políticas jerárquicas ("hierarchical policies that divide resources among high-level entities", p. 3), por eso ya no se agrupa con un supuesto de «mismo derecho». PDF: `fuentes/pdf/narayanan-gavel-2020.pdf`, actas de USENIX OSDI 2020.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:clusteres-industriales}` ¶2 · «Gavel, un planificador consciente de la heterogeneidad de los aceleradores que generaliza distintas políticas de planificación al expresarlas como problemas de optimización»
    - Pasaje: "we proposed Gavel, a heterogeneity-aware cluster scheduler that is able to optimize for many high-level" metrics (conclusión, p. 15). La cita que figuraba antes («Gavel is a heterogeneity-aware cluster scheduler») no es literal.
    - Pasaje añadido el 2026-10-04: "we propose Gavel, a heterogeneity-aware scheduler that systematically generalizes a wide range of existing scheduling policies. Gavel expresses these policies as optimization problems" (p. 1, *Abstract*).
    - **Estado:** verificada · 2026-10-04. Se retiró «optimiza políticas de reparto global», que la fuente no dice.

## kwon-pagedattention-2023

- **Versión consultada:** `fuentes/pdf/kwon-pagedattention-2023.pdf`, preprint de arXiv 2309.06180 (versión de SOSP '23). Páginas del PDF.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶2 · «la caché de atención crece con la longitud de cada petición y […] fragmenta la memoria del acelerador hasta desperdiciar una fracción sustancial de la capacidad instalada; resuelven esa fragmentación paginando la caché en bloques de tamaño fijo, con una analogía directa a la memoria virtual»
    - Pasaje: "the key-value cache (KV cache) memory for each request is huge and grows and shrinks dynamically. When managed inefficiently, this memory can be significantly wasted by fragmentation and redundant duplication, limiting the batch size. To address this problem, we propose PagedAttention, an attention algorithm inspired by the classical virtual memory and paging techniques in operating systems" (p. 1, *Abstract*). **Matiz:** la fuente habla de la memoria de la caché KV, no de «la capacidad instalada»; los autores decidieron conservar la redacción (C5-3 no aprobada, 2026-09-27). PDF: preprint arXiv 2309.06180.
    - **Estado:** verificada con matiz · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶4 · **uso anterior retirado el 2026-09-27**: atribuía a Kwon et al. que vLLM «paga ese *throughput* con mayor latencia», cuando la fuente reporta "throughput […] by 2-4× with the same level of latency" (p. 1).
  - `chapters/06-estado-del-arte.tex` · `\label{sec:motores-inferencia}` ¶1 · «PagedAttention, que gestiona el almacén de claves y valores (KV *cache*) mediante principios análogos a la paginación de memoria virtual en sistemas operativos, con lo cual alivia la fragmentación interna, elimina la externa y logra un desperdicio casi nulo de la memoria de la caché»
    - Pasaje: "PagedAttention, an attention algorithm inspired by the classical virtual memory and paging techniques in operating systems. On top of it, we build vLLM, an LLM serving system that achieves (1) near-zero waste in KV cache memory" (p. 1, *Abstract*); "This design alleviates internal fragmentation by using relatively small blocks and allocating them on demand. Moreover, it eliminates external fragmentation as all blocks have the same size." (p. 2)
    - **Estado:** verificada · 2026-10-04. La versión anterior decía que eliminaba «casi en su totalidad la fragmentación interna y externa». La fuente dice que alivia la interna y elimina la externa, y el «casi nulo» se refiere al desperdicio de la caché KV.

## yu-orca-2022

- **Versión consultada:** `fuentes/pdf/yu-orca-2022.pdf`, actas de USENIX OSDI 2022.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶2 · «planificar a nivel de iteración, en lugar de esperar a que el lote completo termine, eleva de forma sustancial el *throughput* agregado del servidor»
    - Pasaje: "In this paper, we propose iteration-level scheduling […] 36.9× throughput improvement at the same level of latency" (p. 2, *Abstract*). PDF: `fuentes/pdf/yu-orca-2022.pdf`, actas de USENIX OSDI 2022.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:motores-inferencia}` ¶1 · «planificación a nivel de iteración (*iteration-level scheduling*)»
    - Pasaje: "In this paper, we propose iteration-level scheduling, a new scheduling mechanism that schedules execution at the granularity of iteration" (p. 2, *Abstract*)
    - **Estado:** verificada · 2026-09-27

## miao-llmservingsurvey-2025

- **Versión consultada:** `fuentes/pdf/miao-llmservingsurvey-2025.pdf`, preprint de arXiv 2312.15234v4 (enviado a *ACM Computing Surveys*; `references.bib` cita la versión publicada). Páginas del PDF.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶1 · «la baja latencia y el alto *throughput* son objetivos complementarios pero a menudo en conflicto»
    - Pasaje: "Basically, low latency and high throughput are dual optimization targets in LLM serving systems, representing complementary but often conflicting objectives" (p. 17, §6)
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶2 · «organizan estas técnicas, junto con la compresión de modelos y la programación de *kernels*, como un espectro continuo de optimización que abarca desde el algoritmo hasta el sistema»
    - Pasaje: "covering a spectrum of solutions, ranging from cutting-edge algorithmic modifications to groundbreaking changes in system designs" (p. 1, *Abstract*) y la taxonomía que incluye "model compression, low-bit quantization, […] and kernel optimization" (p. 2). **Matiz:** «continuo» no está en la fuente; los autores decidieron conservar la redacción (C5-3 no aprobada, 2026-09-27).
    - **Estado:** verificada con matiz · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶4 · «las decisiones de diseño de cada sistema de servicio responden en gran medida a su objetivo de optimización prioritario, y vLLM, por ejemplo, usa la atención paginada para aumentar el tamaño del lote y, con él, el *throughput*»
    - Pasaje: "these different choices of design and implementation are largely determined by their prioritized optimization target. For example, vLLM proposes paged attention to improve the batch size for higher throughput" (p. 17, §6). PDF: preprint arXiv 2312.15234v4, enviado a *ACM Computing Surveys*.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:motores-inferencia}` ¶1 · «procesamiento de lotes continuo combinado con planificación a nivel de iteración»
    - Pasaje: "Plenty of following approaches inherit the selective-batching and iteration-level scheduling policy, such as continuous batching in vLLM and RayLLM" (p. 14)
    - **Estado:** verificada · 2026-09-27

## montesi-apigatewaypatterns-2016

- **Versión consultada:** `fuentes/pdf/montesi-apigatewaypatterns-2016.pdf`, preprint de arXiv 1609.05830.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:identidad-rbac}` ¶2 · «un punto único de entrada que da acceso a varias interfaces y al que resulta natural añadir funciones de descubrimiento de servicios, balanceo de carga, monitoreo y seguridad»
    - Pasaje: "It is a single entry point that provides access to many APIs […] Since an API Gateway is an entry point for the MSA, it is natural to equip it with, e.g., service discovery, load balancing, monitoring, and security." (p. 6, §4). La versión anterior le atribuía «límite de tasa» y «registra el consumo», que la fuente no menciona. PDF: `fuentes/pdf/montesi-apigatewaypatterns-2016.pdf`, preprint arXiv 1609.05830.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:pasarelas-inferencia}` ¶1 · «Este enfoque se sustenta en patrones reconocidos de microservicios»
    - Pasaje: "We review some of the most widely used patterns for the programming of microservices: circuit breaker, service discovery, and API gateway." (p. 1, *Abstract*) y la definición del *API gateway* como "single entry point that provides access to many APIs" (p. 6). La fuente no trata pasarelas para modelos de lenguaje; se cita solo por el patrón.
    - **Estado:** verificada · 2026-09-27

## muiruri-mlinferenceserving-2026

- **Versión consultada:** `fuentes/pdf/muiruri-mlinferenceserving-2026.pdf`, versión publicada en *Software: Practice and Experience* (acceso abierto), descargada por los autores el 2026-09-27.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶2 y `\label{sec:despliegue-inferencia}` ¶1 · **usos retirados el 2026-09-27**. Se le atribuían los objetivos de cada fase (*throughput*, tiempo hasta converger, latencia, estabilidad bajo carga variable) y ser «el punto donde se concentran las decisiones de rendimiento». El PDF (versión publicada, acceso abierto, descargado por los autores) es un estudio multicaso de ocho sistemas y solo respalda la distinción básica: "The two distinct phases of the ML workflow-training and inference-focus on conducting different experiments offline to build an ML model and querying the trained ML model for prediction, respectively." (p. 2, §2). Los reemplazan `gao-dlschedulingtaxonomy-2022` y `miao-llmservingsurvey-2025`.
  - `chapters/06-estado-del-arte.tex` · `\label{sec:estrategia-revision}` ¶2 · «publicadas a partir del año 2015, \citep{eken, muiruri} [retirado]»
    - Pasaje: ninguno. Es un estudio multicaso de ocho sistemas de aprendizaje automático sobre prácticas de despliegue; no trata criterios de selección de literatura.
    - **Estado:** uso retirado el 2026-10-04 (revisión del cap. 06 pedida por un autor), con la misma salvedad que Eken et al.
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶3 y tabla comparativa · **usos retirados el 2026-09-27**. Se le atribuía que «Kubeflow y TensorFlow Serving representan las alternativas más citadas»; la fuente no menciona Kubeflow. Los reemplazan `kreuzberger-mlopsoverview-2023` y `eken-mlopsmultivocalreview-2026`.

## chen-llmquantizationsurvey-2026

- **Versión consultada:** `fuentes/pdf/chen-llmquantizationsurvey-2026.pdf`, versión publicada en *Journal of Computer Science and Technology* 41(1), pp. 341–358, descargada por los autores. **Autores en `references.bib` incorrectos** (el PDF dice Yi-Dong Chen, Kai-Jun Zheng, Zhen-Hua Guo, Qi-Hao Zhang, Yong-Hua Zhang y Ji-Dong Zhai); pendiente del paso de bibliografía.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶3 · «La técnica reduce la precisión numérica con la que se representan los pesos, con una degradación de calidad acotada»
    - Pasaje: "Model quantization, as an effective model compression technique, significantly reduces LLMs' memory footprint and computational requirements by lowering the numerical precision of model parameters and/or activations, while striving to maintain minimal performance loss." (p. 1, *Abstract*). PDF: versión publicada en *Journal of Computer Science and Technology* 41(1), descargada por los autores. **Autores en `references.bib` incorrectos** (el PDF dice Yi-Dong Chen, Kai-Jun Zheng, Zhen-Hua Guo, Qi-Hao Zhang, Yong-Hua Zhang y Ji-Dong Zhai); pendiente de corregir en el paso de bibliografía.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:motores-inferencia}` ¶2 · «La cuantización posentrenamiento […] reduce la precisión numérica de los pesos procurando mantener una pérdida mínima de rendimiento»
    - Pasaje: el mismo pasaje del *Abstract* registrado para el cap. 05 (p. 1). La fuente no menciona GGUF ni *llama.cpp*; la versión anterior la citaba para GGUF y se corrigió.
    - **Estado:** verificada · 2026-10-04. «Pérdida acotada» pasó a «procurando mantener una pérdida mínima de rendimiento» (Chen et al.: «while striving to maintain minimal performance loss»). La frase sobre *llama.cpp* que la antecede no lleva cita.

## gao-dlschedulingtaxonomy-2022

- **Versión consultada:** `fuentes/pdf/gao-dlschedulingtaxonomy-2022.pdf`, preprint de arXiv 2205.11913v3 (2022-06-01). Publicado después en *ACM Computing Surveys* (2024) con otro título; `references.bib` cita el preprint. Páginas del PDF.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:mlops-ciclo-vida}` ¶2 · «describen el entrenamiento como cargas de larga duración que se ejecutan fuera de línea, para las que el planificador busca un buen desempeño de cada trabajo, una alta utilización del centro de datos y equidad entre usuarios, y la inferencia como un servicio en línea que atiende las solicitudes de los usuarios, con exigencias mayores de latencia y con peticiones en ráfagas difíciles de predecir. Por esa diferencia, los autores estudian por separado los planificadores de cada fase»
    - Pasaje: "for model training, the scheduler allocates resources requested by the users to support the long-running offline training workloads. The scheduler needs to achieve high performance for each individual workload, high resource utilization for the entire datacenter, and high fairness among different users" (p. 1); "For model inference, DL applications often serve as online services to answer users' requests. They often have a higher expectation on the response latency" (p. 2); "it is common for the inference application to receive bursty and fluctuating requests, which are unpredictable" (p. 8, C7); "The schedulers for model training and model inference share similar logic flows but have totally different scheduling objectives […] So our survey will investigate them separately" (p. 6, §2.2)
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:despliegue-inferencia}` ¶1 · «ubicar varias cargas de inferencia en un mismo equipo o aumentar el tamaño del lote mejora la utilización y el *throughput*, pero puede elevar la latencia»
    - Pasaje: "To improve the resource utilization and cluster-wide job throughput, we can colocate multiple inference jobs or increase the batch size. However, this can increase the inference latency." (p. 8)
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:crd-operadores}` ¶3 · «describen ese requisito en el entrenamiento distribuido, cuyos trabajos necesitan todas sus GPU asignadas a la vez, en la modalidad de todo o nada conocida como *gang scheduling*»
    - Pasaje: "gang scheduling is that DL training requires all the GPUs to be allocated simultaneously in an all-or-nothing manner" (p. 5, T6). Sustituye «sitúan ese mecanismo entre las políticas de admisión y expropiación», sin respaldo.
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «agrupan los objetivos de estos planificadores en eficiencia, equidad y cumplimiento de plazos»
    - Pasaje: "Different schedulers are designed to achieve different objectives, including efficiency, fairness and deadline guarantee." (p. 9, §3.1). Sustituye la afirmación de que la taxonomía trata «ambas familias por separado porque persiguen objetivos incompatibles», sin respaldo.
    - **Estado:** verificada · 2026-09-27

## carrion-k8sbibliometric-2022

- **Versión consultada:** `fuentes/pdf/carrion-k8sbibliometric-2022.pdf`, versión publicada en *Journal of Grid Computing* 20:42, descargada por los autores (2026-09-27).
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:orquestacion-contenedores}` ¶1 · «lo describe como el estándar de la orquestación de contenedores y ubica la programación de recursos, los microservicios y la inteligencia artificial entre sus temas de investigación más activos»
    - Pasaje: "Nowadays, Kubernetes is a leading open-source container orchestration platform that has become the de facto standard." y "The hottest research topics on Kubernetes are mainly centered on \"cloud/fog/edge computing and Internet of Things (IoT)\", \"containers and virtualization\", \"docker\", \"resource scheduling\", \"microservices\" and \"artificial intelligent (AI)\"" (p. 1, *Abstract*). Los autores pidieron escribir «estándar» sin «de facto» (2026-09-27). La versión anterior decía «el cómputo distribuido», que no está en la lista.
    - **Estado:** verificada · 2026-09-27

## shamim-k8smultivocal-2022

- **Versión consultada:** `fuentes/pdf/shamim-k8smultivocal-2022.pdf`, preprint de arXiv 2211.07032 (manuscrito para *Empirical Software Engineering*), igual que cita `references.bib`.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:orquestacion-contenedores}` ¶1 · «una revisión multivocal documenta, junto a los beneficios que los profesionales reportan, la falta de herramientas de diagnóstico, es decir, de monitoreo y registro, entre los retos que enfrentan»
    - Pasaje: "We find 8 benefits […] Our identified 15 challenges related to Kubernetes include unavailability of diagnostics and security tools" (p. 1, *Abstract*); "Lack of Diagnostics Tools (121): This category describes the lack of diagnostics tools, i.e., monitoring and logging tools for Kubernetes" (p. 25)
    - **Estado:** verificada · 2026-09-27

## xu-k8soperatorbugs-2024

- **Versión consultada:** `fuentes/pdf/xu-k8soperatorbugs-2024.pdf`, versión publicada en las actas de ISSTA '24 (CC BY 4.0), pp. 1746–1758.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:crd-operadores}` ¶2 · «estudiaron 210 defectos recolectados de 36 operadores de uso extendido y encontraron que la mayoría se origina en una observación o un análisis incorrecto de los cambios de estado, y otra parte importante en la propia reconciliación»
    - Pasaje: "we conduct the first comprehensive study on 210 operator bugs from 36 Kubernetes operators" (p. 1); "incorrect state observation and analysis (60%), and incorrect reconciliation (27%)" (p. 2, §1). Los autores pidieron no escribir los porcentajes (2026-09-27).
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:crd-operadores}` · figura `fig:bucle-reconciliacion`, adaptada de la Figura 1 (p. 1, «Control loop»: *Observe*, *Analyze changes*, *Reconcile*).

## burns-borgomegak8s-2016

- **Versión consultada:** `fuentes/pdf/burns-borgomegak8s-2016.pdf`, versión de *ACM Queue* 14(1) publicada en acceso abierto por Google Research. Páginas del PDF (24).
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:crd-operadores}` ¶1 · «el usuario declara el estado que desea que el clúster tenga, y un controlador ejecuta de forma permanente un bucle de reconciliación que compara ese estado con el observado y actúa hasta hacerlos converger. Como toda acción se decide a partir de la observación del estado presente, sin depender de una máquina de estados […], un controlador que falla y se reinicia retoma el trabajo desde lo que encuentra»
    - Pasaje: "it compares a desired state […] against the observed state […], and takes actions to converge the observed and desired states." (p. 13) y "Because all action is based on observation rather than a state diagram, reconciliation loops are robust to failures and perturbations: when a controller fails or restarts it simply picks up where it left off." (p. 14)
    - **Estado:** verificada · 2026-09-27

## moritz-ray-2018

- **Versión consultada:** `fuentes/pdf/moritz-ray-2018.pdf`, actas de USENIX OSDI 2018.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:crd-operadores}` ¶3 · «el *framework* de cómputo distribuido que describen a partir de tareas asíncronas y actores con estado»
    - Pasaje: "a unified interface that can express both task-parallel and actor-based computations" (p. 2) y "stateless computations […] In contrast stateful computations are a good fit" (pp. 3–4); la Tabla 4 describe el modelo de programación de Ray como "Ray, asynchronous tasks" (p. 12)
    - **Estado:** verificada · 2026-09-27

## xiao-gandiva-2018

- **Versión consultada:** `fuentes/pdf/xiao-gandiva-2018.pdf`, actas de USENIX OSDI 2018.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «aprovechan la regularidad de las iteraciones del entrenamiento para repartir las GPU por turnos entre varios trabajos, migrarlos y agruparlos»
    - Pasaje: "Gandiva exploits intra-job predictability to time-slice GPUs efficiently across multiple jobs […] This predictability is also used for introspecting job performance and dynamically migrating jobs" (p. 2, *Abstract*); "it packs multiple jobs on the same GPU only when they have low memory and GPU utilization; it dynamically migrates a communication intensive job to more affinitized GPUs" (p. 3)
    - **Estado:** verificada · 2026-09-27

## qiao-pollux-2021

- **Versión consultada:** `fuentes/pdf/qiao-pollux-2021.pdf`, actas de USENIX OSDI 2021.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶1 · «(equidad) con un ajuste conjunto de los recursos y de los parámetros de cada entrenamiento»
    - Pasaje: "Pollux improves scheduling performance in deep learning (DL) clusters by adaptively co-optimizing inter-dependent factors both at the per-job level and at the cluster-wide level." y "Pollux promotes fairness among DL jobs competing for resources" (p. 2, *Abstract*); "The amount of resources, batch size, and learning rate are" los factores que co-optimiza por trabajo (p. 2)
    - **Estado:** verificada · 2026-09-27

## verma-borg-2015

- **Versión consultada:** `fuentes/pdf/verma-borg-2015.pdf`, versión de Google Research del artículo de EuroSys '15.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶2 · «Cada trabajo tiene una prioridad, una tarea de prioridad alta puede obtener recursos a costa de una de prioridad menor aunque eso implique expropiarla, y la cuota decide qué trabajos se admiten para su planificación»
    - Pasaje: "Every job has a priority, a small positive integer. A high-priority task can obtain resources at the expense of a lower-priority one, even if that involves preempting (killing) the latter." y "Quota is used to decide which jobs to admit for scheduling. […] Quota-checking is part of admission control, not scheduling" (p. 3, §2.5). La versión anterior la ponía como base de la familia que supone «el mismo derecho», contradicho por este pasaje.
    - **Estado:** verificada · 2026-09-27

## george-hpcgpuclassroom-2020

- **Versión consultada:** `fuentes/pdf/george-hpcgpuclassroom-2020.pdf`, preprint de arXiv 2005.07598v1. **Es un informe de un solo autor, sin revisión por pares**; su permanencia la deciden los autores.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶2 · «describe un clúster universitario con pocas GPU que atiende a decenas de estudiantes y profesores, en el que se limita cuántos trabajos puede enviar y ejecutar cada estudiante y se da a los profesores una prioridad algo mayor que a los estudiantes»
    - Pasaje: "we required a system which uses a limited number of GPUs (6) to serve dozens of students and faculty" (p. 2); "we set limits for students as to how many jobs they can submit, how many concurrent jobs they can run at once, and how long their jobs can run […] we give faculty a slightly higher priority than students for running jobs" (p. 4)
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶4 · «el uso simultáneo de los equipos durante las clases o en las horas de mayor demanda»
    - Pasaje: "students will often use the system simultaneously during classes or peak hours" (p. 2). Sustituye la versión anterior («población estudiantil rotativa… antes que en maximizar el retorno económico»), sin respaldo.
    - **Estado:** verificada · 2026-09-27
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶3 · «el clúster que describe limita los trabajos de cada estudiante y da a los profesores una prioridad algo mayor»
    - Pasaje: el pasaje de p. 4 registrado arriba
    - **Estado:** verificada · 2026-09-27

## cohen-cloudovercommit-2019

- **Versión consultada:** `fuentes/pdf/cohen-cloudovercommit-2019.pdf`, versión de autor con la maquetación de *Management Science* 65(7), pp. 3255–3271.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶3 · «el problema se ha formalizado como un empaquetado bajo restricciones probabilísticas»
    - Pasaje: "It is often observed that the requested capacities are not fully utilized, hence offering an opportunity to employ an overcommitment policy […] We introduce and study a model that quantifies the value of overcommitment by modeling the problem as bin packing with chance constraints." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-27

## bashir-peakovercommit-2021

- **Versión consultada:** `fuentes/pdf/bashir-peakovercommit-2021.pdf`, versión de autor del artículo de EuroSys '21.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶3 · «desplegado a escala de producción en múltiples centros de datos»
    - Pasaje: "We also deploy these policies to machines inside Google's datacenters serving its internal production workload." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-27

## cortez-resourcecentral-2017

- **Versión consultada:** `fuentes/pdf/cortez-resourcecentral-2017.pdf`, versión de Microsoft Research del artículo de SOSP '17.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:gobernanza-recursos-compartidos}` ¶3 · «muestran, en las máquinas virtuales de Microsoft Azure, que ciertos comportamientos de una carga se mantienen consistentes a lo largo de su vida, de modo que su historia predice su comportamiento futuro, y usan esas predicciones para sobresuscribir servidores sin degradar el desempeño»
    - Pasaje: "We then show that certain VM behaviors are fairly consistent over multiple lifetimes, i.e. history is an accurate predictor of future behavior. […] we modify Azure's VM scheduler to leverage predictions in oversubscribing servers […] while retaining high VM performance." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-27

## li-rbaccloudsurvey-2015

- **Versión consultada:** `fuentes/pdf/li-rbaccloudsurvey-2015.pdf`, capítulo publicado en W. E. Wong (ed.), *Proceedings of the 4th International Conference on Computer Engineering and Networks* (Springer, 2015), descargado por los autores. **Autores en `references.bib` incorrectos** (el PDF dice Hongjiao Li, Shan Wang, Xiuxia Tian, Weimin Wei y Chaochao Sun); pendiente de corregir en el paso de bibliografía.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:identidad-rbac}` ¶1 · «En entornos de cómputo en la nube, el control de acceso basado en roles resulta más escalable y adecuado que los modelos discrecional y obligatorio, y admite extensiones que incorporan a la decisión los atributos del solicitante y su grado de confianza»
    - Pasaje: "When it comes to being used in cloud computing environments, RBAC is more scalable and more suitable compared with traditional discretionary and mandatory access control models. […] several extended role-based access control schemes are surveyed from basic extension, A-RBAC, and trust-based RBAC" (p. 1, *Abstract*). Sustituye «sigue siendo el modelo de referencia», afirmación sobre el estado del campo que la fuente no hace.
    - **Estado:** verificada · 2026-09-27

## fett-oauth2security-2016

- **Versión consultada:** `fuentes/pdf/fett-oauth2security-2016.pdf`, versión extendida de arXiv 1601.01229v4; la de CCS '16 es una versión abreviada.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:identidad-rbac}` ¶1 · «establecen mediante análisis formal las garantías de autorización, autenticación e integridad de sesión que ofrece OAuth 2.0 bajo ese esquema, una vez corregidas las vulnerabilidades que su propio análisis descubrió»
    - Pasaje: "When proving the security of OAuth in our model, we discovered four attacks which break the security of OAuth. […] we show that the fixed version of OAuth (with security recommendations and best practices in place) provides the authorization, authentication, and session integrity properties we specify." (p. 1, *Abstract*)
    - **Estado:** verificada · 2026-09-27

## li-observabilitysurvey-2021

- **Versión consultada:** `fuentes/pdf/li-observabilitysurvey-2021.xml`, texto completo de la versión publicada en *Empirical Software Engineering* 27(1):25, obtenido de Europe PMC (PMC8629732). Sin paginación; se cita la sección.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶1 · «En los sistemas de microservicios, que suelen desplegarse sobre entornos de nube complejos, asegurar la observabilidad es esencial para entender su comportamiento y diagnosticar sus problemas»
    - Pasaje: "Microservice systems are often deployed in complex cloud-based environments […] It is thus essential to ensure observability to understand these microservice systems' behaviors and troubleshoot their problems." (*Abstract*)
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶1 · «tres señales complementarias, cada una con un propósito propio, que son los registros, las trazas y las métricas (Sridharan, 2018, como se citó en Li et al.)»
    - Pasaje: "Logs, traces, and metrics are often known as the three pillars of observability and serve their own unique purpose and are complementary (Sridharan 2018)." (sección *Distributed Tracing*). Cita de segunda mano, marcada como tal en el texto.
    - **Estado:** verificada · 2026-09-27
  - `chapters/05-marco-teorico.tex` · `\label{sec:observabilidad-telemetria}` ¶1 · «los registros incluyen los de la aplicación y los del sistema, las trazas siguen el recorrido de cada solicitud entre los servicios que la atienden y las métricas abarcan las del sistema, como el consumo de procesador y de memoria, y las de la aplicación, como la latencia y la tasa de errores»
    - Pasaje: "For a microservice system, the logs include application logs, system logs, and also span logs; the traces are produced by the distributed tracing system […] the metrics include both system metrics (e.g., CPU/memory consumption rate) and application metrics (e.g., latency and error rate of service invocations)." (sección *Distributed Tracing*) y "tracing requests as they flow between services" (*Introduction*). La versión anterior definía la observabilidad «a partir de lo que puede medirse desde afuera», que la fuente no dice.
    - **Estado:** verificada · 2026-09-27

## jiang-loadtestingsurvey-2015

- **Versión consultada:** `fuentes/pdf/jiang-loadtestingsurvey-2015.pdf`, versión de autor con la maquetación de *IEEE Transactions on Software Engineering* 41(11), pp. 1091–1118.
- **Usos:**
  - `chapters/05-marco-teorico.tex` · `\label{sec:marco-conceptual}` ¶2 · «pruebas de carga cuyo diseño, ejecución y análisis siguen la sistematización que elaboran sobre la literatura de pruebas de carga en sistemas de gran escala»
    - Pasaje: "we survey the state of load testing research and practice. We compare and contrast current techniques that are used in the three phases of a load test: (1) designing a proper load, (2) executing a load test, and (3) analyzing the results of a load test." (p. 1091 impresa, *Abstract*)
    - **Estado:** verificada · 2026-09-27
  - `chapters/07-metodologia.tex` · `\label{sec:estrategia-metodologica}` ¶5 · **uso retirado el 2026-09-27** al condensar el párrafo por pedido de los autores. La fuente sigue citada en el cap. 05 §5.8.

## schwaber-scrumguide-2020

- **Versión consultada:** `fuentes/pdf/schwaber-scrumguide-2020.pdf`, versión oficial de noviembre de 2020 publicada en scrumguides.org. Páginas del PDF.
- **Usos:**
  - `chapters/07-metodologia.tex` · `\label{sec:estrategia-metodologica}` ¶1 · «proceso de desarrollo iterativo e incremental de tipo Scrum, siguiendo la *Scrum Guide* […], organizado en *sprints* de tres semanas»
    - Pasaje: "Scrum employs an iterative, incremental approach to optimize predictability and to control risk." (p. 4) y "They are fixed length events of one month or less to create consistency." (p. 8, *The Sprint*). **Matiz:** la guía también dice "The Scrum framework, as outlined herein, is immutable. While implementing only parts of Scrum is possible, the result is not Scrum." (p. 14), y el capítulo reconoce que el equipo no practica el *daily scrum* ni las retrospectivas. Los autores decidieron conservar la redacción (C7-1 no aprobada, 2026-09-27).
    - **Estado:** verificada con matiz · 2026-09-27

## litellm-overview-2026

- **Versión consultada:** `fuentes/pdf/litellm-overview-2026.html`, página *Getting Started* de la documentación oficial (<https://docs.litellm.ai/docs/>), descargada el 2026-10-04. Es documentación técnica, no producción arbitrada.
- **Usos:**
  - `chapters/06-estado-del-arte.tex` · `\label{sec:pasarelas-inferencia}` ¶2 · «biblioteca de código abierto que ofrece una interfaz unificada para invocar más de cien modelos de lenguaje con el formato de OpenAI, con lógica de reintentos y de respaldo entre varios despliegues, y […] una pasarela autoalojada con llaves virtuales, seguimiento de costos y presupuestos por llave, equipo o usuario»
    - Pasaje: "LiteLLM is an open-source library that gives you a single, unified interface to call 100+ LLMs (OpenAI, Anthropic, Vertex AI, Bedrock, and more) using the OpenAI format."; "Built-in retry / fallback logic across multiple deployments via the Router"; "Self-hosted LLM Gateway (Proxy) with virtual keys, cost tracking, and an admin UI"; "Virtual keys with per-key/team/user budgets"
    - **Estado:** verificada · 2026-10-04
  - `chapters/06-estado-del-arte.tex` · tabla comparativa y `\label{sec:pasarelas-inferencia}` ¶3 · «sin describir el despliegue ni la gestión de las instancias que los sirven» · **lectura de los autores**: es una ausencia en la documentación, no una afirmación de la fuente, y el texto la declara así.
    - **Estado:** lectura propia, sin cita de la ausencia · 2026-10-04

## litellm-proxyusers-2026

- **Versión consultada:** `fuentes/pdf/litellm-proxyusers-2026.html`, página *Budgets, Rate Limits* (<https://docs.litellm.ai/docs/proxy/users>), descargada el 2026-10-04.
- **Usos:**
  - `chapters/06-estado-del-arte.tex` · `\label{sec:pasarelas-inferencia}` ¶2 · «límites de tokens por minuto, de peticiones por minuto y de peticiones en paralelo por llave o equipo»
    - Pasaje: "You can set: tpm limits (tokens per minute) rpm limits (requests per minute) max parallel requests rpm / tpm limits per model for a given key or team"
    - **Estado:** verificada · 2026-10-04

## kubeflow-profiles-2026

- **Versión consultada:** `fuentes/pdf/kubeflow-profiles-2026.html`, página *Profiles and Namespaces* de la documentación oficial (<https://www.kubeflow.org/docs/components/central-dash/profiles/>), descargada el 2026-10-04.
- **Usos:**
  - `chapters/06-estado-del-arte.tex` · `\label{sec:ecosistemas-mlops}` ¶3 · «perfiles que envuelven un espacio de nombres de Kubernetes, con un propietario y colaboradores de solo lectura o de edición, y permite crear opcionalmente una cuota de recursos para cada perfil»
    - Pasaje: "A Kubeflow Profile is a Kubernetes CRD introduced by Kubeflow that wraps a Kubernetes Namespace. Profiles are owned by a single user, and can have multiple contributors with view or modify access."; "optionally create a ResourceQuota for the profile" (manifiesto de ejemplo, campo `resourceQuotaSpec`)
    - **Estado:** verificada · 2026-10-04
  - mismo lugar · «Su documentación no describe niveles de prioridad por rol ni reservas de cupos» · **lectura de los autores** sobre esa página; no se revisó el resto de la documentación de Kubeflow.
    - **Estado:** lectura propia, alcance limitado a esta página · 2026-10-04

## slurm-overview-2026

- **Versión consultada:** `fuentes/pdf/slurm-overview-2026.html`, página *Overview* de la documentación oficial de SchedMD (<https://slurm.schedmd.com/overview.html>), descargada el 2026-10-04.
- **Usos:**
  - `chapters/06-estado-del-arte.tex` · `\label{sec:entornos-universitarios}` ¶1 · «un sistema de gestión de clústeres y planificación de trabajos que asigna recursos y arbitra su disputa mediante una cola de trabajos pendientes»
    - Pasaje: "Slurm is an open source, fault-tolerant, and highly scalable cluster management and job scheduling system for large and small Linux clusters."; "it allocates exclusive and/or non-exclusive access to resources (compute nodes) to users for some duration of time"; "it arbitrates contention for resources by managing a queue of pending work."
    - **Estado:** verificada · 2026-10-04

## llamacpp-readme-2026

- **Versión consultada:** `fuentes/pdf/llamacpp-readme-2026.md`, archivo *README* de la rama principal de <https://github.com/ggml-org/llama.cpp>, descargado el 2026-10-04. Es documentación técnica, no producción arbitrada.
- **Usos:**
  - `chapters/06-estado-del-arte.tex` · `\label{sec:motores-inferencia}` ¶2 · «se plantea como objetivo la inferencia de modelos con una configuración mínima, y su implementación en C/C++ no tiene dependencias y admite cuantización a enteros de entre 1,5 y 8 bits, con núcleos CUDA propios para las GPU de NVIDIA»
    - Pasaje: "The main goal of `llama.cpp` is to enable LLM (and VLM) inference with minimal setup and state-of-the-art performance on a wide range of hardware"; "Plain C/C++ implementation without any dependencies"; "1.5-bit, 2-bit, 3-bit, 4-bit, 5-bit, 6-bit, and 8-bit integer quantization for faster inference and reduced memory use"; "Custom CUDA kernels for running LLMs on NVIDIA GPUs"
    - **Estado:** verificada · 2026-10-04. **Matices:** el README no describe el formato GGUF ni el tamaño de los modelos que caben en 24 GB, y esas dos afirmaciones quedan sin cita como hechos del proyecto (`project-context/technologies.md`). Tampoco dice «sobrecarga mínima», por lo que se retiró esa expresión. La frase anterior «carece de orquestación distribuida nativa» se retiró porque el README lista un *backend* RPC; la nueva frase sobre políticas multiusuario es una lectura de los autores sobre la documentación.

