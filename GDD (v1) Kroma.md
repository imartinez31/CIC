# Kroma: Game Design Document (GDD v1)

**Documento de Diseño Conceptual y Técnico**  
**Versión:** 1.0 (Entrega Fase 1 - GitHub)  
**Plataformas Objetivo:** Web (HTML5/Canvas), Dispositivos Móviles (Android/iOS)  
**Motor de Desarrollo:** Godot Engine 4 (o Phaser 3)  

---

## Presentación Rápida: Pitch de 1 Minuto

* **¿Qué experiencia ofrece?**  
  *Kroma* es un videojuego de lógica y puzle espacial minimalista donde el jugador experimenta la satisfacción de restaurar el orden y la armonía a través de la síntesis cromática y la física determinista sin presión de tiempo.
* **¿Cuál es el core loop?**  
  El jugador analiza el tablero, traza mentalmente trayectorias de inercia y desliza bloques de color. Al colisionar, los bloques se fusionan o sirven de freno para encajar en casillas meta, las cuales se petrifican en nuevos muros, permitiendo iterar libremente mediante *Undo* instantáneo hasta estabilizar el sector.
* **¿Cuál es el riesgo técnico?**  
  La consistencia matemática del movimiento por inercia y la generación de niveles que eviten callejones sin salida accidentales o soluciones triviales.
* **¿Por qué es viable en 3 meses?**  
  Porque su mecánica opera sobre una matriz discreta 2D (sin simulaciones físicas continuas complejas), utiliza una cámara fija sin scroll, carece de dependencias narrativas o multijugador, y su núcleo es testeable en *greybox* desde la primera semana.

---

## 1. High Concept

**Kroma** es un videojuego de lógica espacial bidimensional en cuadrícula ortogonal minimalista, donde el jugador desliza bloques elementales de energía con desplazamiento inercial continuo para sintetizar colores secundarios y encajarlos en receptores terminales, transformando progresivamente la topología del tablero con cada acierto.

---

## 2. Experiencia Central

La experiencia busca inducir un estado de concentración relajada y flujo reflexivo (*mindful puzzle solving*) mediante los siguientes pilares:

* **Claridad y reducción del caos:** La transición de un circuito caótico, monocromático e inerte hacia un sistema iluminado y cromáticamente armónico.
* **Seguridad psicológica en la experimentación:** Eliminación absoluta del castigo (sin vidas, sin cronómetro, sin penalización por error) gracias al sistema de retroceso inmediato (*Undo*).
* **Epifanía deductiva (Momento "Eureka"):** Comprender que las piezas no son únicamente objetivos a mover, sino herramientas y frenos de conveniencia para manipular a las demás.

---

## 3. Perfil del Jugador

| Dimensión | Detalle del Perfil |
| :--- | :--- |
| **Rango de Edad / Demográfico** | Tweens y Teens tempranos (10 a 15 años). Audiencia habituada a mecánicas lógicas táctiles y consumo en sesiones ágiles. |
| **Taxonomía de Bartle / Schell** | **Achiever** (♦): Orientado a la superación de desafíos lógicos concretos y completismo de sectores sin pistas externas. |
| **Taxonomía de LeBlanc (Estética)** | **Challenge** (Superación de problemas estructurados), **Discovery** (Deducción de propiedades de combinación e inercia) y **Submission** (Desconexión y concentración estructurada). |
| **Demanda Cognitiva (Dobrowolski et al.)** | Estimulación de funciones ejecutivas, memoria de trabajo espacial, control inhibitorio y *Task Switching* (alternar entre el razonamiento de color y el cálculo vectorial de trayectorias). |
| **Patrón de Sesión** | Sesiones *bite-sized* de 3 a 7 minutos, compuestas por resolución de niveles de 45 a 90 segundos. |

---

## 4. Core Loop (Bucle de Juego)

El bucle operativo de interacción y retroalimentación se estructura en cinco fases continuas:

1. **Observar e Interpretar:** El jugador evalúa la distribución del tablero (posiciones iniciales de bloques, muros fijos, abismos y casillas meta receptoras).
2. **Planificar Vector (Backtracking Mental):** Deduce hacia atrás la trayectoria requerida: *"Para encajar en la meta, el bloque necesita frenar en la celda adyacente; por ende, requiere un obstáculo previo"*.
3. **Ejecutar Acción (Deslizar):** Aplica un impulso cardinal (Swipe / Teclado) que lanza el bloque con inercia total.
4. **Evaluar Consecuencia Dinámica:**
   * *Colisión con pared / bloque inerte:* Freno en casilla previa.
   * *Colisión con bloque compatible:* Fusión cromática inmediata.
   * *Caída en abismo o bloqueo insalvable:* Estado no resoluble identificado por el jugador.
   * *Llegada a meta correcta:* Bloqueo de pieza y transformación a muro rígido.
5. **Ajustar o Iterar (Undo / Win):** Si la maniobra fue errónea, el jugador presiona *Undo* para retroceder los pasos necesarios; si se completan todas las metas, el circuito se ilumina y se avanza al siguiente nivel.

---

## 5. Mecánicas Principales

### 5.1 Verbos Operativos (Acciones del Jugador)

* **Deslizar (Slide):** Aplicar un vector unitario en 4 direcciones cardinales (Norte, Sur, Este, Oeste). El bloque se desplaza celda por celda sin detenerse hasta impactar con un colisionable o salir del plano.
* **Fusionar (Merge):** Colisión directa entre dos bloques primarios compatibles. El bloque en movimiento absorbe al bloque estático, transformándose en el color resultante (Rojo + Azul = Magenta/Púrpura; Azul + Amarillo = Verde; Amarillo + Rojo = Naranja) sin alterar su inercia si aún le queda recorrido por vector libre.
* **Encajar (Slot):** Introducir un bloque en su receptor terminal correspondiente. Al validarse, la pieza queda fija para siempre en ese nivel, pierde su capacidad de deslizamiento y se convierte en un **muro rígido reflectante** para los bloques restantes.

### 5.2 Mecánica de Soporte

* **Undo Ilimitado (State Stack):** Pila de memoria que guarda el estado exacto de cada celda y bloque por turno. Permite revertir N movimientos sin límite ni castigo de puntuación.
* **Reinicio Rápido (Quick Restart):** Reinicio instantáneo del tablero con un solo toque o tecla ("R").

### 5.3 Obstáculos y Entorno

* **Muro Rígido (Tope Estático):** Casilla no transitable que disipa la inercia del bloque y lo detiene en la celda anterior, habilitando un nuevo eje de giro a 90°.
* **Abismo (Celda Nula):** Vacío en la cuadrícula. Si un bloque pasa por esta casilla, cae fuera del circuito (requiere *Undo* para recuperarlo).
* **Bloque Inerte / Colisión Fallida:** Impacto contra bloques que no admiten síntesis cromática mutua. Actúan como cuerpo rígido, frenando al bloque agresor en la casilla previa.

---

## 6. Dinámicas Esperadas (Comportamientos Emergentes)

* **Freno de Conveniencia (Sacrificio Posicional):** Mover intencionalmente un bloque no hacia su meta, sino hacia una posición intermedia para que sirva de obstáculo móvil y detenga a otra pieza en un punto clave.
* **Mutación Topológica Dinámica:** Al encajar un bloque en su meta y convertirse en muro, el espacio transitable se encoge y cambia los ángulos posibles del puzle para las piezas restantes.
* **Deducción en Reversa (Retro-análisis):** El jugador deja de mover piezas intuitivamente hacia adelante y comienza a analizar el problema desde la meta hacia el origen.
* **Auto-corrección sin Fricción:** El ciclo constante de ensayo, error y reversión reduce la aversión a la pérdida y promueve el razonamiento deductivo experimental.

---

## 7. Mundo y Conflicto (Marco Narrativo Minimalista)

* **Filosofía Meat & Salt (Scott Rogers):** La narrativa es condimento puro ("sal"); el núcleo cinemático y mecánico es el juego ("carne"). No existen textos de exposición ni cinemáticas.
* **Entorno:** Una matriz digital suspendida, oscura y monocromática, que representa un sector de procesamiento en entropía.
* **Conflicto:** Fragmentación y dispersión de la energía cromática. Los buses de datos están apagados debido a la desalineación de los núcleos.
* **Objetivo Semántico:** Al estabilizar todos los nodos de un sector, las líneas vectoriales del fondo emiten pulsos luminosos de color, señalando la purificación y reactivación del módulo.
* **Triángulo de la Extrañeza:** Dos vértices familiares (Objetos = formas geométricas limpias; Mundo = tablero matricial) y un único vértice extraño (Reglas = inercia infinita combinada con síntesis cromática y metamorfosis topológica).

---

## 8. Interfaz Conceptual (UI / Wireframe)

La pantalla se compone de un diseño centrado en un único viewport estático (sin scroll de cámara), optimizado para aspecto vertical (9:16 móvil) o apaisado centrado (PC):

```text
+-------------------------------------------------------------+
|  [|| Pausa]          SECTOR 02 - NODO 07        [↺ Reiniciar]|
|                                                             |
|                       [ Weenie Visual ]                     |
|                                                             |
|         +-----+-----+-----+-----+-----+-----+-----+         |
|         |     |     |     |     |     | [M] |     |         |
|         +-----+-----+-----+-----+-----+-----+-----+         |
|         |     |  #  |     |     |     |     |     |         |
|         +-----+-----+-----+-----+-----+-----+-----+         |
|         |     |     | (B1)| ===>|     |  #  |     |         |
|         +-----+-----+-----+-----+-----+-----+-----+         |
|         |     |     |     |     | (B2)|     |     |         |
|         +-----+-----+-----+-----+-----+-----+-----+         |
|         |     |  X  |     |     |     |     | [G] |         |
|         +-----+-----+-----+-----+-----+-----+-----+         |
|                                                             |
|                  ÁREA ACTIVA DE GESTOS / INPUT              |
|                                                             |
|  [ ↩ DESHACER (Undo) ]                      [ LUZ / ESTADO ] |
+-------------------------------------------------------------+
Leyenda:
(B1), (B2) = Bloques de color con glifo interior (ej. Azul, Amarillo)
[M], [G]   = Metas receptoras con pulsación de brillo (Weenies)
#          = Muro rígido estático
X          = Celda nula (Abismo)
