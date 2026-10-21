# Mi Ruleta Lectora — primera versión

App web personal pensada para iPhone, con estética bookish romántica/pastel.

## Funciones
- Importa CSV delimitado por coma, punto y coma o tabulador.
- Reconoce el CSV de Libib (title, creators, tags, status, ean_isbn13, description, began, completed) y encabezados habituales en español e inglés. Separa las etiquetas de Libib en categorías filtrables. Traduce Completed → Leído, In progress → Leyendo y Not begun → Pendiente; si el estado viene vacío, utiliza las fechas de lectura cuando están disponibles.
- Filtra por categoría y estado.
- Ruleta animada que elige al azar entre los libros disponibles.
- Los libros elegidos no vuelven a salir hasta reiniciar la selección.
- Estados: Pendiente, Leyendo, Leído y Pausado.
- Busca, elimina libros y exporta una copia CSV.
- Guarda los datos localmente en el navegador de ese dispositivo.

## Importante sobre privacidad y persistencia
Los libros quedan en el almacenamiento local del navegador. No se envían a un servidor. Usa **Exportar CSV** periódicamente como respaldo. Si borras los datos del sitio/navegador o cambias de navegador/dispositivo, la biblioteca local podría perderse. No hay sincronización en la nube.

## Cómo probar en iPhone
Para que se pueda añadir a la pantalla de inicio y funcione como web app instalable, los archivos deben servirse desde una dirección HTTPS. La opción sencilla es publicar esta carpeta en un repositorio privado/público de GitHub y activar GitHub Pages, o usar un servicio estático HTTPS de confianza. Después:
1. Abre la URL HTTPS en Safari en tu iPhone.
2. Toca Compartir.
3. Elige “Añadir a pantalla de inicio”.
4. Abre el icono “Ruleta Lectora”.

La app puede funcionar sin conexión después de la primera carga gracias al service worker; primero hay que abrirla con conexión para que se guarden los archivos de la app. La disponibilidad de “Añadir a pantalla de inicio” puede variar según versión de iOS y configuración.

## CSV recomendado
Guarda como CSV UTF-8 con encabezados:
`Título;Autor;Categoría;Estado`

Ejemplo:
`Book Lovers;Emily Henry;Romance;Pendiente`
`Fourth Wing;Rebecca Yarros;Romantasy;Pendiente`

La importación añade libros y omite posibles duplicados por ISBN o por combinación de título y autor. La detección de duplicados es una ayuda, no una garantía absoluta.

## Pruebas sugeridas
1. Importa un CSV de prueba con 5–10 libros y dos categorías.
2. Elige una categoría y confirma que la ruleta solo considera esa categoría.
3. Gira la ruleta varias veces: un libro elegido no debe volver a aparecer en la misma ronda.
4. Pulsa “Reiniciar libros elegidos” y confirma que vuelven a estar disponibles.
5. Cambia un estado a “Leído” y selecciona “Solo pendientes”: ese libro ya no debe entrar en la ruleta.
6. Exporta CSV y verifica que se descargue una copia.
7. Cierra y vuelve a abrir la app; los datos deben permanecer en el mismo navegador.

## Limitación de esta primera versión
No incluye imágenes de portadas ni edición de título/autor/categoría desde la interfaz. Los datos se pueden editar en el CSV y volver a importar (recuerda que la importación añade registros). La versión está diseñada como una web app estática, no como una app nativa de App Store.


## Adaptación a Libib
El CSV exportado por Libib incluye 249 libros en el archivo original que se usó para adaptar esta versión. Las etiquetas múltiples se convierten en filtros separados. La colección no se sincroniza automáticamente con Libib: cuando actualices tu catálogo, exporta un nuevo CSV e impórtalo. Los duplicados detectables por ISBN o título+autor se omiten.
