

# Crea tu Juego en Blender:

¿Que es blender?
  - BLender es un programa que integra herramientas para la creacion de un amplio rango de contenido 3D.
  - Ademas esta destinado a artistas y profesionales de multimedia, Blender puede ser usado para crear desde visualizaciones 3D hasta  imagenes y videos de alta calidad
  
Ventajas:
    - Es gratis
    - MultiPlataforma
    - Tiene una comunidad que abarca todo el mundo
    - ocupa muy poco espacio
    - arquitectura 3D de alta calidad
    
    
Juego en Blender:
Blender utiliza python para todo, pero uno puede utilizarun poco de  python para crear algunas cosas.
los objetos que tendra nuestro juego son cuatro:
la bala
el arma 
el enemigo
la nave
para poder realizar un juego en blender, uno debe estar en game logic. Una estando en game logic tendran debajo podran añadir la "logica a cada objeto", y en el caso de la nave deberan colocar la siguiente logica:
            
en la foto se pued ver 2 logicas:
1)El primer sensor llamado Keyboard, esta configurado para que la nave se mueva de manera horizonzal hacia un lado y el otro.
2)El ultimo sensor es de colicion, la cual su funcion es hacer que el objeto "nave" desaparezca al colicionar con el objeto "enemigo".

Luego con el objeto "enemigo" esta la siguiente logica:

El sensor de colicion tiene la misma logica que la nave, pero en vez de eliminarse al colisionar el cuadrado con la nave.

AHORA EXPLICARE EL CODIGO QUE SE REALIZO:

import bge

def main(): 

    cont = bge.logic.getCurrentController() ###"cont" contiene toda la logica de los controles de blender###
    
    enemigo = cont.owner ### "enemigo" que tiene como valor el "count"###
    
    if enemigo.position.x > 20 : 
        enemigo["mv"] *= -1      |### creamos un if que es para el movimiento de los enemigos y  
                                      el if consiste en : si la posision del enemigo es mayor a 20 (en el eje x), que el movimiento (mv) que es una propiedad que le añadi, que pase en el sentido opuesto del movimiento del eje x que tiene actualmente por ej si tiene 0.3 movimiento en x, pasara a tener -0.3 moviento en x (se movera para el lado opusto del que venia).###
        
        enemigo.position.y -= 3  | ###hace que el enemigo baje en "-3" en el eje Y###
        
        
    if enemigo.position.x < -20 :   | ###Hace lo mismo que el if anterior###
        enemigo["mv"] *= -1       
        
        enemigo.position.y -= 3   | ###hace que el enemigo baje en "-3" en el eje Y###

    enemigo.position.x += enemigo["mv"] ### hace que se corran las propiedades del juego###

main()



