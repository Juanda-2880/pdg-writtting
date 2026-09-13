En este archivo se encuentran las busquedas que hice y los links ( NO ACADEMICOS) que me ayudaron a armar el marco teorico y a entener bien el proceso del proyecto. El orden presentado es el orden en que se investigo pero no necesarimanete tiene que ser el orden en el que se presenten en el marco teorico y mucho menos con esas fuentes, se tienen que utilizar fuentes academicas y de preferencia que sean recientes, pero estas fuentes me ayudaron a entender el proceso y a armar el marco teorico.

- En el marco teorico hay que definir que se considera como una carga de despliegue y de entrenamiento para nuestro proyecto, no solo son LLMs, sino que tambien son modelos de ML. Es despliegue de IA en general
1. Model deployment de IBM https://www.ibm.com/think/topics/model-deployment
2. Que es la inferencia IBM https://www.ibm.com/think/topics/ai-inference
3. Kubernetes, no lo investigue como tal porque ya se como es, pero se que tiene que ir mencionado en el marco teorico
4. Motores de inferencia (Aqui tambien hay que hablar de tecnicas de inferencia de LLM)
5. Extensiones de kubernetes como KubeRay, KubeFlow para entrenar, RayJobs, Kueue, GPU operator y cualquiera otra interesante para la arquitectua
6. Telemetria 

Tecnologias que vale la pena investigar: (Todo claramente corre dentro de nuestro cluster de kubernetes)
TensorFlow Serving 

---

## Dónde quedó cada punto (aplicado 2026-09-13)

| Punto de la lista de arriba | Dónde está ahora |
| :--- | :--- |
| Definir carga de despliegue contra carga de entrenamiento, para IA en general y no solo LLMs | `thesis/chapters/05-marco-teorico.tex` §4.1, con el criterio de punto de envío, y fila 1 de la tabla del marco conceptual |
| Model deployment / AI inference (IBM) | Reemplazados por fuentes académicas en §4.2 (`muiruri-mlinferenceserving-2026`). Los enlaces de IBM sirvieron de guía conceptual y no se citan |
| Kubernetes | §4.3, con el modelo declarativo y el bucle de reconciliación (`burns-borgomegak8s-2016`) |
| Motores de inferencia y técnicas de inferencia de LLM | §4.2: paginación de caché, programación por iteración y cuantización posentrenamiento |
| Extensiones de Kubernetes (KubeRay, RayJobs, Kueue, GPU Operator) | §4.3, precedidas de la explicación de CRDs y del patrón operador (`xu-k8soperatorbugs-2024`) |
| Telemetría | §4.5: las tres señales de observabilidad y el conjunto Prometheus, Loki, Grafana y exportador DCGM |
| TensorFlow Serving, Kubeflow | **Estado del arte (cap. 06)**, no marco teórico: son alternativas de solución ya propuestas, que es lo que el formato pide caracterizar allí |
| Comparación vLLM contra llama.cpp | Salió del marco teórico por límite de extensión (4 páginas) y pasa al **estado del arte** |
