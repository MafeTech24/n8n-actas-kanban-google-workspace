# 🎯 Automatización de Actas + Kanban con n8n y Google Workspace

Este proyecto implementa un flujo automatizado para:

✔ transcribir reuniones

✔ generar actas automáticas en Google Docs

✔ crear y actualizar tablero Kanban en Google Sheets

✔ sincronizar estado de tareas

✔ exportar documentos

✔ mantener trazabilidad del proyecto

El workflow está desarrollado en n8n y se integra con:

- Google Drive

- Google Docs

- Google Sheets

- Gemini / LLM para resumen y extracción de tareas

<hr>

## 🚀 Flujo general del sistema

**1).**  Se carga un audio al Google Drive

**2).** n8n detecta el archivo nuevo

**3).** Se descarga el audio

**4).** Se transcribe la reunión

**5).** Un modelo LLM:

- resume

- detecta tareas

- asigna responsables

**6).** Se genera un acta en Google Docs

**7).** Se llena o actualiza el tablero Kanban en Google Sheets

**8).** Se exporta el documento si es necesario

<hr>

## 📌 El workflow completo se encuentra en:

````
workflow/kanban-actas-n8n.json
````
<hr>

## 🔗 Conexión con Herramientas de Google

El proyecto usa 3 integraciones:

1️⃣ Google Drive

Usado para:

* trigger cuando se sube o actualiza un archivo de audio

* descargar archivo

* guardar documentos generados

En n8n:

* **Nodo**: Google Drive Trigger

* **Evento**: fileUpdated ó fileCreated

<hr>

2️⃣ Google Docs

Usado para:

* generar actas formales de reunión

* insertar resumen y tareas

* actualizar documentos existentes

Nodos principales:

* **Create a document**

* **Update a document**

Contenido generado automáticamente:

* Título del acta

* Fecha y hora

* Resumen general

* Lista de tareas acordadas

* responsables

* fechas límite

* estado

<hr>

3️⃣ Google Sheets (Kanban)

Se utiliza para construir el tablero **Kanban** con columnas:

* TAREA

* RESPONSABLE

* FECHA LÍMITE

* TO DO

* DOING

* DONE

Funciones implementadas:

✅ carga automática de tareas

✅ normalización de estados

✅ validación de columnas

✅ sync bidireccional (editable desde Sheets)

Nodo responsable:
````
Append or Update Row in Sheet
````

<hr>

## 🧠 Inteligencia Artificial utilizada

Se usa un modelo LLM para:

* transcribir reunión

* resumir puntos principales

* estructurar tareas en JSON

* asignar responsables

Formato de salida:

````
{
  "resumen": "texto…",
  "tareas": [
    {
      "descripcion": "",
      "responsable": "",
      "fecha_limite": "",
      "estado": "Pendiente"
    }
  ]
}
````

<hr>

## 🛠️ Requisitos

Instalar:

* n8n

cuenta Google Cloud

* habilitar APIs:

* Google Drive

* Google Docs

* Google Sheets
  
También se requiere:

* clave de modelo IA (Gemini / OpenAI / etc.)
  
<hr>

## ▶️ Cómo ejecutar el proyecto

**1)** Importar JSON del workflow en n8n

**2)** Configurar credenciales de Google

**3)** Vincular cuentas:

* Google Drive

* Google Docs

* Google Sheets

**4)** Activar workflow

**5)** Subir audio a carpeta de Drive

📌 Ver resultados en:

- **Google Docs → acta creada**

- **Google Sheets → tablero Kanban actualizado**

<hr>

## 📌 Estado del proyecto

✔️ Generación automática de actas

✔️ Extracción de tareas

✔️ Creación de tablero Kanban

✔️ Actualización automática

✔️ Sincronización desde Sheets

⏳ Dashboard avanzado (opcional)

⏳ Notificaciones Slack / Email (opcional)

<hr>

## 👩‍💻 Autora


María Fernanda Moreno
