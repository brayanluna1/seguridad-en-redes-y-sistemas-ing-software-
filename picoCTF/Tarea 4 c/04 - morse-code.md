# Descripción

El desafío **morse-code** proporciona un archivo de audio en formato `.wav` que contiene un mensaje codificado en **Código Morse**. El objetivo es decodificar ese mensaje y convertirlo al formato de _flag_ esperado por picoCTF. El walkthrough del video (_PicoCTF morse-code_, canal COZT) muestra un método rápido utilizando un decodificador en línea en lugar de herramientas más pesadas como Audacity.

# Solución

1. **Obtener el archivo de audio** del reto (`Morse_code_Challenge.wav`).
    
2. **Identificar la pista del desafío:** se menciona el uso de **Audacity** para analizar el audio, aunque no es estrictamente necesario.
    
3. **Método rápido:** cargar el archivo en un **decodificador de Morse online**.
    
4. **Decodificar el contenido del audio:** reproducir el `.wav` en el decodificador para obtener el **texto plano** resultante.
    
5. **Formatear la flag:**
    
    - Tomar la cadena decodificada.
        
    - Reemplazar todos los **espacios** con **guiones bajos `_`**.
        
    - Envolver la cadena resultante dentro de `picoCTF{...}`.
        
6. **Enviar la flag generada:** si el formato es correcto, el reto se resuelve exitosamente.
    

# Notas adicionales

- La pista sobre Audacity sirve solo para análisis manual, pero no es necesaria.
    
- Los decodificadores online interpretan el audio de forma automática, ahorrando tiempo.
    
- Morse convierte tonos largos/cortos (– •) en letras, por lo que mientras el audio sea claro, la decodificación será directa.
    
- El paso más importante es **aplicar el formato correcto de picoCTF** al texto resultante.
    

# Referencias

- Video: _PicoCTF morse-code_ — COZT  
    [http://googleusercontent.com/youtube_content/21](http://googleusercontent.com/youtube_content/21)