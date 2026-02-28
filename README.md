## <img src="URL_DEL_LOGO" width="30" align="absmiddle"> [Nombre del Servicio - Ej: Amazon S3]

**Categoría en el Pipeline:** [Ej: Almacenamiento / Ingesta / Procesamiento / IA]

### 1. Descripción y Funcionalidad
[Escribe aquí tu descripción]

### 2. Patrones y Casos de Uso Idóneos
* **Patrón principal:** [Ej: Almacenamiento masivo de objetos / Streaming en tiempo real]
* **Caso de uso 1:** [Ej: Creación de la capa "Raw" de un Data Lake]
* **Caso de uso 2:** [Ej: Backup y archivado a largo plazo]

### 3. Trade-offs y Alternativas (Justificación)
* **Alternativa:** [Ej: Amazon EBS o Amazon Redshift]
* **Trade-offs (Pros/Contras):** [Ej: A diferencia de EBS, S3 ofrece almacenamiento ilimitado y más barato, pero sacrifica la latencia ultra-baja necesaria para un sistema operativo. Aporta mayor escalabilidad pero no soporta modificaciones de archivos en bloque.]

### 4. Operación, Escalabilidad y Seguridad
* **Complejidad operativa:** [Ej: Totalmente gestionado (Serverless). No requiere provisionar servidores.]
* **Escalabilidad:** [Ej: Escala automáticamente en capacidad de almacenamiento sin intervención manual.]
* **Seguridad:** [Ej: Integración nativa con AWS IAM. Soporta cifrado en reposo (SSE-S3, KMS) y protección contra ransomware con Object Lock.]

### 5. Límites y Cuotas Principales
* [Ej: Tamaño máximo por objeto: 5 TB]
* [Ej: Máximo de 100 buckets por cuenta por defecto (ampliable a 1000)]

### 6. Estimación de Costes (FinOps)
* **Modelo de precios:** [Ej: Pago por GB almacenado/mes + cantidad de solicitudes (PUT/GET)]
* **Escenario propuesto:** [Ej: Almacenar 1 TB de datos en capa Standard durante un mes con 100,000 peticiones GET]
* **Coste estimado mensual:** [Ej: ~$23.50 USD]
* **Evidencia:** [Enlace a tu estimación pública en AWS Pricing Calculator]

---

