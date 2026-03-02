Categoría: Almacenamiento y Bases de Datos

## <img src="./img/S3.png" width="30" align="absmiddle"> Amazon S3 (Simple Storage Service)

### 1. Descripción y funcionalidad
Amazon S3 es un servicio de almacenamiento de objetos que ofrece escalabilidad, disponibilidad de datos, seguridad y rendimiento líderes en la industria. Permite almacenar y proteger cualquier cantidad de datos para una amplia variedad de casos de uso, como sitios web, aplicaciones móviles, copias de seguridad y análisis de *big data*.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** Almacenamiento de datos no estructurados con durabilidad de 99.999999999%.
* **Caso de uso 1:** Creación de un repositorio centralizado para grandes volúmenes de datos brutos y procesados.
* **Caso de uso 2:** Alojamiento de contenido estático y archivos de copia de seguridad (backup) a largo plazo.

### 3. Latencia y rendimiento
* **Latencia:** Milisegundos para el acceso al primer byte. Está diseñado para ofrecer una latencia baja y predecible.
* **Rendimiento:** Escala de manera automática para manejar miles de transacciones por segundo, permitiendo el acceso concurrente masivo a los objetos almacenados.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Baja. Es un servicio gestionado donde AWS se encarga de la replicación de datos entre múltiples Zonas de Disponibilidad de forma transparente.
* **Escalabilidad:** Prácticamente ilimitada. El almacenamiento se ajusta elásticamente al volumen de datos sin necesidad de aprovisionamiento previo.
* **Seguridad:** Soporta cifrado del lado del servidor, control de acceso mediante S3 Bucket Policies y roles de IAM, y funcionalidades de bloqueo de acceso público.

### 5. Límites y cuotas principales
* Tamaño máximo de un solo objeto: 5 TB.
* Límite predeterminado de 100 buckets por cuenta (ampliable bajo petición).
* Tasa de peticiones por prefijo: 3.500 PUT y 5.500 GET por segundo.

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Pago por GB almacenado al mes y por volumen de peticiones. El coste se optimiza mediante la selección de la **Clase de Almacenamiento (Storage Class)** adecuada.
* **Escenario propuesto:** Almacenamiento de 500 GB de datos. Se utiliza la categoría **S3 Standard** para la ingesta activa y **S3 Glacier Instant Retrieval** para el archivado histórico, permitiendo un ahorro significativo en el almacenamiento de larga duración con recuperación inmediata.
* **Coste estimado mensual:** 12.04 USD.
* **Evidencia:** https://calculator.aws/#/estimate?id=737658b6cf47179caf7d2d78499f521a7bf31cd7

### 7. Referencias y Documentación Oficial
* [Documentación oficial de Amazon S3](https://docs.aws.amazon.com/s3/)
* [Guía de clases de almacenamiento de S3](https://aws.amazon.com/s3/storage-classes/)

## <img src="./img/DynamoDB.png" width="30" align="absmiddle"> Amazon DynamoDB

### 1. Descripción y funcionalidad
Amazon DynamoDB es una base de datos de clave-valor y documentos NoSQL totalmente gestionada y serverless. Proporciona un rendimiento rápido con escalabilidad automática, eliminando la necesidad de administrar clústeres, parches o hardware subyacente.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** Almacenamiento de datos semiestructurados que requieren alta frecuencia de lectura/escritura y latencia constante.
* **Caso de uso 1:** Aplicaciones de alta concurrencia que necesitan respuestas en milisegundos de un solo dígito (perfiles de usuario, carritos de compra).
* **Caso de uso 2:** Registro de estados y metadatos operativos en arquitecturas de microservicios y aplicaciones impulsadas por eventos.

### 3. Latencia y rendimiento
* **Latencia:** Ofrece latencias de lectura y escritura extremadamente bajas (inferiores a 10ms) de forma consistente, independientemente del volumen de datos.
* **Rendimiento:** Altamente escalable. Utiliza particionamiento automático para distribuir los datos y el tráfico, manteniendo un rendimiento lineal.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Muy baja. Al ser un servicio serverless, AWS gestiona la alta disponibilidad, la replicación y la seguridad del motor de base de datos.
* **Escalabilidad:** Totalmente elástica. Puede gestionar picos de tráfico repentinos sin intervención manual mediante sus modos de capacidad automática.
* **Seguridad:** Cifrado en reposo por defecto. Integración con IAM para acceso granular a nivel de tabla, atributo o ítem.

### 5. Límites y cuotas principales
* Tamaño máximo de un ítem (fila): 400 KB incluyendo nombres de atributos.
* Límites de transacciones por segundo (TPS) condicionados por las cuotas regionales de la cuenta.

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Basado en el modo de capacidad seleccionado: **Provisioned** (capacidad fija) o **On-Demand** (pago por petición).
* **Escenario propuesto:** Uso del modo **On-Demand** para procesar 1 millón de lecturas/escrituras mensuales. Esta categoría es ideal para cargas de trabajo variables.
* **Coste estimado mensual:** 5.02 USD.
* **Evidencia:** https://calculator.aws/#/estimate?id=45ca3b09ff7bc25441f19d545603caac2ff9205f

### 7. Referencias y documentación oficial
* [Documentación Oficial de Amazon DynamoDB](https://docs.aws.amazon.com/dynamodb/)
* [Modos de capacidad en DynamoDB](https://aws.amazon.com/dynamodb/pricing/)

---

### Tabla comparativa: Amazon S3 vs Amazon DynamoDB

| Característica | Amazon S3 (Objeto) | Amazon DynamoDB (NoSQL) |
| :--- | :--- | :--- |
| **Tipo de servicio** | Almacenamiento de archivos/objetos | Base de datos clave-valor |
| **Estructura de datos** | No estructurados (Blobs) | Semiestructurados (JSON) |
| **Latencia de acceso** | Decenas de milisegundos | Milisegundos de un solo dígito |
| **Escalabilidad** | Ilimitada por volumen de datos | Elástica por rendimiento (TPS) |
| **Categoría de Precio** | Basada en Clases de Almacenamiento | Basada en Modos de Capacidad |

### Síntesis y trade-offs de la categoría

Para la capa de persistencia y gestión de datos, hemos analizado **S3** y **DynamoDB**. La elección entre ambos representa un trade-off fundamental entre **volumen y variedad vs velocidad y estructura**.

Amazon S3 se establece como la opción preferente para el almacenamiento de gran volumen. Su ventaja principal es el coste por GB, optimizado mediante el uso de clases de almacenamiento. La elección estratégica de S3 Standard permite un procesamiento inmediato, mientras que la transición a Glacier mediante políticas de ciclo de vida garantiza la durabilidad a largo plazo con un impacto económico mínimo. El trade-off asumido es la **latencia de acceso vs la ausencia de indexación nativa** sobre el contenido.

Por el contrario, **DynamoDB** es la pieza clave para la agilidad operativa y el acceso de baja latencia. Al ser un servicio serverless, elimina la complejidad de administrar clústeres, pero impone restricciones de tamaño (400KB por registro). El trade-off reside en el **coste de transacción vs la flexibilidad**. En cuanto a la facturación, seleccionar el modo On-Demand es la opción más rentable para proyectos con picos variables de tráfico, ya que evita el pago de capacidad infrautilizada. DynamoDB compensa la falta de estructura de S3 aportando acceso indexado y consultas de baja latencia sobre datos estructurados.

Normalmente se utiliza una estrategia híbrida que permite que el sistema pague solo por lo que usa. **S3** actúa como el sistema de registro histórico (persistencia), mientras que **DynamoDB** funciona como el motor de estado y búsqueda rápida (operación). Integrar ambos servicios permite responder en milisegundos ante eventos críticos sin renunciar a la persistencia de un volumen de datos masivo.