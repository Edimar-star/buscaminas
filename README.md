# Calculo de heuristica

Para el calculo de la heuristica, se hace lo siguiente:  

- Se toma una celda, vacia y se forma un cuadrado en diagonal hacia ella, para revisar si es un caso especial, sino se halla la heuristica de forma normal

- Ejemplo de caso especial:  
    - Primero, se toma una celda vacia con celdas adyacentes con numeros y se forma un cuadrado en diagonal, asi:  
    
    ![image](https://github.com/user-attachments/assets/d144aa9c-1ba2-4fff-ad7f-38ac56af487e)
    
    - Luego nos desplazamos a la celda numerica diagonal a la celda vacia:  
    
    ![image](https://github.com/user-attachments/assets/6962cea3-d90b-4ccc-b701-a0bc6de6d1d5)
    
    - Si el valor de la celda coincide con el numero de celdas vacias que tiene alrededor, entonces la celda vacia que evaluamos es una mina

- Ejemplo de caso general:
    - En caso de que no se haya encontrado un caso especial, se halla la heuristica con una celda vacia con celdas adyacentes numericas, asi:  
    
    ![image](https://github.com/user-attachments/assets/f2c60812-8ab8-41f5-ac1c-4d89eaf30de7)
    
    - A esa celda vacia buscamos sus celdas adyacentes con numeros y sumaremos sus valores (LLamemoslo M):  
    
    ![image](https://github.com/user-attachments/assets/378d00d9-b1b3-43b9-a1c3-2429bd2194de)
    
    - Ademas a esas celdas, contaremos las celdas vacias que tengan alrededor (Llamemoslo EC) y el numero de minas alrededor (MP):  
    
    ![image](https://github.com/user-attachments/assets/81da865e-9caa-4e18-8b94-9403748dc94d)
    
    - Si nos basamos del caso especial, la siguiente celda es una mina:  
    
    ![image](https://github.com/user-attachments/assets/d813dec5-4f49-4f2b-81b8-332e48b2fe8d)

    - Finalmente, la heuristica se halla asi:  
    
    $H = \dfrac{M - MP}{EC} = \dfrac{3 - 1}{4} = \dfrac{2}{4} = \dfrac{1}{2} = 0.5$

    - Nota: Si EC es cero, entonces H es 1 si hay minas por colocar

# Algoritmo para resolver el buscaminas

La logica del algoritmo es encontrar las posibilidades (se limitan) de posicionar las minas en el tablero y que sea valido, luego con esas posibilidades se halla una probabilidad.

El algoritmo hace lo siguiente:
1. Calcula la heuristica de las celdas de la tabla que cumplan la condicion para ser calculadas
2. De esas heuristicas se eliminan los movimientos invalidos  
    - Un movimiento es invalido si se intento colocar una mina, pero al colocarse rompe las reglas de buscaminas
3. Primeramente, se revisa si se puede continuar poniendo minas en el tablero (si alguna celda numerica le falta una mina alrededor) o si tengo heuristicas a evaluar
    - Si no es posible continuar, se revisa si el tablero que se formo es valido
    - Si el tablero es valido, se guarda esa posibilidad, sino nos devolvemos
4. De esas heuristicas restantes se obtiene la mayor heuristica
    - Si el valor de esa heuristica es 100 (caso especial), entonces se descartan las demas heuristicas
5. Se crea un nuevo tablero con ese movimiento
    - Si ese tablero ya fue visitado nos devolvemos, sino se añade a los tableros ya visitidos y continuamos
6. Se revisa si el movimiento es valido
    - Si ese movimiento es valido en el tablero, se vuelven a calcular las heuristicas y se sigue con el algoritmo
    - Si no es valido, se añade como movimiento invalido para las iteraciones hermanas
7. Se siguen revisando posibilidades quitando el movimiento anterior, pero con las mismas heuristicas
8. El algoritmo termina cuando se haya alcanzado el numero maximo de posibilidades o no haya más heuristicas que evaluar
9. Con los tableros obtenidos se halla la probabilidad de que haya una mina en las posiciones y se devuelve el mejor movimiento

<strong>NOTA:</strong>
1. El tablero es valido solo
    - El tablero es valido solo si esta lleno y todas las celdas numericas tienen el mismo numero de minas alrededor que lo que indica su valor
    - Si no esta lleno y hay alguna celda numerica con un menor numero de minas alrededor que lo que indica su valor
2. Cuanto mayor se el maximo de posibilidades permitido, mejor sera el movimiento que dara como que no es mina, pero se tardara más en el algoritmo.
