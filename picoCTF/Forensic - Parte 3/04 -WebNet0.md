# Descripción
El objetivo de este desafío era recuperar la flag oculta dentro de una captura de paquetes (.pcap) que contenía tráfico cifrado con TLS, utilizando la clave proporcionada. El archivo incluía tráfico HTTPS en el puerto 443 y requería ser descifrado mediante la clave RSA dada para poder visualizar el contenido HTTP.

# Solución
1. Abrí el archivo `capture.pcap` en Wireshark.
2. Verifiqué las estadísticas generales: la captura tenía aproximadamente 39 paquetes, una sola conversación TCP/IP y la mayor parte del tráfico correspondía a TLS. Al seguir un stream TCP, los datos eran ilegibles debido al cifrado.
3. Para descifrar TLS:
   - Fui a Edit > Preferences.
   - Entré a Protocols > TLS.
   - En “RSA Keys List” añadí una nueva entrada:
     - IP Address: 0.0.0.0
     - Port: 443
     - Protocol: http
     - Key File: pico_key
4. Después de aplicar los cambios, Wireshark mostró correctamente las capas HTTP y Line-based text data debajo de TLS.
5. Apliqué el filtro `http` para ver únicamente tráfico HTTP.
6. Seleccioné un paquete HTTP y abrí Follow > HTTP Stream.
7. Dentro de la respuesta HTTP 200 OK encontré un encabezado personalizado llamado “Pico-Flag” que contenía la flag.
8. Flag encontrada:
   picoCTF{n0_5h1m_5hr1mp_cr4ck3r5}

# Notas adicionales
La clave RSA proporcionada permite descifrar sesiones TLS antiguas que usan RSA key exchange. Si el reto hubiera usado Diffie-Hellman, la clave no habría funcionado. La estructura del PCAP y la ausencia de otros protocolos simplifica el análisis, enfocándose en configurar correctamente Wireshark para descifrar HTTPS.

# Referencias
Proceso realizado siguiendo paso a paso el análisis del tráfico TLS, la configuración de claves RSA en Wireshark y la inspección del flujo HTTP descifrado para encontrar la flag.
