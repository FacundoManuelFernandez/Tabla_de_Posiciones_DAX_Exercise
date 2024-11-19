Lo primero a realizar es decir, no podemos crear desde DAX esto es así básicamente porque a una misma variable. Cada equipo puede jugar de local o de visitante. Es decir, en unas rondas figura en la columna Equipo Local y en otras figura en la columna Equipo Visitante. A su vez, el equipo puede recibir o marcar goles jugando de local o jugando de visitante. A priori, no es posible desde una columna de resultado de estilo "2-1" crear, ya que al juga en algunas ocasiones un mismo equipo representa Team 1 y en otras Team2, y no se puede identificar en una misma columna a un equipo si su valor alterna entre dos posibilidades distintas.

La solución para ello radico primero en crear cuatro tablas, una por cada posibilidad existente, a saber:
1. Goles a favor del equipo jugando de local.
2. Goles en contra del equipo jugando de local.
3. Goles a favor del equipo jugando de visitante.
4. Goles en contra del equipo jugando de visitante.

Ver fórmulas a utilizar en el script "Creación de Tablas de Goles"

Una vez fueron realizadas las cuatro tablas, se crea una tabla resumen donde ya ahora vamos a poder unificar en dos columnas distintas "Goles a favor" y "Goles en contra" para cada equipo.

En esta tabla ya podemos almacenar dentro de una misma columna los resultados para un equipo tanto cuando juega de local como cuando juega de visitante.

Ver fórmulas a utilizar en el script "Creación Tabla Resumen"
quipo 1 jugando de visitante
. 3 Equipo 2 jugando de local
