# Descripción
El reto proporciona una imagen llamada `buildings.png` y sugiere que hay información oculta dentro de ella. La frase “hay algo en el edificio” indica que se trata de un reto de esteganografía, donde la información suele encontrarse dentro de los bits de un archivo multimedia. La tarea consiste en extraer la bandera oculta en la imagen.

# Solución
## Paso 1: Descarga del archivo
Se obtiene el archivo para su análisis:

```bash
wget https://jupiter.challenges.picoctf.org/static/011955b303f2d52a522423acf93d3879/buildings.png
```

## Paso 2: Reconocimiento inicial
Se valida el tipo de archivo y se revisan cadenas internas:

```bash
file buildings.png
# PNG image data, 657 x 438, 8-bit/color RGBA, non-interlaced
```

```bash
strings buildings.png | grep pico
# (Sin resultados)
```

Esto indica que la bandera no está visible en texto plano.

## Paso 3: Análisis esteganográfico
Dado que el archivo es PNG con canal alfa, se analiza en busca de datos ocultos usando los bits menos significativos (LSB). Para ello se usa la herramienta `zsteg`:

```bash
zsteg -a buildings.png
```

Salida relevante:

```
b1,rgb,lsb,xy .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"
```

La bandera estaba oculta manipulando el bit menos significativo de los canales RGB, técnica clásica de esteganografía LSB. `zsteg` reconstruyó automáticamente el mensaje.

## Bandera:
```
picoCTF{h1d1ng_1n_th3_b1t5}
```

# Notas adicionales
- El archivo PNG no mostraba corrupción, lo cual es típico en esteganografía LSB.
- El canal alfa no contenía información oculta significativa, todo estaba en los canales RGB.
- `zsteg` es especialmente eficaz con PNG y BMP, por lo que suele ser una de las primeras herramientas a utilizar.
- La bandera se identifica leyendo el LSB de cada canal en orden secuencial (xy).

# Referencias
- Herramienta zsteg: https://github.com/zed-0xff/zsteg
- Concepto LSB Steganography: https://en.wikipedia.org/wiki/Least_significant_bit
- Comandos útiles:
  - `sudo gem install zsteg`
  - `zsteg -a <archivo>`

