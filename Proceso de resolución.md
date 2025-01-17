Paso 1: Planteo del desafío 

Tenemos a priori tres columnas:
- Equipo local
- Resultado (en formato "X-Y", donde X son los goles marcados por el equipo local e Y los goles del equipo visitante)
- Equipo visitante

Por ronda cada equipo puede jugar de local o de visitante. Es decir, en algunas rondas figura en la columna "Equipo Local" y en otras figura en la columna "Equipo Visitante". No puede jugar bajo ambas condiciones en una misma ronda. A su vez, el equipo puede recibir o marcar goles jugando de local y recibir o marcar goles jugando de visitante.

El desafío de este ejercicio radica en que, mediante DAX, no es posible directamente descomponer una columna de resultados en formato "X-Y" (por ejemplo, "2-1", "2-3") en dos columnas que unifiquen los goles a favor y en contra de un equipo en una misma tabla. Esto se debe a la estructura del modelo de datos.

Por un lado, está la doble representación de equipos: Cada equipo puede aparecer en dos columnas diferentes: como equipo local (Team 1) o como equipo visitante (Team 2). Dependiendo del partido, los goles marcados y recibidos por un equipo pueden encontrarse en diferentes posiciones dentro del resultado.

Por otro lado, está la alternancia entre local y visitante: Para un equipo que juega de local, sus goles a favor se encuentran en la primera parte del resultado (X), mientras que los goles en contra están en la segunda parte (Y). Y, cuando el mismo equipo juega de visitante, la posición de los datos se invierte: Sus goles a favor están en la segunda parte del resultado y sus goles en contra se encuentran en la primera parte.

Debido a que los goles de un equipo dependen de su rol (local o visitante) y se distribuyen entre dos campos distintos, no se pueden consolidar en una sola operación de DAX dentro de una única tabla. Sería imposible su unificación directa.

Paso 2: Construcción de tablas auxiliares

Es necesario, entonces, crear cuatro tablas, una por cada posibilidad existente:

1. Goles a favor del equipo jugando de local (GolesXTeam1)
2. Goles en contra del equipo jugando de local (GolesYTeam1)
3. Goles a favor del equipo jugando de visitante (GolesYTeam2)
4. Goles en contra del equipo jugando de visitante (GolesXTeam2)

Cada una de estas tablas debería contener tres columnas, a saber:
1. Equipo (nombre del equipo)
2. Goles (a favor o en contra dependiendo de la tabla)
3. Index (ID del partido)**

** Para este ejercicio demostrativo no es necesario contar con una columna 'Index', pero puede resultar particularmente útil si tenemos un modelo de datos más desarollado para relacionar las tablas.

En el script '1. Fórmula Tablas de Goles' se encuentran las fórmulas a utilizar para construir las tablas auxiliares.

Paso 3: Construcción de la tabla resumen

Una vez generadas las cuatro tablas individuales, el siguiente paso es consolidar toda esta información en una tabla resumen. Esta nueva tabla unifica en una misma columna el nombre de los equipos (cuyos valores originalmente estaban distribuidos entre las columnas "Equipo Local" y "Equipo visitante") y, además, permite crear las dos columnas que estábamos buscando: "Goles a favor" y "Goles en contra".

Como resultado, esta tabla resumen contiene cuatro columnas, a saber:

1. Equipo (nombre del equipo)
2. Goles a favor (almacena los goles de las tablas "GolesXTeam1" y "GolesYTeam2")
3. Goles en contra (almacena los goles de las tablas "GolesYTeam1" y "GolesXTeam2")
4. Index (ID del partido)

En el script '2. Fórmula Tabla Resumen (Métricas "Goles a favor" y "Goles en contra")' se encuentran las fórmulas a utilizar a tal fin.

Paso 4. Creación de métricas

Ahora ya podemos crear sobre esta tabla resumen, con una columna unificada de equipo, las demás métricas sin inconveniente alguno.

En los siguientes scripts se encuentran las fórmulas a utilizar:

3. Fórmula Métrica "Puntos totales"
4. Fórmula Métrica "Partidos jugados" 
5. Fórmula Métrica "Partidos ganados"
6. Fórmula Métrica "Partidos empatados"
7. Fórmula Métrica "Partidos perdidos"
8. Fórmula Métrica "Win Rate (%)"
