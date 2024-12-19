# Unidad 2 - Jugabilidad básica

## Lección 2.1: 
1. **Crear y importar proyecto**: Primero cree un nuevo proyecto en 3D llamado "prototype_2" en el cual importamos los archivos necesarios y en las escenas eliminamos la escena llamada "sampleEscene"
2. **Agregar el jugador, animales y comida**: En este paso agregamos 1 humano, 3 animales y 1 comida, además de cambiarle el nombre al humano por "Player" y por último ajustamos la escala de la comida.
3. **Obtener la entrada horizontal de los usuarios**: \
  3.1. En la carpeta **Assets**, creé una carpeta llamada **Scripts** y un guión llamado **PlayerController** dentro. \
  3.2. Luego, arrastre el Script hasta el archivo de Player y lo abrí. \
  3.3. En la parte superior de **PlayerController.cs**, declaré una nueva variable de tipo flotante público llamada   
  **horizontalInput**. \
  3.4. Después en la función **Update()**, asigné **horizontalInput** a `Input.GetAxis("Horizontal")` y probé para asegurarme de que     
  funcionara en el Inspector. 
4. **Mover el jugador de Izquierda a Derecha**: \
   4.1 Primero, declaré una nueva variable pública de tipo flotante llamada speed y la establecí en 15.0. \
   4.2 Luego, en el método Update(), hice que el jugador se moviera de lado a lado en función de horizontalInput y speed. 
5. **Mantener a la jugador@ dentro**: \
   5.1 Primero, en el método Update(), escribí una sentencia if para verificar si la posición X izquierda del jugador es menor que un 
   valor determinado. \
   5.2 Luego, en la sentencia if, establecí la posición del jugador en su posición actual, pero con una ubicación X fija. 
6. **Limpia tu código y variables**: \
   6.1 Repetí este proceso para el lado derecho de la pantalla. \
   6.2 Luego, declaré una nueva variable llamada xRange y reemplacé los valores codificados con ella. \
   6.3 Además, añadí comentarios a mi código para hacerlo más claro.

## Lección 2.2
1. **Hacer que el proyectil vuele hacia adelante**: \
   1.1: Primero, creé un nuevo script llamado MoveForward, lo adjunté al objeto de comida y luego lo abrí. \
   1.2: Declaré una nueva variable pública de tipo flotante para la velocidad. \
   1.3: En el método Update(), añadí transform.Translate(Vector3.forward * Time.deltaTime * speed); y luego guardé los cambios. \
   1.4: Finalmente, en el Inspector, configuré la variable de velocidad del proyectil y probé para asegurarme de que funcionara 
   correctamente.
2. **Convertir el proyectil en una prefabricada**: \
   2.1: Creé una nueva carpeta llamada Prefabs, arrastré mi objeto de comida hacia ella y elegí Prefab original. \
   2.2: Luego, en PlayerController.cs, declaré una nueva variable pública de tipo GameObject llamada projectilePrefab. \
   2.3: Después, seleccioné el jugador en la jerarquía y arrastré el objeto desde mi carpeta Prefabs hacia el nuevo cuadro de Prefab de 
   proyectil en el Inspector. \
   2.4: Finalmente, intenté arrastrar el proyectil hacia la escena en tiempo de ejecución para asegurarme de que volaba correctamente.
3. **Prueba de pulsación de la barra espaciadora**: \
   3.1: En PlayerController.cs, en el método Update(), agregué una declaración if para verificar si se presiona la barra espaciadora con 
   if (Input.GetKeyDown(KeyCode.Space)). \
   3.2: Dentro de esta declaración if, añadí un comentario que indica que debo (Lanzar un proyectil desde el jugador).
4. **Lanzar proyectil al presionar la barra espaciadora**: \
   4.1: Dentro de la declaración if, utilicé el método Instantiate para generar un proyectil en la ubicación del jugador con la rotación del prefabricado.
5. **Convierte animales en prefab**: \
   5.1: Primero, giré todos los animales en el eje Y 180 grados para que quedaran boca abajo. \
   5.2: Luego, seleccioné los tres animales en la jerarquía y seleccioné Agregar componente > Avanzar. \
   5.3: Después, edité sus valores de velocidad y probé para ver cómo se veían. \
   5.4: Finalmente, arrastré los tres animales a la carpeta Prefabs y elegí “Prefab original”. \
   5.5: Probé arrastrando los prefabs a la vista de escena durante el juego para asegurarme de que todo funcionara correctamente.
6. **Destruye proyectiles fuera de la pantalla**: \
   6.1: Creé el script llamado DestroyOutOfBounds y lo apliqué al proyectil. \
   6.2: Luego, agregué una nueva variable privada de tipo flotante llamada topBound y la inicialicé a 30. \
   6.3: Escribí el código para destruir el objeto si está fuera de los límites superiores utilizando if (transform.position.z > topBound) { Destroy(gameObject); }. \
   6.4: Finalmente, en el menú desplegable Inspector Overrides, hice clic en "Apply all" para aplicarlo al prefab.
7. **Destruir animales fuera de la pantalla**: \
   7.1: Creé una declaración else-if para verificar si los objetos están por debajo del límite inferior utilizando else if (transform.position.z < lowerBound). \
   7.2: Luego, apliqué el script a todos los animales y anulé los prefabricados.

## Lección 2.3
1. **Crear un administrador de spawn**: \
   1.1: En la Hierarchy, creé un objeto vacío llamado SpawnManager. \
   1.2: Luego, creé un nuevo script llamado SpawnManager, lo adjunté al Spawn Manager y lo abrí. \
   1.3: Declaré un nuevo arreglo público de GameObject llamado animalPrefabs. \
   1.4: En el Inspector, cambié el tamaño del arreglo para que coincidiera con la cantidad de animales y luego asigné mis animales 
   arrastrándolos desde la ventana del Proyecto a los espacios vacíos.
2. **Genera un animal si se presiona S**:
   2.1: En el método Update(), escribí una declaración if-then para crear una instancia de un nuevo prefab de animal en la parte superior 
   de la pantalla si se presiona la tecla "S". \
   2.2: Luego, declaré un nuevo entero público llamado animalIndex e incorporé esta variable en la llamada Instantiate. \
   2.3: Después, probé editando el valor en el Inspector para asegurarme de que funcionara correctamente.
3. **Generar animales aleatorios a partir de una matriz**:
   3.1: En la instrucción if que verifica si se presiona la tecla "S", generé un entero animalIndex aleatorio entre 0 y la longitud de la 
   matriz. \
   3.2: Luego, eliminé la variable global animalIndex, ya que solo se necesitaba localmente dentro de la instrucción if.
4. **Aleatorizar la ubicación de aparición**:
   4.1: Reemplacé el valor X de Vector3 con Random.Range(-20, 20), luego probé para asegurarme de que funcionara correctamente. \
   4.2: Dentro de la declaración if, creé una nueva variable local Vector3 llamada spawnPos. En la parte superior de la clase, creé 
   variables privadas de tipo flotante para spawnRangeX y spawnPosZ.
5. **Cambiar la perspectiva de la cámara**:
   5.1: Alterné entre la vista en perspectiva y la vista isométrica en la vista de escena para apreciar la diferencia. \
   5.2: Luego, seleccioné la cámara y cambié la proyección de "Perspectiva" a "Ortográfica".

## Lección 2.4:
1. **Crea un nuevo método para generar animales.**:
   1.1:En SpawnManager.cs, creé una nueva función void SpawnRandomAnimal() {} debajo del método Update(). Corté y pegué el código de la 
   declaración if-then a la nueva función. \
   1.2: Luego, llamé a SpawnRandomAnimal(); si se presionaba la tecla "S".
2. **Generar animales a intervalos cronometrados**:\
   2.1: En el método Start(), utilicé InvokeRepeating para generar los animales en intervalos regulares y luego probé para asegurarme de 
   que funcionara. Eliminé la declaración if-then que comprobaba si se presionaba la tecla "S". \
   2.2: También, declaré nuevas variables privadas llamadas startDelay y spawnInterval, y luego realicé pruebas y ajustes en los valores 
   de estas variables.
3. **Agregar componentes de colisionador y disparador**: \
   3.1: Primero, hice doble clic en uno de los prefabs de animales, luego añadí un componente de Box Collider. \
   3.2: Me aseguré de que "Auto Save" estuviera habilitado en la esquina superior derecha de la vista de escena. \
   3.3: Hice clic en "Edit Collider", luego arrastré los manejadores del collider para abarcar el objeto. Marqué la casilla de 
   verificación "Is Trigger". \
   3.4: Usé el menú desplegable de Overrides para aplicar este Trigger a todos los prefabs de este animal. \
   3.5: Repetí este proceso para cada uno de los animales y el proyectil. \
   3.6: Finalmente, añadí un componente RigidBody al proyectil y desmarqué "use gravity".
4. **Destruir objetos en caso de colisión**: \
   4.1: Primero, creé un nuevo script llamado DetectCollisions.cs y lo añadí a cada prefab de animal, luego lo abrí. \
   4.2: Antes del último }, añadí la función OnTriggerEnter usando la función de autocompletar. \
   4.3: En OnTriggerEnter, incluí Destroy(gameObject); y luego probé para asegurarme de que funcionara. \
   4.4: Después, en OnTriggerEnter, también añadí Destroy(other.gameObject);.
5. **Activar un mensaje de “Juego terminado”**: \
   5.1: En DestroyOutOfBounds.cs, en la condición else-if que verifica si los animales llegan al fondo de la pantalla, añadí un mensaje 
   de "Game Over" con Debug.Log("Game Over!"). \
   5.2: Luego, limpié el código añadiendo comentarios.\
   5.3: Si estás usando Visual Studio, hice clic en Editar > Avanzado > Formatear documento para solucionar cualquier problema de 
   indentación.
# Enlaces:
- [Archivo package](https://github.com/Sergio473/CVU1R2/releases/Prototype)
- [Video demostración de juego lección 2.1 a 2.4](https://drive.google.com/file/d/1Y-Xul7GW-bXNIa3R4WPfGCgYG2nfUh5w/view?usp=drive_link)

# Unidad 3 - Sonidos y efectos

## Lección 3.1
1. **Abrir prototipo y cambiar el fondo**: \
   1.1: Abrí Unity Hub y creé un proyecto vacío llamado "Prototype 3" en el directorio de mi curso, usando la versión correcta de Unity. \
   1.2: Luego, hice clic para descargar los archivos iniciales de Prototype 3, extraje la carpeta comprimida y luego importé el .unitypackage en mi proyecto. \
   1.3: Abrí la escena de Prototype 3 y eliminé la escena de muestra sin guardar. \
   1.4: Después, seleccioné el objeto de fondo en la jerarquía y en el componente Sprite Renderer, seleccioné la imagen _City, _Nature, o _Town.
2. **Elige y configura un personaje jugador**: \
   2.1: Desde la Course Library, en la sección de Characters, arrastré un personaje a la jerarquía, lo renombré como “Player” y luego lo giré en el eje Y para que mirara hacia la 
   derecha. \
   2.2: Añadí un componente de Rigid Body. \
   2.3: Luego, añadí un box collider y edité los límites del collider.
   2.4: Creé una nueva carpeta llamada “Scripts” en Assets, creé un script llamado “PlayerController” dentro y lo adjunté al jugador.
3. **Hacer saltar al jugador al inicio**: \
   3.1: En PlayerController.cs, declaré una nueva variable privada de tipo Rigidbody llamada playerRb. \
   3.2: En el método Start(), inicialicé playerRb con GetComponent<Rigidbody>(). \
   3.3: Además, en Start(), utilicé el método AddForce para hacer que el jugador saltara al inicio del juego. 
4. **Hacer que el jugador salte si se presiona la barra espaciadora**: \
   4.1: En el método Update(), añadí una declaración if-then para verificar si se presiona la barra espaciadora. \
   4.2: Luego, corté y pegué el código AddForce desde Start() dentro de la declaración if. \
   4.3: También añadí el parámetro ForceMode.Impulse a la llamada AddForce y reduje el valor del multiplicador de fuerza.
5. **Ajusta la fuerza del salto y la gravedad**:
   5.1: Reemplacé el valor codificado con una nueva variable pública de tipo flotante llamada jumpForce. \
   5.2: Luego, añadí una nueva variable pública de tipo flotante llamada gravityModifier y, en el método Start(), agregué Physics.gravity *= gravityModifier;. \
   5.3: En el Inspector, ajusté los valores de gravityModifier, jumpForce, y la masa del Rigidbody para hacerlo más divertido.
6. **Evitar que el jugador doble salto**: \
   6.1: Primero, añadí una nueva variable pública de tipo bool llamada isOnGround y la establecí en true. \
   6.2: En la declaración if que permite al jugador saltar, establecí isOnGround = false y luego probé para asegurarme de que funcionara correctamente. \
   6.3: Añadí una condición && isOnGround a la declaración if. \
   6.4: Luego, añadí un nuevo método void OnCollisionEnter y dentro de este método establecí isOnGround = true. Probé nuevamente para confirmar que todo funcionaba correctamente.
7. **Crea un obstáculo y muévelo hacia la izquierda.**: \
   7.1: Desde la Course Library, en la sección de Obstacles, añadí un obstáculo, lo renombré como “Obstacle” y lo posicioné en el lugar donde debería aparecer. \
   7.2: Apliqué un componente Rigid Body y un Box Collider, luego edité los límites del collider para ajustarlo al obstáculo. \
   7.3: Creé una nueva carpeta llamada “Prefabs” y arrastré el obstáculo dentro para crear un nuevo Prefab Original. \
   7.4: Luego, creé un nuevo script llamado MoveLeft, lo apliqué al obstáculo y lo abrí. \
   7.5: En MoveLeft.cs, escribí el código para trasladarlo hacia la izquierda según la variable de velocidad. Finalmente, apliqué el script MoveLeft al fondo.
8. **Crear un administrador de spawn**: \
   8.1: Primero, creé un nuevo objeto vacío llamado "Spawn Manager" y le apliqué un nuevo script llamado SpawnManager.cs. \
   8.2: En SpawnManager.cs, declaré una nueva variable pública de tipo GameObject llamada obstaclePrefab y luego asigné mi prefab a la nueva variable en el Inspector. \
   8.3: Luego, declaré una nueva variable privada de tipo Vector3 llamada spawnPos en mi ubicación de aparición. \
   8.4: En el método Start(), instancié un nuevo prefab de obstáculo, luego eliminé el prefab de la escena y probé para asegurarme de que funcionara correctamente.
9. **Generar obstáculos a intervalos**: \
   9.1: Creé un nuevo método void SpawnObstacle(), luego moví la llamada a Instantiate dentro de este método. \
   9.2: Luego, creé nuevas variables de tipo flotante para startDelay y repeatRate. Hice que mis obstáculos se generaran en intervalos utilizando el método InvokeRepeating(). \
   9.3: En el componente Rigid Body del jugador, expandí las restricciones y congelé todas las posiciones excepto la posición Y.

## Lección 3.2 - Haz que el mundo pase volando
1. **Crear un script para repetir el fondo**:
   1.1 Creé un nuevo script llamado RepeatBackground.cs y lo adjunté al objeto de fondo. \
2. Restablecer la posición del fondo: \
   2.1 Declaré una nueva variable private Vector3 startPos;. \
   2.2 En el método Start(), establecí la variable startPos en su posición inicial asignándole = transform.position;. \
   2.3 En Update(), escribí una declaración if para restablecer la posición si se mueve una cierta distancia.
3. Arreglar la repetición del fondo con un collider:
   3.1 Añadí un componente Box Collider al fondo. \
   3.2 Declaré una nueva variable private float repeatWidth;. \
   3.3 En Start(), obtuve el ancho del box collider, dividido por 2. \
   3.4 Incorporé la variable repeatWidth en la función de repetición.
4. Añadir un nuevo desencadenante de "game over": \
   4.1 En el inspector, añadí una etiqueta “Ground” al suelo y una etiqueta “Obstacle” al prefab del obstáculo. \
   4.2 En PlayerController, declaré una nueva variable pública bool gameOver;. \
   4.3 En OnCollisionEnter, añadí la declaración if-else para verificar si el jugador colisionó con el “Ground” o con un “Obstacle”. \
   4.4 Si colisionaba con el “Ground”, establecía isOnGround = true, y si colisionaba con un “Obstacle”, establecía gameOver = true.
5. Detener MoveLeft en "game over": \
   5.1 En MoveLeft.cs, declaré un nuevo private PlayerController playerControllerScript;. \
   5.2 En Start(), lo inicialicé buscando el jugador y obteniendo el componente PlayerController. \
   5.3 Envolví el método Translate en una declaración if que verifica si el juego no ha terminado.
6. Detener la aparición de obstáculos en "game over": \
   6.1 En SpawnManager.cs, obtuve una referencia a playerControllerScript utilizando la misma técnica que en MoveLeft.cs. \
   6.2 Añadí una condición para instanciar objetos solo si gameOver == false.
7. Destruir obstáculos que salgan de los límites: \
   7.1 En MoveLeft, en Update(), escribí una declaración if para destruir los obstáculos si su posición es menor que una variable leftBound. \
   7.2 Añadí los comentarios necesarios para hacer que el código sea más legible.






   
