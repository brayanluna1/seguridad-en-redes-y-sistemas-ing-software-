# Descripción
This file has a flag in plain sight (aka "in-the-clear"). [Download flag](https://mercury.picoctf.net/static/2d24d50b4ebed90c704575627f1f57b2/flag).

# Solución 
```
brayan@Nitro-Brayan:~$ wget https://mercury.picoctf.net/static/2d24d50b4ebed90c704575627f1f57b2/flag
--2025-09-01 11:17:05--  https://mercury.picoctf.net/static/2d24d50b4ebed90c704575627f1f57b2/flag
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34 [application/octet-stream]
Saving to: ‘flag’

flag                          100%[=================================================>]      34  --.-KB/s    in 0s

2025-09-01 11:17:06 (11.9 MB/s) - ‘flag’ saved [34/34]

brayan@Nitro-Brayan:~$ cat flag
picoCTF{s4n1ty_v3r1f13d_f28ac910}
```
picoCTF{s4n1ty_v3r1f13d_f28ac910}
# Notas adicionales 
usamos cat para ver contenido del archivo 

# Referencias 
