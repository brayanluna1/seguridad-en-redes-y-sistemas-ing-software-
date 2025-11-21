# Descripción

El desafío **substitution2** es la tercera entrega de la serie de cifrados por sustitución de picoCTF 2022. Mantiene la misma base del cifrado clásico: cada letra del texto original es reemplazada por otra según un mapeo fijo.  
A diferencia de _substitution0_ y _substitution1_, esta versión requiere un **análisis más cuidadoso**, ya sea porque el texto es más largo, las frecuencias están más equilibradas o la sustitución genera patrones menos evidentes.  
El video de referencia (_picoCTF 2022 | Cryptography | substitution2_, canal number0x01) muestra cómo utilizar herramientas automáticas de descifrado y complementar el proceso con revisión manual para obtener la flag.

# Solución

1. **Obtener el texto cifrado** del reto.
    
2. **Aplicar una herramienta de análisis de sustitución**, como:
    
    - Automatizadores de análisis de frecuencia.
        
    - Solvers de sustitución monoalfabética.
        
3. **Revisar el descifrado automático inicial**, que usualmente resuelve una parte significativa del texto.
    
4. **Corregir manualmente sustituciones incorrectas** observando:
    
    - Palabras comunes que no encajan.
        
    - Letras que aparecen en contextos imposibles.
        
    - Patrones de repetición y estructura del inglés.
        
5. **Ajustar el mapeo de letras** hasta que el texto tenga coherencia completa.
    
6. **Localizar la flag** dentro del texto ya legible.
    
7. **Copiar la flag en formato picoCTF**, exactamente como aparece en el descifrado final.
    

# Notas adicionales

- El reto depende fuertemente del **análisis de frecuencia**, pero su dificultad radica en que el solver no resuelve todo al 100%.
    
- Las últimas correcciones suelen ser manuales: identificar palabras que “casi” se entienden y ajustar letras individuales.
    
- Es un excelente ejercicio de observación de patrones y validación contextual del inglés.
    
- El video es breve porque el solver hace la mayor parte del trabajo, y solo requiere pequeños ajustes finales.
    

# Referencias

- Video: _picoCTF 2022 | Cryptography | substitution2_ — number0x01  
    [http://googleusercontent.com/youtube_content/25](http://googleusercontent.com/youtube_content/25)