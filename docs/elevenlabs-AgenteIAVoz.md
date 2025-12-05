# 🗣️ Agente de Voz (TTS) para E-commerce con ElevenLabs.io

Este flujo implementa un **Agente de IA conversacional** capaz de interactuar con el usuario mediante comandos de voz/chat. El agente se conecta a un backend de E-commerce (a través de API) para **consultar productos y gestionar órdenes**, y **devuelve la respuesta final en formato de audio** utilizando ElevenLabs.io (Text-to-Speech).

Funciona como un asistente de voz avanzado para soporte de tienda online y consulta de inventario.

---

## 🧠 Flujo Visual

![Diagrama del Agente de Voz para E-commerce, combinando el Agente IA con herramientas de gestión de órdenes y la generación de voz con ElevenLabs.io.]((./img/SIstema_rag_DocumentosIA.png))

---

## 📘 Descripción General

El flujo se activa al recibir la solicitud del usuario (texto o voz transcrita). El Agente de IA orquesta el proceso para decidir si necesita gestionar una orden, consultar un producto del backend, o simplemente responder una pregunta general.

### Fases del Flujo:

1.  **Entrada y Orquestación:** El mensaje del usuario activa el flujo y es procesado por el **AI Agent** (Google Gemini y MongoDB Memory).
2.  **Ejecución de Herramientas:** El agente tiene acceso a múltiples herramientas, incluyendo:
    * **Gestión de Órdenes:** Permite obtener información de órdenes o cambiar direcciones.
    * **Consulta de Productos (Nuevo):** Permite acceder a la lista de productos y stock del backend (a través del subflujo `Obtiene productos de mi backend`).
    * **Envío de Correos:** Para notificaciones.
3.  **Conversión a Voz:** La respuesta final en texto es enviada a **ElevenLabs.io** para generar el archivo de audio.
4.  **Respuesta Final:** El audio es enviado de vuelta al usuario.

---

## ⚙️ Componentes Principales

| Módulo | Tipo | Descripción | Función Principal |
|--------|------|-------------|-------------------|
| **AI Agent** | Orquestador | Procesa la solicitud, usa la memoria y decide qué herramienta de API o acción ejecutar. | Inteligencia y Control. |
| **Google Gemini Chat Model** | Modelo de IA | Genera la respuesta textual y dirige las acciones. | Generación de Texto Base. |
| **MongoDB Chat Memory** | Memoria | Mantiene la coherencia y el contexto de la conversación. | Contexto conversacional. |
| **Subflujo 'Obtiene productos'** | Herramienta (GET) | Conecta con el backend para obtener la lista de productos y su disponibilidad. | Consulta de Inventario. |
| **Subflujo 'get_order_by_id'** | Herramienta (GET/POST) | Permite obtener los detalles de una orden específica (incluye lógica 'If' de validación). | Consulta de Órdenes. |
| **HTTP Request - update_address** | Herramienta (PATCH) | Permite al agente cambiar la dirección de una orden. | Gestión de Órdenes. |
| **Send_email** | Integración | Permite al agente enviar correos electrónicos de confirmación o notificación. | Comunicación Externa. |
| **ElevenLabs.io (TTS)** | Integración de Voz | **Convierte el texto de respuesta del Agente en un archivo de audio.** | Generación de Audio. |

---

## 🔍 Subflujos del Backend

El Agente de IA utiliza estas funcionalidades externas como herramientas:

### 1. Obtiene productos de mi backend

* **Webhook-obtener productos:** Disparador para que el Agente invoque la herramienta.
* **HTTP Request-Obtenemos productos:** Realiza una petición `GET` a la API del backend para recuperar el listado de productos y su información.
* **Responder productos:** Devuelve el JSON con la lista de productos al Agente.

### 2. get_order_by_id

* **Webhook-obtener orden por id:** Disparador para la herramienta.
* **If:** Evalúa si el ID de la orden proporcionado es válido o existe.
    * *TRUE:* Procede a **Obtener order por Id** (petición HTTP).
    * *FALSE:* Responde con **Responder Bad request**.
* **Tenemos una orden? (If):** Verifica si la petición HTTP devolvió datos.
    * *TRUE:* Responde con la orden al Agente (**Responder con la orden**).
    * *FALSE:* Responde con **Responder not found**.

---

## 🧾 Ejemplo de Uso

El usuario (simulando hablar al agente) dice:

```markdown
"¿Está la sudadera azul en stock y cuánto cuesta?"
El agente hace lo siguiente:

El AI Agent invoca la herramienta 'Obtiene productos de mi backend'.

El backend devuelve la lista completa de productos.

El Agente procesa la lista y extrae el precio y el stock de la 'sudadera azul'.

El Agente construye la respuesta de texto: "Sí, la sudadera azul está en stock y tiene un precio de 45 dólares."

ElevenLabs.io convierte el texto a voz, y el agente envía el archivo de audio al usuario.

🚀 Ejecución con Docker
Bash

docker-compose up -d
Luego accede a n8n en:

👉 http://localhost:5678

Importa el flujo JSON desde:

Bash

/workflows/Agente_Voz_E-commerce.json
✉️ Autor Brandon Suárez 📧 brandondulian36@gmail.com 🌐 https://github.com/BrandonGS22b
