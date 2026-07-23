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

## Estado

**Disponibles actualmente: 48 de 118** informes referenciados por el catálogo KMZ de
1.640 puntos de remociones en masa (Atacama, Coquimbo, Valparaíso, Metropolitana).
Los 70 informes restantes quedan pendientes de recopilar y publicar en una futura
actualización del release.
