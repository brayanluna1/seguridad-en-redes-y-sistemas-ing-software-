
## Descripción:
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/325a52d249be0bd3811421eacd2c877a/ende.py) using [this password](https://mercury.picoctf.net/static/325a52d249be0bd3811421eacd2c877a/pw.txt) to get [the flag](https://mercury.picoctf.net/static/325a52d249be0bd3811421eacd2c877a/flag.txt.en)?

# Solución

Se descargas los tres archivos: `ende.py`, `pw.txt` (la contraseña) y `flag.txt.en` (el token cifrado).
Revisamos  `ende.py` 
Ver la contraseña:

```bash
cat pw.txt
# -> ac9bd0ffac9bd0ffac9bd0ffac9bd0ff
```

 Descifrar usando script:
```bash
python3 - <<'PY'
from base64 import b64encode
from cryptography.fernet import Fernet

pw = open('pw.txt').read().strip()
key = b64encode(pw.encode())
f = Fernet(key)
print(f.decrypt(open('flag.txt.en','rb').read()).decode())
PY
```

Respuesta:`picoCTF{4p0110_1n_7h3_h0us3_ac9bd0ff}`
## Notas

## Referencias
 