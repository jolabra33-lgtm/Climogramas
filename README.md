# Taller de Climogramas

Aplicación web de una sola página para que el alumnado construya climogramas: localiza un lugar en un mapa satelital, introduce sus temperaturas y precipitaciones mensuales, y la herramienta genera el climograma, resalta los meses clave y propone —a grandes rasgos— la zona climática y el tipo de clima.

No necesita instalación, cuentas ni base de datos: es un único archivo HTML que se ejecuta por completo en el navegador.

## Funcionalidades

- **Localización sobre mapa satelital** (Esri World Imagery) con búsqueda por nombre de lugar (OpenStreetMap Nominatim) y consulta automática de la altitud (Open-Elevation).
- **Tabla editable** de temperatura media y precipitación mensual, con 10 ejemplos reales de referencia agrupados por zona climática (cálida, templada, fría) tomados del material de clase.
- **Climograma interactivo** (Chart.js) con la escala de precipitación siempre al doble que la de temperatura, sombreado de los meses secos (P < 2×T) y tooltips al pasar el cursor.
- **Análisis climático automático**: localización, temperaturas, precipitaciones, distribución de lluvias y una conclusión orientativa sobre el tipo de clima (incluye la categoría especial de "clima de montaña" cuando la altitud es relevante).
- **Impresión**: el botón de imprimir genera solo la tabla y el climograma, sin el resto de la interfaz.
- **Archivo personal de climogramas**: guarda climogramas en el propio navegador (localStorage) y expórtalos/impórtalos como archivo `.json` para hacer una copia de seguridad o llevarlos de un curso a otro o de un dispositivo a otro.

## Uso

### Opción rápida (sin GitHub)
Descarga `index.html` y ábrelo directamente en el navegador con doble clic. Todo funciona igual, salvo el icono de la pestaña y el icono de "Añadir a pantalla de inicio" (ver más abajo), que requieren subir también la carpeta `icons/`.

### Publicarla en GitHub Pages (recomendado)
1. Crea un repositorio nuevo en GitHub (puede ser público o privado).
2. Sube el contenido de esta carpeta manteniendo la estructura:
   ```
   index.html
   README.md
   icons/
   ```
3. Ve a **Settings → Pages**, en "Source" elige la rama (normalmente `main`) y la carpeta raíz (`/`).
4. Guarda. GitHub te dará una URL del tipo `https://tu-usuario.github.io/nombre-del-repositorio/`.
5. Comparte esa URL con tus alumnos; funciona igual en ordenador, tablet o móvil.

Cada vez que quieras actualizar la aplicación, sustituye `index.html` por la nueva versión y súbelo de nuevo (GitHub Pages se actualiza solo en uno o dos minutos).

## Uso en iPad

La aplicación está adaptada para iPad (probada pensando en iPad Pro de 13", pero funciona en cualquier iPad con Safari):

- Los botones y las celdas de la tabla tienen un tamaño cómodo para el dedo.
- Los campos de texto usan un tamaño de letra que evita el "zoom" automático de Safari al tocar un campo.
- El mapa admite los gestos táctiles habituales (arrastrar, pellizcar para hacer zoom).
- Si abres la URL de GitHub Pages en Safari y usas **Compartir → Añadir a pantalla de inicio**, se instala un icono propio y la aplicación se abre a pantalla completa, como una app.

## Dónde se guardan los datos

- Los climogramas guardados con el botón **"Guardar climograma actual"** se quedan en el propio navegador (localStorage), en ese dispositivo. Si cambias de navegador, de dispositivo, o borras los datos de navegación, se pierden.
- Por eso conviene usar **"Exportar todos (.json)"** de vez en cuando (por ejemplo, al final del curso): descarga un único archivo con todos los climogramas guardados. Guarda ese archivo donde prefieras (Drive, el propio ordenador, etc.).
- Al año siguiente, usa **"Importar (.json)"** con ese mismo archivo para recuperarlos y seguir añadiendo climogramas nuevos al mismo archivo.
- Nada de esto se envía a ningún servidor propio: la aplicación no tiene backend. Sí se hacen peticiones a servicios externos y públicos para el mapa, la búsqueda de lugares y la altitud (ver "Servicios externos" abajo).

## Servicios externos utilizados

Todos son gratuitos y no requieren clave de API. Al estar alojada en GitHub Pages (o abierta en local), la aplicación necesita conexión a internet para que funcionen el mapa, la búsqueda de lugares y el cálculo de altitud; la tabla, el climograma y el análisis funcionan igualmente sin conexión una vez cargada la página.

| Servicio | Uso |
|---|---|
| [OpenStreetMap Nominatim](https://nominatim.org/) | Buscar coordenadas a partir del nombre de un lugar |
| [Open-Elevation](https://open-elevation.com/) | Consultar la altitud aproximada de esas coordenadas |
| [Esri World Imagery](https://www.esri.com/) | Teselas del mapa satelital |
| [Leaflet](https://leafletjs.com/) | Librería de mapas interactivos |
| [Chart.js](https://www.chartjs.org/) | Librería del climograma |
| [Google Fonts](https://fonts.google.com/) (Fraunces, Inter, IBM Plex Mono) | Tipografías |

## Aviso pedagógico

La clasificación climática que ofrece la aplicación es una aproximación con fines didácticos, calibrada sobre los criterios y ejemplos del material de clase (zonas cálidas, templadas y frías, más el caso particular de los climas de montaña). No sustituye una clasificación climática rigurosa como la de Köppen.

## Licencia

Este proyecto no incluye una licencia por defecto. Si quieres compartirlo públicamente en GitHub, puedes añadir el archivo `LICENSE` que prefieras (por ejemplo, MIT si quieres permitir que otros lo reutilicen libremente, o dejarlo sin licencia explícita si solo quieres uso interno del centro).
