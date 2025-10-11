
### ❓ Objetivo
Obtener acceso de administrador para leer el libro "Flag", explotando una clave de firma JWT débil y codificada.

### 🔬 Análisis de la Vulnerabilidad
1.  **Vulnerabilidad:** El código fuente (analizado en el tutorial) revela un *fallback* (respaldo) en el `SecretGenerator.java`.
2.  **Clave Secreta:** La clave de firma del JWT está codificada como **`1234`**.
3.  **Roles:** El rol de administrador es **`Admin`**.

### 🛠️ Pasos de Explotación
1.  **Captura del Token:** Iniciar sesión como `user/user` y obtener el token JWT de la sesión del navegador (Herramientas de Desarrollador > Application > Local Storage).
2.  **Modificación (Payload):** Usar un editor de JWT (como Burp Suite o una herramienta online que permita firmar) para modificar la Carga Útil (Payload) del token:
    * Cambiar `"role": "Free"` a **`"role": "Admin"`**.
    * Cambiar `"userId": 1` a **`"userId": 2`**.
3.  **Re-Firma Forzada:** Firmar el token modificado usando la clave secreta débil **`1234`**.
4.  **Inyección:** Copiar el nuevo token de administrador y reemplazar el token de sesión (`auth-token`) en el **Local Storage** del navegador.
5.  **Resultado:** Recargar la página y acceder al libro "Flag".

### 🔑 Bandera
`picoCTF{w34k_jwt_n0t_g00d_6e5d7df5}`

***

