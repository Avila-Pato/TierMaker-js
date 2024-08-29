# TiERMAKER - Crea y Comparte tus Rankings

Este proyecto permite crear y compartir tus propios rankings mediante una interfaz interactiva. Los usuarios pueden cargar imágenes, organizarlas en diferentes niveles de clasificación (S, A, B, C, D, E) y guardar la lista de clasificación como una imagen.

## Descripción del Proyecto

TiERMAKER es una herramienta para crear listas de clasificación personalizadas. Permite a los usuarios:

- **Cargar Imágenes**: Seleccionar múltiples imágenes desde su dispositivo y visualizarlas en un selector.
- **Organizar Imágenes en Niveles**: Arrastrar y soltar imágenes en diferentes niveles de una lista de clasificación.
- **Guardar la Lista de Clasificación**: Capturar una imagen del contenedor de la lista de clasificación y descargarla.

## Estructura del HTML y CSS

### Estructura Principal

- **`<header id="top-header">`**: Contiene el logo del proyecto.
- **`<section class="tier">`**: Contiene los niveles de la lista de clasificación, desde S hasta E.
- **`<section id="selector">`**: Área para visualizar las imágenes cargadas.
- **`<div id="controls">`**: Contiene los botones para guardar la lista y reiniciar la clasificación.

### Estilos

- **Variables de Color**: Define colores para los diferentes niveles.
- **Diseño de Flexbox**: Utiliza flexbox para organizar la disposición de los elementos.
- **Botones de Interacción**: Botones estilizados para agregar imágenes, guardar la lista y reiniciar.

## Lógica de JavaScript

### Variables y Elementos

- **`selectorItems`**: Contenedor para las imágenes cargadas.
- **`tiers`**: Niveles de la lista de clasificación.
- **`addImageButton`**: Botón para agregar nuevas imágenes.
- **`resetButton`**: Botón para reiniciar la lista de clasificación.
- **`addSaveButton`**: Botón para guardar la lista como imagen.
- **`fileInput`**: Elemento de entrada para seleccionar archivos de imagen.

### Funciones Principales

1. **Guardar Imagen del Contenedor**

   La función para guardar la lista de clasificación como una imagen utiliza la biblioteca `html2canvas` para capturar el contenedor y descargarlo como archivo PNG.

   ```javascript
   addSaveButton.addEventListener('click', () => {
       html2canvas(document.querySelector('.tier')).then(canvas => {
           const link = document.createElement('a');
           link.href = canvas.toDataURL('image/png');
           link.download = 'tier-list.png';
           link.click();
       });
   });
