# Categoría: Red de Entrega y Contenidos

## <img src="img/CloudFront.png" width="30" align="absmiddle"> Amazon CloudFront

### 1. Descripción y funcionalidad
Es una red de entrega de datos de contenido (CDN) que distribuye los archivos web a gran velocidad. Utiliza la red global **Edge Location** para cachear el contenido cerca de los usuarios finales, reduciendo drásticamente la latencia y el tiempo de carga.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** Distribución de baja latencia y alta disponibilidad.
* **Caso de uso 1:** Aceleración de carga de sitios web estáticos almacenados en S3 (imágenes, CSS, JS).
* **Caso de uso 2:** Transmisión de video en streaming minimizando el buffering.

### 3. Trade-offs y alternativas
* **Alternativas:** Servir directamente desde un bucket de S3.
* **Trade-offs:** A diferencia de S3 directo, CloudFront mejora la velocidad global y reduce los costes de salida, pero introduce la complejidad de gestionar la **invalidación de caché** cuando el contenido cambia. 
* **Conclusión:** Mientras que el Servidor de Origen obliga a una latencia alta para usuarios internacionales, CloudFront elimina este cuello de botella mediante el almacenamiento en caché.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Gestionado (Serverless). Requiere configurar el origen y los comportamientos del caché.
* **Escalabilidad:** Automática. Capaz de gestionar picos de tráfico masivos de millones de peticiones.
* **Seguridad:** Protección contra ataques DDoS integrada (**AWS Shield**) y soporte para HTTPS/TLS.

### 5. Límites y cuotas principales
* **Solicitudes por segundo (RPS):** Límite de 10,000 (ajustable bajo solicitud).
* **Tamaño de archivo:** 30 GB por objeto.
* **Certificados SSL:** Límite por cuenta (puede ser un cuello de botella con cientos de dominios).

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Pago por GB transferido + número de solicitudes HTTP.
* **Escenario propuesto:** 500 GB de tráfico mensual en Europa.
* **Coste estimado:** **42.50 USD** mensuales.



\### 6. Estimación de Costes (FinOps)

\* \*\*Modelo:\*\* Pago por GB transferido + número de solicitudes HTTP.

\* \*\*Escenario (Europa):\*\* 500 GB x 0.085$ = \*\*42.50$ USD estimados.\*\*


