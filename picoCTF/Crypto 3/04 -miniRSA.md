# Descripción

El objetivo del reto es descifrar el texto cifrado proporcionado utilizando RSA con un exponente público demasiado pequeño (**E = 3**).  
Este tipo de configuración debilita el cifrado cuando el mensaje original es pequeño y cumple que ( M^3 < N ), permitiendo recuperar el mensaje sin necesidad de factorizar el módulo.

# Solución

1. **Obtención de parámetros del archivo ciphertext**
    
    |Parámetro|Valor obtenido|Método|
    |---|---|---|
    |Texto cifrado (C)|Número entero muy grande|Descargando el archivo _ciphertext_ y visualizando con `cat`|
    |Módulo (N)|Entero de 284 bits|Extraído del archivo|
    |Exponente público (E)|**3**|Extraído del archivo y confirmado por la pista|
    
2. **Identificación de la vulnerabilidad**  
    La pista indicaba: _“¿Cómo podría un valor E demasiado pequeño afectar la seguridad?”_  
    Esto apunta al ataque de **Low Public Exponent (E=3)**.  
    Si se cumple:  
    [  
    M^3 < N  
    ]  
    entonces no hay reducción modular y:  
    [  
    C = M^3  
    ]  
    Para recuperar el mensaje basta con calcular la **raíz cúbica exacta** de ( C ).
    
3. **Procedimiento aplicado**
    
    - Se ingresaron los valores **C**, **N** y **E=3** en una herramienta online de descifrado/solver RSA.
        
    - La herramienta aplicó el ataque automáticamente.
        
    - Se obtuvo el valor de ( M ) (mensaje original) y luego su conversión a texto.
        
4. **Resultado final**
    
    |Resultado|Contenido|
    |---|---|
    |Flag descifrada|`picoCTF{need_a_larger_encode}`|
    

# Notas adicionales

- RSA con **E=3** solo es seguro si se aplican correctamente padding y técnicas como OAEP.
    
- Este reto demuestra por qué los mensajes sin padding son vulnerables incluso sin factorizar N.
    

# Referencias

- Documentación clásica del ataque Low Public Exponent (E=3).
    
- Material oficial de picoCTF sobre criptografía RSA.