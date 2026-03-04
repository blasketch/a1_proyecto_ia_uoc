# Categoría: Seguridad, Identidad y Redes

## <img src="img/IAM.png" width="30" align="absmiddle"> AWS IAM (Identity and Access Management)

**Responsable:** Antonio
**Categoría en el Pipeline:** Seguridad e Identidad (Gobernanza)

### 1. Descripción y funcionalidad
Es el servicio central para controlar quién puede acceder a qué recursos en AWS. Permite gestionar Usuarios, Grupos, Roles y sus permisos mediante políticas en formato **JSON**.

### 2. Patrones y casos de uso idóneos
* **Principio de menor privilegio:** Crear credenciales específicas para desarrolladores evitando el uso de la cuenta "Root".
* **Roles para servicios:** Configuración de permisos para que servicios (ej. Lambda) interactúen entre sí sin usar claves estáticas.
* **Federación:** Permitir que usuarios externos (Google, Azure AD) accedan a AWS mediante identidades existentes.

### 3. Trade-offs y alternativas
* **Alternativa:** **AWS IAM Identity Center** (para SSO empresarial) o ABAC.
* **Trade-offs:** IAM es el estándar para control granular técnico, pero requiere una gestión manual cuidadosa. Para entornos multi-cuenta, Identity Center es superior al centralizar la gobernanza.

### 4. Operación y auditoría
* **Propagación:** Los cambios en las políticas son globales pero la propagación no es instantánea.
* **Auditoría:** Uso de **IAM Access Analyzer** para identificar recursos con acceso público o externo no deseado.

---

## <img src="img/VPC.png" width="30" align="absmiddle"> Amazon VPC (Virtual Private Cloud)

**Categoría en el Pipeline:** Redes (Networking)

### 1. Descripción y funcionalidad
Permite aprovisionar una sección lógicamente aislada de la nube de AWS donde se lanzan recursos en una red virtual definida por el usuario, con control total sobre subredes y tablas de rutas.

### 2. Patrones y casos de uso idóneos
* **Aislamiento de infraestructura:** Alojamiento de bases de datos en **Subredes Privadas** sin exposición directa a internet.
* **Conectividad privada:** Uso de **VPC Endpoints** para conectar de forma segura con servicios como S3 o DynamoDB sin navegar por la red pública.

### 3. Trade-offs y seguridad
* **Alternativa:** Uso de VPC Peering para conexiones punto a punto vs. Transit Gateway para redes complejas.
* **Seguridad:** Implementación de seguridad en capas mediante **Security Groups** (firewall a nivel de instancia) y **Network ACLs** (firewall a nivel de subred).

### 4. Estimación de costes (FinOps)
* **Modelo de precios:** La VPC básica no tiene coste. Se factura por el uso de NAT Gateways, VPNs y transferencias de datos entre zonas de disponibilidad.
* **Coste estimado:** Configuración estándar con tráfico moderado: **~35.00 - 50.00 USD/mes**.

### Síntesis y trade-offs de la categoría
La gestión de seguridad y red es el pilar de la infraestructura. Mientras que **IAM** garantiza que solo las entidades autorizadas operen en el entorno, la **VPC** asegura que el tráfico fluya por canales aislados. El trade-off principal es la **complejidad operativa**: una configuración robusta de red requiere conocimientos avanzados, pero es indispensable para mitigar riesgos de exposición de datos..


