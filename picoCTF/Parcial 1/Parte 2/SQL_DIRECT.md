# Descripción

Connect to our database and find the flag. All the information you need is in the connection details.

# Solución

Primero, me conecté directamente a la base de datos PostgreSQL usando el cliente `psql` y las credenciales proporcionadas.

Bash

```
┌──(BenduOlo253㉿LaBenduPC)-[~]
└─$ psql -h saturn.picoctf.net -p 60715 -U postgres pico
Password for user postgres:
psql (17.6 (Debian 17.6-1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=#
```

Una vez dentro, la descripción del reto implicaba que la solución era directa. Dado que en los CTF las banderas a menudo se encuentran en tablas con nombres obvios, ejecuté una consulta para ver todo el contenido de la tabla `flags`.

SQL

```
pico=# SELECT * FROM flags;
 id | firstname | lastname  |                address
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)

pico=#
```

La bandera apareció directamente en la columna `address` de la primera fila.

**Solución:** `picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}`

# Notas adicionales

Este reto es una introducción fundamental a la interacción con bases de datos en un entorno de CTF.

### `psql` (PostgreSQL Client)

- `psql` es la herramienta de línea de comandos estándar para conectarse e interactuar con servidores de bases de datos PostgreSQL.
    
- Los parámetros `-h` (host), `-p` (puerto), `-U` (usuario) y `-d` (base de datos) son los más comunes para establecer una conexión.
    

### `SELECT * FROM <table>;`

- Esta es la consulta SQL más básica y una de las más importantes.
    
- `SELECT *`: Indica que queremos seleccionar (leer) **todas las columnas**.
    
- `FROM flags`: Especifica que queremos leer los datos de la tabla llamada `flags`.
    
- El punto y coma (`;`) al final es necesario para terminar y ejecutar la instrucción en `psql`.
    

# Referencias

No se requirieron referencias externas, ya que la solución se basa en el conocimiento fundamental del comando `SELECT` de SQL.