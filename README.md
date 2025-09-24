# Desafío Técnico de Backend - Upay

Bienvenido/a al desafío técnico de Upay. Esta prueba está diseñada para evaluar tus habilidades en el desarrollo de APIs REST y tu familiaridad con las buenas prácticas de la industria. Te animamos a tomarte tu tiempo, escribir código limpio y bien documentado, y a pensar en la robustez y escalabilidad de tu solución.

---

### **Objetivo del Desafío**

El objetivo es desarrollar una API REST funcional en **Java con Spring Boot** que gestione el ciclo de vida básico de los usuarios y operaciones de cálculo, además de registrar un historial de actividad. La solución completa debe ser desplegable fácilmente usando Docker.

---

### **Requisitos Funcionales**

Tu API debe incluir las siguientes funcionalidades:

1.  **Gestión de Usuarios:**
    * `POST /api/v1/auth/signup`: Registro de nuevos usuarios.
    * `POST /api/v1/auth/login`: Autenticación de usuarios. Debe retornar un token de acceso (JWT o similar) para que el usuario pueda interactuar con los endpoints protegidos.
    * `POST /api/v1/auth/logout`: Cierre de sesión del usuario.

2.  **Operación de Cálculo:**
    * `POST /api/v1/calculator/sum`: Suma dos números.
    * **Requerimiento Clave**: Este endpoint **solo** debe ser accesible para usuarios autenticados.

3.  **Historial de Actividad:**
    * `GET /api/v1/audit/history`: Retorna el historial de todos los llamados a todos los endpoints.
    * **Requerimiento Clave**: La respuesta debe ser un JSON, con **paginación** (`page` y `size`) para manejar grandes volúmenes de datos.
    * **Almacenamiento**: El historial y la información de los usuarios deben persistir en una base de datos **PostgreSQL**.

---

### **Requisitos Técnicos Adicionales**

* **Manejo de Errores**: Incluir un manejo de errores robusto. Se esperan mensajes y descripciones claras para los errores de la serie `4xx` (ej. `401 Unauthorized`, `403 Forbidden`, `400 Bad Request`).
* **Contenedores**:
    * La API debe ser desplegable en un **contenedor Docker**.
    * La base de datos PostgreSQL debe correr en un contenedor Docker.
    * **Recomendación**: Usa `docker-compose` para orquestar ambos servicios (`API` y `PostgreSQL`) de forma sencilla.
* **Documentación de la API**:
    * Proporciona una **Postman Collection** o usa **Swagger (OpenAPI)** para que podamos probar la API fácilmente. Esto es un requisito obligatorio.

---

### **Entrega del Desafío**

1.  Crea un **repositorio público** en GitHub.
2.  El repositorio debe contener todo el código fuente de tu solución.
3.  Incluye un archivo `README.md` detallado con las siguientes instrucciones:
    * **Instalación y Despliegue**: Pasos claros para clonar el repositorio y desplegar el servicio (ej. `docker-compose up`).
    * **Uso de la API**: Instrucciones sobre cómo consumir los endpoints, incluyendo la autenticación y el uso del token de acceso.
    * **Estructura del Proyecto**: Una breve descripción de la arquitectura y el diseño que utilizaste.

---

### **Bonus Tracks (Desafíos Adicionales)**

Estos puntos no son obligatorios para completar el desafío, pero nos ayudarán a entender tu potencial y la forma en que resuelves problemas complejos. Si te animas a implementar alguno, ¡documenta tu decisión en el `README`!

1.  **Mensajería Asíncrona (Kafka)**: Implementa un mecanismo para registrar el historial de auditoría de forma asíncrona. En lugar de escribir directamente en la base de datos dentro del flujo de la API, envía un mensaje a un *topic* de Kafka y haz que un servicio independiente consuma y persista esos eventos. Esto demuestra tu conocimiento de sistemas distribuidos y del **Patrón Outbox**.

2.  **Tests de Cobertura**: Agrega **pruebas unitarias y de integración** para los componentes críticos de tu API. Esto nos muestra tu compromiso con la calidad del código y la fiabilidad del software.

3.  **Métricas y Monitoreo**: Expón métricas de la API, como la latencia de los endpoints y el volumen de requests, para que puedan ser monitoreadas con herramientas como **Prometheus y Grafana**. Esto refleja tu familiaridad con la observabilidad de los sistemas.

4.  **Seguridad**: Piensa en cómo harías más segura la comunicación entre servicios si esta arquitectura escalara. Por ejemplo, podrías implementar la validación del token de acceso con una librería más robusta o considerar un sistema de autorización más complejo.
