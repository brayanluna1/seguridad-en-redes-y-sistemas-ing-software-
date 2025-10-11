# Descripción

Our company is looking for a hash cracking expert. To apply for the job, you need to answer a few questions to prove your skills.

# Solución

Primero, me conecté al servidor usando `netcat`.

Bash

```
┌──(BenduOlo253㉿LaBenduPC)-[~]
└─$ nc saturn.picoctf.net 52970
Please md5 hash the text between quotes, excluding the quotes: 'Albert Einstein'
Answer:
```

El servidor pedía calcular el hash **MD5** de una cadena de texto. Usé una herramienta externa (como una página web o un script) para calcular el hash y lo pegué en la terminal.

Bash

```
7560afa1f46d5e5fefe4ad93e42a293d
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'a morgue'
Answer:
1c5d1684ae8cd2f62a070044e5fc40c7
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Babe Ruth'
Answer:
3875acc0c1561d949c39685e96b9a4bb
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
```

Después de responder correctamente a tres preguntas, el servidor me entregó la bandera.

**Solución:** `picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}`

# Notas adicionales

Este reto evalúa la capacidad de identificar y calcular un tipo de hash común (MD5) y de interactuar con un servicio de red de forma rápida.

### Hashing y MD5

- Un **hash** es una función criptográfica que convierte una entrada de tamaño variable en una salida de tamaño fijo. Es un proceso de **un solo sentido**, lo que significa que es computacionalmente inviable revertirlo (obtener el texto original a partir del hash).
    
- **MD5** es un algoritmo de hashing que produce un valor de 128 bits, comúnmente representado como una cadena hexadecimal de 32 caracteres.
    
- **Importante:** MD5 se considera **criptográficamente inseguro** para propósitos de seguridad (como almacenar contraseñas) debido a que se han encontrado colisiones, pero todavía se usa a veces para verificar la integridad de archivos.
    
# Referencias

- Herramienta de red `nc` (netcat).
    
- Un generador de hash MD5 (ya sea una herramienta en línea o una librería como `hashlib` de Python).