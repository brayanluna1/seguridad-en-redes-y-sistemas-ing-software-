# Descripción
Se nos da una cadena de valores ASCII en formato hexadecimal que representan la flag.  
La instrucción es convertir estos valores en caracteres legibles.

Cadena dada:
```
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x35 0x63 0x31 0x31 0x5f 0x6e 0x30 0x5f 0x71 0x75 0x33 0x35 0x37 0x31 0x30 0x6e 0x35 0x5f 0x31 0x6c 0x6c 0x5f 0x74 0x33 0x31 0x31 0x5f 0x79 0x33 0x5f 0x6e 0x30 0x5f 0x6c 0x31 0x33 0x35 0x5f 0x34 0x34 0x35 0x64 0x34 0x31 0x38 0x30 0x7d
```

# Solución
Bastó con convertir cada valor hexadecimal a su carácter ASCII.

Puede hacerse con CyberChef usando la operación “From Hex”, o en terminal:

```bash
echo "70 69 63 6f 43 54 46 7b 34 35 63 31 31 5f 6e 30 5f 71 75 33 35 37 31 30 6e 35 5f 31 6c 6c 5f 74 33 31 31 5f 79 33 5f 6e 30 5f 6c 31 33 35 5f 34 34 35 64 34 31 38 30 7d" | xxd -r -p
```

Salida:
```
picoCTF{45c11_n0_qu35710n5_1ll_t311_y3_n0_l135_445d4180}
```

# Notas adicionales
- Los valores comenzaban con `0x`, pero no afecta la conversión tras eliminarlos o ignorarlos.
- CyberChef es la herramienta más rápida para este tipo de retos.
- Todos los valores estaban en ASCII imprimible.

# Referencias
- CyberChef (“From Hex”)
- Tabla ASCII y hex
- Comando `xxd`

