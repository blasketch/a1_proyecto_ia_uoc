# Categoría: [Nombre de la Categoría - Ej: Computación / Almacenamiento / IA]

---

## <img src="URL_DEL_LOGO_A" width="30" align="absmiddle"> [Nombre del Servicio A - Ej: AWS Lambda]

**Categoría en el Pipeline:** [Ej: Procesamiento]

### 1. Descripción y Funcionalidad
[Escribe aquí tu descripción]

### 2. Patrones y Casos de Uso Idóneos
* **Patrón principal:** [Ej: Arquitecturas orientadas a eventos]
* **Caso de uso 1:** [Ej: Procesamiento en tiempo real al subir un archivo]
* **Caso de uso 2:** [Ej: APIs Serverless]

### 3. Latencia y Rendimiento
* **Latencia:** [Ej: Posibles "Cold Starts" (arranques en frío) que añaden milisegundos en la primera ejecución si la función lleva tiempo inactiva.]
* **Rendimiento:** [Ej: Escala el rendimiento automáticamente asignando CPU proporcional a la memoria configurada.]

### 4. Trade-offs y Alternativas (Justificación)
* **Alternativa:** [Ej: Amazon EC2]
* **Trade-offs (Pros/Contras):** [Ej: A diferencia de EC2, Lambda ofrece simplicidad extrema sin servidores, pero sacrifica el control del entorno subyacente y tiene un límite de tiempo de ejecución de 15 minutos.]

### 5. Operación, Escalabilidad y Seguridad
* **Complejidad operativa:** [Ej: Totalmente gestionado (Serverless). No requiere provisionar servidores.]
* **Escalabilidad:** [Ej: Escala automáticamente por cada evento concurrente.]
* **Seguridad:** [Ej: Integración nativa con AWS IAM para roles de ejecución. Soporta VPC.]

### 6. Límites y Cuotas Principales
* [Ej: Tiempo máximo de ejecución: 15 minutos]
* [Ej: Memoria máxima asignable: 10 GB]

### 7. Estimación de Costes (FinOps)
* **Modelo de precios:** [Ej: Pago por milisegundo de ejecución y número de peticiones]
* **Escenario propuesto:** [Ej: 1 millón de invocaciones al mes, 100ms duración, 512MB RAM]
* **Coste estimado mensual:** [Ej: ~$0.83 USD]
* **Evidencia:** [Enlace a tu estimación pública en AWS Pricing Calculator]

---

## <img src="URL_DEL_LOGO_B" width="30" align="absmiddle"> [Nombre del Servicio B - Ej: Amazon EC2]

**Categoría en el Pipeline:** [Ej: Procesamiento]

### 1. Descripción y Funcionalidad
[Escribe aquí tu descripción]

### 2. Patrones y Casos de Uso Idóneos
* **Patrón principal:** [Ej: Cargas de trabajo ininterrumpidas 24/7]
* **Caso de uso 1:** [Ej: Aplicaciones monolíticas tradicionales (legacy)]
* **Caso de uso 2:** [Ej: Modelos de ML que requieren hardware dedicado]

### 3. Latencia y Rendimiento
* **Latencia:** [Ej: Latencia constante e inmediata, sin arranques en frío.]
* **Rendimiento:** [Ej: Rendimiento dedicado y personalizable según la familia de instancia elegida (optimizada para cómputo, memoria, etc.).]

### 4. Trade-offs y Alternativas (Justificación)
* **Alternativa:** [Ej: AWS Lambda]
* **Trade-offs (Pros/Contras):** [Ej: EC2 ofrece control total y ejecución ilimitada en el tiempo. El trade-off es asumir una alta carga operativa (parches, seguridad, red) y el riesgo de pagar por recursos inactivos.]

### 5. Operación, Escalabilidad y Seguridad
* **Complejidad operativa:** [Ej: Alta (IaaS). Requiere gestionar el sistema operativo, actualizaciones y red.]
* **Escalabilidad:** [Ej: Manual o mediante la configuración de Auto Scaling Groups.]
* **Seguridad:** [Ej: Modelo de responsabilidad compartida. El cliente gestiona el firewall (Security Groups) y el SO.]

### 6. Límites y Cuotas Principales
* [Ej: Límite regional de vCPUs concurrentes por cuenta de AWS]
* [Ej: Requiere paradas programadas para escalar verticalmente el tamaño de la instancia]

### 7. Estimación de Costes (FinOps)
* **Modelo de precios:** [Ej: Pago por hora/segundo de instancia encendida]
* **Escenario propuesto:** [Ej: 1 instancia t3.micro Linux bajo demanda encendida 24/7 (730 horas/mes)]
* **Coste estimado mensual:** [Ej: ~$7.60 USD]
* **Evidencia:** [Enlace a tu estimación pública en AWS Pricing Calculator]

---

## Tabla Comparativa: [Servicio A] vs [Servicio B]

| Característica | [Servicio A - Ej: AWS Lambda] | [Servicio B - Ej: Amazon EC2] |
| :--- | :--- | :--- |
| **Gestión de Infraestructura** | [Ej: Serverless (Ninguna)] | [Ej: IaaS (Total: SO, parches, red)] |
| **Latencia / Rendimiento** | [Ej: Posibles Cold Starts] | [Ej: Latencia constante e inmediata] |
| **Modelo de Pago** | [Ej: Por milisegundo de uso] | [Ej: Por hora/segundo (incluso inactivo)] |
| **Límites Críticos** | [Ej: 15 min de ejecución máximo] | [Ej: Límite regional de vCPUs] |
| **Escalabilidad** | [Ej: Automática por evento] | [Ej: Manual con Auto Scaling Groups] |

---

## Síntesis y Trade-offs de la Categoría

*[Instrucciones para el equipo: Redactad aquí un texto de máximo 500 palabras. Explicad **por qué** se han elegido estos dos servicios análogos para esta categoría y justificad el trade-off principal (ej. Simplicidad vs. Control, Coste vs. Rendimiento). Terminad dando una recomendación clara de en qué escenario es mejor usar cada uno, basándote en criterios técnicos y de negocio.]*

[Escribe aquí tu síntesis...]
