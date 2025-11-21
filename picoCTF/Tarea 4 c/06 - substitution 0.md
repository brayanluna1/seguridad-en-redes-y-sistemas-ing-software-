# Descripción

El desafío **substitution 0** utiliza un **cifrado por sustitución**, donde cada letra del texto original es reemplazada sistemáticamente por otra letra o símbolo. Este tipo de cifrados suele representarse mediante un desplazamiento (César / ROT-N), un mapeo directo de alfabeto o una clave corta de sustitución.  
El video de referencia (_substitution 0 | Cryptography | picoCTF Walkthrough_, canal PenTest Fusion) muestra el proceso típico de introducir el texto cifrado en una herramienta de sustitución y aplicar el método adecuado hasta revelar un mensaje legible que contiene la flag.

# Solución

1. **Obtener el texto cifrado** proporcionado por el reto.
    
2. **Identificar el tipo de sustitución** probando métodos comunes:
    
    - Cifrado César / ROT-N.
        
    - ROT13.
        
    - Sustitución directa con abecedario reorganizado.
        
    - Vigenère con clave simple (si el reto lo sugiere).
        
3. **Ingresar el texto cifrado** en una herramienta de sustitución (online o local).
    
4. **Probar desplazamientos o claves** hasta que el resultado sea legible.
    
5. **Detectar el mensaje claro** y ubicar la flag dentro del texto descifrado.
    
6. **Copiar la flag** exactamente en el formato picoCTF.
    

# Notas adicionales

- El reto está diseñado como introducción básica a los cifrados de sustitución.
    
- La pista principal suele ser que el texto descifrado se vuelve legible tras aplicar un simple ROT-N.
    
- No requiere análisis estadístico avanzado.
    
- El video confirma que el proceso completo es directo: elegir método → aplicar sustitución → leer flag.
    

# Referencias

- Video: _substitution 0 | Cryptography | picoCTF Walkthrough_ — PenTest Fusion  
    [http://googleusercontent.com/youtube_content/23](http://googleusercontent.com/youtube_content/23)