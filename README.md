# Unidad 2 - Jugabilidad básica

## Enlaces a archivo y video:
- [Archivo package](https://github.com/Sergio473/CVU1R2/releases/Prototype)
- [Video demostración de juego lección 2.1 a 2.4](https://drive.google.com/file/d/1Y-Xul7GW-bXNIa3R4WPfGCgYG2nfUh5w/view?usp=drive_link)

# Unidad 3 - Sonidos y efectos

## Enlaces a archivo y video:
- [Archivo package](https://github.com/Sergio473/CVU1R2/releases/Prototype)
- [Video demostración de juego lección 2.1 a 2.4](https://drive.google.com/file/d/1Y-Xul7GW-bXNIa3R4WPfGCgYG2nfUh5w/view?usp=drive_link)
  
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
## Lección 3.3 - No te quedes ahí parado
1. Explorar las animaciones del jugador: \
   1.1 Hice doble clic en el controlador de animación del jugador, luego exploré las diferentes capas, haciendo doble clic en los estados para ver sus animaciones y en las transiciones 
   para ver sus condiciones.
2. Hacer que el jugador comience corriendo: \
   2.1 En la pestaña de Parámetros, cambié la variable Speed_f a 1.0. \
   2.2 Hice clic derecho en Run_Static y seleccioné Set as Layer Default State. \
   2.3 Hice clic una sola vez en el estado Run_Static y ajusté el valor de velocidad en el inspector para que coincidiera con la velocidad del fondo.
3. Configurar una animación de salto: \
   3.1 En PlayerController.cs, declaré un nuevo private Animator playerAnim;. \
   3.2 En Start(), establecí playerAnim = GetComponent<Animator>();. \
   3.3 En la declaración if para cuando el jugador salta, activé el salto con playerAnim.SetTrigger("Jump_trig");.
4. Ajustar la animación de salto: \
   4.1 En la ventana del Animator, hice clic en el estado Running_Jump, luego en el inspector y reduje su valor de velocidad para ralentizar la animación. \
   4.2 Ajusté la masa del jugador, la fuerza del salto y el modificador de gravedad para que el salto fuera perfecto.
5. Configurar una animación de caída: \
   5.1 En la condición de que el jugador colisione con un obstáculo, establecí el bool Death en true. \
   5.2 En la misma declaración if, establecí el entero DeathType en 1.
6. Evitar que el jugador salte estando inconsciente: \
   6.1 Para evitar que el jugador salte mientras está inconsciente, añadí && !gameOver a la condición de salto.

Lección 3.4 - Particles and Sound Effects
1. Personalizar una partícula de explosión: \
   1.1 Desde la Course Library, en la sección Particles, arrastré FX_Explosion_Smoke a la jerarquía y luego utilicé los botones Play / Restart / Stop para previsualizarla. \
   1.2 Jugué con los ajustes para que el sistema de partículas quedara como quería. \
   1.3 Me aseguré de desmarcar la opción Play on Awake. \ 1.4 Arrastré la partícula sobre mi jugador para convertirla en un objeto hijo y luego la posicioné en relación con el jugador.
2. Reproducir la partícula en colisión: \
   2.1 En PlayerController.cs, declaré una nueva variable pública ParticleSystem explosionParticle;. \
   2.2 En el Inspector, asigné la explosión a la variable de partículas de explosión. \
   2.3 En la declaración if donde el jugador colisiona con un obstáculo, llamé a explosionParticle.Play(); y luego probé y ajusté las propiedades de la partícula.
3. Añadir una partícula de salpicadura de tierra: \
   3.1 Arrastré FX_DirtSplatter como objeto hijo del jugador, lo reposicioné, lo roté y edité sus ajustes. \
   3.2 Declaré una nueva variable pública ParticleSystem dirtParticle; y luego la asigné en el Inspector. \
   3.3 Añadí dirtParticle.Stop(); cuando el jugador salta o colisiona con un obstáculo. \
   3.4 Añadí dirtParticle.Play(); cuando el jugador aterriza en el suelo.
4. Añadir música al objeto de la cámara: \
   4.1 Seleccioné el objeto Main Camera y luego añadí el componente Audio Source. \
   4.2 Desde la Course Library, en la sección Sound, arrastré un clip de música a la variable AudioClip en el Inspector. \
   4.3 Reduje el volumen para que fuera más fácil escuchar los efectos de sonido. \
   4.4 Marqué la casilla de verificación Loop.
5. Declarar variables para los clips de audio: \
   5.1 En PlayerController.cs, declaré una nueva variable pública AudioClip jumpSound; y una nueva variable pública AudioClip crashSound;. \
   5.2 Desde la Course Library, en la sección Sound, arrastré un clip a cada nueva variable de sonido en el Inspector.
6. Reproducir clips de audio al saltar y chocar: \
   6.1 Añadí un componente Audio Source al jugador. \
   6.2 Declaré una nueva variable privada AudioSource playerAudio; y la inicialicé como playerAudio = GetComponent<AudioSource>();. \
   6.3 Llamé a playerAudio.PlayOneShot(jumpSound, 1.0f); cuando el personaje saltaba. \
   6.4 Llamé a playerAudio.PlayOneShot(crashSound, 1.0f); cuando el personaje chocaba.
   




   
