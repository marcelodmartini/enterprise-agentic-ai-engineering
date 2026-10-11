AI DEEP COURSE — LOCAL IMAGE REFERENCES
=======================================

Entrada principal:
  index.html

Galerías:
  Spanish/gallery/index.html
  English/gallery/index.html

IMPORTANTE
----------
Las galerías ya NO cargan imágenes desde Google Drive.
Cada imagen usa rutas relativas a las carpetas locales:

  Spanish/gallery/index.html -> ../week1/archivo.png
  English/gallery/index.html -> ../week1/archivo.png

Esto permite:
1. Descargar la carpeta completa desde Google Drive como ZIP.
2. Descomprimirla manteniendo la estructura.
3. Abrir index.html localmente.
4. Publicar la misma estructura en GitHub Pages.

No renombrar:
- Spanish / English
- gallery
- week1 ... week33
- archivos de imagen

Nota detectada al validar Drive:
- English/week17 está actualmente vacío, por lo que la galería muestra esa semana sin imágenes.
