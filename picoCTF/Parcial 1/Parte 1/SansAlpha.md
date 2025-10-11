# Descripción

The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.

# Solución

Primero, me conecté al servidor e investigué el sistema de archivos usando comodines y aprovechando los mensajes de error para obtener información.

Bash

```
SansAlpha$ *
bash: blargh: command not found
```

Este error me reveló la existencia de un archivo o directorio llamado `blargh`. Luego, intenté explorar un nivel más profundo.

Bash

```
SansAlpha$ */*
bash: blargh/flag.txt: Permission denied
```

Este segundo error fue aún más útil, ya que me confirmó que `blargh` era un directorio y que dentro contenía el archivo `flag.txt`. Como no podía usar comandos como `cat` para leerlo, busqué una forma alternativa de acceder al contenido del archivo. La solución fue usar el comando `base64`.

Construí un "glob" o patrón de comodines muy específico para ejecutar `/usr/bin/base64` y le pasé la ruta al archivo de la bandera.

Bash

```
SansAlpha$ /???/???[!_]64 ??????/????.???
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV8zNmE2NzRjMH0=
```

El servidor ejecutó el comando y me devolvió el contenido del archivo `flag.txt` codificado en Base64. Finalmente, decodifiqué la cadena en mi máquina local para obtener la bandera.

Bash

```
┌──(BenduOlo253㉿LaBenduPC)-[~]
└─$ echo "cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV8zNmE2NzRjMH0=" | base64 -d
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_36a674c0}
```

**Solución:** `picoCTF{7h15_mu171v3r53_15_m4dn355_36a674c0}`

# Notas adicionales

Esta solución es un excelente ejemplo de cómo explotar un entorno altamente restringido mediante la combinación de varias técnicas avanzadas.

### Fuga de Información por Errores (Information Leaks)

Los mensajes de error como `command not found` o `Permission denied` no fueron fallos, sino **éxitos**. Nos proporcionaron información crucial sobre la estructura del sistema de archivos (nombres de archivos y directorios) que de otro modo estaría oculta.

### Globbing Avanzado con `[!...]`

El patrón `/???/???[!_]64` es una forma muy inteligente de apuntar a `/usr/bin/base64`.

- `[...]` define un conjunto de caracteres a coincidir.
    
- `[!...]` define un conjunto **negado**, es decir, coincide con cualquier carácter **excepto** los que están dentro.
    
- El patrón `???[!_]64` busca un nombre de archivo que empiece con tres caracteres cualesquiera, seguido de un carácter que **no sea un guion bajo (`_`)**, y que termine en `64`. Esta especificidad fue clave para evitar que el patrón coincidiera con otros archivos del sistema.
    

### `base64` como Alternativa a `cat`

Cuando un sistema te impide leer archivos directamente (bloqueando `cat`, `head`, `more`, etc.), puedes usar otros programas que procesen archivos y muestren su salida en la terminal. `base64` es una opción perfecta: lee el archivo, lo codifica en texto plano (que sí se puede imprimir) y te permite decodificarlo tranquilamente en tu propia máquina.

# Referencias

- Investigación y experimentación propia.
- https://medium.com/@niceselol/picoctf-2024-sansalpha-86bbdb58bde6
- Asistente Gemini