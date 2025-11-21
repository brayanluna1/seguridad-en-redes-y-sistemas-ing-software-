# Descripción
**Título del Reto:** Mind Your P's and Q's  
**Plataforma/Categoría:** picoCTF, Criptografía (RSA).  
**Enunciado:** Se entrega un ciphertext y un módulo RSA que aparentan ser seguros, pero en realidad el valor de **N es demasiado pequeño**, lo que permite factorizarlo y obtener la clave privada.  
**Objetivo:** Recuperar la flag descifrando el ciphertext.  
**Mecanismo:** Usar herramientas automáticas (como RsaCtfTool) para factorizar N, obtener p y q, construir la clave privada y descifrar el mensaje.

# Solución
Se utilizó **RsaCtfTool** para automatizar el ataque. Debido a que el módulo **N era pequeño**, la herramienta logró factorizarlo utilizando el método **factordb**.

## Proceso
- Se ejecuta RsaCtfTool con el ciphertext y el archivo del reto.  
- La herramienta detecta que el tamaño de N permite factorizarlo sin esfuerzo.  
- Factordb devuelve los primos **p** y **q**.  
- Con ellos, RsaCtfTool calcula el totiente φ(n), obtiene **d** (clave privada) y descifra el ciphertext.  
- El resultado aparece tanto en formato raw (bytes) como en texto utf-8.

### Salida obtenida
- **STR:** `b'\x00picoCTF{sma11_N_n0_g0od_45369387}'`  

La flag final fue correctamente decodificada a partir de la salida en utf-8.

# Notas adicionales
- El reto demuestra por qué RSA NO debe usar módulos pequeños: se vuelven vulnerables a ataques de factorización triviales.  
- **Factordb** es suficiente para romper claves RSA pequeñas sin necesidad de cálculos avanzados.  
- RsaCtfTool es una herramienta esencial para analizar retos RSA: prueba múltiples ataques automáticamente.  
- El prefijo `\x00` en los bytes es normal en resultados RSA cuando el padding o la conversión incluye un byte nulo al inicio.

# Referencias
- Documentación oficial de **RsaCtfTool**.  
- Base de datos **factordb.com** para factorización de enteros.  
- Material de picoCTF sobre ataques a RSA con módulos pequeños.
