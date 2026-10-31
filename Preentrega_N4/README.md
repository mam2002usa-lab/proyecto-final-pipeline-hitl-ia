# Preentrega N.º 4 – Integraciones avanzadas en n8n

## 1. Autor

**Nombre:** Marcos Menghi
**Año:** 2026

## 2. Objetivo

Integrar el workflow existente del Módulo 3 con tres herramientas externas mediante OAuth2: HubSpot, Gmail y Slack.

Incorporar controles preventivos para identificar respuestas automáticas, evitar contactos duplicados y mantener la revisión humana antes del envío de correos electrónicos.

## 3. Herramientas integradas

* **Orquestador:** n8n.
* **CRM:** HubSpot.
* **Correo electrónico:** Gmail.
* **Mensajería interna:** Slack.

Las tres herramientas se conectaron mediante credenciales OAuth2.

## 4. Controles implementados

1. **IF2 – Filtro anti-auto-respuestas:** identifica asuntos y remitentes asociados a respuestas automáticas, como `Auto-reply`, `Out of office`, `Undeliverable` y remitentes automáticos.
2. **Search contacts – HubSpot:** busca contactos por correo electrónico antes de decidir si corresponde crear uno.
3. **IF3 – Validación de existencia:** dirige el flujo según el resultado de la búsqueda, evitando crear contactos duplicados.
4. **Create Draft – Gmail:** genera un borrador para revisión humana. No envía automáticamente el correo.
5. **Edit Fields5 – Limpieza del payload:** prepara los campos `From`, `Subject` y `BodyText`.
6. **IF4 – Validación del remitente:** comprueba que el campo `From` no esté vacío antes de continuar.
7. **Send a message1 – Slack:** comunica la recepción de una consulta al canal de operaciones.

**Nota:** el campo `BodyText` se obtiene del atributo `snippet` de Gmail, que contiene un fragmento de vista previa del mensaje.

## 5. Guía de ejecución

1. Importar `checkpoint4_marcos_menghi.json` en n8n mediante la opción de importar workflow.
2. Configurar las credenciales OAuth2 propias de HubSpot, Gmail y Slack.
3. Verificar que las tres credenciales indiquen conexión correcta.
4. Ejecutar una prueba del Gmail Trigger con un correo de consulta.
5. Comprobar el funcionamiento del IF2.
6. Verificar la búsqueda de contactos en HubSpot y la decisión del IF3.
7. Comprobar que Gmail cree un borrador mediante la operación Create Draft, sin enviar el correo.
8. Ejecutar Edit Fields5 y verificar los campos `From`, `Subject` y `BodyText`.
9. Ejecutar IF4 y comprobar que un remitente con contenido pase por True y uno vacío no continúe hacia Slack.
10. Ejecutar Slack y comprobar la recepción de la notificación en el canal configurado.

**Importante:** las pruebas se realizan manualmente. El workflow se mantiene sin publicar ni activar automáticamente.

## 6. Evidencias

Las capturas de pantalla se encuentran dentro de la carpeta `Preentrega_N4` del repositorio.

Incluyen:

* Conexiones OAuth2 de HubSpot, Gmail y Slack.
* Configuración del IF2.
* Búsqueda de contactos en HubSpot.
* Configuración de Gmail Create Draft.
* Prueba exitosa de Slack.
* Validación de los campos mediante Edit Fields5.
* Pruebas de las salidas True y False del IF4.

Estas evidencias permiten verificar la configuración y las pruebas de los principales nodos del workflow.

## 7. Archivo del workflow

**Archivo:** `checkpoint4_marcos_menghi.json`

El archivo JSON permite importar el workflow en n8n. Para utilizarlo, se deben configurar las credenciales propias de cada servicio.

## 8. Seguridad y revisión humana

La integración utiliza OAuth2 para conectar los servicios externos.

Gmail trabaja exclusivamente con la operación **Create Draft**, manteniendo la revisión humana antes del envío.

Los permisos OAuth2 deben limitarse a los accesos necesarios para las operaciones implementadas. La verificación específica de los scopes concedidos a cada aplicación queda sujeta a la revisión de las credenciales.

## 9. Autor

**Marcos Menghi – 2026**
