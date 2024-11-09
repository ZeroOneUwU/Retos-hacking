## Objetivo

¡Conéctese a este servidor PostgreSQL y encuentre la bandera!

Detalles adicionales estarán disponibles después de lanzar su instancia de desafío.

## Pistas
## Solución

┌──(kali㉿kali)-[~]
└─$ psql -h saturn.picoctf.net -p 49476 -U postgres pico
Password for user postgres: 
psql (16.1 (Debian 16.1-1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=# \l
pico=# 
pico=# \c pico
psql (16.1 (Debian 16.1-1), server 15.2 (Debian 15.2-1.pgdg110+1))
You are now connected to database "pico" as user "postgres".
pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico=# SELECT flags
pico-# select * from flags;
ERROR:  syntax error at or near "*"
LINE 2: select * from flags;
               ^
pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico=# select * from flags;
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)

pico=# 


## Notas adicionales
## Referencias