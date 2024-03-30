# Lab_2_Robotica

Lab 2 Robotica

# Integrantes 

Joyner Stiven Caballero Abril 

Juan Felipe Triana 

# Descripcion del codigo realizado

# Inicialización y Configuración del Robot

![image](https://github.com/JoyS06/Lab_2_Robotica/assets/105253521/0478a726-b192-4b75-abf6-d5ec6c58e8f0)

Motor On: Este comando es fundamental al inicio de cualquier secuencia de programación de robots EPSON. Asegura que el robot esté listo para recibir y ejecutar comandos de movimiento.

Power Low: Pone el robot en un estado de bajo consumo de energía. Esto es particularmente útil en un entorno de desarrollo o cuando se realizan pruebas repetitivas, ya que ayuda a reducir el consumo energético sin comprometer la capacidad del robot para ejecutar tareas.

# Ejecución Condicional de Funciones de Paletizado

Este bucle Do...Loop está diseñado para ejecutar continuamente una serie de funciones de paletizado. Sin embargo, las condiciones basadas en el estado de los interruptores (entradas digitales Sw(9), Sw(10), Sw(11)) están comentadas. 

# Función paletizado_z

![image](https://github.com/JoyS06/Lab_2_Robotica/assets/105253521/cb2b5c44-9a4c-4de6-bcca-fa92e6ecbfa4)

#define estado_paletizado_z 11: Esta directiva define un identificador para la salida digital número 11, que se usará para señalizar cuando la función paletizado_z esté activa.

Pallet 1, Origen, EjeX, EjeY, 3, 3: Configura un palet de 3x3 posiciones. Este palet se define con un punto de origen (Origen) y se extiende en las direcciones EjeX y EjeY para crear una matriz de 9 puntos.

On estado_paletizado_z: Activa la salida digital asociada al paletizado en Z, indicando que esta tarea específica está en progreso.

Bucle For: Itera sobre cada uno de los 9 puntos del palet, ejecutando un movimiento hacia arriba (:Z(200)) antes y después de acercarse a cada punto (Go Pallet(1, i)). Esto asegura que el robot se eleve 200mm sobre cada posición antes de moverse hacia o desde esa posición, evitando colisiones.

Off estado_paletizado_z: Desactiva la salida digital al finalizar la secuencia de movimientos, señalando el fin de la tarea.

# Función paletizado_s

![image](https://github.com/JoyS06/Lab_2_Robotica/assets/105253521/4551210c-00ed-4e7a-9b52-eca0add4d1d6)


#define estado_paletizado_s 12: Define un identificador para la salida digital número 12, usada para indicar la ejecución de paletizado_s.

Pallet 1, Origen, EjeX, EjeY, 3, 3: Similar a paletizado_z, define un palet de 3x3.

On estado_paletizado_s: Activa la señal de inicio de la tarea de paletizado en forma de "S".

Tres Bucles For: Estos bucles crean un patrón de movimiento en "S" sobre el palet. El primer y tercer bucle avanzan en orden ascendente, mientras que el segundo bucle recorre posiciones en orden descendente (Step -1), creando así el patrón deseado.

Off estado_paletizado_s: Indica el fin de esta tarea desactivando la salida digital correspondiente.

# Función paletizado_externo

![image](https://github.com/JoyS06/Lab_2_Robotica/assets/105253521/0ab5ccc4-dfbf-4f9b-90ac-404bd5ebfbab)

#define estado_paletizado_externo 12: Asigna un identificador a la salida digital número 12, que se usará para controlar la señalización de la tarea de paletizado externo.

Pallet Outside, 2, Origen, EjeX, EjeY, 3, 3: Este comando configura un palet extendido, utilizando la misma base de 3x3 pero extendiéndose para incluir una cuarta fila y columna, creando así un total de 16 puntos. La referencia 2 indica que este es el segundo palet definido en el programa.

On estado_paletizado_externo: Activa la salida digital para señalar el inicio de la operación de paletizado externo.

Doble Bucle For: Navega a través de cada punto del palet extendido de 4x4, asegurando el movimiento en Z antes y después de cada posición para evitar obstáculos.

Off estado_paletizado_externo: Finaliza la tarea desactivando la señal correspondiente.

# Videos

Video simulación: https://youtu.be/rWDIucTXfMs

Video robot fisico: https://www.youtube.com/watch?v=m3bDK3r0nCM
