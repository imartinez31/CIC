**Eco**

**-Concepto**

Un juego de puzles y exploración en 2D donde el jugador controla a un personaje que se mueve por cuevas completamente oscuras. No hay luz. La única forma de "ver" el entorno es emitir un pulso de sonido (como un sonar) que revela brevemente las paredes, plataformas y peligros a su alrededor, dibujándolos como líneas que se desvanecen en 2-3 segundos.

**-Elementos formales**

-Mecánica principal
El jugador presiona un botón para emitir un pulso sonoro que ilumina el entorno cercano durante un tiempo limitado. Mientras el eco está activo, puede ver y planear su ruta; cuando se apaga, el escenario vuelve a la oscuridad y debe moverse "a ciegas" basándose en lo que memorizó.

-Objetivo del jugador
Llegar a la salida de cada cueva evitando caídas, criaturas ciegas (que detectan al jugador por el sonido que él mismo genera) y trampas, usando la menor cantidad de pulsos posible.

**-Reglas básicas**

1. Cada pulso de sonido tiene un radio y una duración limitados.
2. Emitir un pulso también alerta a las criaturas cercanas, que se mueven hacia el origen del sonido.
3. El jugador tiene un número limitado de pulsos por nivel (un recurso, no infinito).
4. Moverse en la oscuridad sin pulso es más rápido y silencioso, pero arriesgado (se puede caer o chocar).
5. Recoger cristales opcionales requiere desviarse de la ruta segura, aumentando el riesgo.

**-Experiencia buscada**

El jugador debe sentir tensión contenida y concentración, similar a contener la respiración. Cada pulso es una decisión cargada de peso: ver implica exponerse. Esto genera un ritmo de alternancia entre momentos de información (seguridad momentánea) y momentos de incertidumbre (avance a ciegas, confiando en la memoria).

La mecánica de "ver = ser visto" es la que produce esto directamente: no hay forma de tener información gratis, así que el jugador nunca se siente completamente cómodo, pero tampoco frustrado, porque siempre tiene la opción de pausar y pulsar de nuevo si el riesgo se vuelve demasiado alto. Es una tensión regulable, no impuesta.

**-Coherencia del diseño (marco MDA)**
- Mecánica → Dinámica: el pulso limitado y el ruido que atrae enemigos generan la dinámica de "explorar con cautela, avanzar de memoria". El jugador desarrolla un ritmo natural de pulso-avance-pausa sin que el juego se lo diga explícitamente.
- Dinámica → Estética: esa dinámica de exposición controlada produce la estética de tensión/suspenso y descubrimiento, porque cada pulso es tanto una revelación visual como un riesgo estratégico.
- Objetivo y reglas refuerzan la estética: el recurso limitado de pulsos impide que el jugador abuse del sistema (spamear luz), obligándolo a tomar decisiones significativas en vez de trivializar el reto. Los cristales opcionales añaden una capa de tensión adicional: tentar al jugador a arriesgarse más de lo necesario, profundizando la sensación de vulnerabilidad autoimpuesta.
