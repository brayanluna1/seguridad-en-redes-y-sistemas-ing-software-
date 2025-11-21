# Descripción

El desafío consiste en descifrar una secuencia de **banderas marítimas internacionales** mostradas en una imagen.  
Cada bandera representa una **letra**, **número** o **carácter especial** del _International Code of Signals (ICS)_.  
El objetivo es mapear cada bandera a su símbolo correspondiente hasta reconstruir la flag final en formato `picoCTF{...}`.

# Solución

1. **Análisis inicial**
    
    - Se descarga la imagen del reto.
        
    - La pista indica que el significado de las banderas revela directamente la flag.
        
2. **Método de descifrado**
    
    - Se utiliza el estándar del **International Marine Signal Flags**.
        
    - Cada bandera se compara con la tabla ICS para obtener su equivalente alfanumérico.
        
    - También se puede usar una IA o una herramienta de reconocimiento para acelerar el mapeo.
        
3. **Proceso aplicado**
    
    - Se identificó la secuencia completa de banderas presentes en la imagen.
        
    - Las banderas fueron decodificadas una por una siguiendo el código ICS.
        
    - Durante el proceso se detectó un error menor (una ‘C’ mal interpretada), pero no afectó el resultado final.
        
4. **Flag obtenida**  
    `picoCTF{red_flags_and_stuff}`
    

# Notas adicionales

- El reto enseña a reconocer alfabetos no tradicionales (en este caso visuales).
    
- Las banderas marítimas siempre representan un único carácter, lo que facilita la decodificación.
    

# Referencias

- International Code of Signals (ICS) — Tabla de banderas marítimas.
    
- Estándar de banderas de señales internacionales utilizadas para comunicación naval.