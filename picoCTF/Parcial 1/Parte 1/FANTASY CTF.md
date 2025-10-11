# Descripción

Play this short game to get familiar with terminal applications and some of the most important rules in scope for picoCTF.

# Solución

Primero, me conecté al servidor usando `netcat` (`nc`).

Bash

```
┌──(BenduOlo253㉿LaBenduPC)-[~]
└─$ nc verbal-sleep.picoctf.net 62505
FANTASY CTF SIMULATION

The simulation begins in the private room of Eibhilin, a bright, young student.
...
```

El comando inició un juego de ficción interactiva que te guía a través de las reglas de picoCTF. Siguiendo la historia y tomando las decisiones correctas (como registrar una sola cuenta y jugar el juego en lugar de buscar la bandera en internet), el juego mismo te revela la bandera al final.

La parte final de la interacción fue la siguiente:

```
...
"Thanks, Nyx! Here's the flag I found: picoCTF{m1113n1um_3d1710n_dd015572}"

---
(Press Enter to continue...)
---
```

**Solución:** `picoCTF{m1113n1um_3d1710n_dd015572}`

# Notas adicionales

Este reto es un "sanity check" o reto de bienvenida, diseñado para enseñar los conceptos básicos y las reglas de la competencia de una manera interactiva.

### `nc` (netcat)

- `nc` es una herramienta de red fundamental para leer y escribir datos a través de conexiones de red usando TCP o UDP.
    
- En los CTF, es la herramienta principal para interactuar con servicios remotos que no son páginas web, como en este caso.
    

### Reglas de picoCTF aprendidas

El juego enseña varias reglas importantes para la competencia:

- **No registrar múltiples cuentas.**
    
- **No compartir cuentas con otros jugadores.**
    
- **No compartir las banderas o los archivos de los retos.**
    
- **No publicar write-ups** hasta después de que la competencia haya finalizado oficialmente.
    

# Referencias

No se requirieron referencias externas ya que la solución se obtiene siguiendo las instrucciones del propio reto.