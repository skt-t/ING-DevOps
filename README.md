# 🚀 Evaluación Parcial 2 - Arquitectura de Microservicios y DevOps

## 📖 Descripción del Proyecto
Este proyecto implementa una arquitectura basada en microservicios gestionada bajo un enfoque de **Monorepo**. El ecosistema está diseñado para el procesamiento y gestión de transacciones comerciales, separando lógicamente los dominios en dos servicios backend independientes (Ventas y Despachos), los cuales son consumidos por una interfaz de usuario centralizada. Toda la infraestructura se encuentra contenerizada y administrada mediante prácticas de Integración y Despliegue Continuo (CI/CD), garantizando la calidad del código, la seguridad y la automatización del flujo de entrega.

---

## 📂 Estructura del Repositorio

La arquitectura del proyecto en el repositorio se distribuye de la siguiente manera:

```text
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
└── 📄 docker-compose.yml
🛠️ Tecnologías Utilizadas
Backend: Java 17, Spring Boot, Maven

Base de Datos: MySQL

Frontend: Interfaz de usuario (Web)

Contenerización y Orquestación Local: Docker, Docker Compose V2

CI/CD Pipeline: GitHub Actions

Container Registry: Docker Hub

🚀 Instrucciones de Despliegue Local
Para levantar todo el entorno de desarrollo de forma local y simultánea, asegúrese de tener el demonio de Docker en ejecución. Navegue hasta la raíz del repositorio clonado:

Bash
cd <ruta-del-repositorio>
Ejecute el siguiente comando para construir las imágenes a partir de los Dockerfile de cada directorio y levantar la base de datos, los backends y el frontend en segundo plano:

Bash
docker compose up -d --build
Para detener el ecosistema y limpiar los contenedores, utilice:

Bash
docker compose down
⚙️ Explicación del Pipeline CI/CD
El proyecto cuenta con un flujo automatizado configurado en GitHub Actions (.github/workflows/deploy.yml). Este pipeline se ejecuta bajo un esquema estricto de validación y consta de las siguientes etapas:

Testing Automático: Ejecuta la suite de pruebas unitarias implementadas con JUnit en ambos servicios backend para validar la integridad de la lógica de negocio antes de cualquier compilación, apoyándose en una base de datos efímera.

Seguridad y Gobernanza: Realiza un análisis estático de dependencias utilizando Snyk. Si se detectan vulnerabilidades críticas o altas, el sistema genera un reporte detallado (modo auditoría) para su mitigación, cumpliendo con los estándares de seguridad shift-left.

Build (Construcción): Una vez aprobadas las validaciones anteriores, el flujo procesa de manera independiente cada Dockerfile para empaquetar los microservicios y el frontend en imágenes Docker optimizadas.

Push a Registry: Autentica de forma segura y realiza un push automatizado de los artefactos construidos hacia nuestro repositorio centralizado en Docker Hub, dejándolos listos para un eventual despliegue en producción.

📊 Trazabilidad y Evidencia
A continuación, se documentan las pruebas de la correcta ejecución de nuestras estrategias DevOps:

Ejecución Exitosa del Pipeline en GitHub Actions
![Evidencia GitHub Actions]

<img width="1898" height="739" alt="image1" src="https://github.com/user-attachments/assets/00a3fee4-a883-443a-8c8e-c95b07fc24aa" />

Imágenes Construidas y Publicadas en Docker Hub
![Evidencia Docker Hub]

<img width="1849" height="537" alt="image2" src="https://github.com/user-attachments/assets/99005c89-a806-4ca1-906f-89668d2db06f" />

Reporte de Vulnerabilidades y Gobernanza (Snyk)
![Evidencia Snyk]
![Imagen de prueba: snyk impide subir imagen con problemas de seguridad]
<img width="1878" height="742" alt="image4" src="https://github.com/user-attachments/assets/be82e27e-9cc2-4775-8ef9-a26576fc5eb6" />

![Imagen de prueba: snyk permite subir la imagen]
<img width="1898" height="877" alt="image3" src="https://github.com/user-attachments/assets/88b3170f-3fa2-4ec1-8bac-e9aa92493e32" />

![Imagen de prueba: observacion de ambas pipelines]
<img width="1452" height="386" alt="image4" src="https://github.com/user-attachments/assets/ae6b0f21-8ed8-4e1d-b7a1-1bd93d0fa52c" />


🤖 Declaración de Uso de Herramientas de IA
Por medio del presente párrafo, se declara de manera formal que se utilizaron herramientas de Inteligencia Artificial (IA) generativa como apoyo exclusivo para la estructuración, formato Markdown y redacción técnica de este documento README.md. Este uso se ciñe estrictamente a las labores de documentación y generación de diagramas conceptuales, cumpliendo en su totalidad con las normativas éticas y académicas establecidas en la rúbrica del curso.

🧠 Reflexión Crítica y Conclusiones Individuales
Cory Leveke
Con este proyecto aprendi a trabajar en un entorno donde el CI/CD se integra de forma eficiente, a pesar de las dificultades que existen en entornos donde muchas personas colaboran, la division por branch de feature, fix y choir simplifica mucho el trabajo en equipo.
Tambien aprendi lo eficiente que puede ser una pipeline en github actions, subir de forma automatica una imagen simplifica y agiliza mucho el trabajo de despliegue, y con la implementacion de snyk, la segurirdad va sobrada. claro que configurar el sistema es complejo, pero una vez listo, es un peso menos de encima.

Allan Nuñez
[Cada integrante redactará su conclusión aquí de forma manual, ya que está prohibido el uso de IA para esta sección según la rúbrica]

Benjamín Ruz
[Cada integrante redactará su conclusión aquí de forma manual, ya que está prohibido el uso de IA para esta sección según la rúbrica]
