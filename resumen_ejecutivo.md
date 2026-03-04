# Resumen Ejecutivo — Arquitectura Global y Estrategia FinOps

## 1. Objetivo

Este documento presenta una visión global del proyecto de análisis de servicios gestionados en AWS. El objetivo es integrar las distintas categorías analizadas por el equipo dentro de una arquitectura común y ofrecer una estimación aproximada de costes siguiendo un enfoque FinOps.

De esta forma, el documento permite entender no solo qué servicios se han analizado, sino también cómo se combinan dentro de una arquitectura realista y qué impacto tienen a nivel técnico y económico.

---

## 2. Caso de uso de referencia

Para contextualizar el análisis se propone una arquitectura de **Data Lake analítico en AWS**.

En este escenario, los datos se recopilan, se almacenan en un repositorio central y posteriormente se procesan para obtener información útil para análisis y toma de decisiones.

El flujo general sería:

- Ingesta de datos mediante servicios de cómputo.
- Almacenamiento centralizado en **Amazon S3**, que actúa como Data Lake.
- Procesamiento y transformación de datos mediante herramientas de ETL y Big Data.
- Generación de datasets listos para su consumo analítico.

Esta arquitectura combina servicios **Serverless** con servicios de infraestructura gestionada, permitiendo equilibrar simplicidad operativa, escalabilidad y control técnico.

---

## 3. Diagrama de arquitectura

![Diagrama global](img/diagrama_global.png)

El diagrama muestra cómo se integran los servicios analizados por el equipo dentro de una arquitectura completa:

- **AWS Lambda** para procesamientos automáticos y cargas intermitentes.
- **Amazon EC2** como infraestructura de cómputo cuando se requiere mayor control.
- **Amazon S3** como repositorio central del Data Lake.
- **AWS Glue** para procesos ETL y catalogación de datos.
- **Amazon EMR** para procesamiento distribuido de grandes volúmenes de datos.
- **Amazon CloudFront** para mejorar la entrega de contenido y reducir la latencia global.
- **Amazon VPC** para aislar la infraestructura dentro de una red privada y segura.
- **AWS IAM** para gestionar identidades y permisos dentro del entorno AWS.

De esta manera se puede observar cómo las decisiones técnicas de cada categoría se combinan para construir una arquitectura completa.

---

## 4. Presupuesto global consolidado (FinOps)

El siguiente presupuesto consolida las estimaciones aproximadas obtenidas a partir de los análisis individuales realizados por cada miembro del equipo.

| Servicio | Categoría | Coste mensual (USD) |
|--------|--------|--------|
| AWS Lambda | Computación Serverless | 1.03 |
| Amazon EC2 | Computación IaaS | 8.32 |
| AWS Glue | ETL gestionado | 132.00 |
| Amazon EMR | Procesamiento Big Data | 105.12 |
| Amazon CloudFront | Red de entrega de contenido | 42.50 |
| Amazon VPC | Networking | ~40.00 |
| AWS IAM | Seguridad e identidad | 0 |

**Coste total estimado: ~330 USD/mes**

Las estimaciones se expresan en **USD**, ya que es la moneda utilizada por la AWS Pricing Calculator.

Este presupuesto representa una aproximación basada en los escenarios planteados en cada análisis individual y se actualizará si se modifican los supuestos de uso.

---

## 5. Estrategia FinOps y optimización de costes

Desde una perspectiva FinOps, la arquitectura permite aplicar varias estrategias para optimizar costes:

- Uso de **Savings Plans o instancias reservadas** para cargas estables en EC2.
- Ajuste de tamaño de clústeres EMR para evitar sobredimensionamiento.
- Uso de **CloudFront** para optimizar el tráfico y reducir costes de transferencia.
- Aplicación de políticas de almacenamiento en **S3** para mover datos antiguos a capas más económicas.
- Uso de servicios **Serverless** cuando la carga de trabajo es variable.

Estas prácticas permiten mejorar la eficiencia económica sin comprometer la escalabilidad de la arquitectura.

---

## 6. Conclusión global y trade-offs

El diseño de arquitecturas en AWS implica equilibrar diferentes factores como coste, escalabilidad y complejidad operativa.

En este proyecto se observa un claro equilibrio entre:

- **Simplicidad operativa** mediante servicios Serverless como Lambda o Glue.
- **Control y flexibilidad** mediante servicios de infraestructura como EC2 o EMR.

Además, servicios como **CloudFront**, **VPC** e **IAM** añaden capas fundamentales de rendimiento, red y seguridad.

La arquitectura resultante permite visualizar cómo cada decisión técnica impacta tanto en el funcionamiento del sistema como en su coste mensual, facilitando así la evaluación de diferentes alternativas dentro del diseño de infraestructuras cloud.