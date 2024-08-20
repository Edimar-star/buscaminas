# buscaminas

1. Hallar heuristica de todos las celdas disponibles (celdas con 0) que tengan por lo menos 2 celdas adyacentes con numeros positivos.
2. Elegir la celda con mayor heuristica y marcar la celda como mina
3. Verificar que sea una mina en una posicion valida
4. Si la mina es valida, volver al paso 1, sino es valida, descartarla y tomar la siguiente celda con mayor heuristica y hacer de nuevo el paso 3
5. El algoritmo termina cuando no sea posible marcar mas minas
6. Se elije como mejor movimiento aquella celda disponible (que tenga por lo menos 2 celdas adyacentes con numeros positivos) con mas minas alrededor

# Calculo de la heuristica:

1. Se halla las celdas adyacentes con numeros positivos
3. A aquellas celdas del paso 1 se les resta a su valor la cantidad de minas alrededor (Llamemoslo M)
4. A aquellas celdas de paso 1 se les halla la cantidad de celdas vacias alrededor, si 2 celdas comparten 1 misma celda vacia solo contara como 1 sola y no 1 para cada uno (Llamemoslo EC)
4. Se resta el resultado del paso 2 con 3 y se divide a ese resultado el paso 4, asi: M / EC