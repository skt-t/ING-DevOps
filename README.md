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
![Evidencia GitHub Actions](https://media.discordapp.net/attachments/1249956660756222063/1507594481174708264/image.png?ex=6a127846&is=6a1126c6&hm=31dfc55783c83362db609c957a53bf20c4cef1b22103fcd789f50e2ccb67eb22&=&format=webp&quality=lossless&width=1872&height=729)

Imágenes Construidas y Publicadas en Docker Hub
![Evidencia Docker Hub](https://cdn.discordapp.com/attachments/1249956660756222063/1507594925917601832/Captura_de_pantalla_20260523_000305.png?ex=6a1278b0&is=6a112730&hm=ede52f7d0e6961403a9bd5b3b4de5efa34225f395b04006579c9509e7fe1b990&)

Reporte de Vulnerabilidades y Gobernanza (Snyk)
![Evidencia Snyk](https://cdn.discordapp.com/attachments/1249956660756222063/1507607607634825266/image.png?ex=6a12847f&is=6a1132ff&hm=55c3af6f223d09e966e176c5f91d57728a1be5060bf0119e95ee399a243379cb&)

🤖 Declaración de Uso de Herramientas de IA
Por medio del presente párrafo, se declara de manera formal que se utilizaron herramientas de Inteligencia Artificial (IA) generativa como apoyo exclusivo para la estructuración, formato Markdown y redacción técnica de este documento README.md. Este uso se ciñe estrictamente a las labores de documentación y generación de diagramas conceptuales, cumpliendo en su totalidad con las normativas éticas y académicas establecidas en la rúbrica del curso.

🧠 Reflexión Crítica y Conclusiones Individuales
Cory Leveke
[Cada integrante redactará su conclusión aquí de forma manual, ya que está prohibido el uso de IA para esta sección según la rúbrica]

Allan Nuñez
[Cada integrante redactará su conclusión aquí de forma manual, ya que está prohibido el uso de IA para esta sección según la rúbrica]

Benjamín Ruz
[Cada integrante redactará su conclusión aquí de forma manual, ya que está prohibido el uso de IA para esta sección según la rúbrica]
