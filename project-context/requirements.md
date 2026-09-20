# Requerimientos de desarrollo de IAsLab ORCHID

> [!IMPORTANT]
> Es la especificación de lo que el equipo va a construir. Contiene requerimientos que sí se escriben en el documento de grado y requerimientos que **no** se escriben allí, aunque igual se desarrollen.
>
> **Regla de lectura para cualquier agente o persona que trabaje aquí:**
>
> 1. **Todos** los requerimientos de este documento se tienen en cuenta para el desarrollo del proyecto.
> 2. **Solo** los requerimientos de la [sección 2](#2-requerimientos-por-objetivo) pueden escribirse en `thesis/`. Los de la [sección 3](#3-requerimientos-sin-compromiso) se construyen, pero **no se mencionan en el documento de grado**, no aparecen en los objetivos, ni en la metodología, ni en la trazabilidad de resultados.
> 3. Un requerimiento de la sección 3 **no amplía el alcance del PDG**. Si algún texto del documento de grado empieza a depender de uno de ellos, eso es un error de redacción, no un cambio de alcance.

**Proyecto:** *IAsLab ORCHID: Plataforma de Orquestación y Gobernanza de Cargas de IA/ML en la Infraestructura de la Universidad Icesi*, Universidad Icesi.

**Reglas de escritura:** las restricciones de estilo de `../CLAUDE.md` (regla 8) aplican a `thesis/` y **no** a este documento.

---

## 1. Propósito y alcance del proyecto

### 1.1 Propósito

Dotar al Laboratorio de Inteligencia Artificial y Arquitectura de Software (IAsLab) de una plataforma de clúster sobre Kubernetes para el despliegue, la observabilidad, la gobernanza de recursos y la evaluación de cargas de trabajo de inteligencia artificial, en modo concurrente y multiusuario, ejecutándose estrictamente sobre la infraestructura propia de la universidad.

La plataforma debe servir **dos clases de carga de trabajo**: modelos grandes de lenguaje (LLM) y otras cargas de inteligencia artificial que no son de lenguaje (por ejemplo, modelos de visión o modelos PyTorch arbitrarios). Ninguna capacidad de la plataforma puede asumir que la carga es siempre un LLM.

### 1.2 Incluye

- Despliegue de un clúster Kubernetes sobre las estaciones de trabajo de la sala 104M, con soporte de GPU.
- Módulo de observabilidad de hardware, de logs y de carga servida, basado en Prometheus, Thanos, Loki, Grafana y el exportador DCGM de NVIDIA.
- Sistema de gobernanza de recursos y cuotas por rol, integrado con el servicio institucional SAAMFI vía OAuth2/OIDC, con admisión, encolamiento, prioridad y reservas anticipadas.
- Orquestación de motores de inferencia empaquetados como imágenes de contenedor y declarados sobre el clúster.
- Ejecución de cargas de IA que no son modelos de lenguaje sobre el mismo flujo de despliegue.
- Interfaz web para desplegar modelos y administrar cuotas.
- Motor de medición automatizado para las pruebas de carga.
- Configuración del clúster versionada y automatizada, redesplegable en otra sala del laboratorio.
- Documentación técnica y de usuario.

### 1.3 No incluye

- **Entrenamiento o *fine-tuning* de modelos como funcionalidad del documento de grado.** El soporte de cargas de entrenamiento se construye, pero está en la [sección 3](#3-requerimientos-sin-compromiso).
- Inferencia distribuida entre nodos por red. La red de 10 Gbit/s de la sala no la sostiene y un modelo corre en una sola máquina.
- Cuantización de modelos como proceso propio de la plataforma. La plataforma despliega pesos que ya vienen cuantizados, y puede apoyarse en la cuantización que el motor aplique al cargar el modelo.
- Nube privada con OpenStack por debajo de la plataforma.
- Soporte y mantenimiento de la plataforma después del cierre del proyecto, que queda a cargo del IAsLab.

---

## 2. Requerimientos por objetivo

Cada requerimiento es una unidad de trabajo asignable. La columna **Prioridad** indica el orden de construcción.

### 2.1 Objetivo 1 — Módulo de observabilidad

> Desarrollar un módulo de observabilidad de la plataforma para la captura y visualización de métricas de *hardware* y de carga de trabajo de los nodos de cómputo del IAsLab, orientado a la supervisión del estado de dichos nodos.

#### 2.1.1 Infraestructura base de telemetría

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R1-01 | El sistema debe desplegar Prometheus dentro del clúster como servicio permanente para centralizar la recolección de métricas de todos sus componentes. | Alta |
| R1-02 | El sistema debe recolectar las métricas nativas de Kubernetes mediante `kube-state-metrics` y `node-exporter` para observar el estado de nodos, *pods* y *deployments* sin instrumentación adicional. | Alta |
| R1-03 | El sistema debe desplegar Thanos sobre Prometheus para conservar las series temporales a largo plazo y consultarlas desde un punto único, sin que la retención quede limitada al disco de una sola instancia. | Alta |
| R1-04 | El sistema debe desplegar Loki junto con un agente de recolección en cada nodo para centralizar la salida estándar y de error de todos los *pods* del clúster. | Alta |
| R1-05 | El sistema debe desplegar Grafana con Prometheus, Thanos y Loki registrados como fuentes de datos para consultar métricas y registros desde una sola interfaz. | Alta |
| R1-06 | El sistema debe permitir configurar la ventana de retención de métricas y registros para sostener el análisis posterior de las pruebas de carga. | Media |
| R1-07 | El sistema debe etiquetar métricas y registros con las mismas etiquetas de nodo, *namespace*, *pod* y despliegue para poder pasar de una anomalía en una gráfica a los registros que la produjeron. | Alta |
| R1-08 | El sistema debe reflejar la telemetría con una latencia de actualización suficiente para que una condición de riesgo se detecte mientras todavía puede evitarse. | Alta |

#### 2.1.2 Telemetría de hardware

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R1-09 | El sistema debe ejecutar el exportador DCGM de NVIDIA como *DaemonSet* en los nodos con GPU para exponer a Prometheus las métricas que residen en el *firmware* de la tarjeta. | Alta |
| R1-10 | El sistema debe recolectar la temperatura del núcleo y de la memoria de cada GPU para detectar sobrecalentamiento antes de que degrade el servicio. | Alta |
| R1-11 | El sistema debe recolectar la utilización de VRAM de cada GPU, en valor absoluto y en porcentaje, para detectar la saturación que precede al congelamiento del equipo. | Alta |
| R1-12 | El sistema debe recolectar el consumo de potencia en vatios de cada GPU para vigilar el límite de la fuente de poder de la torre, que el laboratorio identificó como causa física del congelamiento. | Media |
| R1-13 | El sistema debe recolectar los estados de limitación térmica y de potencia (*throttling*) de cada GPU para distinguir una caída de rendimiento por límite físico de una por contención de carga. | Media |
| R1-14 | El sistema debe recolectar el *throughput* del bus PCIe de cada GPU para identificar cuellos de botella de transferencia entre memoria de sistema y memoria de video. | Media |
| R1-15 | El sistema debe recolectar el uso de CPU, la RAM de sistema y la E/S de disco de cada nodo para observar el estado del equipo más allá del acelerador. | Alta |
| R1-16 | El sistema debe recolectar el espacio disponible en la partición dedicada a pesos de modelos para anticipar el agotamiento del almacenamiento. | Media |
| R1-17 | El sistema debe recolectar el estado de alcanzabilidad de cada nodo para distinguir un equipo apagado de uno encendido que dejó de responder. | Media |
| R1-18 | El sistema debe capturar la telemetría de hardware de un nodo sin importar qué carga esté corriendo en él, para que ninguna carga quede como punto ciego. | Alta |

#### 2.1.3 Telemetría de la carga servida

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R1-19 | El sistema debe exponer un punto `/metrics` en cada *pod* de motor de inferencia y registrarlo como objetivo de recolección de Prometheus para incorporar sus métricas al mismo almacén que las de hardware. | Alta |
| R1-20 | El sistema debe medir el tiempo hasta el primer *token* por despliegue y por modelo para cuantificar la latencia percibida al inicio de una respuesta. | Alta |
| R1-21 | El sistema debe medir la latencia entre *tokens* consecutivos por despliegue para cuantificar la fluidez de la generación. | Alta |
| R1-22 | El sistema debe medir los *tokens* por segundo de entrada y de salida por despliegue para dimensionar el rendimiento del motor bajo carga. | Alta |
| R1-23 | El sistema debe medir la cantidad de peticiones en cola y el nivel de saturación de concurrencia de cada motor para anticipar la degradación antes de que se manifieste en latencia. | Media |
| R1-24 | El sistema debe medir la latencia de petición y la tasa de peticiones atendidas de las cargas de IA que no son de lenguaje para observarlas sin depender de métricas de *tokens*. | Alta |
| R1-25 | El sistema debe medir la tasa de errores y de peticiones rechazadas por despliegue para separar la degradación del fallo. | Media |
| R1-26 | El sistema debe asociar cada métrica de carga al usuario y al despliegue que la originó para que el consumo sea atribuible a un responsable. | Alta |

#### 2.1.4 Visualización y alertas

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R1-27 | El sistema debe ofrecer un panel de hardware filtrable por nodo, con temperatura, VRAM, potencia, PCIe, CPU y RAM, para diagnosticar el estado de un equipo concreto. | Alta |
| R1-28 | El sistema debe ofrecer un panel de carga servida filtrable por modelo y por despliegue, con tiempo al primer *token*, latencia, *throughput* y saturación, para comparar el comportamiento entre despliegues. | Alta |
| R1-29 | El sistema debe ofrecer un panel de consumo por usuario para que el administrador vea cuánta cuota consume cada uno sin recurrir a la línea de comandos. | Alta |
| R1-30 | El sistema debe permitir definir reglas de alerta sobre cualquiera de las métricas recolectadas, con umbrales configurables, para anticipar condiciones de riesgo sin vigilancia manual. | Alta |
| R1-31 | El sistema debe notificar las alertas al administrador por un canal configurable para que no dependan de que alguien esté mirando el panel. | Media |
| R1-32 | El sistema debe reiniciar automáticamente el contenedor de inferencia que deja de responder para recuperar el servicio sin intervención manual. | Media |
| R1-33 | El sistema debe conservar los registros y la telemetría previos a un fallo de nodo para permitir el diagnóstico posterior de un modo de fallo que el laboratorio reporta como frecuente. | Media |

### 2.2 Objetivo 2 — Gobernanza de recursos y cuotas por rol

> Implementar un sistema de cuotas y restricciones de infraestructura, acoplado a los roles provistos por SAAMFI y a un rol de administrador de la plataforma, que reserve cupos de cómputo para las cargas de inferencia, con el fin de prevenir la monopolización de las GPU.

#### 2.2.1 Identidad y control de acceso

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R2-01 | El sistema debe autenticar a los usuarios contra SAAMFI mediante OAuth2/OIDC para que nadie acceda a la plataforma con credenciales propias de esta. | Alta |
| R2-02 | El sistema debe redirigir al usuario autenticado al panel principal de la aplicación para cerrar el flujo de autenticación de extremo a extremo entre frontend y backend. | Alta |
| R2-03 | El sistema debe traducir los atributos del *token* de SAAMFI a los roles de la plataforma en un componente aislado, para que un cambio en el proveedor de identidad obligue a ajustar solo ese componente. | Alta |
| R2-04 | El sistema debe definir un rol de administrador propio, gestionable de forma independiente de SAAMFI, para operar la plataforma sin depender de cambios en el proveedor institucional. | Alta |
| R2-05 | El sistema debe asignar el rol de usuario por defecto a toda identidad autenticada que no sea administradora, para que el acceso quede definido sin configuración manual por persona. | Alta |
| R2-06 | El sistema debe derivar del rol de la plataforma los permisos con los que el usuario opera sobre el clúster, para que nadie actúe fuera de su ámbito ni esquive la plataforma usando la API del clúster. | Alta |
| R2-07 | El sistema debe registrar quién desplegó, detuvo o modificó cada recurso y cada cuota, para que el consumo y los cambios de política sean auditables. | Media |

#### 2.2.2 Cuotas y aislamiento

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R2-08 | El sistema debe contar con un mecanismo de cuotas que acote el consumo de CPU, memoria y GPU de cada usuario, para que ninguno agote por sí solo la capacidad de la sala. | Alta |
| R2-09 | El sistema debe aislar los recursos de cada usuario para que la carga de uno no interfiera con el desempeño ni con los despliegues de otro. | Alta |
| R2-10 | El sistema debe acotar también el consumo de un despliegue individual, para que una sola carga no agote la cuota completa de su dueño. | Media |
| R2-11 | El sistema debe rechazar o encolar la solicitud que excede la cuota del usuario, devolviendo un mensaje que explique cuál límite se alcanzó, para que el usuario entienda el rechazo sin consultar al administrador. | Alta |
| R2-12 | El sistema debe definir las cuotas como plantillas por rol, con la posibilidad de sobrescribirlas para un usuario concreto, para administrar el caso general sin perder el caso particular. | Media |
| R2-13 | El sistema debe reservar CPU y memoria para los componentes de la propia plataforma y dejar la GPU para los motores de inferencia, para que la infraestructura no compita con la carga útil por el acelerador. | Alta |
| R2-14 | El sistema debe permitir una sobreasignación configurable entre el 10 % y el 20 % sobre la capacidad nominal para aprovechar que los usuarios no agotan su cuota de forma simultánea. | Media |
| R2-15 | El sistema debe impedir que la sobreasignación lleve un nodo más allá de su capacidad física real para que el margen no se traduzca en inestabilidad del clúster. | Media |
| R2-16 | El sistema debe garantizar que la falla o el congelamiento del contenedor de un usuario no desestabilice los contenedores vecinos ni el nodo anfitrión, para que un fallo individual no se propague a la sala. | Alta |

#### 2.2.3 Admisión, prioridad y reservas

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R2-17 | El sistema debe encolar la solicitud que no encuentra capacidad disponible, en lugar de descartarla, para que el trabajo se ejecute cuando la capacidad se libere. | Alta |
| R2-18 | El sistema debe informar al usuario su posición en la cola y una estimación de espera para que sepa si conviene esperar o reservar. | Baja |
| R2-19 | El sistema debe asociar un nivel de prioridad a cada rol para que la contención de recursos se resuelva por una regla declarada y no por orden de llegada. | Alta |
| R2-20 | El sistema debe permitir que una solicitud de rol prioritario expropie los recursos de una carga de menor prioridad cuando no haya capacidad libre, para garantizar el acceso de la clase superior. | Alta *[verify: ADR-034]* |
| R2-21 | El sistema debe avisar al usuario cuya carga fue expropiada y conservar sus registros de sesión para que la expropiación no se traduzca en pérdida de trabajo silenciosa. | Media |
| R2-22 | El sistema debe permitir reservar cupos de GPU por adelantado para una ventana de tiempo definida, para que un usuario asegure capacidad antes de necesitarla. | Media |
| R2-23 | El sistema debe iniciar y terminar la reserva de forma automática en las horas declaradas para que nadie dependa de una acción manual en el límite de la ventana. | Media |
| R2-24 | El sistema debe avisar al usuario antes del vencimiento de su reserva para que alcance a cerrar su trabajo. | Media |
| R2-25 | El sistema debe guardar los registros y el estado de la sesión al vencer la reserva, antes de liberar o congelar el contenedor, para que la sesión pueda retomarse o revisarse después. | Media |
| R2-26 | El sistema debe liberar los recursos de una reserva vencida para que una reserva caducada no siga ocupando la GPU. | Alta |
| R2-27 | El sistema debe rechazar la reserva que exceda la capacidad disponible de la sala en esa ventana para no comprometer capacidad que no existe. | Media |
| R2-28 | El sistema debe exponer una API con operaciones de creación, consulta, modificación y borrado sobre cuotas y reservas para que el módulo administrativo la consuma. | Alta |
| R2-29 | El sistema debe aplicar las cuotas, la prioridad y la contabilidad de consumo a cualquier carga de inteligencia artificial, sea o no un modelo de lenguaje, para que la gobernanza no dependa de que el consumo se mida en *tokens*. | Alta |

#### 2.2.4 Módulo administrativo

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R2-30 | El sistema debe ofrecer una interfaz administrativa web que cubra toda la operación de gobernanza para que el administrador no necesite la línea de comandos ni conocer Kubernetes. | Alta |
| R2-31 | El sistema debe permitir al administrador modificar los límites de cuota de un rol o de un usuario y aplicar el cambio al clúster sin reiniciar nada, para ajustar la política en caliente. | Alta |
| R2-32 | El sistema debe permitir al administrador asignar y retirar el rol de administrador a otra identidad para que la operación no dependa de una sola persona. | Media |
| R2-33 | El sistema debe mostrar al administrador todos los despliegues en ejecución, sin importar de qué usuario sean, para que tenga visibilidad completa del clúster. | Alta |
| R2-34 | El sistema debe permitir al administrador encender, apagar o deshabilitar cualquier despliegue para recuperar capacidad ante una contención o un abuso. | Alta |
| R2-35 | El sistema debe mostrar al administrador el consumo de cuota de cada usuario en un periodo consultable para sustentar los ajustes de política con datos. | Alta |
| R2-36 | El sistema debe mostrar al administrador la capacidad libre y comprometida por nodo para que pueda planear las reservas sobre el estado real de la sala. | Media |

### 2.3 Objetivo 3 — Despliegue de modelos y ejecución de cargas de IA

> Implementar sobre el clúster de cómputo del IAsLab el despliegue concurrente de modelos de inteligencia artificial ya entrenados, mediante motores de inferencia empaquetados como imágenes de contenedor, con el fin de llevar los modelos del laboratorio a una fase de servicio consumible.

#### 2.3.1 Clúster base

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R3-01 | El sistema debe correr sobre un clúster de Kubernetes instalado en las estaciones de trabajo de la sala 104M, con un nodo de control y el resto como nodos de trabajo, para convertir equipos sueltos en capacidad agregada. | Alta |
| R3-02 | El sistema debe alojar el nodo de control en una máquina que permanezca encendida sin reinicios no anunciados para que la caída de una estación de la sala no tumbe el plano de control. | Alta |
| R3-03 | El sistema debe configurar la red del clúster con un CNI para que los *pods* de distintos nodos se comuniquen entre sí según la política de red definida. | Alta |
| R3-04 | El sistema debe desplegar el NVIDIA GPU Operator para aprovisionar controladores, *runtime* y complemento de dispositivo de forma declarativa, de modo que los nodos expongan el recurso `nvidia.com/gpu`. | Alta |
| R3-05 | El sistema debe dirigir las cargas aceleradas únicamente a los nodos con GPU mediante selectores de nodo, marcas y tolerancias, para que un *pod* sin acelerador no ocupe una máquina que lo tiene. | Alta |
| R3-06 | El sistema debe etiquetar cada nodo con sus capacidades de hardware para que las decisiones de planificación se tomen sobre datos declarados y no sobre nombres de máquina. | Media |
| R3-07 | El sistema debe permitir incorporar o retirar un nodo del clúster sin reinstalar los demás para que la sala pueda crecer o encogerse según la disponibilidad. | Media |
| R3-08 | El sistema debe limitar los recursos que toma de cada estación para que los equipos sigan siendo utilizables en las clases que se dictan en la sala. | Alta |
| R3-09 | El sistema debe permitir marcar un nodo como no planificable y desalojar sus cargas de forma ordenada para liberar una máquina que se necesita para una clase. | Media |
| R3-10 | El sistema debe mantener toda la configuración del clúster versionada en un repositorio y aplicable de forma automatizada, para que la infraestructura pueda redesplegarse en otra sala sin reconstruirla a mano. | Alta |
| R3-11 | El sistema debe funcionar por completo sobre la infraestructura del laboratorio, sin depender de servicios de nube pública, para cumplir la restricción institucional de operación *on-premise*. | Alta |
| R3-12 | El sistema debe almacenar los pesos de los modelos en una partición de disco dedicada, separada del disco raíz y de los registros del sistema, para que el crecimiento del catálogo no comprometa el sistema operativo del nodo. | Alta |
| R3-13 | El sistema debe exponer esa partición al clúster como volumen persistente reclamable por los despliegues para que los *pods* accedan a los pesos sin copiarlos. | Alta |
| R3-14 | El sistema debe conservar los pesos descargados entre reinicios de *pod* para no volver a descargar un modelo que ya está en disco. | Alta |

#### 2.3.2 Orquestación de cargas

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R3-15 | El sistema debe declarar cada servicio de inferencia como un recurso del clúster gestionado por un controlador, para que su ciclo de vida se administre de forma declarativa y no con pasos manuales. | Alta |
| R3-16 | El sistema debe traducir la petición de despliegue de un usuario en la declaración que el clúster aplica, para que el usuario no escriba manifiestos. | Alta |
| R3-17 | El sistema debe desplegar cada modelo dentro de un solo nodo, sin repartirlo entre máquinas, porque la red de la sala no sostiene la inferencia distribuida. | Alta |
| R3-18 | El sistema debe sostener varios despliegues concurrentes de distintos usuarios sobre el clúster sin degradación significativa dentro de los límites de cuota, para que la sala se use de verdad en paralelo. | Alta |
| R3-19 | El sistema debe reflejar el estado real de cada despliegue, distinguiendo al menos pendiente, en ejecución, fallido y detenido, para que el usuario sepa qué está pasando con su carga. | Alta |
| R3-20 | El sistema debe exponer al usuario los registros de su propio despliegue para que diagnostique un fallo sin pedir acceso al clúster. | Media |
| R3-21 | El sistema debe dejar el modelo desplegado accesible dentro del clúster para que pueda consumirse y someterse a las pruebas de carga del objetivo 4. | Alta |

#### 2.3.3 Motores y modelos

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R3-22 | El sistema debe empaquetar cada motor de inferencia como imagen de contenedor versionada en un registro accesible desde el clúster, para que el despliegue no dependa de instalaciones manuales en el nodo. | Alta |
| R3-23 | El sistema debe incluir una imagen de `llama.cpp` compilada para el hardware de la sala, capaz de ejecutar pesos GGUF cuantizados dentro de los 24 GB de VRAM de una RTX 4090. | Alta |
| R3-24 | El sistema debe incluir una imagen de vLLM para comparar su enfoque de gestión de memoria frente a `llama.cpp` bajo cargas idénticas. | Baja |
| R3-25 | El sistema debe permitir añadir un motor de inferencia nuevo sin modificar el resto de la plataforma, para no quedar atado al motor elegido hoy. | Alta |
| R3-26 | El sistema debe desplegar modelos cuyos pesos ya vienen cuantizados, y apoyarse en la cuantización que el motor aplique al cargarlos, sin ejecutar un proceso de cuantización propio, porque construir uno queda fuera del alcance. | Alta |
| R3-27 | El sistema debe ejecutar cargas de inteligencia artificial que no son modelos de lenguaje, entregadas como archivo de pesos más un servidor propio, por el mismo camino de despliegue que un modelo de lenguaje, para que la plataforma no quede atada al caso de uso de lenguaje. | Alta |
| R3-28 | El sistema debe rechazar, con un mensaje explicativo, el despliegue de un modelo que no cabe en la memoria de video de un nodo, para evitar el fallo por falta de memoria en tiempo de ejecución. | Media |
| R3-29 | El sistema debe permitir dar de alta un modelo nuevo indicando un identificador de repositorio externo o subiendo el archivo de pesos, para que el catálogo crezca sin intervención del administrador. | Media |
| R3-30 | El sistema debe proponer los parámetros de ejecución de un modelo recién dado de alta a partir de sus características, para reducir el ensayo y error al configurarlo. | Baja |

#### 2.3.4 Interfaz de despliegue

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R3-31 | El sistema debe ofrecer al usuario un catálogo de los modelos ya entrenados disponibles para que elija sin conocer su ubicación en disco. | Alta |
| R3-32 | El sistema debe permitir al usuario elegir el motor de ejecución entre los habilitados antes de desplegar, para que compare el comportamiento de su modelo entre ellos. | Alta |
| R3-33 | El sistema debe permitir al usuario fijar el nodo de despliegue o dejar la decisión al planificador del clúster, para reservar un equipo concreto cuando la prueba lo exige. | Media |
| R3-34 | El sistema debe permitir al usuario iniciar y detener su despliegue desde la interfaz, para que libere la GPU cuando termine sin pedírselo al administrador. | Alta |
| R3-35 | El sistema debe mostrar al usuario su cuota asignada y su consumo actual para que sepa cuánto le queda antes de que se lo rechacen. | Alta |
| R3-36 | El sistema debe ser operable por un estudiante sin conocimientos de línea de comandos ni de Kubernetes, para no reproducir la barrera de acceso que motivó el proyecto. | Alta |

### 2.4 Objetivo 4 — Evaluación de desempeño y aceptación

> Evaluar el desempeño y la aceptación de la plataforma mediante pruebas de carga y la aplicación del *System Usability Scale* a usuarios del laboratorio.

#### 2.4.1 Medición de desempeño

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| R4-01 | El sistema debe contar con un motor de medición automatizado que ejecute escenarios de prueba declarados en un archivo de especificación, para que una prueba sea repetible sin reconstruirla a mano. | Alta *[verify: ADR-031]* |
| R4-02 | El sistema debe permitir configurar el número de usuarios simultáneos del escenario de carga para observar el comportamiento de la plataforma a distintos niveles de concurrencia. | Alta |
| R4-03 | El sistema debe generar peticiones de inferencia concurrentes contra los despliegues activos para reproducir el uso real de varios usuarios a la vez. | Alta |
| R4-04 | El sistema debe medir en cada ejecución el tiempo al primer *token*, la latencia entre *tokens*, los *tokens* por segundo de entrada y de salida, el tiempo total de respuesta y la tasa de error, para sostener con datos la comparación entre escenarios. | Alta |
| R4-05 | El sistema debe correlacionar los resultados de la prueba con la telemetría de hardware del mismo periodo para explicar una degradación por el estado de los nodos. | Alta |
| R4-06 | El sistema debe registrar las métricas de red durante la prueba para descartar explícitamente el ancho de banda de la sala como cuello de botella silencioso. | Alta |
| R4-07 | El sistema debe permitir ejecutar el mismo escenario contra motores de inferencia distintos en condiciones idénticas para que la comparación entre ellos sea válida. | Media |
| R4-08 | El sistema debe exportar los resultados en un formato comparable entre ejecuciones para que las mediciones de fases distintas puedan contrastarse. | Media |
| R4-09 | El sistema debe permitir programar la ejecución de las pruebas fuera del horario de clases, porque toda prueba que degrade el rendimiento de los equipos debe correr cuando la sala está libre. | Alta |
| R4-10 | El sistema debe evaluar la calidad del código que generan los modelos servidos, para complementar la velocidad de generación con una medida de utilidad. | Baja |
| R4-11 | El proyecto debe producir un reporte que compare latencias y *throughput* entre escenarios de carga y entre motores, para sustentar con evidencia la evaluación de desempeño técnico. | Alta |

---

## 3. Requerimientos sin compromiso

> [!WARNING]
> **Todo lo de esta sección se construye, y nada de esta sección se escribe en `thesis/`.**
>
> Son acuerdos de desarrollo con el tutor que **no amplían el alcance del PDG**. No aparecen en los objetivos del anteproyecto, ni en las fases de la metodología, ni en la trazabilidad de resultados y entregables. Ningún texto del documento de grado puede depender de ellos.

### 3.1 Módulo de soporte de cargas de entrenamiento

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| RSC-01 | El sistema debe contar con un módulo que soporte cargas de entrenamiento de modelos de lenguaje y de otros modelos de inteligencia artificial, para que el laboratorio cubra el ciclo completo sobre la misma infraestructura. | Alta |
| RSC-02 | El sistema debe permitir enviar un trabajo de entrenamiento desde la plataforma y programarlo sobre un nodo con GPU por el mismo camino que un despliegue de inferencia, para no mantener dos flujos separados. | Alta |
| RSC-03 | El sistema debe contabilizar el consumo de GPU, CPU y memoria de un trabajo de entrenamiento dentro de la misma cuota del usuario que lo envió, para que el entrenamiento no escape a la gobernanza. | Alta |
| RSC-04 | El sistema debe aplicar a los trabajos de entrenamiento las mismas reglas de admisión, prioridad, expropiación y sobreasignación que a las cargas de inferencia, para que ninguna clase de carga tenga trato privilegiado por omisión. | Alta |
| RSC-05 | El sistema debe etiquetar la telemetría con la clase de carga para que los paneles separen el consumo de entrenamiento del de inferencia sobre un mismo nodo. | Media |
| RSC-06 | El sistema debe determinar la clase de una carga a partir del plano de control por el que entró, y no por una heurística sobre su telemetría, para que la clasificación sea determinista y auditable. | Media |
| RSC-07 | El sistema debe mostrar el estado, el progreso y los recursos consumidos por un trabajo de entrenamiento, tanto a su dueño como al administrador, para que un entrenamiento largo no sea una caja negra. | Media |
| RSC-08 | El sistema debe conservar en almacenamiento persistente los puntos de control que produce un entrenamiento para que una interrupción no obligue a empezar de cero. | Media |
| RSC-09 | El sistema debe permitir detener un trabajo de entrenamiento desde el módulo administrativo para recuperar capacidad ante una contención. | Media |

### 3.2 Consumo externo de los modelos desplegados

El objetivo 3 compromete que un usuario despliegue un modelo desde la plataforma y que ese modelo quede accesible dentro del clúster (R3-21). Todo lo que expone ese modelo hacia afuera del clúster, y la capa que gobierna ese tráfico, se construye pero no se compromete en el documento.

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| RSC-10 | El sistema debe concentrar las peticiones hacia los modelos desplegados en un único punto de entrada para aplicar en un solo lugar las políticas transversales de acceso y consumo. | Alta |
| RSC-11 | El sistema debe emitir a cada usuario un *token* de API con periodo de expiración para que consuma los modelos desplegados desde fuera de la interfaz web. | Alta |
| RSC-12 | El sistema debe permitir revocar un *token* de API antes de su expiración para cortar el acceso de una credencial comprometida. | Media |
| RSC-13 | El sistema debe aplicar límites de tasa por usuario o por *token* en ese punto de entrada, rechazando o encolando las peticiones que los excedan, para impedir que un usuario acapare el servicio. | Alta |
| RSC-14 | El sistema debe registrar el consumo de cada petición atendida para alimentar la contabilidad de cuotas con el uso real del modelo. | Alta |
| RSC-15 | El sistema debe entregar al usuario el punto de acceso de su modelo en servicio para que pueda consumirlo desde sus propias herramientas. | Alta |
| RSC-16 | El sistema debe enrutar cada petición al despliegue que corresponde al modelo solicitado, repartiéndola entre las réplicas disponibles, para que el cliente no necesite conocer dónde corre el modelo. | Alta |
| RSC-17 | El sistema debe enrutar la petición al perfil de máquina adecuado según si requiere un modelo potente o uno rápido, para no gastar una GPU grande en una consulta liviana. | Baja |
| RSC-18 | El sistema debe ser accesible desde la red del campus, y de forma remota autorizada a través del enrutamiento institucional, para que el laboratorio no sea el único punto de acceso. | Media |

### 3.3 Prioridad de reserva por curso académico

| ID | Requerimiento | Prioridad |
| :--- | :--- | :--- |
| RSC-19 | El sistema debe permitir marcar una reserva como perteneciente a un curso académico para distinguirla de una reserva individual. | Media |
| RSC-20 | El sistema debe dar a las reservas de curso prioridad configurable sobre las reservas individuales de trabajo de grado o exploración, para que una clase programada no quede sin capacidad. | Media |
| RSC-21 | El sistema debe asociar usuarios y reservas a un curso desde su propia administración, sin consultar el sistema de horarios de la universidad, porque esa integración quedó fuera del proyecto. | Media |

**Por qué está aquí.** El tutor dejó fuera de este PDG el sistema de cuotas por curso y horario el 2026-09-09, y registró que la gestión de cursos no vive en SAAMFI. La capacidad sigue siendo útil para el laboratorio, así que se desarrolla y no se escribe en el documento.
