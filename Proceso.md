Lo primero a realizar es decir, no podemos crear desde DAX esto es así básicamente porque a una misma variable.

Cada equipo puede jugar de local o de visitante. Es decir, en unas rondas figura en la columna "Equipo Local" y en otras figura en la columna "Equipo Visitante".

A su vez, el equipo puede recibir o marcar goles jugando de local o jugando de visitante.

A priori, no es posible crear desde una columna de resultado de estilo "X-Y" (al estilo de "2-1", "2-3", etc), ya que, como cada equipo representa en algunas ocasiones el Team 1 y en otras el Team 2, el valor (el nombre del equipo) se almacena en dos campos distintos. En consecuencia, no se puede identificar en una misma columna a un equipo si su valor alterna entre dos posibilidades distintas.

Suponiendo representa

La solución para ello radico primero en crear cuatro tablas, una por cada posibilidad existente, a saber:
1. Goles a favor del equipo jugando de local (GolesXTeam1)
2. Goles en contra del equipo jugando de local (GolesYTeam1)
3. Goles a favor del equipo jugando de visitante (GolesYTeam2)
4. Goles en contra del equipo jugando de visitante(GolesXTeam2)

En estas tablas guardamos cuatro a saber:
1. Equipo (nombre del equipo)
2. Goles (a favor o en contra dependiendo de la tabla)
3. Index (ID del partido, en tanto asignamos a cada partido un identificador único)

Ver fórmulas a utilizar en el script "Creación de Tablas de Goles"

Una vez creadas las cuatro tablas, se crea una tabla resumen donde ya ahora vamos a poder unificar en dos columnas distintas "Goles a favor" y "Goles en contra" para cada equipo. Al mismo tiempo, ya podemos almacenar en una columna unificada "Equipo" tanto cuando un equipo juega de local como cuando juega de visitante.

Ver fórmulas a utilizar en el script "Creación Tabla Resumen"
quipo 1 jugando de visitante
. 3 Equipo 2 jugando de local
