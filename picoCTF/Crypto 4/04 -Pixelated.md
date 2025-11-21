# Descripción

Se tienen dos imágenes **scrambled1.png** y **scrambled2.png**, que están **pixeladas o mezcladas**.  
El objetivo del desafío es **reconstruir la imagen original** combinando ambas y así obtener la _flag_ oculta en la imagen resultante.

# Solución

1. **Obtención de las imágenes**
    
    ```bash
    wget https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled1.png
    wget https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled2.png
    ```
    
    - Ambas imágenes fueron descargadas correctamente y tienen tamaños similares (~193 KB).
        
2. **Preparación del entorno Python**
    
    - Se creó un entorno virtual `venv_ctf` y se instaló **Pillow** para manipular imágenes:
        
        ```bash
        pip install Pillow
        ```
        
    - Esto permitió trabajar con scripts de Python que procesan las imágenes.
        
3. **Reconstrucción de la imagen**
    
    - Se escribió un script `imagen2.py` para **combinar las imágenes**.
        
    - El método consistió en iterar sobre los píxeles de ambas imágenes y reconstruir el contenido original mediante técnicas de superposición o mezcla según patrón conocido.
        
    - **Ejecución del script:**
        
        ```bash
        python3 imagen2.py
        ```
        
        - Esto generó un archivo `flag.png` que contiene la imagen completa y la _flag_ legible visualmente.
            
4. **Visualización de la imagen resultante**
    
    - En entornos de terminal sin GUI se utilizó **catimg**:
        
        ```bash
        sudo apt install catimg
        catimg flag.png
        ```
        
    - Alternativamente, en entornos con GUI se podría abrir con `xdg-open flag.png`.
        
5. **Obtención de la flag**
    
    - Al visualizar `flag.png`, la _flag_ se mostró claramente como texto incrustado en la imagen.
        
    - **Flag final:**
        
        ```
        picoCTF{pixelated_flag_here}
        ```
        

# Notas adicionales

- El reto es un clásico de **esteganografía visual** donde la información está fragmentada en múltiples imágenes.
    
- Herramientas clave utilizadas: **Python + Pillow**, **catimg** para terminal.
    
- La solución requiere **analizar patrones de píxeles** y reconstruir la imagen completa para leer la flag.
    

# Referencias

- Pillow Documentation: [https://pillow.readthedocs.io](https://pillow.readthedocs.io/)
    
- catimg (terminal image viewer): [https://github.com/posva/catimg](https://github.com/posva/catimg)
    
- Técnicas de esteganografía y pixel scrambling en CTFs.