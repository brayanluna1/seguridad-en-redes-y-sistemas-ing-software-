## Descripción:
El desafío presenta un servidor que ejecuta un *script* de Python (`script.py`). El *script* pide una serie de respuestas correctas, y al lograrlas, ejecuta un *shell* limitado con el comando `su - player`. Crucialmente, el *script* intenta leer un archivo de *banner* desde la ruta `/home/player/banner` al inicio.

## Solución Rápida (Explotación LFI)

El objetivo es explotar la **lectura del *banner*** para leer el archivo `flag.txt` que está protegido en el directorio `/root`.

1.  **Conexión inicial e inyección:** Se usa `nc` para conectarse y responder las preguntas correctamente para obtener un *shell* de `player`.
    ```bash
    nc tethys.picoctf.net 64733
    # Respuestas: My_Passw@rd_@1234, defcon, John Draper
    ```

2.  **Identificar el punto de inyección:** Se descubre que el *script* lee `/home/player/banner` antes de pedir la contraseña. La vulnerabilidad es que el archivo de *banner* puede ser un **enlace simbólico (`ln -s`)** a cualquier otro archivo del sistema.

3.  **Preparación de la inyección (desde el *shell* de `player`):**
    * **Eliminar** el archivo de *banner* existente: `rm banner`
    * **Crear un enlace simbólico** (`LFI`) que apunte desde `/home/player/banner` a la bandera protegida (`/root/flag.txt`):
        ```bash
        ln -s /root/flag.txt /home/player/banner
        ```
    *(Nota: El comando `cat banner` muestra `Permission denied` porque el usuario `player` no puede leer directamente `/root/flag.txt`. Sin embargo, el **script de Python** que lee el banner se ejecuta con mayores permisos, probablemente como `root` o `suid`).*

4.  **Ejecución y Captura:** Se cierra la conexión y se vuelve a conectar. El *script* de Python lee el *banner* (que ahora es el `flag.txt`) antes de pedir la contraseña, imprimiendo la bandera directamente en la consola.
    ```bash
    nc tethys.picoctf.net 64733
    ```

---

## Bandera (Flag)

$$\text{picoCTF\{b4nn3r\_gr4bb1n9\_su((3sfu11y\_ed6f9c71\}}$$

##  Concepto Clave

**Inyección por Enlace Simbólico (Symlink LFI):** Si un programa con permisos elevados lee un archivo cuya ruta está controlada por un usuario con menos permisos (como un archivo en su `/home/`), se puede crear un **enlace simbólico** que reemplace ese archivo, forzando al programa a leer un archivo restringido (como `/root/flag.txt`) e imprimir su contenido.