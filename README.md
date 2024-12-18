# CVU1R2

# Repositorio CVU1R2

# Jugabilidad básica


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
# Enlace a video:
- [Lección 1](https://link-a-leccion-1.com)
- [Desafío 1](https://link-a-desafio-1.com)
- [Laboratorio 1](https://link-a-laboratorio-1.com)
- [Prueba 1](https://link-a-prueba-1.com)
