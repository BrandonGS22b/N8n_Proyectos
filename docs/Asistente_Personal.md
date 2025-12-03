# 🧩 Flujo Automatizado — Obtener Información Detallada de Pokémon (API)

Este flujo es un **sub-workflow** encargado de consultar una API externa (PokeAPI) para obtener información detallada de un Pokémon, utilizando un ID o nombre enviado desde otro flujo superior.

---

## 🧠 Flujo Visual

![Flujo Pokemon API](./img/Asistente_Personal.png),
![Flujo Pokemon API](./img/MCP_AsistentePersonal_Calendar.png),
![Flujo Pokemon API](./img/MCP_AsistentePersonal_Gmail.png),
![Flujo Pokemon API](./img/Tool_AsistentePersonal_Pokemon.png)

---

## 📘 Descripción General

Este flujo se activa únicamente cuando otro workflow lo llama. Su función es tomar un ID de Pokémon, hacer la consulta externa y devolver los datos listos para ser usados.

1. **Recibe el ID del Pokémon** enviado desde el flujo principal.
2. **Realiza una solicitud HTTP** a la API `PokeAPI`.
3. **Estructura la información recibida**, dejando solo los campos necesarios.
4. **Retorna la respuesta procesada** al workflow que lo invocó.

---

## ⚙️ Componentes Principales

| Módulo | Tipo | Descripción |
|--------|------|-------------|
| **Execute Workflow Trigger** | Disparador | Permite que este sub-workflow sea ejecutado por otro flujo. |
| **Entrada (ID del Pokémon)** | Datos | Recibe el parámetro que indica qué Pokémon consultar. |
| **HTTP Request** | API Externa | Consulta la API `https://pokeapi.co/api/v2/pokemon/{id}`. |
| **Edit Fields Manual** | Transformación | Limpia, transforma y selecciona los datos que se enviarán de vuelta. |

---

## 🧾 Ejemplo de Configuración

**Entrada desde otro flujo:**
```json
{
  "pokemonId": 25
}
Endpoint usado:

bash
Copiar código
GET https://pokeapi.co/api/v2/pokemon/25
Datos que se devuelven:

ID

Nombre

Tipos

Habilidades

Sprite frontal

🚀 Ejecución con Docker
bash
Copiar código
docker-compose up -d
Accede al panel n8n en:

👉 http://localhost:5678

Importa este flujo desde:

bash
Copiar código
/workflows/Flujo_Informacion_Pokemon_v2.json
✉️ Autor

Brandon Suárez
📧 brandondulian36@gmail.com
🌐 github.com/BrandonGS22b


