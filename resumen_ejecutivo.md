# Resumen Ejecutivo — Arquitectura Global y FinOps

## 1. Objetivo del documento
Este documento consolida la visión global del proyecto, integrando los servicios gestionados de AWS analizados por el equipo en una arquitectura coherente y aportando una estimación consolidada de costes (FinOps).

## 2. Caso de uso de referencia
Se plantea una arquitectura de **Data Lake analítico en AWS**, donde los datos son ingeridos, almacenados, transformados y procesados mediante servicios gestionados, combinando enfoques Serverless e IaaS según necesidades.

## 3. Diagrama de arquitectura
*(Pendiente de integrar imagen en carpeta img/diagrama_global.png)*

## 4. Presupuesto global consolidado

| Servicio | Categoría | Coste mensual (USD) |
|----------|----------|---------------------|
| AWS Lambda | Computación Serverless | 1,03 |
| Amazon EC2 | Computación IaaS | 8,32 |
| AWS Glue | ETL gestionado | 132,00 |
| Amazon EMR | Procesamiento Big Data | 105,12 |

**Total estimado parcial: 246,47 USD/mes**

> Nota: El total se ampliará conforme se integren el resto de categorías (Almacenamiento, IA/ML, Redes y Seguridad).

## 5. Estrategia FinOps y optimización
- Aplicar Savings Plans para cargas estables en EC2.
- Ajustar tamaño de instancias (rightsizing) en EMR y EC2.
- Aplicar políticas de ciclo de vida y almacenamiento optimizado en S3.

## 6. Conclusión global
La arquitectura refleja el principal trade-off en AWS entre simplicidad operativa (Serverless) y control total (IaaS/cluster). Las decisiones deben equilibrar coste, escalabilidad y carga operativa según el patrón de uso.