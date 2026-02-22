# Proyecto-Integrador

Este apartado documenta la transición de estructuras lineales a geometrías complejas y la implementación de movimiento cinematográfico en Blender.

### 1. Lógica del Pasillo Curvo
Para generar un pasillo que describa un arco circular, se sustituye la traslación lineal por un sistema de **coordenadas polares**:

* **Cálculo de Posición**: Se utilizan las funciones `math.cos` y `math.sin` para ubicar cada bloque en un radio específico respecto al centro.
* **Doble Pared**: El script calcula dos radios distintos (`r_izq` y `r_der`) para crear el espacio interno del pasillo.
* **Orientación Dinámica**: Cada bloque se rota automáticamente en el eje Z (`rotation_euler.z = angulo`) para que las caras siempre sigan la trayectoria de la curva.
* **Alternancia Estética**: Se aplica una lógica de materiales y escalamiento intercalado (`i % 2 == 0`) para generar ritmo visual en las paredes.

<img width="750" height="500" alt="Captura de pantalla 2026-02-22 104433" src="https://github.com/user-attachments/assets/956dc11f-3afe-4ffc-907d-e367a785dce5" />

### 2. Animación mediante Fotogramas Clave (Keyframes)
La animación permite dar vida al escenario mediante el registro de estados de los objetos en la línea de tiempo.

* **Keyframes**: Representados como rombos amarillos en el panel de **Dope Sheet**, guardan la posición y rotación de la cámara en fotogramas específicos (ej. 1, 84, 192, 216).
* **Interpolación**: Blender calcula automáticamente el movimiento entre las llaves, creando un recorrido fluido a través del pasillo.
* **Vista de Cámara**: El visor de "Camera Perspective" permite previsualizar el encuadre final que tendrá la animación.

<img width="750" height="500" alt="Captura de pantalla 2026-02-22 104423" src="https://github.com/user-attachments/assets/fa9fda52-7a45-4f82-8f90-ca7adecd55c2" />  

### 3. Procedimiento General de Ejecución
1.  **Scripting**: Se ejecuta el código para generar la geometría curva.
2.  **Keyframing**: Se selecciona la cámara y se presiona la tecla `I` en diferentes puntos de la línea de tiempo para registrar el movimiento.
3.  **Renderizado**: Se procesa la secuencia para obtener el video final del recorrido.
   
