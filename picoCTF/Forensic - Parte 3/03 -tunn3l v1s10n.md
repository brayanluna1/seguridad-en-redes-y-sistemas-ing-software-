# Descripción
El desafío consiste en recuperar una *flag* oculta dentro de un archivo aparentemente corrupto llamado `flag`. Aunque el archivo era de tipo Bitmap (`.bmp`), su cabecera estaba dañada y las dimensiones de la imagen ocultaban parte del contenido. La resolución implicó reparar la cabecera y ajustar la altura de la imagen para revelar la flag.

# Solución
1. **Análisis inicial y reparación de la cabecera**
   - Se identificó el tipo de archivo mediante un editor hexadecimal:
     ```bash
     xxd flag | head
     ```
   - Resultado: secuencia inicial `42 4D`, confirmando **Bitmap (`.bmp`)**.
   - Se renombró el archivo:
     ```bash
     mv flag flag.bmp
     ```
   - Se detectó corrupción en la cabecera comparando con un archivo BMP estándar y se corrigieron los valores de cabecera incorrectos (`36 00`, `28 00`).

2. **Determinación de dimensiones actuales**
   - Se usó `exiftool` para verificar dimensiones:
     ```bash
     exiftool flag.bmp
     ```
   - Dimensiones reportadas: **1134 x 306** (ancho x alto).
   - Los bytes de la altura y ancho estaban en **Little Endian**:
     - Ancho (1134) = `0x46E` → `6E 04`
     - Alto (306) = `0x132` → `32 01`

3. **Ajuste de altura para revelar contenido**
   - Se aumentó la altura a 850 píxeles:
     - 850 = `0x352` → Little Endian = `52 03`
   - Se reemplazaron los bytes de altura en la cabecera:
     ```hex
     32 01 → 52 03
     ```

4. **Visualización y recuperación de la flag**
   - Al abrir `flag.bmp` con la altura corregida, la parte inferior de la imagen reveló la flag oculta:
     ```text
     picoCTF{qu1t3_a_v13w_2020}
     ```

# Notas adicionales
- El nombre del reto (“tunnel vision”) fue clave para inferir que el contenido estaba parcialmente oculto por la altura de la imagen.
- Los valores de cabecera de un BMP deben respetar formato y Little Endian para que el archivo sea válido.
- Este reto combina **análisis forense de archivos** y **edición hexadecimal** para revelar información oculta.

# Resultado final
```
picoCTF{qu1t3_a_v13w_2020}
```

