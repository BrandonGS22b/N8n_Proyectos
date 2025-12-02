🧠 Agente Empresarial – Documentación del Proyecto

Este proyecto implementa un Agente de IA utilizando n8n, capaz de recibir mensajes, decidir cómo responder y conectarse con memoria y herramientas externas como Wikipedia.
Además, contiene un entorno web básico para pruebas y documentación visual del flujo.
---
📁 Estructura del Proyecto
/
├── docker/
├── docs/
│   ├── img/
│   │   ├── Form-Ropa.png
│   │   ├── imagePokemon.png
│   │   ├── Scraping.png
│   │   ├── Wikipedia-Agente.png
│   │
│   ├── Proyecto_gestionCamisas.md
│   ├── Proyecto_Pokemon.md
│   ├── Scraping-curso.md
│   ├── Wikipedia-Agente.md
│
├── web/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   └── node_modules/
│
├── workflows/
│   └── Agente_Empresa.json
│
├── .gitignore
└── README.md
---
📌 1. Descripción del Proyecto

El Agente Empresarial es un flujo automatizado creado en n8n que permite:

Recibir mensajes desde un sistema externo (chat, API, webhook).

Usar un AI Agent como cerebro central.

Conectarse a modelos de chat (OpenAI, Google Gemini, Ollama).

Recordar conversaciones mediante MongoDB Chat Memory.

Consultar información externa mediante la herramienta Wikipedia.

Responder mensajes de forma inteligente y contextual.

El objetivo es proporcionar una base para construir chatbots empresariales, asistentes internos y automatizaciones inteligentes.

⚙️ 2. Arquitectura del Flujo

A continuación, se muestra el diagrama incluido en /docs/img/:

🧩 Componentes:
1️⃣ When Chat Message Received

Este nodo es el disparador que activa todo el flujo.
Cada que llega un mensaje → se inicia el proceso.

2️⃣ AI Agent (n8n)

Es el motor principal.
Decide cómo responder en cada interacción utilizando:

Chat Models

Memory

Tools

3️⃣ Modelos de Chat

Conectados directamente al agente:

OpenAI Chat Model

Google Gemini Chat Model

Ollama Chat Model

Estos permiten cambiar entre proveedores sin modificar el flujo.

4️⃣ MongoDB Chat Memory

El nodo almacena conversaciones para:

mantener contexto

recordar interacciones pasadas

mejorar coherencia en respuestas

5️⃣ Wikipedia Tool

Permite al agente consultar información externa y responder preguntas con datos reales usando:

"Buscar en Wikipedia"

Ideal para asistentes educativos o informativos.

🛠️ 3. Instalación del Proyecto
✔️ Requisitos

n8n instalado (Cloud, Docker o Local)

Node.js (para el mini sitio web)

MongoDB (Atlas o local)

📥 Importar el flujo en n8n

Ir a n8n → Workflows

Clic en Import

Seleccionar el archivo:

workflows/Agente_Empresa.json


Guardar y activar el flujo.

🧪 4. Uso del Proyecto
▶️ 1. Enviar un mensaje al chatbot

Puede ser desde:

Webhook

Telegram

WhatsApp

Web Chat

Cualquier integración soportada por n8n

🤖 2. El agente analiza:

historial de mensajes (MongoDB Memory)

herramientas disponibles

modelo de IA configurado

📤 3. El bot responde con contexto

Ejemplos:

Usuario: “¿Quién es Albert Einstein?”
→ el agente usa Wikipedia

Usuario: “¿Recuerdas lo que hablamos ayer?”
→ usa la memoria en MongoDB

🌐 5. Carpeta Web

La carpeta /web contiene un ejemplo de interfaz sencilla:
---
web/
├── index.html
├── package.json
└── node_modules/
---

Sirve para pruebas o como base para un chat web conectado al flujo.

🖼️ 6. Imágenes del Proyecto

Dentro de docs/img/ están los recursos visuales:

Archivo	Descripción
Form-Ropa.png	Ejemplo de flujo de formulario
imagePokemon.png	Ilustración del proyecto Pokémon
Scraping.png	Ejemplo de flujo de scraping
Wikipedia-Agente.png	Arquitectura del agente IA
📚 7. Documentos Incluidos

En la carpeta /docs/ vienen manuales de otros proyectos:

Proyecto_gestionCamisas.md

Proyecto_Pokemon.md

Scraping-curso.md

Wikipedia-Agente.md

Sirven como ejemplos para documentar flujos.

🚀 8. Objetivo del Proyecto

Crear una base sólida de automatización + IA + memoria + herramientas externas que permita construir:

Asistentes virtuales empresariales

Bots que respondan con información real

Automatizaciones inteligentes

Chatbots con memoria

Integraciones con sistemas internos

👨‍💻 9. Autor

Desarrollado por Brandon Suárez, como parte de su portafolio de automatización con n8n y agentes inteligentes.

📝 10. Licencia

Este proyecto se puede usar libremente para aprendizaje y desarrollo personal.