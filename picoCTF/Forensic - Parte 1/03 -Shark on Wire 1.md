
Shark on Wire 1 

# Descripción
Desafío de la categoría **Forense** (*Forensics*) cuyo objetivo es recuperar la *flag* oculta dentro de un archivo de **captura de paquetes** (`capture.pcap`) [00:00:20]. La solución requiere el uso de una herramienta de análisis de protocolos de red como **Wireshark** para inspeccionar las corrientes de datos y reconstruir la comunicación.

## 💡 Concepto Clave: Análisis de Tráfico de Red (PCAP)
Los archivos **PCAP** (Packet Capture) contienen una grabación de todo el tráfico que pasa por una interfaz de red. El desafío se resuelve examinando el contenido de las sesiones de comunicación para identificar texto claro (la *flag*) transmitido.

# Solución
La solución se lleva a cabo analizando el archivo `capture.pcap` con Wireshark, enfocándose en la búsqueda y reconstrucción de las corrientes de datos (streams) relevantes.

## 🐧 Fase 1: Descarga y Apertura
1.  **Descargar el Archivo:** Se utiliza `wget` para obtener el archivo de captura (`.pcap`) [00:00:45].
    ```bash
    wget [URL_DEL_ARCHIVO] -O capture.pcap
    ```
2.  **Abrir con Wireshark:** En entornos Linux, se usa `xdg-open` para iniciar el programa asociado con la extensión (`.pcap`), que es **Wireshark** [00:01:24].
    ```bash
    xdg-open capture.pcap
    ```

## 🦈 Fase 2: Análisis en Wireshark
1.  **Búsqueda Inicial:** Se utiliza la función de búsqueda (`Ctrl + F`) para buscar la cadena de texto **"pico"** dentro de los bytes del paquete, ya que este es el prefijo estándar de todas las *flags* de PicoCTF [00:02:32].
2.  **Seguimiento del Stream:** Una vez que se identifica un paquete que contiene la cadena "pico" (paquete sospechoso) [00:02:39], se hace clic derecho sobre él y se selecciona la opción **"Follow"** y luego **"UDP Stream"** [00:02:52] (dado que el tráfico encontrado estaba usando UDP).
3.  **Identificación de la Flag:** Dentro de la ventana de seguimiento de la corriente (stream), se navega a través de las diferentes corrientes de comunicación (Stream 0, 1, 2, etc.) hasta que se encuentra aquella que contiene el texto de la *flag* completa. En el *walkthrough* del video, la *flag* se encuentra en el **Stream #6** [00:03:27].
4.  **Recuperación:** Se copia la *flag* (`pctf{...}`) de la ventana del stream.

# Notas adicionales
El paso crucial fue la **reconstrucción de la sesión de comunicación** utilizando la función "Follow Stream" . Sin esta función, intentar buscar la *flag* manualmente en cada uno de los más de 2300 paquetes sería impráctico [00:01:43]. Esta técnica aísla toda la conversación (bidireccional) entre dos *endpoints* específicos, facilitando la identificación de la información sensible.

# Referencias
* Reto PicoCTF: Shark on Wire 1
* Video Walkthrough: [picoCTF 2019 - Forensics - Shark on Wire 1](http://www.youtube.com/watch?v=sfG-gL1ztFY)
* Herramienta principal: **Wireshark**
* Técnica: Análisis Forense de Red (Network Forensics)**