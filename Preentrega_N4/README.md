# Preentrega N.º 4 – Integraciones avanzadas en n8n

## 1. Autor

**Marcos Menghi**
**Año:** 2026

## 2. Objetivo

Integrar el workflow existente de n8n con tres herramientas externas para conectar el sistema multi-agente con el CRM, la casilla de soporte y el canal de operaciones, incorporando controles preventivos.

## 3. Herramientas integradas

* **Orquestador:** n8n.
* **CRM:** HubSpot.
* **Correo electrónico:** Gmail.
* **Mensajería interna:** Slack.

Las tres herramientas fueron conectadas mediante credenciales OAuth2.

## 4. Controles implementados

1. **IF anti-auto-respuestas:** filtra correos automáticos para evitar bucles.
2. **Búsqueda en HubSpot:** consulta si el contacto existe antes de realizar una operación de creación o actualización.
3. **IF de validación:** determina la ruta del workflow según el resultado de la búsqueda.
4. **Create Draft en Gmail:** genera un borrador para revisión humana, sin enviar automáticamente el correo.
5. **Edit Fields:** reduce y organiza los datos que se envían a Slack.
6. **Notificación en Slack:** informa sobre la consulta recibida y el borrador generado.

## 5. Archivo del workflow

El archivo exportado desde n8n es:

`checkpoint4_marcos_menghi.json`

Permite importar el workflow y revisar su configuración.

**Ubicación:** directorio principal del repositorio.

## 6. Guía de ejecución

1. Ingresar a n8n.
2. Importar el archivo JSON mediante la opción de importar workflow.
3. Configurar las credenciales propias de HubSpot, Gmail y Slack.
4. Verificar las conexiones antes de ejecutar las pruebas.
5. Probar el filtro IF con correos de prueba.
6. Verificar la búsqueda de contactos en HubSpot.
7. Comprobar que Gmail genere un borrador y no envíe el mensaje.
8. Verificar que Slack reciba la notificación con los campos configurados.

El workflow debe mantenerse desactivado durante las pruebas manuales para evitar ejecuciones no deseadas.

## 7. Pruebas realizadas

Se realizaron pruebas individuales de los nodos principales:

* Recepción de correos mediante Gmail Trigger.
* Clasificación mediante IF.
* Búsqueda de contactos en HubSpot.
* Validación de existencia del contacto.
* Creación de borrador en Gmail.
* Preparación del payload mediante Edit Fields.
* Envío de notificación de prueba a Slack.

## 8. Evidencias

Las capturas de pantalla de las conexiones y de los nodos principales se encuentran en la carpeta `evidencias` del repositorio.

## 9. Seguridad y control humano

La solución utiliza OAuth2 para conectar los servicios externos. La operación Create Draft establece una instancia de revisión humana antes del envío definitivo.

Los permisos deben limitarse a las operaciones y datos necesarios para cada integración.

## 10. Repositorio

Proyecto integrador de automatización IA – mates.mam.
