# Categoría: Datos y ETL (Procesamiento y transformación)

## <img src="https://www.awsicon.com/static/images/Service-Icons/Analytics/64/png5x/Glue.png" width="30" align="absmiddle"> AWS Glue

### 1. Descripción y Funcionalidad
AWS Glue es un servicio de integración de datos y ETL (Extracción, Transformación y Carga) totalmente gestionado y *Serverless* (sin servidor). Su función principal es descubrir, preparar, mover e integrar datos desde múltiples fuentes para analítica, machine learning y desarrollo de aplicaciones. Incluye un Catálogo de Datos centralizado para indexar la información.

### 2. Patrones y Casos de Uso Idóneos
* **Patrón principal:** Procesamiento Batch (por lotes) sin gestión de infraestructura, y catalogación automática de datos.
* **Caso de uso 1:** Limpieza y transformación de datos brutos alojados en un Data Lake (S3) antes de enviarlos a un Data Warehouse (Redshift).
* **Caso de uso 2:** Descubrimiento automático de esquemas de datos usando "Glue Crawlers".

### 3. Trade-offs y Alternativas (Justificación)
* **Alternativa:** Amazon EMR.
* **Trade-offs (Pros/Contras):** Frente a EMR, Glue ofrece una simplicidad operativa extrema al ser *Serverless* (no hay que aprovisionar ni mantener clústeres), lo que ahorra costes de personal. El sacrificio (*trade-off*) es que ofrece menos flexibilidad para afinar el rendimiento del motor subyacente (Apache Spark) y el coste por hora de computación pura es más elevado que alquilar servidores en EMR.

### 4. Operación, Escalabilidad y Seguridad
* **Complejidad operativa:** Muy baja. Al ser Serverless, AWS escala automáticamente los recursos según el volumen de datos.
* **Seguridad:** Integración profunda con IAM para control de accesos a nivel de tabla o columna. Los trabajos se pueden ejecutar dentro de una VPC privada y soporta cifrado en reposo y en tránsito mediante AWS KMS.

### 5. Límites y Cuotas Principales
* Límite de 1,000 DPUs (Data Processing Units) por cuenta para trabajos de Spark (ampliable bajo petición).
* Timeout máximo de un trabajo: 48 horas.

### 6. Estimación de Costes (FinOps)
* **Modelo de precios:** Pago por segundo de consumo de DPUs (mínimo de 1 minuto).
* **Escenario propuesto:** Ejecutar un trabajo ETL diario que consume 10 DPUs y tarda 1 hora en completarse (Total: 300 horas DPU al mes). Precio aprox. $0.44 por DPU/hora.
* **Coste estimado mensual:** Alrededor de$132.00 USD.
* **Evidencia:** [Enlace a tu estimación en AWS Pricing Calculator -> URL_CALCULADORA]

---

## <img src="https://www.awsicon.com/static/images/Service-Icons/Analytics/64/png5x/EMR.png" width="30" align="absmiddle"> Amazon EMR (Elastic MapReduce)

### 1. Descripción y Funcionalidad
Amazon EMR es una plataforma de clústeres gestionada que simplifica la ejecución de frameworks de Big Data como Apache Hadoop y Apache Spark en AWS. Permite procesar y analizar grandes cantidades de datos distribuyendo la carga de trabajo entre múltiples instancias (servidores virtuales) de Amazon EC2.

### 2. Patrones y Casos de Uso Idóneos
* **Patrón principal:** Procesamiento masivo de petabytes de datos, Machine Learning a gran escala y pipelines de datos 24/7.
* **Caso de uso 1:** Migración de entornos Hadoop locales (On-Premises) a la nube.
* **Caso de uso 2:** Análisis de streaming en tiempo real y machine learning complejo usando Apache Spark de forma continua.

### 3. Trade-offs y Alternativas (Justificación)
* **Alternativa:** AWS Glue.
* **Trade-offs (Pros/Contras):** EMR ofrece un control granular absoluto sobre el software y la infraestructura (ideal para equipos con expertos en Big Data). Aunque la complejidad operativa es mucho mayor que en Glue, permite un ahorro de costes masivo al usar instancias *Spot* (servidores de bajo coste de AWS) para cargas de trabajo ininterrumpidas y pesadas.

### 4. Operación, Escalabilidad y Seguridad
* **Complejidad operativa:** Alta. Requiere configurar los tipos de nodos (Master, Core, Task), gestionar actualizaciones del sistema y definir políticas de escalado.
* **Seguridad:** Utiliza Security Groups (firewalls de instancia) de EC2 y roles de IAM específicos (Service Role y EC2 Instance Profile). Soporta integración con AWS Lake Formation.

### 5. Límites y Cuotas Principales
* El tamaño del clúster está directamente limitado por las cuotas de instancias EC2 que tenga la cuenta de AWS en esa región (ej. límite de vCPUs concurrentes).
* Tiempo de arranque del clúster: Suele tardar entre 5 y 10 minutos en estar operativo.

### 6. Estimación de Costes (FinOps)
* **Modelo de precios:** Tarifa por hora de Amazon EC2 (los servidores) + tarifa por hora de Amazon EMR (el software), pagado por segundo.
* **Escenario propuesto:** Un clúster pequeño con 1 nodo Master y 2 nodos Core (tipo m5.xlarge) funcionando ininterrumpidamente durante 1 mes (730 horas).
* **Coste estimado mensual:** ~$420.00 USD.
* **Evidencia:** [Enlace a tu estimación en AWS Pricing Calculator -> URL_CALCULADORA]

---

### Síntesis de la Categoría: Datos y ETL (Trade-offs)

Para la capa de procesamiento y transformación de datos, hemos analizado **AWS Glue** y **Amazon EMR**. La elección entre ambos representa uno de los trade-offs más críticos en arquitecturas de Big Data: **Simplicidad y Agilidad frente a Control y Rendimiento a gran escala.**

Recomendamos **AWS Glue** como la opción predeterminada para el inicio de cualquier proyecto analítico moderno. Al ser un servicio *Serverless*, reduce drásticamente la complejidad operativa, permitiendo que el equipo se centre en escribir la lógica de transformación de datos en lugar de gestionar servidores. Es ideal para trabajos transitorios y esporádicos, ya que solo se paga por el tiempo exacto de ejecución.

Por otro lado, **Amazon EMR** se posiciona como la elección necesaria cuando el volumen de datos alcanza el nivel de petabytes, las cargas de trabajo requieren ejecución ininterrumpida (24/7) o el equipo necesita acceso a nivel de sistema operativo para optimizar el rendimiento del motor (como Apache Spark). Aunque exige un mayor esfuerzo de administración, EMR permite estrategias de reducción de costes agresivas, como la incorporación de instancias EC2 *Spot*, haciéndolo mucho más rentable que Glue a largo plazo para procesos continuos masivos.
