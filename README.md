# buscaminas

1. Hallar heuristica de todos las celdas disponibles (celdas con 0) que tengan celdas adyacentes con numeros positivos.
2. Elegir la celda con mayor heuristica y marcar la celda como mina (-2)
3. Verificar que sea una mina en una posicion valida
4. Si la mina es valida, seguir y repetir desde el paso 1, sino es valida, descartarla y tomar la siguiente celda con mayor heuristica y empezar desde el paso 2
5. El algoritmo termina cuando no sea posible marcar mas minas
6. Se elije como mejor movimiento aquella celda disponible que tenga menos posibilidad de ser una mina

# Calculo de la heuristica:

1. Se halla las celdas adyacentes con numeros positivos
3. A aquellas celdas del paso 1 se les resta a su valor la cantidad de minas alrededor y se va acumulando ese valor (Llamemoslo M)
4. A aquellas celdas de paso 1 se les halla la cantidad de celdas vacias alrededor, si 2 celdas comparten 1 misma celda vacia solo contara como 1 sola y no 1 para cada uno (Llamemoslo EC)
5. Se resta el resultado del paso 2 con 3 y se divide a ese resultado el paso 4, asi: M / EC

# Adicional

1. El valor de una celda con mina es -2
2. El valor de una celda vacia en la que no se puede jugar es -1
3. El valor de una celda vacia en la que se puede jugar es 0