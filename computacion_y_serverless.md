# Categoría: Computación y Serverless

## <img src="img/Lambda.png" width="30" align="absmiddle"> AWS Lambda

### 1. Descripción y funcionalidad
AWS Lambda es un servicio de computación serverless (sin servidor) impulsado por eventos. Permite ejecutar código en lenguajes como Python, Node.js o Java, sin necesidad de aprovisionar ni administrar servidores. AWS se encarga automáticamente de ejecutar y escalar el código con alta disponibilidad en respuesta a desencadenadores (triggers) como peticiones HTTP, cambios en bases de datos o subida de archivos.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** Arquitecturas orientadas a eventos, microservicios y tareas de corta duración.
* **Caso de uso 1:** Procesamiento en tiempo real de archivos subidos a S3, como por ejemplo, redimensionar una imagen automáticamente al momento de subirla.
* **Caso de uso 2:** Creación de APIs serverless altamente escalables en combinación con Amazon API Gateway.

### 3. Latencia y rendimiento
* **Latencia:** Al ser serverless, está sujeto a posibles cold starts o arranques en frío. Si una función lleva un tiempo inactiva, AWS debe asignar los contenedores subyacentes en la primera invocación, lo que puede añadir desde unos milisegundos hasta un par de segundos de latencia.
* **Rendimiento:** Escala el rendimiento automáticamente. Al asignar más memoria RAM a una función, AWS asigna proporcionalmente más potencia de CPU y ancho de banda de red.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Nula. El equipo de desarrollo se desentiende del sistema operativo, los parches y el mantenimiento del hardware.
* **Escalabilidad:** Completamente automática y prácticamente ilimitada. Lambda escala de forma instantánea ejecutando una instancia de la función por cada evento concurrente recibido, sin ninguna intervención manual. El límite predeterminado de 1.000 ejecuciones concurrentes por región es ampliable bajo petición. Para evitar escalados inesperados con impacto económico, es posible configurar un límite de concurrencia reservada por función.
* **Seguridad:** Utiliza roles de ejecución de IAM muy granulares para limitar a qué otros servicios puede acceder el código. Se puede configurar para ejecutarse de forma segura dentro de una VPC privada.

### 5. Límites y cuotas principales
* Tiempo máximo de ejecución: 15 minutos.
* Memoria máxima asignable por función: 10 GB.
* Límite predeterminado de 1.000 ejecuciones concurrentes por región (ampliable bajo petición).

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Pago por número de solicitudes y por duración de la ejecución, medido en milisegundos.
* **Escenario propuesto:** 1 millón de invocaciones al mes. Cada ejecución dura 100 milisegundos y tiene 512 MB de memoria RAM asignada.
* **Coste estimado mensual:** 1,03 USD (Totalmente gratuito si se aplica la capa gratuita de AWS).
* **Evidencia:** https://calculator.aws/#/estimate?id=876ec7332199bbe95c0a753927f7d290c7844e62

### 7. Referencias y Documentación Oficial
* [Documentación oficial de AWS Lambda](https://docs.aws.amazon.com/es_es/lambda/latest/dg/welcome.html)
* [Precios y facturación de AWS Lambda](https://aws.amazon.com/es/lambda/pricing/)

---

## <img src="img/EC2.png" width="30" align="absmiddle"> Amazon EC2 (Elastic Compute Cloud)

### 1. Descripción y funcionalidad
Amazon EC2 proporciona capacidad de computación escalable en la nube mediante un modelo de infraestructura como servicio (IaaS). Permite a los usuarios alquilar máquinas virtuales (instancias) para ejecutar sus propias aplicaciones, ofreciendo un control absoluto y permitiendo elegir el sistema operativo, la CPU, la memoria y el almacenamiento según necesidades específicas.

### 2. Patrones y casos de uso idóneos
* **Patrón principal:** Cargas de trabajo de larga duración ininterrumpidas, aplicaciones heredadas (legacy) y bases de datos personalizadas.
* **Caso de uso 1:** Alojamiento de aplicaciones monolíticas tradicionales que requieren acceso directo y de bajo nivel al sistema operativo.
* **Caso de uso 2:** Modelos de machine learning e inferencia que requieren hardware dedicado corriendo 24/7.

### 3. Latencia y rendimiento
* **Latencia:** Una vez que la instancia EC2 está encendida, la latencia es inmediata y constante. Al estar los recursos dedicados, no existe el problema de los cold starts.
* **Rendimiento:** Totalmente predecible y personalizable. Permite seleccionar familias de instancias optimizadas para computación, memoria, almacenamiento o aceleración gráfica según el cuello de botella de la aplicación.

### 4. Operación, escalabilidad y seguridad
* **Complejidad operativa:** Alta. El cliente gestiona el sistema operativo, aplica los parches de seguridad, configura la red y diseña las estrategias de backup (AMIs).
* **Escalabilidad:** Posible pero de configuración manual. El escalado horizontal se consigue mediante auto scaling groups (ASG), que lanzan o terminan instancias automáticamente en base a métricas de CloudWatch como uso de CPU o tráfico de red. El escalado vertical, en cambio, requiere detener la instancia para cambiar su tipo, lo que implica una breve ventana de inactividad. Ambas estrategias requieren diseño y configuración explícita por parte del equipo.
* **Seguridad:** Modelo de responsabilidad compartida. AWS protege el hardware, pero el cliente debe configurar rigurosamente los security groups y mantener el sistema operativo libre de vulnerabilidades.

### 5. Límites y cuotas principales
* Límite en el número de vCPUs concurrentes que se pueden ejecutar por región en una cuenta de AWS.
* Escalar verticalmente requiere detener e iniciar la instancia, lo que implica breves ventanas de inactividad.

### 6. Estimación de costes (FinOps)
* **Modelo de precios:** Pago por hora o por segundo según el tipo de instancia, con opciones de ahorro.
* **Escenario propuesto:** 1 instancia de propósito general tipo `t3.micro` con Linux, ejecutándose ininterrumpidamente bajo demanda durante 1 mes (730 horas).
* **Coste estimado mensual:** 8,32 USD (sin contar volúmenes de almacenamiento EBS).
* **Evidencia:** https://calculator.aws/#/estimate?id=17fe6504a2425fa3e15442fb9f4d45a196f23993

### 7. Referencias y documentación oficial
* [Documentación Oficial de Amazon EC2](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/concepts.html)
* [Tipos de instancias de EC2](https://aws.amazon.com/es/ec2/instance-types/)

---

## Tabla comparativa: AWS Lambda vs Amazon EC2

| Característica | AWS Lambda (Serverless) | Amazon EC2 (IaaS) |
| :--- | :--- | :--- |
| **Gestión de infraestructura** | Serverless (Mantenimiento nulo del SO y servidores) | IaaS (Requiere gestión total del SO, parches y red) |
| **Latencia / Rendimiento** | Posibles arranques en frío (cold starts) | Latencia inmediata y rendimiento constante 24/7 |
| **Modelo de pago** | Por milisegundo de ejecución (0$ si no se usa) | Por hora o segundo de servidor encendido (incluso inactivo) |
| **Límites críticos** | 15 minutos de tiempo máximo de ejecución | Limitado por las cuotas de vCPUs de la cuenta en la región |
| **Escalabilidad** | Automática e independiente por cada evento | Manual o configurando políticas en auto scaling groups |

---

## Síntesis y trade-offs de la categoría

Para la capa de computación, hemos evaluado **AWS Lambda** y **Amazon EC2**, representando los dos extremos del espectro de gestión de infraestructura. La elección entre ambos representa un trade-off directo entre **simplicidad operativa y agilidad frente a control absoluto del entorno**.

Recomendamos **AWS Lambda** como la opción preferida por defecto para arquitecturas modernas impulsadas por eventos. Al delegar la gestión del servidor, el equipo de desarrollo se libera de la carga operativa (parcheo, escalado) y adopta un modelo de pago estrictamente ligado al uso real. Sus límites técnicos (como el timeout de 15 minutos) actúan como un mecanismo que obliga a diseñar procesos modulares y eficientes. Reduce drásticamente el coste total de propiedad en cargas de trabajo intermitentes o impredecibles.

En contraposición, **Amazon EC2** es indispensable cuando la carga de trabajo requiere superar las limitaciones del mundo serverless. EC2 es la elección técnica correcta para procesos ininterrumpidos, aplicaciones monolíticas heredadas o cuando se necesita acceso de bajo nivel a recursos hardware específicos (como GPUs). El trade-off asumido es un aumento significativo en la responsabilidad de administración, pero se justifica en escenarios de alta demanda constante donde reservar capacidad en EC2 resulta más rentable económicamente que el pago por invocación de Lambda.
