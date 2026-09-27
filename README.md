#      {{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{FLUJO #tetris{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{


# 1. Hay que designar un índex para los tipos de movimientos que requerirá tetris
    a. No sirven int para definir funciones(*)
    b. Se deben enumerar idealmente asimilando con una escala nominal estilo label
        . → Para ello resulta realmente útil la función Enum contenida en el package enum.
        Una vez definidos los 4 movimientos posibles de la pieza (Right, Left, Down, ROTATE), proseguimos con...
#               **** PARA LLAMAR A NUESTRA FUNCIÓN ENUM, DEBEMOS PRIMERA Y OBLIGATORIAMENTE, DEFINIR *movement (Enum) DENTRO DE UNA &{#CLASS.{


# 2. Debemos definir cuál será el workspace de tetris
    a. Así, definimos que será un tablero de 10x10 y la pieza ocupara una forma de 」(90° sentido horario) con una estequiometría de 4 realms proporcionales.
    b. Se debe considerar que esta será una función, por lo cual es importante definirla.
        i. Estructura de función def()
            1. La función #def() puede definir cualquier tipo de función que queramos crear, idealmente se debe usar cuando debemos resolver un ejercicio de lógica, de programación, matemáticas o física en modo backtracking, especialmente y solo por decir algunas de las funciones que la citan.
                            forma: {def tetris():
            2. En el caso del Tetris, se imprimirá nuestro tablero.
                                    {def tetris():
                                            {screen =   [
                                                        ["🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔳", "🔳", "🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
                                                        ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"]
                                                        ]
            3. Debe retornar la variable que estamos definiendo
                                            return screen  # Asegúrate de que tu función está devolviendo 'screen' → para definir la función tetris()
            4. La variable que definimos, debemos hacer su igualdad con la función que estamos definiendo 
                                    screen = tetris()
# @                                              Se define tetris (), función es equivalente. ¡LÓGICA!

# 3. Ahora que ya tenemos definida la función en la que se desplazarán las variables que vayamos definiendo más adelante en nuestro algoritmo diagrama de flujo, es momento de definir su formato.
    a. En este caso, no dejaremos espacio entre los realms que puede desplazarse nuestra figura.
                        for row in screen:
#                            **print("".join(map(str,row)))**

                En el ejemplo expuesto se muestra que no dejamos espacio entre las ' " ', además juntamos los string de cada fila.
                    Se debe considerar que los string son cadenas que no se condicionan, en este caso, a la mezcla de distintos tipos de datos,
                    por lo que cada fila será una cadena y no un tuple.
                            Entonces, las funciones que llamemos a nuestra TrunkFunction, se moverán por las filas (LISTAS DE UNA LISTA ABASALLADORA), entre cada elemento del string que conforma.



# 4. Una vez tenemos definido totalmente el **formato** con el que se desarrollará el algoritmo, se deben comenzar a definir las funciones que lo recorrerán.
#    a. Primeramente, definiremos la funcion move_piece →→☻7  {{{{{**FUNDAMENTO DEL JUEGO*{{{{{
        i. Para ello, debemos entender que hasta ahora tenemos 4 movimientos, que definimos en la función #Enum
            i. Los cuales recorrerán nuestro **screen (Matriz)**, que está compuesto en jerarquía descendente, por
                a. Una lista
                b.1. Filas (elementos de la lista → SON LISTAS)
                b.2 Columnas (elementos del string)
                c. String

            ii. Quedaría definida bajo la función →→→→ 
#                                                        "def move_piece(screen: list, movement:movement):"

                (*). Se debe tener en consideración que en el caso anterior, la función #enum → tiene 2 dimensiones de movimiento, (RIGHT; LEFT; DOWN)
                    
                    (**). Se puede agregar otra dimensión en la jerarquía "movement", que sería ROTATE, la cual tendremos que definir posteriormente. JUEGO DE PIVOTES
            

5. Luego, tenemos que definir nuestro new_screen, el cual constará de la misma matriz, extirpándole la figura tetris.
                                          new_screen = [["🔲"] * 10 for _ in range(10)]
                                          
# 5.1. Junto a tal definición, debemos considerar definir como se moverá la figura dentro del screen() →→→☻6 
        i. Inicialmente será solo para abajo.
                                        screen=move_piece(screen, movement.DOWN)



# 6. Ahora, debemos definir el número de las filas para ir afinando la capacidad de desplazamiento de nuestra figura.
                                            for row_index, row in enumerate(screen):
                                                for column_index, item in enumerate(row):
               
                                                     if item == "🔳":

                                                        new_row_index = 0       #no debería ser 
                                                        new_column_index = 0


# 7. Teniendo definido el movimiento de nuestra figura a través de las los elementos de la lista (FILA) Y los elementos del string (Columna),
        i. Debemos definir el movimiento que tendrá la figura, 
            a. Considerando los parámetros de movimiento que le hemos definido.

                                                    match movement: 
                                                        case movement.DOWN:
                                                            new_row_index = row_index +1
                                                            new_column_index = column_index
                                                        case movement. RIGHT:
                                                            break
                                                        case movement. LEFT:
                                                            break
                                                        case movement. ROTATE:
                                                            break


# 8. Posteriormente, teniendo definido los índex de nuestro tablero, y como se moverá nuestra figura, 
        a. Debemos definirle un carácter a la intersección de nuestras funciones, en este caso será: 
                                                    new_screen[new_row_index][new_column_index] = "🔳"

                    i. Que si nos fijamos, es la intersección elementos matriciales:
                        a. Espacio Vectorial, sobreponiendo nuestra función new_screen en nuestro screen a.k. tetris ()
                        b. Fila
                        c. Columna




# 9. Teniendo definido ya:
    a. Plantilla Tetris
    b. Pantalla superpuesta blanca completa
    c. Figura que se sobrepone a pantalla blanca completa
        i. Indexada con movimientos

 
# 9.1. Debemos crear una función que realice nuestro &{Print
    a. En este caso, imprimiremos la lista de nuestra matriz,
    b. Que hará el recorrido comandado en la función, por las filas de la pantalla, 
    c. Dándole el formato del screen que definimos en el paso [3]


def print_screen(screen: list):
                                print("Pantalla Tetris")
                                for row in screen:
                                        print("".join(map(str, row)))



# {{{{Considerar que la indexación de la figura en PivotList, quedó definida en el paso 6
        # {{{Configurando el carácter "🔳" en el recorrido de nuestra figura por las filas y columnas.




                
#                                 {{{{ CONFIGURACIÓN FINAL DEL ALGORHYTM {{{{



from enum import Enum

## Para importar la función Enum, primero debemos crear una Clase.
class movement(Enum):
        DOWN = 1
        RIGHT = 2
        LEFT = 3
        ROTATE = 4

def tetris():
    screen = [["🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔳", "🔳", "🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"]]
    
    return screen
                                ####$$$$$$ En paso 2, print_screen(screen)
# Llamamos a la función y asignamos el resultado a la variable 'screen'
screen = tetris()

# Ahora podemos utilizar 'screen' fuera de la función
for row in screen:
        print("".join(map(str,row)))



# PASO 2: Creando una función que defina los movimientos de la pieza
        # Parámetro movement, va a ser del tipo movement, definido en Class
                # Solo tendrá 4 valores
def move_piece(screen: list, movement:movement):
        
        new_screen = [["🔲"] * 10 for _ in range(10)]
        #
        screen=move_piece(screen, movement.DOWN)
              
        for row_index, row in enumerate(screen):
                for column_index, item in enumerate(row):
               
                        if item == "🔳":
               
                                new_row_index = 0
                                new_column_index = 0
                
                        match movement: 
                                case movement.DOWN:
                                        new_row_index = row_index +1
                                        new_column_index = column_index
                                case movement. RIGHT:
                                        break
                                case movement. LEFT:
                                        break
                                case movement. ROTATE:
                                        break
                          
                        new_screen[new_row_index][new_column_index] = "🔳"
        
        
def print_screen(screen: list):
                                print("Pantalla Tetris")
                                for row in screen:
                                        print("".join(map(str, row)))








# {{{{{ RESULTADO: LA PIEZA QUEDA FIJADA EN EL TABLERO →☻7 en su posición inicial.     {{{{{







# {{{{{{{{{{      MOVER LA PIEZA HACIA ABAJO       {{{{{{{{{{




# 1. En el último paso del 1er algorythm, definimos la función: {{def print_screen (screen:list)

#    a. Ahora definiremos tal función al comienzo, después de darle formato a nuestro screen.

for row in screen:
        print("".join(map(str,row)))


def print_screen(screen: list):
    print("Pantalla Tetris")
    for row in screen:
        print("".join(map(str, row)))

def move_piece(screen: list, movement:movement):

        new_screen = [["🔲"] * 10 for _ in range(10)]


# QUEDA IGUAL PERO ARRIBA


# La única diferencia es que definimos las restricciones del movimiento de nuestra figura en nuestro #FRAMEWORK.
    Y se agrega: → return new_screen después de la definición de las funciones de movimiento.



from enum import Enum

## Para importar la función Enum, primero debemos crear una Clase.
class movement(Enum):
        DOWN = 1
        RIGHT = 2
        LEFT = 3
        ROTATE = 4

def tetris():
    screen = [["🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔳", "🔳", "🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"]]
    
    return screen  # Asegúrate de que tu función está devolviendo 'screen'
                                ####$$$$$$ Profe en paso 2, hace print_screen(screen)
# Llamamos a la función y asignamos el resultado a la variable 'screen'
screen = tetris()

# Ahora podemos utilizar 'screen' fuera de la función
for row in screen:
        print("".join(map(str,row)))


def print_screen(screen: list):
    print("Pantalla Tetris")
    for row in screen:
        print("".join(map(str, row)))

def move_piece(screen: list, movement:movement):
        
    new_screen = [["🔲"] * 10 for _ in range(10)]
          
    for row_index, row in enumerate(screen):
        for column_index, item in enumerate(row):
            if item == "🔳":
                new_row_index = row_index
                new_column_index = column_index
#                                       YA NO SON IGUAL A 0, SON IGUAL A LA VERSIÓN OLD. 
                match movement: 
                    case movement.DOWN:
                        new_row_index = row_index + 1
                        new_column_index = column_index
                    case movement.RIGHT:
                        break
                    case movement.LEFT:
                        break
                    case movement.ROTATE:
                        break
                  
              
                if 0 <= new_row_index < len(screen) and 0 <= new_column_index < len(row):
                    new_screen[new_row_index][new_column_index] = "🔳"
# SE AGREGA {RETURN NEW_SCREEN
    return new_screen

screen = move_piece(screen, movement.DOWN)
print_screen(screen)
        



# LA FIGURA SE MUEVE PARA LOS LADOS.
#                                       BIDIMENSIONALIDAD → COMPLETE.


# 1. Agregar funciones de movimiento {RIGHT - {LEFT
        a. en función de la función para el movimiento {DOWN.



from enum import Enum

## Para importar la función Enum, primero debemos crear una Clase.
class movement(Enum):
        DOWN = 1
        RIGHT = 2
        LEFT = 3
        ROTATE = 4

def tetris():
    screen = [["🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔳", "🔳", "🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"]]
    
    return screen
    
# Llamamos a la función y asignamos el resultado a la variable 'screen'
screen = tetris()

# Ahora podemos utilizar 'screen' fuera de la función
for row in screen:
        print("".join(map(str,row)))


def print_screen(screen: list):
    print("Pantalla Tetris")
    for row in screen:
        print("".join(map(str, row)))

def move_piece(screen: list, movement:movement):
        
    new_screen = [["🔲"] * 10 for _ in range(10)]
          
    for row_index, row in enumerate(screen):
        for column_index, item in enumerate(row):
            if item == "🔳":
                new_row_index = row_index
                new_column_index = column_index
                
                match movement: 
                    case movement.DOWN:
                        new_row_index = row_index + 1
                        new_column_index = column_index
                    case movement.RIGHT:
                        new_row_index = row_index
                        new_column_index = column_index + 4
                    case movement.LEFT:
                        new_row_index = row_index
                        new_column_index = column_index
                    case movement.ROTATE:
                        break
                  
              
                if 0 <= new_row_index < len(screen) and 0 <= new_column_index < len(row):
                    new_screen[new_row_index][new_column_index] = "🔳"
    
#    return new_screen     &%&%&&&;;;;;#    New_screen no alcanza a ser definido dentro de los límites del tablero, por lo que la figura

screen = move_piece(screen, movement.DOWN)
screen = move_piece(screen, movement.RIGHT)
screen = move_piece(screen, movement.RIGHT)

print_screen(screen)
        
        
#                                IGUAL LA PIEZA SALE DE LOS MÁRGENES, PERO COMPLETA ARROJARÁ ERROR EN EL SIGUIENTE PASO  {{{{{{ERROR.




# DUDA

# Estoy haciendo un backtracking, y necesito encontrar el [NewIndexFila (Y function)] = [Valor de la fila en que me encuentro posicionado][0: creo que es por la matriz nula, me corriges si me equivoco][0: si es fila, 1: si es columna, me corriges si me equivoco)]

# CONTEXTO:
# Programación de tetri, definiendo la función rotate (le aporta un elemento de tridimensionalidad al programa, más alla de moverme entre los elementos de las listas para filas y entre los elementos de la cadena  para las columnas

                    case movement.ROTATE:
                        new_row_index = row_index + rotations[rotation_item][0]
                        new_column_index = column_index + rotations[rotation_item][1]


#No se necesita una matriz nula para sumar valores de matriz
    rotations = ([(0,1), (-1,0), (0,-1), (1,-2)],
                [(0,1), (-1,0), (0,-1), (1,-2)],
                [(0,2), (1,1), (-1,1), (-2,0)],
                [(0,1), (1,0), (2,-1), (1,-2)])

#                                                                        CON POSICIÓN

    screen = [["🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔳", "🔳", "🔳", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"],
              ["🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲", "🔲"]]


                    case movement.ROTATE:
                        new_row_index = row_index + rotations[rotation_item][0]
                        new_column_index = column_index + rotations[rotation_item][1]
                        rotation_item += 1

#                       PROBAR CON:


case movement.ROTATE:
    rotation_item = rotate_block(rotation_item, rotations)
    new_row_index = int(row_index) + int(rotations[rotation_item][0])
    new_column_index = list[0,column_index] + rotations[rotation_item][1]





