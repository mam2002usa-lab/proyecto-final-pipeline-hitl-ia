# Preentrega N.º 4 – Integraciones avanzadas en n8n

## 1. Autor

**Marcos Menghi**
**Año:** 2026

## 2. Objetivo

Integrar el workflow existente del Módulo 3 con tres herramientas externas mediante OAuth2: HubSpot, Gmail y Slack. Incorporar controles preventivos para evitar respuestas automáticas, contactos duplicados y envíos de correos sin revisión humana.

## 3. Herramientas integradas

* **Orquestador:** n8n.
* **CRM:** HubSpot.
* **Correo electrónico:** Gmail.
* **Mensajería interna:** Slack.

Las tres credenciales se conectaron mediante OAuth2.

## 4. Controles implementados

1. **IF2 – Filtro anti-auto-respuestas:** identifica asuntos y remitentes asociados a respuestas automáticas.
2. **Search contacts – HubSpot:** busca contactos por correo electrónico antes de decidir si corresponde crear uno.
3. **IF3 – Validación de existencia:** dirige el flujo según el resultado de la búsqueda.
4. **Create Draft – Gmail:** genera un borrador para revisión humana. No envía automáticamente el correo.
5. **Edit Fields5 – Limpieza del payload:** prepara únicamente los campos `From`, `Subject` y `BodyText`.
6. **Send a message1 – Slack:** comunica la recepción de una consulta y los datos correspondientes al equipo de operaciones.

## 5. Guía de ejecución

1. Importar `checkpoint4_marcos_menghi.json` en n8n mediante la opción de importar workflow.
2. Configurar las credenciales OAuth2 propias de HubSpot, Gmail y Slack.
3. Verificar que las tres credenciales indiquen conexión correcta.
4. Ejecutar una prueba del Gmail Trigger con un correo de consulta.
5. Comprobar el funcionamiento del IF2.
6. Verificar la búsqueda de contactos en HubSpot y la decisión del IF3.
7. Comprobar que Gmail cree un borrador, sin enviar el correo.
8. Ejecutar Edit Fields5 y verificar los campos `From`, `Subject` y `BodyText`.
9. Ejecutar Slack y comprobar la recepción de la notificación en el canal configurado.

**Importante:** las pruebas se realizan manualmente. El workflow se mantiene sin publicar ni activar automáticamente.

## 6. Evidencias

La carpeta `evidencias` contiene las capturas de las conexiones OAuth2 y las pruebas de los nodos principales.

## 7. Archivo del workflow

`checkpoint4_marcos_menghi.json`

El archivo JSON permite importar el workflow en n8n.

## 8. Seguridad y revisión humana

La integración utiliza OAuth2. Gmail trabaja exclusivamente con la operación **Create Draft**, manteniendo la revisión humana antes del envío.

La revisión específica de los scopes de mínimo privilegio debe realizarse sobre los permisos concedidos a cada aplicación.

## 9. Autor

Marcos Menghi – 2026
