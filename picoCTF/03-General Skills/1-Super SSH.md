# Super SSH (picoCTF)

## 📄 Descripción
Using a Secure Shell (SSH) is going to be pretty important. Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `52072` to get the flag? You'll also need the password `84b12bae`. If asked, accept the fingerprint with `yes`.

## 🛠️ Solución
El reto se resuelve conectándose al servidor remoto mediante SSH con los parámetros proporcionados.

1.  **Ejecutar el comando SSH** en la terminal:
    ```bash
    brayan@Nitro-Brayan:~$ ssh -p 52072 ctf-player@titan.picoctf.net
    ```

2.  **Aceptar la huella digital** (fingerprint) al ser solicitado, escribiendo `yes`:
    ```
    [...]
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added '[titan.picoctf.net]:52072' (ED25519) to the list of known hosts.
    ```

3.  **Introducir la contraseña** (`84b12bae`) cuando se solicite:
    ```
    ctf-player@titan.picoctf.net's password: [Contraseña introducida]
    ```

4.  **Resultado de la conexión (Flag obtenida):**
    ```
    Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_07a987ac}
    Connection to titan.picoctf.net closed.
    ```
flag
`picoCTF{s3cur3_c0nn3ct10n_07a987ac}`
# Notas adicionales 

# Referencias 
