# Descripción

Este desafío consiste en analizar un archivo **.csr (Certificate Signing Request)** para encontrar una _flag_ oculta.  
El objetivo es **inspeccionar, decodificar y leer** el contenido del certificado para revelar los campos internos donde se encuentra la información escondida.

# Solución

1. **Obtención del archivo**
    
    - Se descarga el archivo `.csr` proporcionado por el reto (generalmente con `wget` o `curl`).
        
    - El archivo contiene el formato estándar PEM:
        
        ```
        -----BEGIN CERTIFICATE REQUEST-----
        (Base64)
        -----END CERTIFICATE REQUEST-----
        ```
        
2. **Análisis del CSR (primer vistazo)**
    
    - Se visualiza el archivo usando:
        
        ```bash
        cat challenge.csr
        ```
        
    - Se confirma que el contenido está codificado en **Base64**, encapsulado en formato PEM.
        
3. **Método principal de decodificación — OpenSSL**
    
    - Se utiliza la herramienta `openssl` para parsear la estructura del CSR y mostrar su contenido en texto:
        
        ```bash
        openssl req -in challenge.csr -text -noout
        ```
        
    - Esto despliega todos los campos internos del certificado, especialmente el **Subject**, donde normalmente se oculta la flag.
        
4. **Método alternativo — Decodificación Base64 manual**
    
    - Se eliminan las cabeceras PEM y se decodifica únicamente el bloque Base64:
        
        ```bash
        cat challenge.csr | grep -v "REQUEST" | base64 -d
        ```
        
    - Al decodificar, el contenido revela directamente estructuras internas donde aparece la flag.
        
5. **Flag obtenida**
    
    - En ambos métodos, la flag está incrustada dentro del campo **Common Name (CN)** del certificado.
        
    - **Flag final:**
        
        ```
        picoCTF{base64_decoding_is_easy}
        ```
        

# Notas adicionales

- Este reto demuestra que los archivos `.csr` no están cifrados, sólo **codificados**, por lo que su contenido puede ser inspeccionado libremente.
    
- `openssl req -text -noout` es una herramienta estándar para análisis de certificados en retos forenses y criptográficos.
    
- La estructura PEM es simplemente un contenedor Base64, no una capa de seguridad.
    

# Referencias

- OpenSSL Documentation — CSR Parsing
    
- Formato PEM y codificación Base64
    
- Análisis básico de certificados X.509 en CTFs