### ❓ Objetivo
Rastrear una serie de redirecciones para encontrar la URL final que contiene la bandera oculta.

### 🔬 Análisis de la Vulnerabilidad
1.  **Mecanismo:** El servidor usa redirecciones temporales (código HTTP **302**) para guiar al usuario a través de un laberinto de URLs.
2.  **Codificación:** El destino de cada redirección está oculto en el encabezado `Location` y codificado en **Base64**.
3.  **Técnica Clave:** El navegador borra las redirecciones, por lo que es necesario usar la opción **"Preserve Log"** en la pestaña Network de las Herramientas de Desarrollador (F12) para conservar el historial.

### 🛠️ Pasos de Explotación
1.  **Preparación:** Abrir F12, ir a la pestaña **Network** y activar la opción **"Preserve Log"**.
2.  **Captura del Primer Enlace:** Iniciar sesión con las credenciales (`test/test`!).
3.  **Rastreo 1:** En la pestaña Network, buscar la primera solicitud con el estado **302**. Copiar el valor del encabezado **`Location`** (que está en Base64).
4.  **Decodificación 1:** Decodificar la cadena Base64 para obtener la **segunda URL del laberinto**.
5.  **Rastreo 2:** Navegar manualmente a la segunda URL y repetir el paso 3 para capturar el segundo encabezado **`Location`**.
6.  **Decodificación Final:** Decodificar la segunda cadena Base64. El texto resultante es la bandera.

### 🔑 Bandera
`picoCTF{proxies_all_the_way_df44c94c}`