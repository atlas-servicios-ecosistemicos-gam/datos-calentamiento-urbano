# Datos de calentamiento urbano
Todos los comandos de esta sección asumen que en cada directorio está copiado el archivo en CR05/CRTM05 (EPSG:5367) disponible en el repositorio datos-fuentes-originales.

Los comandos GDAL realizan las conversiones a Web Mercator (EPSG:3857) y WGS84 (EPSG:4326).

## Calentamiento urbano
### GAM

```shell
cd gam

# Temperatura superficial
gdalwarp -t_srs EPSG:3857 -of vrt PROBABILIDAD_CONECTIVIDAD_BOSQUE_BRIPARIO.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ PROBABILIDAD_CONECTIVIDAD_BOSQUE_BRIPARIO_WEB.TIF
del PROBABILIDAD_CONECTIVIDAD_BOSQUE_BRIPARIO.*
gdalwarp -t_srs EPSG:4326 -of vrt PROBABILIDAD_CONECTIVIDAD_BOSQUE_BRIPARIO_WEB.TIF /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ PROBABILIDAD_CONECTIVIDAD_BOSQUE_BRIPARIO.TIF
```
