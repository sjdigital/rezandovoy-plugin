# Plugin de Rezandovoy

Paquete portable para conectar ChatGPT y Codex con el servidor MCP público de Rezandovoy. Permite encontrar una oración para cada momento y escucharla en un reproductor integrado.

El plugin es de solo lectura y utiliza `https://apinueva.rezando.es/mcp`. No contiene claves ni accede directamente a la base de datos.

## Contenido

- `plugin.json`: manifiesto portable Agent Plugins.
- `mcp.json`: conexión MCP Streamable HTTP.
- `.codex-plugin/plugin.json`: manifiesto de compatibilidad para clientes Codex.
- `.mcp.json`: conexión de compatibilidad para clientes Codex.
- `.app.json`: asociación con la aplicación registrada en ChatGPT.
- `assets/rv-icon.png`: icono cuadrado preparado a partir de la marca oficial.
- `SUBMISSION.md`: ficha, pruebas y lista de comprobación para la publicación pública.
- `DATA-HANDLING.md`: inventario técnico para revisar la política de privacidad de la integración.

La aplicación está registrada en ChatGPT en modo desarrollador y usa componentes visuales para reproducir la oración diaria, las búsquedas y las oraciones concretas. La publicación universal requiere superar la revisión de OpenAI; el material necesario está preparado en `SUBMISSION.md`.

## Experiencias principales

- “Ponme la oración de hoy”: muestra la oración diaria con su reproductor.
- “Quiero una oración por mi cumpleaños”: busca coincidencias y permite escucharlas o cambiar entre varias opciones dentro de la tarjeta.
- “Busca una serie para Adviento”: consulta las series publicadas.

El servicio es anónimo y de solo lectura. No crea oraciones, no modifica el catálogo y no sustituye el acompañamiento humano, espiritual, médico o psicológico.
