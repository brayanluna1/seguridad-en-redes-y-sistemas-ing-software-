# Reto
Most Cookies (Flask Session Tampering)

# Descripción
El desafío requería obtener la *flag* de un sitio web construido con el *framework* **Flask** al escalar privilegios a la sesión de administrador. La aplicación utilizaba **cookies de sesión firmadas** para mantener el estado del usuario. La vulnerabilidad residía en que la **clave secreta** (`app.secret_key`) utilizada para la firma criptográfica se seleccionaba de una lista pequeña y conocida de 28 nombres de galletas, lo que la hacía predecible y vulnerable a un ataque de fuerza bruta.

# Solución
El ataque se denominó **Falsificación de Cookie de Sesión por Secreto Predecible** (*Flask Session Tampering*):
1.  **Fuerza Bruta del Secreto:** Se utilizó la herramienta `flask-unsign` (integrada en un *script* de Python) para iterar a través de la lista de 28 posibles claves secretas (nombres de galletas).
2.  **Falsificación del Payload:** Con cada secreto de la lista, se firmó una nueva *cookie* de sesión con un *payload* que definía el valor de la sesión como administrador: `{"very_auth": "admin"}`.
3.  **Explotación:** La *cookie* recién firmada se envió al servidor. Cuando la *cookie* firmada con el secreto correcto (`peanut butter`, `fortune`, o similar) fue validada por el servidor, este otorgó acceso a la página del administrador, que contenía la *flag*.

# Notas adicionales
Este es un caso clásico de **Weak Secret Key** (clave secreta débil). Aunque las sesiones de Flask están protegidas criptográficamente con HMAC, si la clave es predecible o conocida, la protección se anula, permitiendo a un atacante generar sesiones válidas para cualquier usuario, incluido el administrador. 

# Referencias
* Reto PicoCTF: Most Cookies
* Herramienta: `flask-unsign`
* Vector de Ataque: Falsificación de Sesión de Flask (Session Tampering)

---

# Reto
SOAP (XXE - XML External Entity)

# Descripción
Este reto explotaba una vulnerabilidad en un servicio web que manejaba la comunicación mediante el protocolo **SOAP**, el cual está basado en **XML** [00:00:15]. El analizador XML del servidor estaba mal configurado, permitiendo el procesamiento de **Entidades Externas XML (XXE)**, un fallo que se puede utilizar para acceder a archivos internos del sistema de archivos.

# Solución
El ataque se denominó **Inyección de Entidad Externa XML (XXE)**:
1.  **Intercepción:** Se utilizó un *proxy* interceptor (como Burp Suite) para capturar la solicitud XML enviada por la aplicación al servidor.
2.  **Definición de Entidad Externa:** Se modificó la solicitud XML inyectando una declaración de tipo de documento (`<!DOCTYPE ...>`) para definir una nueva entidad, por ejemplo `&xxe;`.
3.  **Carga de Archivo Local:** La entidad `&xxe;` fue definida para cargar un recurso del sistema de archivos local utilizando el descriptor `SYSTEM`, apuntando a la ubicación esperada de la *flag* (e.g., `SYSTEM "file:///flag"`).
4.  **Inyección:** Finalmente, se insertó la referencia a la entidad (`&xxe;`) en un campo de datos de la solicitud (e.g., dentro de la etiqueta `<ID>`). Al procesar la solicitud, el analizador XML del servidor leyó el contenido del archivo `/flag` y lo sustituyó por la referencia a la entidad, devolviendo el contenido sensible en la respuesta al atacante. 

# Notas adicionales
La vulnerabilidad XXE ocurre cuando el analizador XML del servidor tiene habilitada la función de procesamiento de entidades externas. Es un fallo crítico que puede llevar a la divulgación de archivos locales, ejecución remota de código (RCE) en algunos casos, y ataques *Denegación de Servicio* (DoS) a través de la "Bomba XML" (Billion Laughs Attack).

# Referencias
* Reto PicoCTF: SOAP
* Vector de Ataque: XML External Entity (XXE)
* Protocolo: SOAP/XML