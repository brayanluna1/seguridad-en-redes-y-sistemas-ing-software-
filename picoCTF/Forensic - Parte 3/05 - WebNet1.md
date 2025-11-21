# Descripción
El objetivo de este desafío era recuperar la flag oculta dentro de un archivo de captura de paquetes cifrado con TLS. Se proporcionó una clave privada que permitía descifrar el tráfico y extraer el contenido de la capa de aplicación. A diferencia de otros retos de TLS, en este caso se usó una herramienta de línea de comandos para realizar el análisis.

# Solución
1. En lugar de Wireshark, utilicé la herramienta de terminal `ssldump`, ideal para descifrar tráfico TLS directamente desde la línea de comandos.
2. Ejecuté el comando de descifrado proporcionando el archivo de captura y la clave privada:
   ssldump -r [archivo_captura] -k [archivo_clave] -d > output
   - `-r` carga el archivo de captura.
   - `-k` especifica la clave privada.
   - `-d` imprime la información de la capa de aplicación descifrada.
3. Todo el tráfico descifrado quedó almacenado en el archivo `output`.
4. Revisé su contenido con:
   cat output
5. Dentro del archivo busqué la cadena relacionada con PicoCTF.
6. Identifiqué varias falsas flags que contenían el mensaje “this is not your flag anymore”.
7. Tras revisar cuidadosamente, encontré la flag válida con el formato correcto:
   picoCTF{honey_roasted_peanuts}

# Notas adicionales
El uso de `ssldump` simplifica el análisis cuando no se necesita inspección gráfica. Este método funciona solo en capturas TLS que usan RSA key exchange; no sirve para sesiones que emplean claves efímeras como DHE o ECDHE. El reto también incluye falsas flags para obligar a revisar cuidadosamente el tráfico descifrado.

# Referencias
Proceso realizado utilizando ssldump para descifrar tráfico TLS, búsqueda manual en el archivo de salida y verificación de la flag correcta dentro del contenido descifrado.
