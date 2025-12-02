# 🧩 Flujo Automatizado — Agente IA con Wikipedia

Este flujo implementa un **Agente de IA** en **n8n**, capaz de recibir mensajes, consultar Wikipedia, usar memoria, razonar y responder de forma inteligente mediante modelos de IA.

---

## 🧠 Flujo Visual  

![Flujo Agente Wikipedia](./img/Wikipedia-Agente.png)

---

## 📘 Descripción General

Este flujo permite crear un **asistente inteligente** que:

1. **Recibe mensajes** desde un sistema externo (webhook, chat o API).
2. **Procesa el mensaje** usando un **AI Agent** como cerebro central.
3. **Consulta Wikipedia automáticamente**, si el agente lo necesita.
4. **Mantiene memoria** gracias a MongoDB Chat Memory.
5. **Genera una respuesta contextualizada** mediante un modelo de IA.
6. **Retorna la respuesta** al usuario o sistema que envió el mensaje.

Ideal para:

- Chatbots educativos  
- Asistentes informativos  
- Bots de consultas rápidas  
- Asistentes internos con memoria  

---

## ⚙️ Componentes Principales

| Módulo | Tipo | Descripción |
|--------|------|-------------|
| **When Chat Message Received** | Disparador | Activa el flujo con cada mensaje entrante. |
| **AI Agent (n8n)** | Motor de IA | Procesa el mensaje, decide si usar herramientas y produce la respuesta. |
| **Chat Models (OpenAI / Gemini / Ollama)** | Modelo de IA | Genera respuestas en lenguaje natural. |
| **MongoDB Chat Memory** | Memoria | Guarda conversaciones previas para proporcionar contexto continuo. |
| **Wikipedia Tool** | Herramienta externa | Permite acceder a información real de Wikipedia. |

---

## 🧾 Ejemplo de Funcionamiento

### **Entrada del usuario:**
¿Quién fue Nikola Tesla?

yaml
Copiar código

### **Acciones del flujo:**
- El agente analiza el mensaje.  
- Detecta que necesita información histórica.  
- Llama a **Wikipedia Tool**.  
- Procesa y resume la información.  
- Devuelve una respuesta clara y precisa.

### **Salida:**
Respuesta generada por el modelo de IA con información verificada.

---

## 🚀 Ejecución con Docker

Si tu entorno usa Docker:

```bash
docker-compose up -d
Luego accede a n8n en:
👉 http://localhost:5678

Importa el flujo desde:

bash
Copiar código
/workflows/Wikipedia-Agente.json
🗂️ Archivos Relacionados
Dentro de /docs/:

Wikipedia-Agente.md ← Este archivo

Proyecto_Pokemon.md

Proyecto_gestionCamisas.md

Scraping-curso.md

Las imágenes se encuentran en:
/docs/img/Wikipedia-Agente.png

✉️ Autor
Brandon Suárez
📧 brandondulian36@gmail.com
🌐 github.com/BrandonGS22b