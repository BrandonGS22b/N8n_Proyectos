🧩 Flujo Automatizado — Extracción y Actualización de Cursos desde Sitios Web

Proyecto n8n + OpenAI + Web Scraping

Este flujo automatiza la obtención, análisis, extracción, actualización y documentación de cursos obtenidos desde sitios web externos. Combina scraping, procesamiento con IA y almacenamiento estructurado.

🧠 Flujo Visual

(Inserta aquí tu imagen)
![Flujo Cursos](./img/Scraping.png)

📘 Descripción General

El flujo permite tomar una lista de sitios web, obtener su contenido, convertirlo, procesarlo con OpenAI para extraer cursos, y luego actualizar la información de cada curso de forma automatizada.

Funciona tanto de forma manual como programada.

🔄 Proceso General

Obtiene los sitios web a investigar desde una hoja o fuente origen.

Filtra los enlaces válidos y con el formato esperado.

Obtiene el HTML del sitio y lo transforma a Markdown para facilitar el análisis.

Envía la información a OpenAI, donde un modelo extrae un arreglo de cursos.

Itera sobre cada curso:

Actualiza la información general.

Realiza scraping adicional (ej: Udemy).

Crea o actualiza documentos con la información del curso.

Actualiza la URL del temario.

Envia la información a OpenAI para mejorar o estructurar el contenido.

Actualiza el documento final con el temario.

Finaliza el proceso dejando todos los cursos actualizados en documentos y bases de datos.

⚙️ Componentes Principales del Flujo
Módulo	Tipo	Función
Obtener sitios a investigar	Entrada	Lee los enlaces desde una base de datos o Google Sheets.
Filtrar sitios Web con enlace	Lógica	Valida que la URL tenga el formato correcto.
Obtener HTML del Sitio Web	Scraping	Descarga el contenido HTML del sitio.
Transformar a Markdown	Conversión	Convierte la página web a formato Markdown para comprensión de IA.
Enviar información a OpenAI	IA	El modelo analiza y entrega un arreglo de cursos.
Extraer arreglo de cursos	Función	Separa cada curso para su procesamiento individual.
Barrer cada curso	Loop	Recorre uno por uno todos los cursos encontrados.
Actualizar Información General del Curso	Base de datos / Google Sheets	Actualiza título, descripción, categoría, etc.
Scrapear información de Udemy	Scraping	Obtiene datos adicionales desde Udemy u otra plataforma.
Crear documento del curso	Docs	Genera o actualiza un archivo donde se guarda toda la información.
Actualizar URL del temario	Escritura	Guarda la URL del temario procesado.
Enviar información a OpenAI (temario)	IA	Genera un temario estructurado y limpio.
Actualizar temario dentro del documento	Documentos	Inserta el temario generado automáticamente.
Fin de lectura del curso	Finalizador	Cierra la iteración y pasa al siguiente curso.
🧾 Ejemplo de Datos de Entrada

Hoja o BD de origen:

Nombre: SitiosCursos

Columnas:

URL
Nombre del Curso
Instructor
DevTalles
Descripccion
