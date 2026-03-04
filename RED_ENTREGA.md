\# Red de Entrega y Contenidos (Content Delivery)



\## 1. Amazon CloudFront

!\[CloudFront](./img/CloudFront.png)



\*\*Responsable:\*\* Antonio

\*\*Categoría en el Pipeline:\*\* Entrega de Contenido



\### 1. Descripción y Funcionalidad

Es una red de entrega de datos de contenido que distribuye los archivos web a gran velocidad. Utiliza la red global \*\*Edge Location\*\* para cachear el contenido cerca de los usuarios finales, reduciendo drásticamente la latencia.



\### 2. Patrones y Casos de Uso Idóneos

\* \*\*Patrón principal:\*\* Distribución de baja latencia y alta disponibilidad.

\* \*\*Caso de uso 1:\*\* Aceleración de carga de sitios web estáticos almacenados en S3 (imágenes, CSS, JS).

\* \*\*Caso de uso 2:\*\* Transmisión de video en streaming minimizando el buffering.



\### 3. Trade-offs y Alternativas

\* \*\*Alternativas:\*\* Servir directamente desde un bucket de S3.

\* \*\*Trade-offs:\*\* A diferencia de S3 directo, CloudFront mejora la velocidad global y reduce los costes de salida, pero introduce la complejidad de gestionar la \*\*invalidación de caché\*\* cuando el contenido cambia. En conlusion, mientras que el Servidor de Origen obliga a una latencia alta para usuarios internacionales (ej. un usuario en Japón accediendo a una región en Virginia), CloudFront elimina este cuello de botella mediante el almacenamiento en caché en Edge Locations. La decisión de usar CloudFront se justifica por la mejora en el SEO y la reducción drástica del tiempo de carga



\### 4. Operación, Escalabilidad y Seguridad

\* \*\*Operación:\*\* Gestionado (Serverless). Requiere configurar el origen y los comportamientos del caché.

\* \*\*Escalabilidad:\*\* Automática. Capaz de gestionar picos de tráfico masivos de millones de peticiones.

\* \*\*Seguridad:\*\* Protección contra ataques DDoS integrada (\*\*AWS Shield\*\*) y soporte para HTTPS/TLS.



\### 5. Límites y Cuotas Principales

\* \*\*Solicitudes por segundo (RPS):\*\* Límite de 10,000 (ajustable bajo solicitud).

\* \*\*Tamaño de archivo:\*\* 30 GB por objeto.

\* \*\*Certificados SSL:\*\* Límite por cuenta (puede ser un cuello de botella con cientos de dominios).



\### 6. Estimación de Costes (FinOps)

\* \*\*Modelo:\*\* Pago por GB transferido + número de solicitudes HTTP.

\* \*\*Escenario (Europa):\*\* 500 GB x 0.085$ = \*\*42.50$ USD estimados.\*\*

