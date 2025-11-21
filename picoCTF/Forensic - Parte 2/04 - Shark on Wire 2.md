# Descripción
Este reto consiste en analizar un archivo de captura de red (PCAP) para encontrar datos transmitidos sin cifrar que contienen la bandera del desafío. El análisis se realiza principalmente con Wireshark, filtrando protocolos y revisando flujos de comunicación donde podría aparecer texto plano con la bandera.

# Solución
1. Descargar el archivo PCAP proporcionado por el reto.
2. Abrir el archivo en Wireshark.
3. Aplicar filtros para reducir el tráfico visible:
   - Ver solo tráfico HTTP:
     ```
     http
     ```
   - Buscar directamente patrones que coincidan con la bandera:
     ```
     frame contains "picoCTF"
     ```
   - Explorar otros protocolos no cifrados:
     ```
     ftp or telnet
     ```
4. Seleccionar un paquete relevante y seguir el flujo completo:
   - Clic derecho → "Follow" → "TCP Stream".
   - Revisar la conversación en texto plano.
5. Ubicar la bandera dentro del flujo analizado. Aparecerá con el formato típico:
   ```
   picoCTF{...}
   ```

# Notas adicionales
- En retos tipo PCAP, las banderas suelen estar en protocolos no cifrados como HTTP, FTP o TELNET.
- “Follow TCP Stream” es una de las funciones más poderosas para ver datos concatenados y reconstruidos.
- Algunos paquetes pueden contener partes de la bandera separados, por lo que siempre es útil revisar múltiples flujos si el primero no la contiene.

# Referencias
- Video guía: https://www.youtube.com/watch?v=e_k9fFqu-BU
- Documentación Wireshark: https://www.wireshark.org/docs/

