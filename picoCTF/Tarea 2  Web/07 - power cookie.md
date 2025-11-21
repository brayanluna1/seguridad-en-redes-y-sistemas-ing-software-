# Descripción  
El reto **power cookie** consiste en explotar la mala gestión de cookies dentro de una aplicación web. El sitio asigna un valor dentro de una cookie que determina los privilegios del usuario (por ejemplo, invitado vs. usuario autorizado). Si el valor se modifica manualmente, el servidor no valida adecuadamente la integridad de dicha cookie, permitiendo elevar privilegios y acceder a la flag.

# Solución  
1. Acceder al sitio y seleccionar **“continue as guest”**.  
2. Observar que el sistema rechaza a los usuarios invitados y no permite continuar.  
3. Abrir las herramientas de desarrollador (DevTools) → pestaña **Application** → sección **Cookies**.  
4. Localizar la cookie relevante (por ejemplo, `wiki` o valor equivalente) que controla el estado del usuario.  
5. Cambiar su valor de **0** (invitado) a **1** (acceso/autorizado).  
6. Recargar la página para que el servidor lea el nuevo valor.  
7. La página mostrará ahora la **flag** de picoCTF.

# Notas adicionales  
- Este reto es un ejemplo clásico de **inseguridad en cookies sin firma**, donde no se valida la integridad ni autenticidad del valor almacenado.  
- También enseña la importancia de usar cookies firmadas, JWT o mecanismos de sesión robustos.  
- Puede resolverse sin herramientas externas, únicamente con DevTools del navegador.

# Referencias  
- Video: *power cookie | picoCTF 2022*  
- Canal: Rahul Singh Chauhan  
- URL del video: http://www.youtube.com/watch?v=zJD75nuAlbQ  
- Contenido accesible: http://googleusercontent.com/youtube_content/5
