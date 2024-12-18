# CVU1R2

# Repositorio CVU1R2

## Enlaces a actividades

# Lección 2.1: 
1. **Crear y importar proyecto**: Primero cree un nuevo proyecto en 3D llamado "prototype_2" en el cual importamos los archivos necesarios y en las escenas eliminamos la escena llamada "sampleEscene"
2. **Agregar el jugador, animales y comida**: En este paso agregamos 1 humano, 3 animales y 1 comida, además de cambiarle el nombre al humano por "Player" y por último ajustamos la escala de la comida.
3. **Obtener la entrada horizontal de los usuarios**: \
  3.1. En la carpeta **Assets**, creé una carpeta llamada **Scripts** y un guión llamado **JugadorControlador** dentro. \
  3.2. Luego, arrastre el Script hasta el archivo de Player y lo abrí. \
  3.3. En la parte superior de **PlayerController.cs**, declaré una nueva variable de tipo flotante público llamada   
  **horizontalInput**. \
  3.4. Después en la función **Update()**, asigné **horizontalInput** a `Input.GetAxis("Horizontal")` y probé para asegurarme de que     
  funcionara en el Inspector. 
4. **Mover el jugador de Izquierda a Derecha**: \
   4.1 Primero, declaré una nueva variable pública de tipo flotante llamada speed y la establecí en 10.0. \
   4.2 Luego, en el método Update(), hice que el jugador se moviera de lado a lado en función de horizontalInput y speed. 
5. **Mantener a la jugador@ dentro**: \
   5.1 Primero, en el método Update(), escribí una sentencia if para verificar si la posición X izquierda del jugador es menor que un 
   valor determinado. \
   5.2 Luego, en la sentencia if, establecí la posición del jugador en su posición actual, pero con una ubicación X fija. 
6. **Limpia tu código y variables**: \
   6.1 Repetí este proceso para el lado derecho de la pantalla. \
   6.2 Luego, declaré una nueva variable llamada xRange y reemplacé los valores codificados con ella. \
   6.3 Además, añadí comentarios a mi código para hacerlo más claro.
### Nueva Funcionalidad
He implementado una nueva funcionalidad en mi juego: ahora puedo moverme hacia la izquierda y hacia la derecha según las pulsaciones de las teclas izquierda y derecha. También me aseguré de que no pueda salir del área de juego por ninguno de los lados.
### Nuevos Conceptos y Habilidades
He aprendido a ajustar la escala de los objetos y a utilizar declaraciones con operadores mayor/menor que.

# Lección 2.2
1. **Hacer que el proyectil vuele hacia adelante**: \
   1.1: Primero, creé un nuevo script llamado MoveForward, lo adjunté al objeto de comida y luego lo abrí. \
   1.2: Declaré una nueva variable pública de tipo flotante para la velocidad. \
   1.3 En el método Update(), añadí transform.Translate(Vector3.forward * Time.deltaTime * speed); y luego guardé los cambios. \
   1.4 Finalmente, en el Inspector, configuré la variable de velocidad del proyectil y probé para asegurarme de que funcionara 
   correctamente.
2. **Convertir el proyectil en una prefabricada**: \
   2.1: Creé una nueva carpeta llamada Prefabs, arrastré mi objeto de comida hacia ella y elegí Prefab original. \
   2.2: Luego, en PlayerController.cs, declaré una nueva variable pública de tipo GameObject llamada projectilePrefab. \
   2.3 Después, seleccioné el jugador en la jerarquía y arrastré el objeto desde mi carpeta Prefabs hacia el nuevo cuadro de Prefab de 
   proyectil en el Inspector. \
   2.4: Finalmente, intenté arrastrar el proyectil hacia la escena en tiempo de ejecución para asegurarme de que volaba correctamente.
3. **Prueba de pulsación de la barra espaciadora**: \
   3.1: En PlayerController.cs, en el método Update(), agregué una declaración if para verificar si se presiona la barra espaciadora con 
   if (Input.GetKeyDown(KeyCode.Space)). \
   3.2: Dentro de esta declaración if, añadí un comentario que indica que debo (Lanzar un proyectil desde el jugador).
   
# Enlace a video:
- [Lección 1](https://link-a-leccion-1.com)
- [Desafío 1](https://link-a-desafio-1.com)
- [Laboratorio 1](https://link-a-laboratorio-1.com)
- [Prueba 1](https://link-a-prueba-1.com)
