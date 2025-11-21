# Reto
waves over lambda

# Descripción
**Título del Reto:** waves over lambda  
**Competencia/Categoría:** picoCTF 2019, Criptografía.  
**Objetivo:** Descifrar un mensaje codificado para encontrar la flag secreta .  
**Mecanismo:** Identificar y aplicar el método correcto de descifrado según el patrón del texto cifrado.

# Solución
La resolución se basa en analizar el texto cifrado mediante una herramienta web para identificar el tipo de cifrado y luego aplicar una ruptura automática del mismo.

1. **Obtención del texto cifrado:**  
   El video muestra directamente el texto ya cifrado y listo para decodificar (el proceso de obtención no se incluye) .

2. **Uso de una herramienta de análisis de cifrado:**  
   Se emplea una herramienta web donde el texto cifrado es pegado para iniciar el análisis .

3. **Primer intento de descifrado:**  
   Tras pegar el texto, la herramienta genera un resultado, pero este no es legible ni interpretable .

4. **Segundo intento mediante ruptura de cifrado:**  
   El resultado generado se copia nuevamente .  
   Luego se utiliza la función **Break Cipher** de la herramienta, diseñada para analizar patrones y forzar la decodificación incluso sin clave conocida .  
   Esto sugiere que el cifrado podía corresponder a un método como transposición o un cifrado polialfabético sin clave explícita.

5. **Descifrado y obtención de la flag:**  
   Tras la ruptura del cifrado, el texto se vuelve legible en inglés , mostrando el mensaje:  
   **"Congrats! Here is your Flag"** .  
   En este mensaje aparece la flag final en formato **picoCTF{...}**, que se toma y se entrega en la plataforma.
6.  flag:  frequency_is_c_over_lambda_b613e7dd

# Notas adicionales
- La herramienta utilizada permite romper cifrados sin necesidad de conocer la clave, lo cual es ideal para retos donde el tipo de cifrado no está explícito.  
- El cifrado no se identifica directamente, pero el uso de funciones automáticas indica que utiliza patrones predecibles.  
- El flujo del video sugiere que el cifrado requería más que un simple descifrado directo.

# Referencias
- Herramienta web de análisis y ruptura de cifrados mostrada en el video.  
- Plataforma picoCTF 2019 para validación de la flag.
