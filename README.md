# informes-rmasa

Catálogo de informes técnicos (PDF) de Remociones en Masa (RMASA), re-hosteados desde
`portalgeo.sernageomin.cl/Informes_PDF_Nac/` para servirlos con cabecera CORS habilitada
(`Access-Control-Allow-Origin: *`, provista por GitHub) a la PWA
[`remociones-en-masa`](https://github.com/cvenegas-sernageomin/catastro-remociones)
("Ingreso de Remociones en Masa"), que descarga los PDFs vía `fetch()` + `blob` para
funcionar correctamente en modo standalone en iOS.

El portal original no envía cabecera CORS, por lo que sus PDFs no pueden consumirse
directamente desde la PWA.

## Contenido

Los PDFs no están en este repositorio git (para mantenerlo liviano). Están publicados
como assets del [Release `v1`](../../releases/tag/v1), con URLs de descarga del tipo:

```
https://github.com/cvenegas-sernageomin/informes-rmasa/releases/download/v1/RM-YYYY-NN.pdf
```

## Catálogo (KMZ)

`catalogo_rmasa.kmz` — 1.640 puntos (Atacama, Coquimbo, Valparaíso, Metropolitana).
Cada `Placemark` trae en su `ExtendedData`:

- `ENLACE`: mejor URL de descarga (Release de este repo si el informe ya está
  disponible; si no, el portal original de SERNAGEOMIN).
- `ENLACE_PORTAL`: URL original en `portalgeo.sernageomin.cl` (siempre presente,
  como referencia).
- `DISPONIBLE`: `1` si el PDF ya está re-hosteado en el Release (permite descarga
  vía `fetch()+blob` sin problemas de CORS), `0` si aún apunta solo al portal.

Se sirve sin caché desde `raw.githubusercontent.com` (rama `main`), consistente con
el patrón usado por [`mapas-peligros-overlays`](https://github.com/cvenegas-sernageomin/mapas-peligros-overlays).

## Estado

**Disponibles actualmente: 48 de 118** informes referenciados por el catálogo KMZ de
1.640 puntos de remociones en masa (Atacama, Coquimbo, Valparaíso, Metropolitana).
Los 70 informes restantes quedan pendientes de recopilar y publicar en una futura
actualización del release.
