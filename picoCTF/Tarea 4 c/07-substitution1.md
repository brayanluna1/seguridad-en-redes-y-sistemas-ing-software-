
# Descripción

El desafío **substitution1** es la continuación directa de _substitution0_ y también utiliza un **cifrado por sustitución simple**. A diferencia del reto anterior, aquí **no se proporciona un alfabeto de referencia**, por lo que la única forma práctica de romper el cifrado es mediante **análisis de frecuencia**.  
El video de referencia (_pico2022 substitution1_, canal Martin Carlisle) muestra cómo analizar las letras más frecuentes del texto cifrado, compararlas con las más comunes en inglés e ir construyendo el mapeo correcto hasta revelar la flag.

# Solución

1. **Obtener el texto cifrado** del reto.
    
2. **Aplicar análisis de frecuencia** al texto:
    
    - Identificar las letras más repetidas.
        
    - Compararlas con la frecuencia típica del inglés (`e`, `t`, `a`, `o`, `i`, `n`, `s`, `h`, `r`).
        
3. **Ingresar el texto en una herramienta de sustitución** que soporte descifrado por frecuencia.
    
4. **Observar la sustitución automática inicial**, que suele resolver la mayor parte del texto.
    
5. **Corregir manualmente errores** típicos del análisis de frecuencia:
    
    - Revisar letras que no encajan en contexto.
        
    - Ajustar el mapeo (por ejemplo, corregir la sustitución incorrecta de `J` → `Q`).
        
6. **Leer el texto ya consistente** una vez corregidas las sustituciones defectuosas.
    
7. **Identificar y copiar la flag** en el formato picoCTF exacto.
    

# Notas adicionales

- El análisis de frecuencia no es perfecto: siempre es normal que una o dos letras estén equivocadas.
    
- Este reto está diseñado para practicar el ajuste manual tras el descifrado automático.
    
- La mayor parte del trabajo consiste en observar patrones de palabras.
    
- El proceso del video es fluido: analizar → aplicar herramienta → corregir → obtener flag.
    

# Referencias

- Video: _pico2022 substitution1_ — Martin Carlisle  
    [http://googleusercontent.com/youtube_content/24](http://googleusercontent.com/youtube_content/24)