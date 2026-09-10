# Nota técnica sobre tratamiento de datos

Documento técnico para que el equipo responsable de privacidad prepare o revise el texto legal de la integración de Rezandovoy con ChatGPT y Codex. No sustituye una revisión jurídica.

## Datos que puede recibir el MCP

- La consulta escrita por la persona cuando busca una oración.
- Un identificador o slug cuando solicita una oración concreta.
- Fecha, idioma, duración máxima y límite de resultados cuando corresponda.
- Metadatos técnicos de la petición, como agente de usuario, identificador de petición e identidad de red.

El plugin no pide nombre, correo, teléfono, cuenta de Rezandovoy ni datos de pago. Al ser una búsqueda en lenguaje natural, una persona podría incluir voluntariamente información sensible en su consulta; por eso el servidor evita registrar el texto por defecto.

## Uso de los datos

- Consultar el catálogo publicado de Rezandovoy y devolver coincidencias reales.
- Aplicar límites de uso y proteger la disponibilidad del servicio.
- Diagnosticar errores mediante metadatos técnicos mínimos.

No se crean perfiles, no se modifican contenidos y no se realizan operaciones de administración.

## Registros y limitación de uso

- `MCP_LOG_QUERY_CONTENT` está desactivado por defecto, por lo que el texto de búsqueda no aparece en los logs ordinarios.
- Los logs técnicos contienen herramienta, identificador de petición, duración, número de resultados, estado y clasificación del cliente.
- La identidad de red se transforma mediante HMAC para las claves del limitador.
- Las claves de rate limiting distribuidas expiran aproximadamente a los dos minutos.
- El plazo de conservación de los logs de infraestructura debe confirmarlo el equipo de operaciones antes de publicar la política definitiva.

## Proveedores y conexiones

- OpenAI procesa la conversación y decide cuándo invocar el plugin conforme a sus propios términos y políticas.
- El MCP consulta la API de Rezandovoy.
- El reproductor carga el audio directamente desde `https://nuevo.rezando.es`; ese servidor puede generar los registros técnicos habituales de una petición web.

## Puntos que debe cubrir la política pública

- Que la integración puede recibir texto escrito por la persona para encontrar una oración.
- Las finalidades, base jurídica y plazo de conservación aplicables.
- La participación de OpenAI y la carga de audio desde la infraestructura de Rezandovoy.
- El canal para ejercer derechos o solicitar soporte.
