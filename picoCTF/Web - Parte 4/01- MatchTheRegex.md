# Descripción
El reto consiste en hacer coincidir una cadena de texto con una **expresión regular (Regex)** que se encuentra oculta en el código fuente de una página web . Al ingresar un texto que cumpla con el patrón definido por el Regex, el sistema revela la *flag*.

# Solución
1.  **Inspección del Código Fuente:** Se accede al código fuente (View Page Source) del sitio web para encontrar la expresión regular que debe ser igualada .
2.  **Identificación del Regex:** La expresión regular se identifica como: `^P.C.T.F!?$` (o una variante similar que sigue el patrón).
3.  **Análisis del Regex:**
    * `^`: Indica que la cadena debe comenzar inmediatamente.
    * `P`: La cadena debe comenzar con la letra 'P'.
    * `.`: Coincide con cualquier carácter (hay tres de estos).
    * `C`, `T`, `F`: Coinciden con las letras literales 'C', 'T' y 'F' en posiciones específicas.
    * `!?`: Indica que el carácter `!` es **opcional** .
    * `$`: Indica que la cadena debe terminar inmediatamente.
    * **Patrón de Coincidencia:** La cadena de entrada debe tener 7 u 8 caracteres, comenzar con 'P', y tener 'C', 'T', y 'F' en las posiciones definidas por los puntos (`.`).
4.  **Entrada de la Solución:** Se introduce una cadena que se ajusta al patrón. El ejemplo más sencillo y obvio que cumple con el patrón es **`PicoCTF`** (7 caracteres) o **`PicoCTF!`** (8 caracteres) . Al ingresar la cadena válida, el servidor responde con la *flag* .

# Notas adicionales
Este es un desafío de nivel introductorio que pone a prueba la capacidad del usuario para encontrar información en el código fuente y comprender la sintaxis básica de las expresiones regulares, en particular los metacaracteres de anclaje (`^`, `$`), el comodín (`.`) y el cuantificador opcional (`?`).

# Referencias
[picoCTF 2023 MatchTheRegex](http://www.youtube.com/watch?v=Me7vV4_iL6E)