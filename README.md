🚀 Evaluación Parcial 3 - Observabilidad, Calidad y CI/CD en Microservicios
📖 Descripción del Proyecto
Este proyecto implementa una arquitectura basada en microservicios gestionada bajo un enfoque de Monorepo. El ecosistema está diseñado para el procesamiento y gestión de transacciones comerciales, separando lógicamente los dominios en dos servicios backend independientes (Ventas y Despachos), los cuales son consumidos por una interfaz de usuario centralizada.

Para esta fase, la infraestructura se ha fortalecido integrando prácticas avanzadas de DevOps: despliegue en clústeres de Kubernetes (EKS), observabilidad del tráfico en tiempo real, monitoreo de recursos en la nube y un pipeline de CI/CD estricto que asegura la calidad del código y la seguridad antes de cualquier paso a producción.

📂 Estructura del Repositorio
La arquitectura del proyecto en el repositorio se distribuye de la siguiente manera:
```
Plaintext
📦 monorepo-evaluacion
├── 📁 .github
│   └── 📁 workflows
│       └── 📄 deploy.yml
├── 📁 back-Despachos_SpringBoot
│   └── 📁 Springboot-API-REST-DESPACHO
│       ├── 📁 src
│       ├── 📄 pom.xml
│       └── 📄 Dockerfile
├── 📁 back-Ventas_SpringBoot
│   └── 📁 Springboot-API-REST
│       ├── 📁 src
│       ├── 📄 pom.xml
│       └── 📄 Dockerfile
├── 📁 front_despacho
│   ├── 📁 src
│   ├── 📄 package.json
│   └── 📄 Dockerfile
└── 📁 kubernetes
    └── 📄 despliegue-total.yaml
```
🛠️ Tecnologías Utilizadas
Backend: Java 17, Spring Boot, Maven

Base de Datos: MySQL

Frontend: Interfaz de usuario (Web)

Contenerización y Orquestación: Docker, Kubernetes (AWS EKS)

Observabilidad y Malla de Servicios: Istio, Kiali

Monitoreo y Alertas: AWS CloudWatch, AWS SNS

CI/CD Pipeline: GitHub Actions

Calidad y Seguridad (Shift-Left): SonarCloud, Snyk

⚙️ Explicación del Pipeline CI/CD y Calidad
El proyecto cuenta con un flujo automatizado configurado en GitHub Actions (.github/workflows/deploy.yml). Este pipeline opera como una barrera de calidad estricta (Fail-Fast):

Testing Automático: Ejecuta la suite de pruebas unitarias implementadas con JUnit en los servicios backend.

Aseguramiento de Calidad (SonarCloud): Realiza un escaneo profundo del código para detectar deuda técnica, bugs y vulnerabilidades. Si el código no supera el Quality Gate, el pipeline se interrumpe automáticamente.

Gobernanza (Snyk): Análisis estático de dependencias. Bloquea el flujo si se detectan vulnerabilidades críticas.

Build & Push: Empaqueta los microservicios y publica las imágenes en Docker Hub solo si las fases de calidad y pruebas son exitosas.

📊 Trazabilidad y Evidencia
A continuación, se documentan las pruebas de la correcta ejecución de nuestras estrategias DevOps:

1. Ejecución del Pipeline en GitHub Actions
Validación del flujo automatizado, mostrando la capacidad de detener el despliegue ante fallas de análisis y el éxito tras las correcciones.

2. Análisis de Calidad de Código (SonarCloud)
Evidencia de la integración de SonarCloud en el proyecto para auditar la mantenibilidad, confiabilidad y seguridad del código fuente.

3. Observabilidad de la Malla de Servicios (Kiali)
Visualización en tiempo real del tráfico de red entre los microservicios de despachos, ventas y la base de datos dentro del clúster de Kubernetes, gestionado por Istio.

4. Monitoreo y Alertas Críticas (AWS SNS y CloudWatch)
Configuración de un tópico de notificaciones estándar (SNS) para alertar al equipo de operaciones.

Creación de una alarma en CloudWatch configurada para dispararse y notificar si la utilización de CPU del servidor supera el 80% durante un período sostenido.

🤖 Declaración de Uso de Herramientas de IA
Por medio del presente párrafo, se declara de manera formal que se utilizaron herramientas de Inteligencia Artificial (IA) generativa como apoyo exclusivo para la estructuración, formato Markdown y redacción técnica de este documento README.md. Este uso se ciñe estrictamente a las labores de documentación, cumpliendo en su totalidad con las normativas éticas y académicas establecidas en la rúbrica del curso.

Pruebas de Kiali
<img width="1853" height="660" alt="eva3-devops-2" src="https://github.com/user-attachments/assets/071a456e-bd16-47a2-9784-7de491de9612" />

Pruebas de Notificacion por correo al colapsar
<img width="1859" height="933" alt="eva3-devops" src="https://github.com/user-attachments/assets/406c1be2-6125-45eb-b7b7-cc1fdb486eb0" />

Reglas de la alerta, si supera el 80% envia notificacion
<img width="1455" height="712" alt="eva3-devops-3" src="https://github.com/user-attachments/assets/9ac3c757-f3c5-49ef-8931-af41c6b1fbce" />

Pipeline Existoso
<img width="1856" height="497" alt="eva3-devops-4" src="https://github.com/user-attachments/assets/c2802a77-9504-4635-b73c-456306680ab7" />

### 5. Pruebas de Aceptación (UAT) y Aprobación Manual (Gobernanza)
Para asegurar el cumplimiento de normativas de seguridad y evitar despliegues accidentales (IE13), el pipeline final incorpora dos etapas de control estricto antes del paso a producción:

* **Pruebas de Aceptación:** Se configuró un job (`acceptance-tests`) que valida los criterios mínimos del negocio tras la construcción de las imágenes. Si estas pruebas fallan, el código no avanza.
* **Políticas de Aprobación Manual:** Se implementó un entorno protegido (`production`) mediante las *Environment protection rules* de GitHub. El flujo de despliegue continuo se interrumpe intencionalmente, requiriendo la revisión y aprobación explícita (clic manual) de un administrador del repositorio antes de ejecutar los comandos en el clúster de Kubernetes (EKS).

*Evidencia del pipeline detenido por políticas de seguridad, esperando revisión manual:*
<img width="1428" height="827" alt="imagen-pruebas-2" src="https://github.com/user-attachments/assets/cb8cf30d-b1a5-4e99-907f-67bee38128d9" />


*Evidencia de la aprobación y despliegue final exitoso:*
<img width="1422" height="677" alt="imagen-pruebas-3" src="https://github.com/user-attachments/assets/d6b6164a-e4c1-4c2e-8275-d95fcb29d257" />


