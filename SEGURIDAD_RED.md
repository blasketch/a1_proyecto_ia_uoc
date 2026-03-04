\# Identidad, Seguridad y Redes

&nbsp;	

\## 1. AWS IAM (Identity and Access Management)

!\[IAM](./img/IAM.png)



\*\*Responsable:\*\* Antonio  

\*\*Categoría en el Pipeline:\*\* Seguridad e Identidad (Gobernanza)



\### 1. Descripción y Funcionalidad

Servicio central para controlar quién puede acceder a qué recursos. Gestiona Usuarios, Grupos, Roles y permisos mediante \*\*Políticas JSON\*\*.



\### 2. Patrones y Casos de Uso Idóneos

\* \*\*Principio de menor privilegio:\*\* Credenciales específicas para desarrolladores evitando el uso de "Root".

\* \*\*Roles para servicios:\*\* Ejemplo: Lambda leyendo de S3 sin contraseñas.

\* \*\*Federación:\*\* Acceso para usuarios externos (Google, Azure AD).



\### 3. Trade-offs y Alternativas

\* \*\*Alternativa:\*\* \*\*AWS IAM Identity Center\*\* (SSO empresarial) o \*\*ABAC\*\*.

\* \*\*Trade-offs:\*\* IAM es el estándar granular, pero requiere gestión cuidadosa para evitar brechas de seguridad. 



\### 4. Operación y Auditoría

\* \*\*Propagación:\*\* Los cambios son globales pero no instantáneos.

\* \*\*Auditoría:\*\* Uso de \*\*IAM Access Analyzer\*\* para detectar recursos accesibles desde fuera de la cuenta.



---



\## 2. Amazon VPC (Virtual Private Cloud)

!\[VPC](./img/VPC.png)



\*\*Categoría en el Pipeline:\*\* Redes (Networking)



\### 1. Descripción y Funcionalidad

Aprovisiona una sección aislada de la nube de AWS con control total sobre direccionamiento IP, subredes y tablas de rutas.



\### 2. Patrones y Casos de Uso Idóneos

\* \*\*Aislamiento:\*\* Bases de datos en \*\*Subredes Privadas\*\*.

\* \*\*Conectividad Privada:\*\* Uso de \*\*VPC Endpoints\*\* para conectar con S3/DynamoDB sin salir a internet.



\### 3. Trade-offs y Seguridad

\* \*\*Alternativa:\*\* VPC Peering vs. Transit Gateway.

\* \*\*Seguridad:\*\* Doble capa con \*\*Security Groups\*\* (instancia) y \*\*Network ACLs\*\* (subred).



\### 4. Estimación de Costes (FinOps)

\* \*\*Modelo:\*\* VPC básica gratuita. Costes por NAT Gateways y tráfico entre zonas.

\* \*\*Coste estimado:\*\* ~$35.00 - $50.00 USD/mes.

