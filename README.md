# Datos de calentamiento urbano
Todos los comandos de esta sección asumen que en cada directorio está copiado el archivo en CR05/CRTM05 (EPSG:5367) disponible en el repositorio datos-fuentes-originales.

Los comandos GDAL realizan las conversiones a Web Mercator (EPSG:3857) y WGS84 (EPSG:4326).

## Calentamiento urbano
### GAM

```shell
cd gam

# Temperatura superficial
gdalwarp -t_srs EPSG:3857 -of vrt LST_GAM.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ LST_GAM_WEB.TIF
del LST_GAM.*
gdalwarp -t_srs EPSG:4326 -of vrt LST_GAM_WEB.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ LST_GAM.TIF

# Temperatura superficial de infraestructura gris
gdalwarp -t_srs EPSG:3857 -of vrt LST_INFRAESTRUCTURA_GRIS_GAM.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ LST_INFRAESTRUCTURA_GRIS_GAM_WEB.TIF
del LST_INFRAESTRUCTURA_GRIS_GAM.*
gdalwarp -t_srs EPSG:4326 -of vrt LST_INFRAESTRUCTURA_GRIS_GAM_WEB.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ LST_INFRAESTRUCTURA_GRIS_GAM.TIF

# Índice de vegetación
gdalwarp -t_srs EPSG:3857 -of vrt NDVI_GAM.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ NDVI_GAM_WEB.TIF
del NDVI_GAM.*
gdalwarp -t_srs EPSG:4326 -of vrt NDVI_GAM_WEB.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ NDVI_GAM.TIF
```
