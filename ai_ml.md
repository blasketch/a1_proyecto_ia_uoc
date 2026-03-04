Categoría: IA y Machine Learning

## <img src="./img/SageMaker.png" width="30" align="absmiddle"> Amazon SageMaker

### 1. Descripción y funcionalidad
Amazon SageMaker es una plataforma totalmente gestionada que proporciona la capacidad de construir, entrenar y desplegar modelos de aprendizaje automático (ML) rápidamente. Abarca todo el flujo de trabajo de ML, desde la preparación de datos hasta el despliegue de predicciones en producción.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** Gestión del ciclo de vida completo de MLOps (Machine Learning Operations), desde la experimentación en cuadernos Jupyter gestionados hasta la implementación de modelos en endpoints productivos.
* **Caso de uso 1:** Mantenimiento predictivo. Utilización de algoritmos preconstruidos para predecir fallos en maquinaria industrial basándose en telemetría histórica.
* **Caso de uso 2:** Recomendaciones personalizadas. Aplicación de ajuste automático de modelos para crear motores de recomendación que sugieran productos en tiempo real.

### 3. Latencia y rendimiento
* **Latencia:** Los endpoints de inferencia en tiempo real ofrecen latencias de milisegundos. Para procesos masivos asíncronos y no críticos, permite inferencia por lotes (Batch Transform).
* **Rendimiento:** Altamente escalable. Permite el uso de instancias optimizadas para cómputo o GPU y capacidad de entrenamiento distribuido en múltiples instancias GPU/CPU para datasets de gran escala.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Alta. Exige gestionar canalizaciones completas de MLOps, lo que incluye el control de versiones, el despliegue continuo y la monitorización crítica del drift (desviación) de datos y sesgos mediante Amazon SageMaker Model Monitor.
* **Escalabilidad:** Totalmente elástica. Permite el escalado automático (Auto Scaling) de los endpoints de inferencia según las métricas de tráfico y el aprovisionamiento dinámico de clústeres de computación para el entrenamiento, optimizando el uso de recursos.
* **Seguridad:** Cumple con el Modelo de Responsabilidad Compartida de AWS. Ofrece aislamiento mediante VPC privada, cifrado de datos end-to-end con AWS KMS y control de acceso de mínimo privilegio mediante roles de IAM.

### 5. Límites y cuotas principales
* Cuotas regionales restrictivas por familia de instancia (vCPUs/GPUs) para entrenamiento y alojamiento.
* Límite de tamaño máximo del artefacto del modelo (generalmente 30 GB en memoria de contenedor) y tiempos de espera máximos (timeout) con límite de timeout típico de aproximadamente 60 segundos para invocaciones síncronas en endpoints en tiempo real.

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Pago por hora de uso de instancias para experimentación (Notebooks) y alojamiento de modelos (Hosting).
* **Escenario propuesto:** Entrenamiento de un modelo propietario de visión artificial para detectar patrones. Al tratarse de comprobar si el dibujo impreso coincide exactamente con el diseño original exclusivo, es obligatorio entrenar un algoritmo a medida.
  * Desarrollo: 1 instancia básica `ml.t3.medium` encendida 100 horas al mes para la creación y ajuste del modelo.
  * Inferencia: 1 instancia `ml.m5.large` operando 24/7 (730 horas/mes) para evaluar cada imagen.
* **Coste estimado mensual:** ~$97,66 USD
* **Evidencia:** https://calculator.aws/#/estimate?id=e7b15d6353c61f8b71f259bd99796a9f16e0b581

### 7. Referencias y documentación oficial
* [Documentación oficial de Amazon SageMaker](https://docs.aws.amazon.com/sagemaker/)
* [Precios y facturación de Amazon SageMaker](https://aws.amazon.com/sagemaker/pricing/)

## <img src="./img/Rekognition.png" width="30" align="absmiddle"> Amazon Rekognition

### 1. Descripción y funcionalidad
Amazon Rekognition es un servicio de análisis de imágenes y vídeos basado en aprendizaje profundo. Permite identificar objetos, personas, texto y escenas mediante APIs preentrenadas por AWS, eliminando la necesidad de gestionar infraestructura o modelos complejos.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** IA Cognitiva "Plug-and-play" basada en APIs gestionadas sin gestión de infraestructura subyacente.
* **Caso de uso 1:** Moderación automática de imágenes en plataformas digitales para detectar y filtrar contenido inapropiado o inseguro en tiempo real.
* **Caso de uso 2:** Reconocimiento facial y detección de equipos de protección individual (EPIs) para garantizar la seguridad laboral en plantas industriales o streaming de vídeo.

### 3. Latencia y rendimiento
* **Latencia:** Baja latencia constante gestionada por la infraestructura global de AWS. Las respuestas de la API son inmediatas, sin sufrir arranques en frío (cold starts) de modelos.
* **Rendimiento:** Capacidad elástica masiva. Puede procesar miles de imágenes por segundo de forma simultánea o flujos de vídeo en directo sin degradación del servicio.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Muy baja. Al ser serverless, el equipo se desentiende del entrenamiento de modelos, parcheo y escalado. Se consume directamente mediante llamadas a la API.
* **Escalabilidad:** Automática y elástica, pero sujeta a cuotas regionales. Si se superan los límites de Transacciones Por Segundo (TPS) predeterminados de la cuenta, puede producirse throttling (estrangulamiento de peticiones) a menos que se solicite una ampliación a AWS.
* **Seguridad:** Los datos se procesan de forma segura y cifrada. Cumple con normativas de privacidad estrictas y permite el control de acceso granular mediante roles de IAM.

### 5. Límites y cuotas principales
* Tamaño máximo de imagen: 15 MB (vía S3) o 5 MB (binario directo).
* Límite predeterminado de transacciones por segundo (TPS) por región, con riesgo de throttling si no se gestiona la concurrencia.

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Pago por volumen exacto de imágenes analizadas.
* **Escenario propuesto:** Uso de la API preentrenada de AWS para verificar por cámara si el operario lleva puestos los equipos de protección. Se asume una fase de pruebas procesando 1.000 imágenes al mes.
* **Coste estimado mensual:** ~$1.00 USD
* **Evidencia:** https://calculator.aws/#/estimate?nc2=h_pr_calc&id=ee597d9ca0e834be674ec4043118294abec3febd

### 7. Referencias y documentación oficial
* [Documentación oficial de Amazon Rekognition](https://docs.aws.amazon.com/rekognition/)
* [Precios y facturación de Amazon Rekognition](https://aws.amazon.com/rekognition/pricing/)

### Tabla comparativa: Amazon SageMaker vs Amazon Rekognition

| Característica | Amazon SageMaker | Amazon Rekognition |
| :--- | :--- | :--- |
| **Gestión de infraestructura** | PaaS (Requiere aprovisionar y gestionar instancias ML) | Serverless (Totalmente gestionado por AWS) |
| **Latencia / Rendimiento** | Depende del tamaño de la instancia y del modelo | Baja latencia constante e inmediata vía API |
| **Modelo de pago** | Por hora/segundo de instancia activa (incluso inactiva) | Por volumen exacto de imágenes o minutos analizados |
| **Límites críticos** | Tiempo máximo de inferencia y tamaño del modelo | Límite de TPS, riesgo de throttling y tamaño de imagen |
| **Escalabilidad** | Automática configurando políticas de Auto Scaling | Elástica pero sujeta a ampliación de cuotas regionales |

### Síntesis y trade-offs de la categoría

La selección entre Amazon SageMaker y Amazon Rekognition representa el equilibrio entre los dos grandes paradigmas de la inteligencia artificial en la nube: el **desarrollo de modelos a medida vs consumo de servicios de IA preentrenados**. Esta decisión condiciona tanto la agilidad del despliegue como la capacidad de especialización de la solución.

El primer trade-off crítico es la **Simplicidad Operativa vs la Flexibilidad Técnica**. Rekognition, como servicio de visión artificial gestionado, prioriza la velocidad de implementación y elimina la gestión de algoritmos complejos, permitiendo integrar capacidades visuales de forma inmediata. Sin embargo, su rigidez es el precio a pagar, ya que no permite modificar la arquitectura interna de la red neuronal. Por el contrario, SageMaker ofrece control total sobre la operacionalización y gestión del ciclo de vida del modelo, permitiendo el ajuste fino de las variables de entrenamiento. El trade-off asumido en este caso es una mayor complejidad de mantenimiento y la necesidad de perfiles expertos.

El segundo factor decisivo es el  **Coste por Volumen vs Precisión Especializada**. Rekognition sigue un modelo de pago por uso que elimina barreras financieras iniciales, siendo ideal para acelerar el ciclo de lanzamiento al mercado con precisiones estandarizadas. SageMaker, en cambio, implica costes de infraestructura dedicada que pueden ser elevados. No obstante, se vuelve indispensable cuando el caso de uso exige una precisión superior a la estándar o requiere procesar información con características únicas que los modelos genéricos no pueden interpretar correctamente.

Desde una perspectiva estratégica, el uso de Rekognition se prioriza en aquellos escenarios donde las capacidades nativas de la plataforma cubren el espectro operativo necesario. Arquitectónicamente, este enfoque favorece sistemas que reaccionan de forma autónoma ante disparadores, desacoplando la inteligencia visual de la gestión de servidores y optimizando el consumo de recursos computacionales.

En contraposición, SageMaker constituye el núcleo de arquitecturas enfocadas en el flujo y calidad del dato. En este entorno es necesario establecer procesos robustos para el entrenamiento continuo, la monitorización de la pérdida de precisión con el paso del tiempo y el control total sobre la lógica de respuesta. Su uso se justifica exclusivamente cuando la personalización aporta una ventaja competitiva diferencial para el negocio.

