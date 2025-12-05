# ♻️ N8n Proyectos - Gestión de Workflows Automatizados

Este repositorio contiene una colección de flujos (`workflows`) desarrollados en **n8n**, enfocados en la automatización de procesos y tareas recurrentes.  
El proyecto está diseñado para ser fácilmente desplegado mediante **Docker** y **Render**, permitiendo una integración rápida y profesional.

---

## 🧠 Flujos Documentados

| Proyecto | Descripción | Documentación |
|-----------|--------------|----------------|
| 🧬 **Proyecto Pokémon** | Obtiene datos de Pokémon desde una API, actualiza Google Sheets y envía un correo con los resultados. | [Ver documentación](./docs/Proyecto_Pokemon.md) |
| 💼 **Agente Empresa** | Automatiza la gestión de solicitudes empresariales y envío de reportes por correo. | [Ver documentación](./docs/Agente_Empresa.md) |
| 👕 **Gestión de Solicitudes y Stock de T-Shirts (n8n)** | Flujo automatizado que procesa solicitudes de camisetas desde Google Sheets, verifica stock en PostgreSQL y actualiza el inventario y estado de las solicitudes. | [Ver documentación](./docs/Proyecto_gestionCamisas.md) |
| 🧩 **Extracción y Actualización Automática de Cursos (Scraping)** | Flujo que analiza sitios web, extrae cursos usando IA, actualiza información, genera documentos y temarios automáticamente. | [Ver documentación](./docs/Scraping-curso.md) |
| 🌐 **Agente IA con Consulta a Wikipedia** | Agente inteligente que usa modelos de IA, memoria en MongoDB y acceso a herramientas externas como Wikipedia para obtener información real en tiempo real. | [Ver documentación](./docs/Wikipedia-Agente.md) |
| 🤖 **Agente de IA con Herramientas MCP (Gmail, Calendar, Pokémon)** | Agente inteligente que utiliza Google Gemini, memoria en MongoDB y herramientas externas para ejecutar acciones como enviar correos, gestionar eventos de calendario y consultar información de Pokémon en tiempo real. | [Ver documentación](./docs/Asistente_Personal.md) |
| 🛍️ **Agente Tienda Online** | Agente conversacional de soporte que utiliza Google Gemini, memoria en MongoDB y herramientas HTTP para consultar y modificar órdenes de una tienda online. | [Ver documentación](./docs/Agente_tienda_online.md) |
| 💾 **Sistema RAG Documentos-Agente IA** | Implementación de un sistema RAG (Retrieval-Augmented Generation) para indexar documentos en una base de datos vectorial (Postgres) y permitir al Agente IA responder preguntas fundamentadas. | [Ver documentación](./docs/SIstema_rag_DocumentosIA.md) |

---


## 🚀 Características principales

✅ Integración con **GitHub** para control de versiones.  
✅ Compatible con despliegue en **Render** y **Docker Compose**.  
✅ Estructura organizada para flujos de negocio.  
✅ Scripts de configuración automática.  
✅ Listo para entornos de desarrollo y producción.

---

## 🧠 Tecnologías utilizadas

- **n8n** → Plataforma de automatización de flujos de trabajo.  
- **Docker** → Contenerización del entorno.  
- **Node.js (Base de n8n)**  
- **Git & GitHub** → Control de versiones.  
- **Render** → Despliegue continuo en la nube.  

---

## ⚙️ Configuración local con Docker

### 1. Clonar el repositorio

```bash
git clone https://github.com/BrandonGS22b/N8n_Proyectos.git
cd N8n_Proyectos/docker
