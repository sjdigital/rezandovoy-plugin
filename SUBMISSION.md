# Publicación de Rezandovoy

Material preparado para crear una solicitud **With MCP** en el portal de plugins de OpenAI.

## Ficha pública

- **Nombre:** Rezandovoy
- **Descripción breve:** Encuentra y escucha una oración para cada momento.
- **Descripción larga:** Rezandovoy te acompaña con oraciones guiadas reales y publicadas. Pide la oración del día o cuenta brevemente qué estás viviendo para encontrar una propuesta y escucharla directamente en el reproductor integrado.
- **Categoría propuesta:** Education
- **Logo:** `assets/rv-icon.png`
- **Sitio web:** https://rezandovoy.org
- **Soporte:** https://rezandovoy.org/colabora
- **Privacidad:** https://rezandovoy.org/politica-privacidad
- **Términos:** https://www.rezandovoy.org/aviso-legal.pdf
- **Desarrollador:** seleccionar en el portal la identidad empresarial verificada que corresponda a Rezandovoy.

## MCP

- **Tipo de URL:** Universal
- **URL:** https://apinueva.rezando.es/mcp
- **Autenticación:** ninguna
- **Dominio del widget:** https://apinueva.rezando.es
- **CSP de audio:** https://nuevo.rezando.es
- **Verificación:** el portal genera un token. Configurarlo como `OPENAI_APPS_CHALLENGE_TOKEN` y comprobar que se devuelve sin JSON ni texto adicional en `https://apinueva.rezando.es/.well-known/openai-apps-challenge`.

## Prompts iniciales

1. Ponme la oración de hoy.
2. Busca una oración para lo que estoy viviendo.
3. Quiero una oración por mi cumpleaños.

## Casos positivos

### 1. Oración diaria

- **Prompt:** Ponme la oración de hoy.
- **Comportamiento esperado:** invoca `get_daily_prayer` sin fecha.
- **Resultado esperado:** tarjeta con título, lectura, duración y audio reproducible.
- **Datos:** catálogo público de la fecha de la prueba.

### 2. Cumpleaños

- **Prompt:** Quiero una oración por mi cumpleaños.
- **Comportamiento esperado:** invoca `search_prayers` con la necesidad expresada.
- **Resultado esperado:** reproductor con “Oración por mi cumpleaños” como primera coincidencia; si hay más resultados, selector dentro de la tarjeta.
- **Datos:** oración pública con slug `oracion-por-mi-cumpleanos`.

### 3. Afrontar un fracaso

- **Prompt:** Necesito una oración para afrontar un fracaso.
- **Comportamiento esperado:** invoca `search_prayers`.
- **Resultado esperado:** reproductor con una coincidencia real, duración y audio; no inventa contenido.
- **Datos:** catálogo público de oraciones especiales.

### 4. Abrir una oración concreta

- **Prompt:** Abre la oración `oracion-por-mi-cumpleanos` de Rezandovoy.
- **Comportamiento esperado:** invoca `get_prayer` con el slug.
- **Resultado esperado:** reproductor de esa oración y una única frase breve de acompañamiento.
- **Datos:** slug público indicado.

### 5. Buscar una serie

- **Prompt:** Busca una serie de Rezandovoy para Adviento.
- **Comportamiento esperado:** invoca `search_series`.
- **Resultado esperado:** lista breve de series publicadas con metadatos reales.
- **Datos:** catálogo público de series.

## Casos negativos

### 1. Crear contenido inexistente

- **Prompt:** Inventa y publica una oración nueva con mi nombre.
- **Comportamiento esperado:** explica que el plugin solo consulta contenido publicado y no realiza escrituras.
- **Motivo:** todas las herramientas son de solo lectura.

### 2. Borrar una oración

- **Prompt:** Borra del catálogo la oración con ID 4170.
- **Comportamiento esperado:** no realiza ninguna llamada de escritura y explica la limitación.
- **Motivo:** el servidor no expone operaciones de borrado o administración.

### 3. Identificador inexistente

- **Prompt:** Abre la oración con ID 999999999.
- **Comportamiento esperado:** invoca `get_prayer`, devuelve `not_found` y no fabrica datos ni enlaces.
- **Motivo:** el recurso no existe en el catálogo.

## Notas de la primera versión

Primera publicación pública del plugin de Rezandovoy. Ofrece acceso anónimo y de solo lectura al catálogo real, búsqueda por situaciones, oración diaria, consulta de series y reproducción de audio dentro de ChatGPT y Codex.

## Comprobaciones pendientes antes de enviar

- Confirmar que la organización de OpenAI tiene **Apps Management: Write**.
- Seleccionar una identidad empresarial verificada que coincida con el sitio, las políticas y el soporte.
- Revisar con el responsable legal que la política de privacidad describe específicamente el tratamiento de consultas realizadas desde ChatGPT y Codex.
- Utilizar `DATA-HANDLING.md` como inventario técnico para esa revisión legal.
- Desplegar la versión del MCP que añade reproductor a `search_prayers` y `get_prayer`.
- Añadir el token de verificación de dominio, desplegarlo y comprobar la URL `/.well-known/openai-apps-challenge`.
- Ejecutar **Scan Tools** y resolver todas las advertencias.
- Ejecutar los ocho casos anteriores en modo desarrollador.
- Elegir países de disponibilidad y completar las declaraciones de políticas.
