# Plugin de Rezandovoy

Paquete portable para conectar ChatGPT y Codex con el servidor MCP público de Rezandovoy.

El plugin es de solo lectura y utiliza `https://apinueva.rezando.es/mcp`. No contiene claves ni accede directamente a la base de datos.

## Contenido

- `plugin.json`: manifiesto portable Agent Plugins.
- `mcp.json`: conexión MCP Streamable HTTP.
- `.codex-plugin/plugin.json`: manifiesto de compatibilidad para clientes Codex.
- `.mcp.json`: conexión de compatibilidad para clientes Codex.
- `.app.json`: asociación con la aplicación registrada en ChatGPT.

La aplicación está registrada en ChatGPT en modo desarrollador. Los componentes visuales son opcionales y todavía no forman parte de esta versión.
