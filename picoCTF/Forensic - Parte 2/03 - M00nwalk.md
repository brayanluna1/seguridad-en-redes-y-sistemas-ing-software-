# Descripción
El reto consiste en analizar un archivo de audio llamado `message.wav` que contiene una transmisión codificada con SSTV (Slow Scan Television). El objetivo es decodificar esta señal para obtener una imagen oculta, la cual incluye una cadena en Base64 que finalmente revela la bandera del reto.

# Solución
1. Clonar el repositorio de la herramienta utilizada para decodificar señales SSTV:
   ```bash
   git clone https://github.com/dronir/sstv.git
   ```
2. Instalar la herramienta:
   ```bash
   cd sstv
   sudo python3 setup.py install
   ```
3. Ejecutar la decodificación del archivo de audio:
   ```bash
   sstv -d message.wav
   ```
   Esta acción genera el archivo `result.png` que contiene la imagen extraída del audio.
4. Abrir la imagen generada:
   ```bash
   xdg-open result.png
   ```
   En la imagen aparece una cadena en Base64.
5. Decodificar la cadena Base64 para obtener la bandera:
   ```bash
   echo -n "cGljb0NURntiZWVwX2Jvb3BfaW1faW5fc3BhY2V9" | base64 --decode
   ```
   **Bandera final:** `picoCTF{beep_boop_im_in_space}`

# Notas adicionales
- El modo de SSTV es detectado automáticamente por la herramienta (en el video se identificó como “Scotty 1”).
- La herramienta `sstv` permite decodificar audio SSTV sin necesidad de interfaces gráficas adicionales.
- Si `git clone` presenta problemas, se puede descargar el ZIP del repositorio y continuar el proceso normalmente.

# Referencias
- Video utilizado como guía: https://www.youtube.com/watch?v=ZD0Txwlnkqw
- Repositorio de la herramienta SSTV: https://github.com/dronir/sstv
- Documentación de comandos: `base64`, `xdg-open`

