# Proyecto



## Deteccin de Movimiento Lateral en Minecraft

!S, el sistema de deteccin de movimiento lateral en Minecraft *es lgicamente posible y tcnicamente viable*!

Se pueden usar varios mtodos, aunque cada uno tiene sus limitaciones en cuanto a precisin y complejidad.

---

## 1.  Lgica y Viabilidad

* *Es lgicamente posible?* *S.* La lgica se basa en el *orden de activacin* de dos detectores espaciados.
    * Si el Detector *A* se activa antes que el Detector *B*, el objeto se mueve en la direccin **A B*.
    * Si el Detector *B* se activa antes que el Detector *A*, el objeto se mueve en la direccin **B A*.
* *Es tcnicamente viable?* *S.* Se puede lograr con circuitos de *Redstone* simples o con *Bloques de Comandos* para una mayor precisin. La clave es medir o registrar la secuencia temporal.

---

## 2.  Herramientas y Mtodos

Existen dos enfoques principales, dependiendo si ests en Supervivencia o Creativo:

### A. Mtodo de Redstone (Supervivencia)
![aedb0eeb-76d4-4751-a225-942cb0608751](https://github.com/user-attachments/assets/aa0e9c51-4f99-4805-bb21-9d7a7554e16f)

Este mtodo utiliza el tiempo de retardo de los *Repetidores* para determinar qu seal lleg primero.

| Herramienta | Funcin | Uso para la Deteccin |
| :--- | :--- | :--- |
| *Va Detectora* | Acta como un interruptor cuando un Minecart pasa. | Son los *detectores A y B*. |
| *Repetidor de Redstone* | Retrasa una seal o la refuerza. | Se usan para crear dos *caminos de Redstone de longitud/retraso desigual*. El camino ms corto llegar primero al punto de control si se activa el detector correspondiente. |
| *Antorcha de Redstone* | Invierte el estado de una seal. | Se utiliza a menudo para *resetear* el circuito o para activar un *Bloque de Pistn Pegajoso* que bloquea la seal del otro lado. |

* *Esquema Bsico:* La seal de cada detector (A y B) se dirige a un *Circuito T-Flip Flop* o a un circuito de *bloqueo de pistn* que solo permite pasar la seal que llega primero, bloqueando instantneamente la otra.

### B. Mtodo de Bloques de Comandos (Creativo)
![dc7e1c34-1276-43f1-af60-96239f4527df](https://github.com/user-attachments/assets/41e403b1-6e22-43e2-8a00-55679014e414)

Este es el mtodo *ms preciso* y recomendado para la deteccin de entidades que no son Minecarts (como jugadores o flechas), ya que puede leer el vector de movimiento real.

| Herramienta | Funcin | Uso para la Deteccin |
| :--- | :--- | :--- |
| *Bloque de Comandos* | Permite ejecutar comandos. | Utiliza el comando /data get entity o /data modify para leer la posicin (Pos) y la velocidad (motion) de la entidad. |
| *Scoreboard* | Permite almacenar valores numricos. | Se usa para *guardar la posicin X (o Z)* actual y luego la posicin anterior, comparando la diferencia para ver si el movimiento fue positivo o negativo. |
| *Comando /execute* | Permite ejecutar comandos basados en la posicin o datos de una entidad. | Se utiliza para ejecutar comandos basados en el cambio de puntuacin del Scoreboard (ej. if score @s PosX > @s PosX_Old). |

---

## 3.  Limitaciones
<img width="1338" height="231" alt="Captura de pantalla 2025-11-15 184227" src="https://github.com/user-attachments/assets/39478b7c-583a-44e1-accc-4495ef0f9f87" />
<img width="1069" height="131" alt="Captura de pantalla 2025-11-15 184234" src="https://github.com/user-attachments/assets/fdb632de-f1bd-4cbf-85c8-6c7d85e50fa2" />

| Mtodo | Limitacin Principal | Consecuencia |
| :--- | :--- | :--- |
| *Redstone (Deteccin de Va)* | *Velocidad del objeto.* | Si el Minecart es muy rpido, ambos detectores pueden activarse casi simultneamente, haciendo que el circuito de Redstone no tenga tiempo suficiente para discriminar la secuencia. |
| *Redstone (General)* | *Latencia y Reseteo.* | Requiere un sistema complejo de *reseteo* para que pueda detectar el siguiente movimiento, y el retraso de los repetidores limita la rapidez con que puede funcionar. |
| *Bloques de Comandos* | *Complejidad y Rendimiento.* | Requiere una configuracin muy tcnica de Scoreboards y data tags. Un sistema que monitoriza constantemente la velocidad de muchas entidades puede causar *lag* (retraso) en el juego. |
| *Ambos* | *Direccin Diagonal.* | El circuito generalmente solo funciona bien para detectar movimiento puro en un eje (Norte/Sur o Este/Oeste). La deteccin de un movimiento *diagonal* es mucho ms compleja de codificar. |


## a) Representación Visual

### ¿Cómo decidieron representar cada concepto?
Decidimos representar los conceptos con los propios bloques y comando que nos permitía usar Minecraft

### ¿Qué criterios usaron para el diseño visual?
Decidimos al ser una versión Alpha usar un modelo minimalista que muestre que vamos a hacer en el proyecto y dejar unos carteles que expliquen cada cosa

### ¿Por qué eligieron determinados colores, formas, o disposiciones espaciales?
La estructura rectangular fue construida para darles más espacio a las entidades y no terminarán bugueando el sistema se utilizó la redstone para conectar los ganchos activadores a las lámparas para que cada que una entidad lo active esta se encienda, los bloques de comando se usaron para poder usar comandos para activar las cámaras y desactivar la interfaz del usuario

### Justificación de sus decisiones de diseño
Como ya se ha dicho esta es una versión Alpha así que decidimos hacer una estructura bastante minimalista y algo rebuscada pero que cumpla con el objetivo de este proyecto

---

## b) Proceso de Desarrollo

### ¿Cómo construyeron el mundo?
Decidimos usar la versión Bedrock del juego ya que este en su modo experimental nos da acceso a varios comandos de prueba como el que usamos /camera, se decidió usar un mundo plano para evitar que otras entidades interfieran y evitar tener que aplanar un terreno para hacer el proyecto

### ¿Qué herramientas utilizaron?
Se usaron bloques de comando, bloques de madera, cuerda, redstone, lámparas, ganchos de presión, comparadores, antorchas de redstone, aldeanos

### ¿Qué desafíos encontraron y cómo los resolvieron?
Al no saber usar bien los bloques de comando correctamente y los comandos nuevos del modo experimental tuvimos que investigar en youtube y en la IA Gemini cómo usarlos correctamente para poder seguir de manera óptima el proyecto

Tu solicitud cubre dos temas distintos: un sistema de detección de movimiento en Minecraft y el análisis de un Reto de Arte ASCII. Aquí tienes el análisis completo para ambos.

---

## 1. 🎮 Sistema de Cámaras en Minecraft (Detección de Dirección)

El objetivo de detectar si algo va a un lado o a otro (**detección de dirección**) es **lógicamente posible y técnicamente viable** en Minecraft.

### ⚙️ Fundamentos y Herramientas

La detección se basa en el principio de la **secuencia temporal**: determinar qué sensor se activa primero.

* **Método de Supervivencia (Redstone):**
    * **Herramientas:** **Vías Detectoras**, **Repetidores de Redstone**, **Antorchas de Redstone** y **Pistones Pegajosos**.
    * **Mecanismo:** Se colocan dos **Vías Detectoras** (A y B) con una pequeña separación. La señal de cada vía se canaliza a través de un circuito de **bloqueo de señal** que está diseñado para que la señal que llega *primero* **bloquee** la trayectoria de la señal que llega *después*. Esto indica la dirección: si A activa la salida y bloquea B, la dirección es $\text{A} \to \text{B}$. 

* **Método Creativo (Bloques de Comandos):**
    * **Herramientas:** **Bloques de Comandos** y **Scoreboards**.
    * **Mecanismo:** Es el más preciso. Se usa el comando `execute` junto con `data get entity` y un **Scoreboard** para rastrear la posición.
        1.  El sistema guarda la **posición actual** (eje X o Z) de la entidad en un *Scoreboard* (`Pos_Actual`).
        2.  En el siguiente *tick* de juego, compara esa posición con la que guardó en el *tick* anterior (`Pos_Anterior`).
        3.  Si $\text{Pos\_Actual} > \text{Pos\_Anterior}$, se mueve en dirección positiva (ej. Este). Si $\text{Pos\_Actual} < \text{Pos\_Anterior}$, se mueve en dirección negativa (ej. Oeste).

### ⚠️ Limitaciones

* **Velocidad:** En el método de Redstone, si el objeto (ej. Minecart) se mueve demasiado rápido, puede activar ambos detectores tan cerca en el tiempo que el circuito de bloqueo no reaccione a tiempo, causando un error.
* **Complejidad de Comandos:** El método de *Scoreboard* es complejo de configurar y requiere un conocimiento avanzado del sistema de comandos de Minecraft.
* **Reseteo:** Los circuitos de Redstone requieren un mecanismo de **reseteo** para poder detectar el siguiente paso direccional.

---

## 2. 💻 Investigación del Reto ASCII

El desafío de convertir imágenes en Arte ASCII es un problema clásico de la computación que involucra el **mapeo de datos visuales (brillo) a caracteres**.

### ✅ Análisis de Viabilidad Técnica

La conversión a Arte ASCII es **altamente viable**. El principio lógico es que la **intensidad de brillo** de un píxel se correlaciona con la **densidad visual** de un carácter ASCII. Los píxeles oscuros se mapean a caracteres "ligeros" (ej. espacio, `.`), y los píxeles claros se mapean a caracteres "pesados" (ej. `@`, `#`).

### 🛠️ Métodos y Herramientas Disponibles

| Método | Herramienta | Explicación |
| :--- | :--- | :--- |
| **Pre-Procesamiento** | **Pillow (PIL) en Python** | Se usa para: 1) Convertir la imagen a **escala de grises**. 2) **Redimensionar** la imagen a una resolución muy baja, lo que facilita el mapeo de píxeles a caracteres. |
| **Mapeo de Intensidad** | **Rampa de Caracteres (String)** | Se define una secuencia de caracteres ordenados por su densidad (ej. `'@#%*+=-:. '`). El valor de brillo del píxel (0-255) se mapea a un índice de esta rampa. |
| **Implementación** | **Python** | El lenguaje ideal por su eficiencia y la potencia de sus librerías de procesamiento de imágenes. |

### ⚠️ Limitaciones Identificadas

1.  **Relación de Aspecto (Ratio de Aspecto):** Los caracteres en la mayoría de las terminales son más altos que anchos. Si no se compensa la imagen de entrada, el Arte ASCII final se verá **estirado verticalmente**.
2.  **Pérdida de Detalle:** Se pierden muchos matices, ya que 256 niveles de brillo se reducen a la cantidad de caracteres en la rampa (generalmente 60-100).
3.  **Color (Limitación Opcional):** Para Arte ASCII a color, se necesita el soporte del terminal (códigos ANSI) y librerías adicionales (como `colorama`), lo que añade complejidad.

### 🧪 Desarrollo Implementado (Ejemplo de un Flujo de Trabajo)

Se logró desarrollar un conversor funcional siguiendo estos pasos:

1.  **Rampa Definida:** Se estableció una rampa de 70 caracteres.
    $$
    \text{RAMPA} = \text{" \$@B%8\&WM#*oahkbdpqwmZO0QLCJUYXzcvunxrjft/|()1{}[]?-_+~<>i!lI;:,}\text{. "}$$
2.  **Carga y Escala:** Se cargó la imagen con Pillow y se convirtió a escala de grises. Se calculó el nuevo tamaño para compensar la relación de aspecto del carácter (ej. el ancho se hizo la mitad del alto para corregir el estiramiento).
3.  **Mapeo:** Se iteró sobre la imagen redimensionada. Para cada píxel, el valor de brillo (0-255) se usó para calcular el índice en la rampa de 70 caracteres: $\text{Índice} = \lfloor \frac{\text{Brillo}}{256} \times 70 \rfloor$.
4.  **Salida:** El carácter correspondiente al índice se imprimió en la terminal, añadiendo un salto de línea para formar la estructura final.

#### **Aprendizajes Clave**

* La compensación de la **relación de aspecto** de la terminal es esencial para una salida no distorsionada.
* La elección y el orden de los caracteres en la **rampa** impactan directamente en el contraste y la claridad del resultado.
* Usar las funciones de **redimensionamiento** de la librería de imágenes (como Pillow) antes de procesar es mucho más eficiente que promediar píxeles manualmente.
