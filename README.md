# Reto 1. Servicios Gestionados de AWS

Bienvenidos al repositorio central de nuestro proyecto de diseño y evaluación de arquitecturas en **Amazon Web Services (AWS)**.
El objetivo de este proyecto es analizar diferentes capas de una arquitectura Cloud moderna, comparando al menos dos servicios análogos por categoría. Nuestro enfoque no solo describe la tecnología, sino que evalúa críticamente los **trade-offs** técnicos y de negocio, la latencia, la carga operativa y el coste de cada alternativa.

---

## 1. Categorías analizadas

| Categoría | Servicios comparados | Responsable | Análisis |
|---|---|---|---|
| Computación y Serverless | `AWS Lambda` vs `Amazon EC2` | Adrián Blasco Lozano | [Ver análisis](./computacion_y_serverless.md) |
| Datos y ETL | `AWS Glue` vs `Amazon EMR` | Adrián Blasco Lozano | [Ver análisis](./datos_y_etl.md) |
| Almacenamiento y Bases de Datos | `Amazon S3` vs `Amazon DynamoDB` | Enric Gil Baquero | [Ver análisis](./almacenamiento_bd.md) |
| IA y Machine Learning | `Amazon SageMaker` vs `Amazon Rekognition` | Enric Gil Baquero | [Ver análisis](./ia_y_ml.md) |
| Red de entrega y contenidos | `Amazon CloudFront` vs `Servidor de Origen (S3)` | Antonio Sala Llaudis | [Ver análisis](./RED_ENTREGA.md) |
| Identidad y Seguridad | `AWS IAM` vs `Amazon VPC` | Antonio Sala Llaudis | [Ver análisis](./SEGURIDAD_RED.md) |

---

## 2. Documentación adicional

| Documento | Responsable | Enlace |
|---|---|---|
| Resumen ejecutivo consolidado | Hugo Romero Casado | [Ver resumen](./resumen_ejecutivo.md) |

---

## 3. Estructura del repositorio
```text
📦 proyecto-aws-arquitectura
 ┣ 📂 img/                              # Logos oficiales de AWS y diagramas
 ┣ 📜 README.md                         # Documentación principal (este archivo)
 ┣ 📜 resumen_ejecutivo.md              # Resumen ejecutivo consolidado
 ┣ 📜 computacion_y_serverless.md       # Computación y Serverless
 ┣ 📜 datos_y_etl.md                    # Datos y ETL
 ┣ 📜 almacenamiento_bd.md              # Almacenamiento y Bases de Datos
 ┣ 📜 ia_y_ml.md                        # IA y Machine Learning
 ┣ 📜 RED_ENTREGA.md                    # Red de Entrega y Contenidos
 ┗ 📜 SEGURIDAD_RED.md                  # Identidad y Seguridad
```
