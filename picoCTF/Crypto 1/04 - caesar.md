# Descripción
Se proporciona un texto ilegible (“garbled”) cuyo título **caesar** adelanta que está cifrado con un **Cifrado César**.  
El reto consiste en descifrar el mensaje aplicando el desplazamiento correcto (shift), el cual **no se proporciona** explícitamente.  
El objetivo es revelar la **flag en formato picoCTF{...}**.

# Solución
1. Se toma el texto cifrado entregado en el reto.  
2. Como el Cifrado César solo tiene 25 posibles claves, se usa fuerza bruta para probar todos los desplazamientos.  
3. Se emplea una herramienta online de Cifrado César (como *dcode.fr*), que automáticamente muestra los resultados para todos los shifts.  
4. Durante la revisión de las rotaciones, se identifica que **la rotación correcta es la número 4**.  
5. Se copia el texto completamente legible correspondiente al *shift 4*.  
6. Dentro del texto descifrado aparece la **flag**, la cual se extrae y se entrega a la plataforma para completar el reto.

# Notas adicionales
* El Cifrado César es uno de los cifrados más simples, por lo que la técnica estándar es siempre la fuerza bruta.  
* Es importante revisar cada shift buscando texto con estructura coherente, ya que solo uno producirá inglés legible.  
* No se requiere programación ni herramientas avanzadas; una herramienta de rotación automática es suficiente.

# Referencias
* Cifrado César – Explicación clásica del desplazamiento alfabético.  
* Herramienta utilizada: https://www.dcode.fr/caesar-cipher  
* Documentación general de picoCTF y picoGym.
