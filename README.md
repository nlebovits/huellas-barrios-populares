# Huellas de edificaciones en los barrios populares

Este repositorio contiene el anexo de CISUR sobre huellas de edificaciones abiertas y el ReNaBaP, y el sitio de Quarto que lo publica. El tutorial de Python tiene dos versiones con el mismo código y los mismos pasos:

- [tutorial_python_es.ipynb](tutorial_python_es.ipynb): español (versión principal)
- [tutorial_python_en.ipynb](tutorial_python_en.ipynb): inglés

Cada tutorial muestra cómo:

1. Descargar el ReNaBaP, el registro nacional de barrios populares de la Argentina.
2. Descargar con DuckDB las huellas de edificaciones de [VIDA](https://source.coop/vida/google-microsoft-open-buildings) para la Argentina.
3. Contar las edificaciones de cada barrio del ReNaBaP.
4. Comparar con imágenes satelitales las huellas del barrio del ex Club Planeadores, en Los Hornos, La Plata (ID del ReNaBaP 6541), sobre imágenes satelitales.

## Ejecutar un tutorial

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nlebovits/huellas-barrios-populares/blob/main/tutorial_python_es.ipynb)

Abrí el notebook en Colab con el botón de arriba y ejecutá las celdas en orden. No necesitás instalar nada. El archivo de edificaciones ocupa unos 3,4 GB.

Para ejecutarlo en tu computadora, instalá [pixi](https://pixi.sh) y corré:

```bash
pixi run notebook
```

## Sitio web

El sitio es un sitio web de [Quarto](https://quarto.org). El español es el idioma principal, y cada página tiene su versión en inglés.

| Archivo | Qué hace |
|---|---|
| `_quarto.yml` | Lista las páginas y la barra de navegación |
| `_brand.yml` | Colores, fuentes y logo de CISUR, tomados de [cisur.ar](https://cisur.ar) |
| `index.qmd`, `index_en.qmd` | Páginas de inicio en español y en inglés |
| `images/` | Logo y favicon de CISUR |
| `docs/` | Sitio generado, publicado con GitHub Pages |

Quarto genera las páginas de los notebooks a partir de sus resultados guardados. Nunca los ejecuta, porque cada ejecución descarga 3,4 GB.

```bash
pixi run preview     # vista previa del sitio mientras editás
pixi run execute     # vuelve a ejecutar los dos notebooks
pixi run site        # genera el sitio en docs/
```

Para publicar, hacé commit de `docs/`. GitHub Pages publica la carpeta `/docs` de la rama `main`. Cada generación completa reemplaza todo el contenido de `docs/`, así que no edites esos archivos a mano.

Para agregar una página, como un tutorial de QGIS o de R, creá un archivo `.qmd` o `.ipynb` en español y otro en inglés. Después agregá los dos a `project.render` y el de español a `website.navbar`, en `_quarto.yml`.

Cuando cambies un tutorial, hacé el mismo cambio en el otro idioma.

Los enlaces para descargar un notebook llevan el atributo `data-noresolveinput="true"`. Sin ese atributo, Quarto cambia el enlace al `.html` generado y la descarga guarda la página en lugar del notebook.

## Reglas de redacción

`.vale.ini` aplica las reglas de Vale para detectar marcas de escritura generada por IA, copiadas de [portolan-ops](https://github.com/portolan-sdi/portolan-ops). Para revisar un texto, corré:

```bash
vale sync
vale --config .vale.ini archivo.md
```

## Datos locales

Los datos descargados van a `data/`, y las figuras y los mapas van a `outputs/`. Git ignora las dos carpetas.

## Fuentes

- Edificaciones: [VIDA, huellas de edificaciones de Google, Microsoft y OpenStreetMap](https://source.coop/vida/google-microsoft-open-buildings). Consultá la licencia en esa página antes de reutilizar los datos.
- Imágenes satelitales de los mapas: [Esri World Imagery Wayback](https://livingatlas.arcgis.com/wayback/), versión del 18 de noviembre de 2026.
- Barrios populares: [Registro Nacional de Barrios Populares (ReNaBaP)](https://www.argentina.gob.ar/habitat/renabap), versión del 6 de diciembre de 2023.
