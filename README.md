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

Estos puntos no son obligatorios
