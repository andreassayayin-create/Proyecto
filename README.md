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

Este mtodo utiliza el tiempo de retardo de los *Repetidores* para determinar qu seal lleg primero.

| Herramienta | Funcin | Uso para la Deteccin |
| :--- | :--- | :--- |
| *Va Detectora* | Acta como un interruptor cuando un Minecart pasa. | Son los *detectores A y B*. |
| *Repetidor de Redstone* | Retrasa una seal o la refuerza. | Se usan para crear dos *caminos de Redstone de longitud/retraso desigual*. El camino ms corto llegar primero al punto de control si se activa el detector correspondiente. |
| *Antorcha de Redstone* | Invierte el estado de una seal. | Se utiliza a menudo para *resetear* el circuito o para activar un *Bloque de Pistn Pegajoso* que bloquea la seal del otro lado. |

* *Esquema Bsico:* La seal de cada detector (A y B) se dirige a un *Circuito T-Flip Flop* o a un circuito de *bloqueo de pistn* que solo permite pasar la seal que llega primero, bloqueando instantneamente la otra.

### B. Mtodo de Bloques de Comandos (Creativo)

Este es el mtodo *ms preciso* y recomendado para la deteccin de entidades que no son Minecarts (como jugadores o flechas), ya que puede leer el vector de movimiento real.

| Herramienta | Funcin | Uso para la Deteccin |
| :--- | :--- | :--- |
| *Bloque de Comandos* | Permite ejecutar comandos. | Utiliza el comando /data get entity o /data modify para leer la posicin (Pos) y la velocidad (motion) de la entidad. |
| *Scoreboard* | Permite almacenar valores numricos. | Se usa para *guardar la posicin X (o Z)* actual y luego la posicin anterior, comparando la diferencia para ver si el movimiento fue positivo o negativo. |
| *Comando /execute* | Permite ejecutar comandos basados en la posicin o datos de una entidad. | Se utiliza para ejecutar comandos basados en el cambio de puntuacin del Scoreboard (ej. if score @s PosX > @s PosX_Old). |

---

## 3.  Limitaciones

| Mtodo | Limitacin Principal | Consecuencia |
| :--- | :--- | :--- |
| *Redstone (Deteccin de Va)* | *Velocidad del objeto.* | Si el Minecart es muy rpido, ambos detectores pueden activarse casi simultneamente, haciendo que el circuito de Redstone no tenga tiempo suficiente para discriminar la secuencia. |
| *Redstone (General)* | *Latencia y Reseteo.* | Requiere un sistema complejo de *reseteo* para que pueda detectar el siguiente movimiento, y el retraso de los repetidores limita la rapidez con que puede funcionar. |
| *Bloques de Comandos* | *Complejidad y Rendimiento.* | Requiere una configuracin muy tcnica de Scoreboards y data tags. Un sistema que monitoriza constantemente la velocidad de muchas entidades puede causar *lag* (retraso) en el juego. |
| *Ambos* | *Direccin Diagonal.* | El circuito generalmente solo funciona bien para detectar movimiento puro en un eje (Norte/Sur o Este/Oeste). La deteccin de un movimiento *diagonal* es mucho ms compleja de codificar. |
