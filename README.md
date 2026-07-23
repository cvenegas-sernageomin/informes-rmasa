# informes-rmasa

Catálogo de informes técnicos (PDF) de Remociones en Masa (RMASA), re-hosteados desde
`portalgeo.sernageomin.cl/Informes_PDF_Nac/` para servirlos con cabecera CORS habilitada
a la PWA [`remociones-en-masa`](https://github.com/cvenegas-sernageomin/catastro-remociones)
("Ingreso de Remociones en Masa"), que descarga los PDFs vía `fetch()` + `blob` para
funcionar correctamente en modo standalone en iOS.

El portal original no envía cabecera CORS, por lo que sus PDFs no pueden consumirse
directamente desde la PWA.

## Contenido

Los PDFs están **commiteados en `pdfs/`** (no en un Release) y se sirven vía
`raw.githubusercontent.com`, que sí manda `Access-Control-Allow-Origin: *`:

```
https://raw.githubusercontent.com/cvenegas-sernageomin/informes-rmasa/main/pdfs/RM-YYYY-NN.pdf
```

**Nota técnica importante:** se probó primero publicarlos como assets de un GitHub
Release (para no engordar el repo git) — pero los Release assets **no llevan cabecera
CORS** (están pensados para descarga por navegación directa, no para `fetch()`/XHR).
El `fetch()` fallaba exactamente igual que contra el portal original. Por eso los PDFs
volvieron a estar commiteados en el repo: es la única vía confirmada que sirve con CORS.

## Catálogo (KMZ)

`catalogo_rmasa.kmz` — 1.640 puntos (Atacama, Coquimbo, Valparaíso, Metropolitana).
Cada `Placemark` trae en su `ExtendedData`:

- `ENLACE`: mejor URL de descarga (este repo si el informe ya está disponible; si no,
  el portal original de SERNAGEOMIN).
- `ENLACE_PORTAL`: URL original en `portalgeo.sernageomin.cl` (siempre presente,
  como referencia).
- `DISPONIBLE`: `1` si el PDF ya está re-hosteado aquí (permite descarga vía
  `fetch()+blob` sin problemas de CORS), `0` si aún apunta solo al portal (sin CORS,
  la PWA lo ofrece como enlace simple `target="_blank"`, no vía fetch).

Se sirve sin caché desde `raw.githubusercontent.com` (rama `main`), consistente con
el patrón usado por [`mapas-peligros-overlays`](https://github.com/cvenegas-sernageomin/mapas-peligros-overlays).

## Estado

**Disponibles actualmente: 48 de 118** informes referenciados por el catálogo KMZ de
1.640 puntos de remociones en masa. Los 70 informes restantes quedan pendientes;
60 son exclusivos de la región Metropolitana (sin cobertura por ahora) y 10
corresponden a Valparaíso/Coquimbo (RM-2000-03, RM-2002-02, RM-2008-04, RM-2013-06,
RM-2014-32, RM-2020-12, RM-2018-24, RM-2021-01, RM-2021-34, RM-2022-10).

El Release `v1` (creado antes de descubrir el problema de CORS) queda publicado por
compatibilidad, pero ya no es la fuente que usa el KMZ.
