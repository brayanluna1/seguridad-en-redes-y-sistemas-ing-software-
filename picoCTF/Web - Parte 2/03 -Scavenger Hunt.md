# Reto
Scavenger Hunt (picoCTF 2021)

# Descripción
El reto es una "búsqueda del tesoro" (*scavenger hunt*) en un sitio web. La descripción es: "Hay información interesante oculta por el sitio, ¿puedes encontrarla?" El objetivo es buscar la *flag* que está dividida en varias partes y oculta en diferentes archivos comunes de un servidor web.

# Solución
La solución consiste en buscar manualmente las cinco partes de la *flag* navegando a diferentes ubicaciones y archivos del sitio web:

1.  **Parte 1:** Se encuentra en el **código fuente** (View Page Source) de la página principal (HTML) 
2.  **Parte 2:** Se encuentra al inspeccionar el **archivo CSS** (Cascading Style Sheet) que se usa en la página .
3.  **Parte 3:** Se encuentra navegando al archivo **`robots.txt`** (usado para guiar a los rastreadores de motores de búsqueda) .
4.  **Parte 4:** Se encuentra navegando al archivo **`.htaccess`** (un archivo de configuración del servidor Apache) .
5.  **Parte 5:** Se encuentra navegando al archivo **`.DS_Store`** (un archivo de metadatos creado por macOS, a menudo expuesto accidentalmente) .

Una vez obtenidas las cinco partes, la solución se completa **concatenándolas** en el orden correcto para formar la *flag* final de `picoCTF{...}`.

# Notas adicionales
Este desafío es un excelente ejemplo de la fase de **Information Gathering** o **Enumeración de Contenido**, donde se buscan archivos y directorios comunes (a menudo sensibles o con metadatos) que los desarrolladores pueden olvidar restringir. Los archivos como `robots.txt`, `.htaccess`, y `.DS_Store` son objetivos habituales en este tipo de retos de Web Exploitation.

# Referencias
[picoCTF 2021 Scavenger Hunt](http://www.youtube.com/watch?v=6pQw4s5wJGM)
