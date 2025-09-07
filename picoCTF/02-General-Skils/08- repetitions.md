# Descripción
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/476/enc_flag).
# Solución 
Primero descargamos el archivo, y vi el contenido con cat, y analise esto 
```
cat enc_flag
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKVVZXMTRWMDVHV2toalJYUlhDazFyV25sVVZXaHpWakpHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
```
al tener los iguales me di cuenta que era un archivo codificado en base 64, asi que lo decodifique 
```
┌──(Brayan㉿Nitro-Brayan)-[~]
└─$ openssl base64 -d -in dec_flag.txt -out dec_flag2.txt
```
despues entramos en un ciclo sin fin de codificar base64 hastq eu en el ultimo cat nos encontramos esta bella respuesta: 
```
cat dec_flag6.txt
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_4557ec3e}

```
# Notas adicionales 

# Referencias 
