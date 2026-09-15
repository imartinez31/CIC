Evaluación de viabilidad de Zigzag Run
1. Concepto de UI

La interfaz de Zigzag Run debe ser simple para evitar distraer al jugador durante las secuencias de reacción rápida. La mayor parte de la información se comunicará mediante el propio escenario.

HUD:

Barra de progreso del nivel: muestra la distancia recorrida y cuánto falta para llegar al núcleo.
Indicador de peligro: muestra qué tan cerca está el colapso del jugador.
Cronómetro: registra el tiempo empleado en completar el sector.
Puntuación: refleja el rendimiento del jugador durante la partida.

Canales de información:

Visual: grietas, caída de estructuras, luces de emergencia, drones y avance del colapso.
Sonoro: alarmas, explosiones, estructuras rompiéndose y sonidos de los drones.
Interfaz: progreso, peligro, tiempo y puntuación.

Feedback: cuando el jugador realiza correctamente un salto o deslizamiento, la animación y el sonido confirman la acción. Si comete un error, pierde velocidad y el colapso se acerca. El indicador de peligro cambia para comunicar que existe mayor riesgo de perder.

2. Loop principal de interacción

El loop principal es:

Correr automáticamente → observar el escenario → identificar el obstáculo → saltar o deslizar → recibir feedback → mantener distancia del colapso → continuar → llegar al núcleo.

El jugador no controla la velocidad base. Su participación consiste principalmente en interpretar rápidamente los obstáculos y ejecutar la acción correcta.

Al terminar un sector, recibe información sobre su tiempo, puntuación y desempeño. Después comienza un nuevo sector con mayor dificultad.

3. Dinámicas asociadas y regulación mediante UI

La principal dinámica es la presión constante. El jugador debe continuar avanzando porque el escenario se destruye detrás de él. El indicador de peligro permite conocer qué tan cerca está de ser alcanzado sin necesidad de detener la acción.

La segunda dinámica es el dominio de las mecánicas. Al principio, salto y deslizamiento se utilizan de forma aislada. Posteriormente aparecen secuencias que requieren combinar ambas acciones rápidamente.

La tercera dinámica es la búsqueda de mejor rendimiento. El cronómetro, la puntuación y el progreso permiten comparar partidas y motivan al jugador a mejorar.

La UI debe regular estas dinámicas sin saturar la pantalla. La información indispensable durante la partida será el progreso y la cercanía del colapso, mientras que estadísticas más detalladas pueden mostrarse al finalizar el nivel.

4. Principal riesgo del diseño

El mayor riesgo es que la velocidad del juego y la combinación de obstáculos produzcan dificultad injusta en lugar de un reto basado en habilidad.

Si el jugador no tiene suficiente tiempo para identificar una grieta, un escombro o el ataque de un dron, puede sentir que pierde por falta de información y no por haber cometido un error.

Para validarlo se desarrollaría un prototipo jugable de un solo nivel con:

Movimiento automático.
Salto y deslizamiento.
Los tres tipos de obstáculos.
Colapso persiguiendo al jugador.
Indicador básico de peligro y progreso.

Se realizarían pruebas con jugadores modificando la velocidad, distancia entre obstáculos y tiempo disponible para reaccionar. Se registrarían muertes, errores, tiempo de reacción y zonas donde los jugadores fallan repetidamente. También se preguntaría si cada derrota fue percibida como consecuencia de un error propio o de una situación imposible de anticipar.

El prototipo sería viable si los jugadores pueden reconocer por qué fallaron y mejorar después de varios intentos.

5. Trade-off explícito

El principal trade-off es:

Velocidad e intensidad vs. claridad y tiempo de reacción.

Aumentar la velocidad del colapso y la frecuencia de obstáculos produce mayor tensión, pero reduce el tiempo disponible para interpretar el escenario. Por el contrario, proporcionar demasiado tiempo facilita la lectura, pero elimina parte de la presión que define a Zigzag Run.

La decisión sería priorizar claridad antes que velocidad extrema. La dificultad debería aumentar principalmente mediante combinaciones de obstáculos y no únicamente haciendo que el juego sea cada vez más rápido.

6. Justificación de decisiones

La UI minimalista se justifica porque Zigzag Run depende de reacciones rápidas. Agregar demasiados indicadores aumentaría la carga cognitiva y competiría con los obstáculos por la atención del jugador.

El colapso funciona simultáneamente como elemento narrativo y mecánico, por lo que no se necesita explicar constantemente el peligro mediante texto. El escenario proporciona gran parte del feedback.

Finalmente, el prototipo se concentra en validar la relación entre velocidad, obstáculos y capacidad de reacción, porque esta interacción determina si el concepto central resulta divertido y justo. Si este loop no funciona, agregar niveles, gráficos, narrativa o más enemigos no solucionaría el problema principal del diseño.
