# 🤖 Flujo de Trabajo: Gestión de Solicitudes y Stock de T-Shirts (n8n)

## 📝 Resumen

Este flujo de trabajo está diseñado para **procesar solicitudes de camisetas** registradas en un **formulario de Google Sheets**, verificar la existencia de inventario para la talla solicitada en una **base de datos PostgreSQL**, y actualizar tanto el inventario como el estado de la solicitud en la hoja de Google Sheets.  

El flujo opera en un ciclo de **"leer, verificar y actualizar"** por cada solicitud pendiente.

---

## ⚙️ Componentes Principales

| 🧩 Nodo | 🧠 Función Principal | 🛠️ Notas de Configuración |
|----------|----------------------|----------------------------|
| **Google Sheets Trigger** | **Inicio del Flujo.** Dispara el flujo ante la adición de una nueva fila (solicitud) en la hoja de respuestas. | Configurado para el evento `rowAdded` en la hoja *Respuestas de formulario 1*. |
| **Filtrar Registros** | **Control de Duplicados/Procesados.** Filtra las filas asegurando que solo se procesen solicitudes sin correo electrónico (para evitar errores) y que aún no tengan una *Fecha de Verificación* registrada. | Condición: *Dirección de correo electrónico ≠ vacío* **Y** *Fecha de Verificación = vacío*. |
| **Barrer Cada Solicitud (Split In Batches)** | **Iteración de Ítems.** Divide el lote de solicitudes filtradas para procesar cada una de forma individual y secuencial. | Este nodo garantiza que el proceso de inventario se ejecute para cada solicitud. |
| **Obtener Inventario por Talla (Postgres)** | **Verificación de Stock (Lectura).** Consulta la base de datos `inventory` en PostgreSQL para obtener el stock (`in_stock`) y el ID del producto según la talla solicitada. | Ejecuta un `SELECT * FROM inventory` utilizando la talla del formulario. |
| **If Hay existencias?** | **Lógica Condicional.** Determina si el stock retornado en el paso anterior es mayor a cero. | Condición: `{{ $json.in_stock }} > 0` |
| **Restar Inventario (Set)** | **Cálculo de Nuevo Stock.** Si hay existencias, calcula el nuevo valor de stock. | Fórmula: `$json.in_stock - 1` |
| **Actualizar Inventario (Postgres)** | **Actualización de Stock (Escritura).** Actualiza el stock en la base de datos PostgreSQL con el nuevo valor calculado. | Utiliza la operación `UPDATE` con correspondencia por la columna `id`. |
| **Actualizar Respuestas (Google Sheets)** | **Marcado de Éxito.** Marca la solicitud en Google Sheets como `Verificada = TRUE` y añade la *Fecha de Verificación*. | Se ejecuta después de que el stock ha sido reducido exitosamente. |
| **Actualizar Respuestas sin Inventario (Google Sheets)** | **Marcado de Falla.** Marca la solicitud en Google Sheets como `Verificada = FALSE` y añade la *Fecha de Verificación*. | Se ejecuta cuando no hay existencias (`If Hay existencias? = FALSE`). |

---

### 💡 Flujo General

1. 📥 Nueva solicitud registrada en Google Sheets.  
2. 🔍 Se verifica si ya fue procesada.  
3. 🔁 Cada solicitud pendiente se analiza individualmente.  
4. 🧾 Se consulta el inventario en PostgreSQL.  
5. ⚖️ Si hay stock → se descuenta una unidad y se marca como verificada.  
6. ❌ Si no hay stock → se marca como no verificada.  
7. 📊 El inventario y la hoja se mantienen siempre sincronizados.

---

**Autor:** _Brandon Dulian Garcia Suarez_  
**Plataforma:** n8n  
**Base de datos:** PostgreSQL  
**Integraciones:** Google Sheets API, PostgreSQL Node
