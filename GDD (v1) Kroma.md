# PÁGINA 1: TÍTULO, HIGH CONCEPT Y LOGLINE

### 1. Metadatos del Proyecto
* **Título Oficial:** *Kroma*
* **Género:** Puzle 2D minimalista / Lógica espacial determinista
* **Plataformas Objetivo:** Web (HTML5 / Canvas), Dispositivos Móviles (Android / iOS)
* **Público Objetivo:** Tweens y Teens tempranos (10 a 15 años); jugadores tipo *Achiever* orientados a la deducción lógica, patrones visuales y resolución sin presión temporal
* **Motor / Stack Tecnológico:** Godot Engine 4 (o Phaser 3 en TypeScript / HTML5 Canvas)

---

### 2. Logline
> *En una matriz digital en reposo, desliza bloques inerciales de energía pura para sintetizar colores secundarios y encajarlos en receptores terminales que transforman el tablero con cada acierto.*

---

### 3. High Concept
**Kroma** es un videojuego de lógica espacial bidimensional en cuadrícula ortogonal minimalista (de 5×5 a 8×8 celdas) donde los bloques activos carecen de fricción interna y se desplazan con inercia continua hasta colisionar. El diseño combina el desplazamiento inercial discreto con la síntesis cromática determinista y la metamorfosis del tablero: cada bloque encajado exitosamente deja de ser una pieza móvil para petrificarse como un nuevo muro rígido, alterando las rutas y ángulos posibles para las piezas restantes.

---

### 4. Pilares de Diseño
* **Determinismo Espacial Absoluto (Cero Azar):** Toda acción produce un resultado matemático predecible en cuatro ejes cardinales, sin físicas continuas imprecisas ni dispersión.
* **Transformación Topológica Progresiva:** Resolver no consiste en vaciar la matriz; cada acierto reduce el espacio transitable y genera nuevos puntos de apoyo mecánicos para maniobras a 90°.
* **Seguridad Psicológica y Experimentación Heurística:** Ausencia total de cronómetros, vidas o penalizaciones. Respaldado en una pila de *Undo* ilimitado, el error se convierte en una hipótesis descartada dentro del proceso deductivo.

---

### 5. Pitch de 1 Minuto
* **¿Qué experiencia ofrece?** Una experiencia de concentración reflexiva (*Mindful Puzzle Solving*), donde el usuario restaura el orden y la coherencia visual de un sistema apagado sin estrés motriz ni castigo de tiempo.
* **¿Cuál es el Core Loop?** Analizar la disposición geométrica, deducir trayectorias en reversa, deslizar bloques con inercia, fusionar colores primarios o usarlos como tope, y encajar cada bloque en su meta para convertirlo en un nuevo obstáculo físico hasta estabilizar el sector.
* **¿Cuál es el riesgo técnico principal?** El manejo de bloqueos irreversibles (*deadlocks silenciosos*) y la verificación algorítmica de la solvencia matemática en el diseño de niveles.
* **¿Por qué es viable en 3 meses?** Porque opera sobre una matriz discreta 2D en una sola pantalla estática (sin scroll, sin físicas complejas continuas, sin cinemáticas ni multijugador), permitiendo disponer de un *greybox* 100% jugable desde la primera semana[cite: 1, 2].

# PÁGINA 2: Historia y Narrativa Funcional

### Enfoque Meat & Salt

Siguiendo la filosofía de Scott Rogers ("si el gameplay es la carne del juego, la historia debe ser la sal"), Kroma adopta una narrativa mínima y funcional: no existen cinemáticas, diálogos ni texto de exposición. La "sal" narrativa se limita a nombrar y dar sentido temático a un sistema que, mecánicamente, ya funciona por sí solo sin necesidad de historia. Esta decisión no es una omisión, sino una postura de diseño deliberada: en un puzle de lógica espacial, cualquier "carne narrativa" adicional (personajes, diálogos, misiones secundarias) competiría por la atención del jugador contra el razonamiento deductivo que es el corazón de la experiencia, arriesgando diluir el estado de concentración relajada que busca el juego.

### Mundo

Kroma ocurre dentro de una **matriz digital suspendida**: un espacio abstracto, oscuro y monocromático que representa un sector de procesamiento en entropía. No hay geografía física reconocible ni personajes visibles — el "mundo" es literalmente el tablero de juego, y su transformación visual es la única forma en que la narrativa se manifiesta.

### Premisa del conflicto

Los buses de datos del sector están apagados por la desalineación de sus núcleos cromáticos: la energía que antes fluía de forma ordenada quedó fragmentada y dispersa en bloques de color aislados. El jugador no es un personaje dentro de este mundo, sino una fuerza externa de reordenamiento (un "operador" implícito, nunca nombrado ni representado) que restaura la alineación de los núcleos.

### Justificación temática que apoya la jugabilidad

Cada elemento narrativo fue elegido porque **describe literalmente una regla mecánica ya existente**, no porque añada contenido nuevo que el jugador deba recordar:

- La "fragmentación de energía cromática" es la razón temática de que los bloques empiecen dispersos y sin relación entre sí — justifica el estado inicial caótico del tablero sin necesidad de una escena introductoria.
- La "purificación y reactivación del módulo" (los pulsos de luz al completar un sector) es la traducción narrativa directa del estado de victoria ya definido mecánicamente (todas las metas ocupadas). No se trata de una recompensa narrativa añadida, sino del mismo evento de victoria vestido con lenguaje temático.
- La transformación de cada bloque en **muro rígido** al encajar correctamente se lee narrativamente como "estabilización de un núcleo", lo cual refuerza —sin añadir una sola mecánica nueva— la sensación de que el tablero se va "curando" progresivamente, en lugar de simplemente llenando espacios.

En síntesis: la narrativa de Kroma no dirige el diseño, lo *describe*. Esto es consistente con el Triángulo de la Extrañeza adaptado en la v1 del documento, donde se decidió mantener dos vértices familiares (objetos y mundo geométricamente simples y reconocibles) y concentrar toda la originalidad en un único vértice: las reglas del sistema (inercia infinita, síntesis cromática, metamorfosis topológica). Vale aclarar que esta es una adaptación del modelo original del Triángulo (Personajes / Mundo / Actividades) al contexto de un juego sin personajes ni actividades narrativas explícitas, sustituyendo el vértice de "Personajes" por "Reglas" como el eje de originalidad radical del proyecto.

---

# PÁGINA 3: Perfil de Jugador y Experiencia Buscada

### Motivaciones del jugador

**Taxonomía de LeBlanc (estética del juego):** Kroma apunta principalmente a tres de los ocho placeres del juego: **Challenge** (superación de problemas lógicos estructurados, sin pistas externas), **Discovery** (la deducción progresiva de las propiedades de combinación e inercia de cada bloque) y **Submission** (el estado de concentración y desconexión que produce resolver un sistema cerrado y determinista).

**Taxonomía de Bartle:** el perfil describe al jugador objetivo como tipo **Achiever**, orientado al completismo de sectores sin ayuda externa. Es importante aclarar aquí una precisión metodológica: la taxonomía de Bartle fue formulada originalmente para mundos virtuales multijugador persistentes (MUDs), donde el arquetipo "Achiever" se define en relación con otros jugadores y con un mundo social compartido. Kroma es un juego de un solo jugador sin componente social ni multijugador, por lo que la etiqueta "Achiever" se usa aquí **no como aplicación literal del modelo de Bartle**, sino como descriptor prestado de estilo motivacional: un jugador que deriva satisfacción de dominar un sistema de reglas y completar objetivos medibles, independientemente de la ausencia de un contexto social. Esta precisión se deja explícita para evitar una cita incorrecta del marco teórico original.

### Curva de atención y estructura de sesión

El patrón de sesión objetivo es de tipo *bite-sized*: partidas de 3 a 7 minutos compuestas por niveles individuales de 45 a 90 segundos de duración. Esta estructura responde directamente al perfil demográfico (tweens y teens tempranos, 10 a 15 años), un rango etario con ventanas de atención sostenida más cortas que las de un público adulto, y con alta probabilidad de consumo en sesiones interrumpibles (recreos, transporte, tiempos de espera).

Dado que el rango etario declarado cubre un espectro cognitivo amplio (un niño de 10 años y un adolescente de 15 años tienen capacidades de memoria de trabajo y control inhibitorio distintas), se propone que la curva de dificultad no sea uniforme, sino organizada en **bandas de calibración**:

- **Banda introductoria (primeros sectores):** niveles que involucran únicamente la mecánica de Deslizar y Encajar, sin fusión cromática ni frenos de conveniencia, apta para el extremo inferior del rango etario.
- **Banda intermedia:** introducción progresiva de Fusión y de la dinámica de Freno de Conveniencia, exigiendo el primer nivel de Deducción en Reversa.
- **Banda avanzada:** niveles que combinan las tres dinámicas simultáneamente (Freno de Conveniencia, Mutación Topológica y Deducción en Reversa), dirigida al extremo superior del rango etario y a jugadores tipo Achiever que buscan reto sostenido.

### Justificación de la estructura respecto a la audiencia

La ausencia de castigo (sin vidas, sin cronómetro, Undo ilimitado) no es solo una decisión de accesibilidad general, sino una decisión específicamente calibrada para el rango etario declarado: al tratarse de jugadores jóvenes con tolerancia a la frustración aún en desarrollo, eliminar el costo del error permite que el *task switching* cognitivo (alternar entre razonamiento de color y cálculo vectorial de trayectorias, en términos de Dobrowolski et al.) ocurra en un entorno de bajo riesgo emocional, sin que el fallo mecánico se traduzca en fallo evaluativo. Esto sostiene la experiencia de **Submission** (concentración relajada) declarada como pilar central, incluso en los tramos de mayor exigencia lógica de la banda avanzada.

---

# PÁGINA 4: FLUJO DE JUEGO Y CORE LOOP (CON MÁQUINA DE ESTADOS)

### 1. Representación del Bucle de Interacción Principal

```
       ┌────────────────────────────────────────────────────────┐
       │             1. EVALUACIÓN Y FEEDFORWARD                │
       │    Lectura visual de la matriz, glifos y Weenies lumínicos│
       └──────────────────────────┬─────────────────────────────┘
                                  │
                                  ▼
       ┌────────────────────────────────────────────────────────┐
       │             2. BACKTRACKING MENTAL                     │
       │    Inferencia inversa: meta receptora ◄── obstáculo    │
       └──────────────────────────┬─────────────────────────────┘
                                  │
                                  ▼
       ┌────────────────────────────────────────────────────────┐
       │             3. ENTRADA VECTORIAL (SWIPE / KEY)         │
       │    Inyección de vector unitario (N, S, E, O)            │
       └──────────────────────────┬─────────────────────────────┘
                                  │
                                  ▼
       ┌────────────────────────────────────────────────────────┐
       │             4. TRANSICIÓN MECÁNICA DISCRETA            │
       │    Desplazamiento inercial celda a celda con Raycast   │
       └──────────────────────────┬─────────────────────────────┘
                                  │
        ┌─────────────────────────┴─────────────────────────┐
        ▼                                                   ▼
┌───────────────────────────────┐   ┌───────────────────────────────┐
│     COLISIÓN / INTERACCIÓN    │   │      RESOLUCIÓN DE ESTADO     │
│ • Bloque Compatible ──► MERGE │   │ • Encaje en Meta  ──► SLOT    │
│ • Muro / Inerte     ──► FRENO │   │   (Conversión a Muro Rígido)  │
│ • Abismo            ──► VOID  │   │                               │
└───────────────┬───────────────┘   └───────────────┬───────────────┘
                │                                   │
                └─────────────────┬─────────────────┘
                                  │
                                  ▼
       ┌────────────────────────────────────────────────────────┐
       │             5. FEEDBACK MULTIMODAL & VERIFICACIÓN      │
       │    Respuesta háptica/auditiva + Chequeo de Condiciones │
       └──────────────────────────┬─────────────────────────────┘
                                  │
          ┌───────────────────────┴───────────────────────┐
          ▼                                               ▼
┌──────────────────┐                            ┌──────────────────┐
│  NIVEL RESUELTO  │                            │ NIVEL NO RESUELTO│
│  Todas las metas │                            │  Estado activo   │
│   estabilizadas  │                            └─────────┬────────┘
└─────────┬────────┘                                      │
          │                         ┌─────────────────────┴─────────────────────┐
          ▼                         ▼                                           ▼
┌──────────────────┐      ┌──────────────────┐                        ┌──────────────────┐
│ AVANCE DE SECTOR │      │ ITERACIÓN VÁLIDA │                        │ DEADLOCK / ERROR │
│  Transición UI   │      │ Retorno a Paso 1 │                        │  Pulsar [UNDO]   │
└──────────────────┘      └──────────────────┘                        └──────────────────┘
```
### 2. Especificación Formal de la Máquina de Estados Finita (FSM)

* **Estado IDLE (Reposo):**
  * *Condición de Entrada:* Detección de Swipe cardinal válido en bloque activo.
  * *Estado Siguiente:* SLIDING.
  * *Salida Concreta:* Bloqueo de nuevos inputs; cálculo de vector director; apilado del snapshot del tablero en la Pila de Undo.

* **Estado SLIDING (Desplazamiento - Camino Libre):**
  * *Condición de Entrada:* Celda destino inmediata libre de obstáculos.
  * *Estado Siguiente:* SLIDING.
  * *Salida Concreta:* Actualización de posición matricial $(x, y) \to (x \pm 1, y \pm 1)$; emisión de estela visual.

* **Estado SLIDING (Desplazamiento - Impacto Compatible):**
  * *Condición de Entrada:* Celda destino contiene bloque primario compatible.
  * *Estado Siguiente:* MERGING.
  * *Salida Concreta:* Colapso de dos identidades en una; suma aditiva cromática; asignación del nuevo glifo identificador.

* **Estado SLIDING (Desplazamiento - Freno Físico):**
  * *Condición de Entrada:* Celda destino contiene muro estático, bloque inerte o borde perimetral.
  * *Estado Siguiente:* IDLE.
  * *Salida Concreta:* Freno cinemático en celda previa; disipación del vector; emisión de vibración y audio de impacto (*thud*).

* **Estado SLIDING (Desplazamiento - Pérdida):**
  * *Condición de Entrada:* Celda destino es Celda Nula (Abismo).
  * *Estado Siguiente:* VOIDED.
  * *Salida Concreta:* La entidad se destruye visualmente; se notifica al usuario la necesidad de retroceder jugada con Undo.

* **Estado MERGING (Síntesis con Inercia):**
  * *Condición de Entrada:* Bloque resultante conserva inercia y celda frontal libre.
  * *Estado Siguiente:* SLIDING.
  * *Salida Concreta:* Continúa el desplazamiento celda a celda con la nueva entidad sintetizada.

* **Estado MERGING (Síntesis con Freno):**
  * *Condición de Entrada:* Sin inercia remanente o presencia de tope frontal.
  * *Estado Siguiente:* IDLE.
  * *Salida Concreta:* La pieza resultante se asienta en la celda del impacto.

* **Estado IDLE (Encaje en Objetivo):**
  * *Condición de Entrada:* Posición de la pieza coincide con Receptor Meta del color/glifo exacto.
  * *Estado Siguiente:* SLOTTED.
  * *Salida Concreta:* Cambio estructural: la pieza pierde movilidad y se registra lógicamente como obstáculo rígido (*IsSolid = True*).

* **Estado SLOTTED (Resolución de Nivel):**
  * *Condición de Entrada:* Contador de metas pendientes en el tablero == 0.
  * *Estado Siguiente:* LEVEL_CLEAR.
  * *Salida Concreta:* Activación lumínica del sector; bloqueo de input de juego; apertura de botón de avance.

* **Cualquier Estado activo (Rebobinado):**
  * *Condición de Entrada:* Presión de botón [Undo] o tecla asignada.
  * *Estado Siguiente:* REWINDING.
  * *Salida Concreta:* Desapilado del snapshot del Stack; restauración síncrona de posiciones y estados; retorno a IDLE.

---

# PÁGINA 5: MECÁNICAS Y REGLAS DEL SISTEMA
 
## 1. Verbos Operativos (Acciones del Jugador)
 
- **Deslizar (Slide):**
  - **Input:** Swipe direccional / flechas del teclado.
  - **Descripción funcional:** Aplica un vector unitario cardinal (N, S, E, O) sobre el bloque seleccionado. El bloque avanza celda por celda de forma continua hasta colisionar con algo o salir del tablero. No existe movimiento parcial: una vez lanzado, el bloque no se detiene por decisión del jugador.
- **Fusionar (Merge):**
  - **Input:** Resultado automático de colisión.
  - **Descripción funcional:** Ocurre cuando un bloque en movimiento impacta contra un bloque primario compatible en reposo. Ambos colapsan en una sola entidad de color resultante, que puede o no conservar inercia remanente.
- **Encajar (Slot):**
  - **Input:** Resultado automático de posición.
  - **Descripción funcional:** Ocurre cuando un bloque (simple o fusionado) se detiene exactamente sobre un receptor meta cuyo glifo/color coincide. La pieza pierde movilidad de forma permanente.
Estos tres verbos son suficientes para generar toda la profundidad del sistema: no se introducen verbos adicionales (saltar, rotar, duplicar) para mantener el determinismo y evitar ambigüedad en el estado del tablero, en línea con el pilar de diseño "Determinismo Espacial Absoluto".
 
## 2. Desplazamiento Discreto (Modelo de "Física")
 
Kroma no usa un motor de físicas continuo. El tablero es una matriz de datos `grid[x][y]`, y el desplazamiento se calcula por *raycast discreto* sobre esa matriz:
 
- **Paso 1 — Evaluación de celda adyacente:**
  - **Condición de Entrada:** Input direccional recibido.
  - **Salida Concreta:** Se evalúa la celda inmediatamente adyacente en la dirección del vector.
- **Paso 2 — Avance iterativo:**
  - **Condición de Entrada:** Celda adyacente libre.
  - **Salida Concreta:** El bloque se mueve una posición y se vuelve a evaluar la siguiente celda en la misma dirección, repitiendo el proceso hasta encontrar un obstáculo.
- **Paso 3 — Interpolación visual:**
  - **Condición de Entrada:** Movimiento lógico ya resuelto en la matriz.
  - **Salida Concreta:** El desplazamiento visual (tween) es una interpolación puramente estética entre posiciones enteras; la lógica de juego nunca opera con coordenadas fraccionarias.
Esto garantiza que dos jugadores que ejecuten la misma secuencia de movimientos lleguen siempre al mismo estado exacto del tablero, sin variaciones por redondeo o simulación física (requisito directo del pilar "Cero Azar").
 
## 3. Matriz de Colisión (Reglas Atómicas)
 
Cada vez que un bloque en movimiento (`SLIDING`) llega a una celda ocupada o especial, el sistema resuelve la interacción según esta tabla cerrada de casos, sin excepciones implícitas:
 
- **Celda vacía:**
  - **Condición de Entrada:** Celda destino sin contenido.
  - **Resultado:** El bloque avanza y se reevalúa la siguiente celda.
  - **Estado Siguiente:** SLIDING.
- **Bloque primario compatible:**
  - **Condición de Entrada:** Celda destino ocupada por bloque primario compatible.
  - **Resultado:** Fusión cromática (suma aditiva de color).
  - **Estado Siguiente:** MERGING.
- **Bloque incompatible / bloque inerte:**
  - **Condición de Entrada:** Celda destino ocupada por bloque sin síntesis posible.
  - **Resultado:** Frenado inmediato en la celda previa.
  - **Estado Siguiente:** IDLE.
- **Muro rígido (incluye piezas ya SLOTTED):**
  - **Condición de Entrada:** Celda destino marcada como sólida.
  - **Resultado:** Frenado inmediato en la celda previa.
  - **Estado Siguiente:** IDLE.
- **Borde del tablero:**
  - **Condición de Entrada:** Celda destino fuera de los límites de la matriz.
  - **Resultado:** Frenado inmediato en la última celda válida.
  - **Estado Siguiente:** IDLE.
- **Celda nula (Abismo):**
  - **Condición de Entrada:** Celda destino marcada como vacío estructural.
  - **Resultado:** El bloque cae y se elimina del tablero.
  - **Estado Siguiente:** VOIDED.
- **Receptor meta con glifo/color coincidente:**
  - **Condición de Entrada:** Celda destino es meta y coincide identidad cromática.
  - **Resultado:** La pieza se fija como obstáculo permanente.
  - **Estado Siguiente:** SLOTTED.
- **Receptor meta con glifo/color distinto:**
  - **Condición de Entrada:** Celda destino es meta pero no coincide identidad cromática.
  - **Resultado:** Se trata como muro rígido: frena, no encaja.
  - **Estado Siguiente:** IDLE.
**Regla de fusión cromática (colores primarios → secundarios):**
 
- Rojo + Azul → Púrpura.
- Azul + Amarillo → Verde.
- Amarillo + Rojo → Naranja.
- Un bloque ya fusionado (secundario) no puede volver a fusionarse con otro bloque; solo puede encajar o actuar como freno. Esto evita árboles de combinación infinitos y mantiene el espacio de soluciones acotado para el solver.
**Regla de inercia post-fusión:**
 
- Si tras la fusión el nuevo bloque conserva recorrido libre en la misma dirección del vector original, continúa deslizándose (`MERGING → SLIDING`).
- Si no conserva recorrido libre, se asienta en la celda de impacto (`MERGING → IDLE`).
- Esta regla habilita la dinámica emergente de "freno de conveniencia": un jugador puede fusionar dos bloques a mitad de camino específicamente para que el resultado se detenga en un punto útil.
## 4. Principio de Diseño Detrás de las Reglas
 
Todas las reglas atómicas anteriores están escritas como funciones puras sobre el estado de la matriz (mismo input → mismo output), lo cual es lo que hace posible, en la Página 6, tanto el sistema de Undo (snapshot/restauración exacta) como la validación automática de niveles mediante el solver BFS mencionado en la matriz de riesgos.


# PÁGINA 6: CONDICIONES DE VICTORIA, DERROTA Y MANEJO DE ESTADOS
 
## 1. Condición de Victoria
 
- **Nivel Resuelto:**
  - **Condición de Entrada:** Todas las metas receptoras del tablero están ocupadas por un bloque del glifo/color correcto (estado `SLOTTED` en el 100% de los receptores).
  - **Salida Concreta:** Bloqueo de input adicional sobre el tablero; disparo del feedback de "sector estabilizado" (ver Página 9); habilitación del botón de avance al siguiente nivel.
No hay condición de victoria parcial ni puntuación por eficiencia de movimientos dentro del MVP: el nivel está resuelto o no lo está, en coherencia con el pilar de "Seguridad Psicológica" (sin presión de optimizar, solo de completar).
 
## 2. Kroma no tiene "Derrota" en el sentido tradicional
 
Es una decisión de diseño explícita, no una omisión: no existen vidas, cronómetro ni penalización por movimiento incorrecto (pilar "Seguridad Psicológica y Experimentación Heurística"). No hay forma de "perder" el nivel de manera permanente mientras el sistema de Undo esté disponible. El único estado adverso posible es quedar en una posición **subóptima o irresoluble dentro de la partida actual**, lo cual se gestiona como error recuperable, no como derrota.
 
## 3. Manejo de Estados Adversos
 
- **Caso 1 — Pérdida de pieza (Abismo):**
  - **Condición de Entrada:** Un bloque cae en una celda nula.
  - **Estado Siguiente:** VOIDED.
  - **Salida Concreta:** La pieza se elimina visualmente del tablero; el sistema no reinicia el nivel automáticamente, solo notifica al jugador que esa pieza ya no está disponible y que probablemente necesita retroceder con Undo si era necesaria para completar una meta.
- **Caso 2 — Deadlock (bloqueo irresoluble en tiempo real):**
  - **Condición de Entrada:** El jugador mueve una pieza a una posición desde la cual ya no existe secuencia de movimientos que permita resolver el nivel (ej. pieza clave atrapada entre dos muros sin ángulo de salida).
  - **Particularidad:** A diferencia de la caída en abismo, este estado no se detecta de forma trivial en tiempo real dentro del MVP, porque requeriría correr el solver BFS en cada movimiento del jugador (costoso y no planeado como validación runtime).
  - **Mitigación Preventiva (nivel de diseño):** todo nivel se valida en la etapa de creación con el solver BFS mencionado en la matriz de riesgos, garantizando que existe al menos una secuencia de movimientos que lleva a la victoria.
  - **Mitigación Reactiva (nivel de jugador):** si el jugador se queda sin movimientos útiles, la responsabilidad de salir del estado recae en el Undo y el Reinicio Rápido, no en una detección automática de "estás atascado".
## 4. Mecánicas de Soporte para Manejo de Estados
 
- **Undo Ilimitado (State Stack):**
  - **Condición de Entrada:** Cualquier transición `IDLE → SLIDING` apila un snapshot completo del estado del tablero (posición y tipo de cada entidad) antes de ejecutar el movimiento.
  - **Salida Concreta:** Presionar Undo desapila el último snapshot y restaura el tablero de forma síncrona e inmediata, sin animación de "rebobinado" complejo, para no penalizar el tiempo del jugador. No hay límite de usos.
- **Reinicio Rápido (Quick Restart):**
  - **Condición de Entrada:** Input de reinicio (botón o tecla asignada).
  - **Salida Concreta:** Restaura el tablero al snapshot inicial del nivel (posición cero de la pila de Undo) en un solo input; sirve como salida de emergencia cuando el jugador prefiere empezar de nuevo en vez de deshacer movimiento por movimiento.
## 5. Justificación de Coherencia
 
El diseño de "sin derrota, solo estados reversibles" no es una simplificación arbitraria: está directamente alineado con el perfil de jugador definido en la Página 3 (Achiever de 10-15 años, sesiones cortas de 3-7 min, orientado a deducción sin presión externa). Castigar el error con pérdida de progreso contradecería la experiencia buscada de "concentración relajada" (*mindful puzzle solving*) y convertiría cada intento fallido en fricción en lugar de en información útil para la siguiente hipótesis del jugador, que es justamente el rol que cumple el error dentro del loop de "Deducción en Reversa" descrito en la Página 4.
 



# PÁGINA 7: ALCANCE DEL MVP Y NIVELES DE CALIBRACIÓN

## 1. Objetivo del MVP

El MVP de **Kroma** tiene como propósito validar que la combinación de **desplazamiento inercial discreto, síntesis cromática y transformación topológica del tablero** produce situaciones de deducción espacial comprensibles, predecibles y progresivamente desafiantes.

El prototipo no busca demostrar la cantidad de contenido que podría tener el producto final, sino comprobar que el **sistema base es suficientemente sólido para generar distintos niveles de complejidad sin incorporar nuevas mecánicas**.

Para ello se desarrollarán inicialmente **tres niveles greybox**, todos construidos sobre la misma implementación de `grid[x][y]`, la misma Máquina de Estados Finita (FSM) y las mismas reglas atómicas de movimiento y colisión definidas en las páginas anteriores.

Entre niveles no cambia el sistema; cambia únicamente la **configuración inicial del tablero y las relaciones espaciales entre bloques, obstáculos y receptores**.

---

## 2. Alcance Funcional del MVP

El MVP deberá contener como mínimo los siguientes sistemas funcionales:

* Tablero ortogonal de entre **5×5 y 8×8 celdas**.
* Selección de bloques activos.
* Entrada mediante **swipe cardinal** en móvil y **teclas direccionales** en teclado.
* Desplazamiento inercial discreto.
* Colisión contra muros, bordes y otros bloques.
* Fusión de colores primarios compatibles.
* Generación de colores secundarios.
* Encaje de bloques en receptores compatibles.
* Conversión de bloques `SLOTTED` en obstáculos rígidos.
* Celdas nulas o abismos.
* Undo ilimitado mediante pila de estados.
* Reinicio rápido del nivel.
* Detección de condición de victoria.
* Transición al siguiente nivel.
* Feedback visual y sonoro mínimo para movimiento, colisión, fusión, encaje y resolución.

La arquitectura debe permitir representar un nivel principalmente como **datos de configuración de la matriz**, evitando código específico para cada escenario.

---

## 3. Nivel Greybox 01 — Deslizar y Encajar

### Propósito de calibración

Validar que el jugador comprende por sí mismo la regla fundamental de inercia:

> **Una pieza no se mueve una celda: continúa avanzando hasta encontrar un elemento que detenga su trayectoria.**

Este nivel corresponde a la **Banda Introductoria** definida en la Página 3.

### Configuración

* **Tamaño recomendado:** 5×5.
* **Bloques activos:** 1.
* **Receptores:** 1.
* **Colores involucrados:** 1 color primario.
* **Fusión:** No necesaria para resolver el nivel.
* **Abismos:** Ninguno.
* **Obstáculos:** Muros simples.
* **Undo:** Disponible.
* **Reinicio:** Disponible.

### Secuencia cognitiva esperada

El jugador identifica el bloque, observa su receptor y descubre que no puede posicionarlo libremente sobre cualquier celda. Debe utilizar los límites y obstáculos del tablero como superficies de frenado.

La solución debe requerir al menos un cambio de dirección a 90°, evitando que un único swipe resuelva todo el nivel.

### Mecánicas validadas

`Seleccionar → Deslizar → Colisionar → Frenar → Redirigir → Encajar`

### Criterio de éxito del diseño

El nivel cumple su función si el jugador puede descubrir la relación entre **dirección, inercia y obstáculo** mediante experimentación, sin necesidad de una explicación textual extensa.

El error debe ser reversible mediante Undo y nunca debe obligar a repetir una secuencia larga.

---

## 4. Nivel Greybox 02 — Síntesis Cromática

### Propósito de calibración

Introducir la segunda capa del sistema: un receptor secundario no siempre dispone inicialmente de una pieza compatible, por lo que el jugador debe **crear la pieza necesaria mediante fusión**.

Este nivel corresponde a la **Banda Intermedia**.

### Configuración

* **Tamaño recomendado:** 6×6.
* **Bloques activos:** 2 bloques primarios.
* **Receptores:** 1 receptor secundario.
* **Colores involucrados:** 2 primarios + 1 secundario resultante.
* **Fusión:** Obligatoria.
* **Abismos:** Opcionalmente 1, colocado de forma que comunique riesgo sin dominar el nivel.
* **Obstáculos:** Muros y bordes.
* **Undo:** Disponible.
* **Reinicio:** Disponible.

Ejemplo de relación cromática:

`Rojo + Azul → Púrpura → Receptor Púrpura`

### Secuencia cognitiva esperada

El jugador primero identifica que ninguna pieza existente coincide con el receptor. Posteriormente debe inferir que dos bloques primarios pueden colisionar para sintetizar el color requerido.

La dificultad espacial consiste en conseguir que ambos bloques se encuentren en una trayectoria válida y, después de la fusión, posicionar el bloque resultante en el receptor.

### Mecánicas validadas

`Analizar → Posicionar → Deslizar → Fusionar → Continuar/Frenar → Redirigir → Encajar`

### Nueva dinámica introducida

Aparece el **Freno de Conveniencia**.

Una pieza puede utilizarse no únicamente como componente cromático, sino también como elemento espacial para provocar una colisión en una posición determinada.

Por lo tanto, el jugador comienza a razonar simultáneamente sobre:

**identidad cromática + posición + trayectoria.**

### Criterio de éxito del diseño

El nivel es válido si el jugador comprende que la fusión no constituye una acción independiente: es una **consecuencia determinista de organizar correctamente una colisión**.

---

## 5. Nivel Greybox 03 — Mutación Topológica y Deducción en Reversa

### Propósito de calibración

Validar la principal fuente de profundidad de Kroma: cada objetivo completado modifica permanentemente la geometría disponible para resolver los objetivos restantes.

Este nivel representa la entrada a la **Banda Avanzada**.

### Configuración

* **Tamaño recomendado:** 7×7 u 8×8.
* **Bloques activos:** 3–4.
* **Receptores:** 2.
* **Colores involucrados:** primarios y al menos un secundario.
* **Fusión:** Obligatoria para al menos una meta.
* **Abismos:** 1–2.
* **Obstáculos:** Muros, bordes y piezas estabilizadas.
* **Undo:** Disponible.
* **Reinicio:** Disponible.

### Estructura del problema

El primer receptor no representa únicamente un objetivo parcial. Cuando una pieza entra en estado `SLOTTED`, se convierte en:

`Meta completada → IsSolid = True → Nuevo obstáculo`

La nueva pieza rígida modifica las trayectorias disponibles.

Por ello, el orden de resolución se vuelve relevante.

Una meta aparentemente conveniente de completar primero puede eliminar una trayectoria necesaria; de forma inversa, una pieza estabilizada puede convertirse deliberadamente en el **tope requerido para resolver otra trayectoria**.

### Secuencia cognitiva esperada

`Observar metas → Razonar desde la meta hacia atrás → Determinar orden → Preparar trayectoria → Fusionar → Encajar → Transformar tablero → Reevaluar → Resolver segunda meta`

### Dinámicas validadas

Este nivel combina simultáneamente:

* **Freno de Conveniencia.**
* **Mutación Topológica.**
* **Deducción en Reversa.**

El jugador ya no pregunta únicamente:

> “¿Hacia dónde puedo mover esta pieza?”

La pregunta que el diseño pretende provocar es:

> “¿Dónde tendría que existir un obstáculo para que esta pieza termine exactamente aquí?”

Esta inversión del razonamiento constituye una de las competencias centrales buscadas por Kroma.

---

## 6. Progresión de Complejidad

Los tres niveles representan una progresión acumulativa:

**Nivel 01**

`Inercia → Frenado → Encaje`

**Nivel 02**

`Inercia → Colisión → Fusión → Encaje`

**Nivel 03**

`Inercia → Fusión → Encaje → Nuevo obstáculo → Reconfiguración → Segundo encaje`

La dificultad aumenta mediante la **composición de reglas conocidas**, no mediante la incorporación constante de nuevos verbos.

Esto permite comprobar si el sistema posee profundidad emergente suficiente para sostener futuros niveles.

---

## 7. Criterios de Validación del Greybox

El greybox se considerará funcionalmente satisfactorio si permite comprobar los siguientes puntos:

1. El jugador entiende que el movimiento es inercial y cardinal.
2. Puede predecir dónde terminará una pieza antes de ejecutarla.
3. Comprende la relación entre colores primarios y secundarios.
4. Utiliza obstáculos como herramientas de posicionamiento.
5. Reconoce que una pieza `SLOTTED` modifica el tablero.
6. Utiliza Undo como herramienta de experimentación y no únicamente como recuperación de un error.
7. Los tres niveles pueden completarse sin depender de azar, precisión motriz o tiempos de reacción.
8. El solver puede confirmar que cada configuración inicial posee al menos una solución.

No se busca medir todavía retención a largo plazo, monetización ni volumen de contenido. El objetivo es determinar si el **núcleo lógico de Kroma funciona como experiencia jugable**.

---

## 8. Justificación del Alcance

Tres niveles son suficientes para la primera validación porque representan las tres capas fundamentales de complejidad del sistema:

**Movimiento → Combinación → Transformación.**

Si estas tres capas producen decisiones espaciales diferenciadas utilizando la misma implementación base, existe evidencia funcional para continuar ampliando el diseño de niveles.

Si, por el contrario, el tercer nivel no genera una complejidad significativamente distinta del primero, el problema deberá resolverse modificando las reglas centrales antes de invertir recursos en contenido, arte o sistemas secundarios.

---

# PÁGINA 8: OUT OF SCOPE — SISTEMAS QUE NO ESTARÁN EN EL MVP

## 1. Propósito de la Delimitación

El MVP de **Kroma** busca validar una hipótesis específica:

> **¿La combinación de inercia discreta, síntesis cromática y transformación topológica produce un puzle determinista comprensible y suficientemente profundo?**

Todo sistema que no sea indispensable para responder esta pregunta queda fuera del alcance inicial.

La exclusión de características no significa que estén descartadas del producto final. Significa que su implementación se posterga hasta demostrar que el **Core Loop** funciona correctamente.

Esta delimitación protege el calendario de producción de tres meses y evita *scope creep* técnico y de diseño.

---

## 2. Mecánicas Fuera del MVP

No se implementarán nuevos verbos principales más allá de:

`Deslizar → Fusionar → Encajar`

Por lo tanto, quedan fuera del MVP:

* Saltos.
* Rotación manual de piezas.
* Teletransportadores.
* Portales.
* Interruptores.
* Bloques móviles controlados simultáneamente.
* Duplicación de bloques.
* Destrucción manual de obstáculos.
* Cambio manual de color.
* Gravedad dinámica.
* Movimiento diagonal.
* Vectores de velocidad variables.
* Bloques con aceleración o fricción.
* Combinaciones cromáticas terciarias.
* Fusiones sucesivas de bloques secundarios.

### Justificación

Cada verbo adicional aumenta el espacio de estados posibles del tablero y, en consecuencia, incrementa tanto la carga cognitiva del jugador como la complejidad del solver.

El MVP debe comprobar primero cuánto espacio de diseño puede obtenerse mediante la combinación de las tres reglas centrales existentes.

---

## 3. Sistemas de Competencia y Puntuación Fuera del MVP

No estarán presentes:

* Puntuación numérica.
* Sistema de estrellas.
* Clasificación por número de movimientos.
* Cronómetro competitivo.
* Récords personales.
* Leaderboards.
* Rachas.
* Combos.
* Rankings entre jugadores.
* Logros externos.

La condición de éxito continuará siendo binaria:

`Nivel no resuelto → Nivel resuelto`

### Justificación

Estos sistemas introducirían presión de optimización sobre una experiencia diseñada alrededor de **experimentación heurística y seguridad psicológica**.

Durante el MVP interesa comprobar si el jugador disfruta resolviendo el sistema, no si puede resolverlo de manera competitivamente eficiente.

---

## 4. Sistemas de Penalización Fuera del MVP

No existirán:

* Vidas.
* Energía limitada.
* Penalización por Undo.
* Límite de movimientos.
* Game Over tradicional.
* Pérdida permanente de progreso.
* Reinicio automático por error.
* Cronómetro de derrota.

Los estados adversos seguirán siendo recuperables mediante:

`Undo ilimitado + Reinicio rápido`

### Justificación

El error forma parte del proceso deductivo.

Una trayectoria incorrecta debe proporcionar información al jugador acerca del funcionamiento del tablero, no convertirse en un castigo externo.

---

## 5. Sistemas de Ayuda Avanzada Fuera del MVP

No se implementarán inicialmente:

* Sistema automático de pistas.
* Resolución parcial sugerida.
* Visualización completa de la solución.
* Predicción automática de deadlocks.
* Ejecución del solver BFS después de cada movimiento.
* Asistente adaptativo según desempeño.
* Tutoriales textuales extensos.

El solver se utilizará principalmente como **herramienta de validación durante el diseño de niveles**, no como asistente activo del jugador.

### Justificación

La detección runtime de estados irresolubles podría requerir búsquedas frecuentes sobre el espacio de estados y añadir complejidad innecesaria al primer prototipo.

Además, ofrecer pistas automáticas demasiado pronto dificultaría evaluar si el **feedforward visual del propio tablero** es suficiente para comunicar las reglas.

---

## 6. Generación Procedural Fuera del MVP

Los niveles serán diseñados manualmente.

No se implementarán:

* Generación procedural de tableros.
* Generación automática basada en dificultad.
* Solver utilizado como generador de contenido.
* Niveles infinitos.
* Daily Challenges.
* Semillas compartidas.

### Justificación

Generar un tablero matemáticamente resoluble no garantiza que produzca un puzle interesante.

Durante el MVP resulta más importante controlar deliberadamente las situaciones de aprendizaje y calibración que maximizar el volumen de contenido.

---

## 7. Multijugador y Sistemas Sociales Fuera del MVP

Kroma será exclusivamente **single-player** durante esta etapa.

Quedan excluidos:

* Multijugador local.
* Multijugador online.
* PvP.
* Resolución cooperativa.
* Chat.
* Amigos.
* Perfiles públicos.
* Comparación de puntuaciones.
* Compartir soluciones dentro del juego.

### Justificación

Ninguno de estos sistemas es necesario para validar el Core Loop y todos introducirían infraestructura adicional de red, persistencia, sincronización y diseño social.

---

## 8. Persistencia y Metaprogresión Avanzada Fuera del MVP

No se desarrollarán:

* Árboles de progreso.
* Experiencia o XP.
* Monedas.
* Economía interna.
* Tienda.
* Inventario.
* Desbloqueables complejos.
* Misiones diarias.
* Pase de temporada.
* Sistemas de recompensas acumulativas.

La progresión del MVP será únicamente:

`Nivel 1 → Nivel 2 → Nivel 3`

### Justificación

La motivación durante la validación debe provenir de **comprender y dominar las reglas**, no de recompensas extrínsecas añadidas alrededor del puzle.

---

## 9. Narrativa y Presentación Fuera del MVP

En coherencia con el enfoque **Meat & Salt**, quedan fuera:

* Cinemáticas.
* Personajes jugables.
* NPC.
* Diálogos.
* Árboles de conversación.
* Lore coleccionable.
* Misiones narrativas.
* Escenarios tridimensionales.
* Animaciones narrativas complejas.
* Secuencias de introducción extensas.

La narrativa permanecerá integrada directamente en el estado visual del tablero:

`Sector apagado → Interacción → Estabilización → Sector activado`

### Justificación

La historia debe contextualizar la mecánica, no competir con ella por la atención del jugador.

---

## 10. Física y Tecnología Fuera del MVP

No se utilizarán:

* Simulación física continua.
* RigidBodies para determinar resultados lógicos.
* Colisiones dependientes de precisión física.
* Movimiento basado en aceleración.
* Física destructible.
* Partículas con influencia sobre gameplay.
* Simulación 3D.

La lógica continuará siendo:

`Estado discreto → Resolución matemática → Interpolación visual`

Las animaciones pueden representar el movimiento, pero nunca determinar su resultado.

---

## 11. Decorado y Pulido Técnico Postergado

Durante el greybox no constituyen prioridad:

* VFX complejos.
* Sistemas avanzados de partículas.
* Shaders elaborados.
* Iluminación dinámica compleja.
* Transiciones cinematográficas.
* Animaciones extensas.
* Skins.
* Personalización estética.
* Música adaptativa multicapa.

El greybox utilizará únicamente el feedback necesario para distinguir claramente:

**movimiento, colisión, fusión, encaje, error y victoria.**

El pulido visual se realizará únicamente después de confirmar que las reglas son comprensibles sin depender del espectáculo audiovisual.

---

## 12. Alcance Técnico Protegido

La arquitectura del MVP queda reducida conceptualmente a los siguientes módulos:

`Grid Manager`

`↓`

`Input Manager → FSM → Collision Resolver`

`↓`

`Color Merge System`

`↓`

`Slot / Topology System`

`↓`

`Win Condition`

`↓`

`Undo / Restart`

El solver BFS funciona paralelamente como herramienta de validación de niveles.

Todo módulo que no sea necesario para ejecutar esta cadena queda postergado.

---

## 13. Trade-off Principal del Alcance

El principal trade-off del MVP es:

> **Variedad de contenido vs. profundidad del sistema base.**

Kroma sacrifica temporalmente cantidad de mecánicas, modos, recompensas y contenido para concentrar los recursos de producción en comprobar si un conjunto pequeño de reglas puede producir suficiente profundidad combinatoria.

Esto implica que el primer prototipo puede percibirse visualmente limitado y ofrecer muy pocos niveles.

A cambio, permite iterar rápidamente sobre el elemento de mayor riesgo del proyecto: **la calidad de los problemas espaciales producidos por sus reglas centrales**.

---

## 14. Regla de Control de Scope

Durante la producción del MVP, cualquier nueva característica deberá superar la siguiente pregunta:

> **¿Es necesaria para comprobar que inercia, síntesis cromática y transformación topológica producen un puzle funcional?**

Si la respuesta es **no**, la característica se registra para una versión posterior y no entra al sprint actual.

Esto aplica incluso si la característica es sencilla de implementar.

El criterio de inclusión no será:

> “¿Podemos programarlo?”

Sino:

> **“¿Necesitamos programarlo para validar el Core Loop?”**

---

## 15. Definición de MVP Terminado

El MVP de Kroma podrá considerarse terminado cuando exista una versión jugable que permita:

1. Cargar los tres niveles greybox definidos en la Página 7.
2. Deslizar bloques mediante inputs cardinales.
3. Resolver colisiones de forma completamente determinista.
4. Fusionar colores primarios compatibles.
5. Encajar bloques en receptores correctos.
6. Convertir piezas estabilizadas en obstáculos.
7. Resolver correctamente la transformación topológica del tablero.
8. Utilizar Undo ilimitado.
9. Reiniciar inmediatamente un nivel.
10. Detectar la condición de victoria.
11. Confirmar mediante solver que los niveles publicados poseen al menos una solución.
12. Completar los tres niveles sin depender de sistemas que hayan sido clasificados como Out of Scope.

En ese punto, el MVP habrá cumplido su función aunque todavía carezca de arte final, contenido extenso o metaprogresión.

El siguiente ciclo de producción deberá decidirse a partir de los resultados de **playtesting del Core Loop**, y no simplemente por haber completado la implementación técnica.

---

# PÁGINA 9: Interfaz de Usuario (UI/HUD) y Canales de Información

### Wireframe de pantalla

El diseño mantiene el viewport único y estático definido en la v1 del documento (sin scroll de cámara), válido tanto para orientación vertical móvil (9:16) como apaisada en PC:

```text
+-------------------------------------------------------------+
|  [|| Pausa]          SECTOR 02 - NODO 07        [↺ Reiniciar]|
|                                                               |
|                       [ Weenie Visual ]                      |
|                                                               |
|         +-----+-----+-----+-----+-----+-----+-----+          |
|         |     |     |     |     |     | [M] |     |          |
|         +-----+-----+-----+-----+-----+-----+-----+          |
|         |     |  #  |     |     |     |     |     |          |
|         +-----+-----+-----+-----+-----+-----+-----+          |
|         |     |     | (B1)| ===>|     |  #  |     |          |
|         +-----+-----+-----+-----+-----+-----+-----+          |
|         |     |     |     |     | (B2)|     |     |          |
|         +-----+-----+-----+-----+-----+-----+-----+          |
|         |     |  X  |     |     |     |     | [G] |          |
|         +-----+-----+-----+-----+-----+-----+-----+          |
|                                                               |
|                  ÁREA ACTIVA DE GESTOS / INPUT               |
|                                                               |
|  [ ↩ DESHACER (Undo) ]                      [ LUZ / ESTADO ]  |
+-------------------------------------------------------------+
```

### HUD (elementos permanentes)

El HUD se mantiene minimalista, coherente con el pilar de "claridad y reducción del caos": solo cuatro elementos fijos, sin barras de vida ni temporizadores visibles: identificador de sector/nodo actual, botón de pausa, botón de reinicio rápido, y botón de deshacer (Undo) siempre accesible.

### Feedforward (información previa a la acción)

Antes de ejecutar un deslizamiento, el sistema debe comunicar de forma anticipada la trayectoria probable del bloque seleccionado: al tocar o seleccionar un bloque, se traza una guía visual tenue (línea punteada) en las cuatro direcciones cardinales, indicando hasta dónde llegaría el bloque si se desliza en cada una, sin necesidad de ejecutar el movimiento. Esta guía se actualiza dinámicamente si el estado del tablero cambia (por ejemplo, tras un movimiento previo que añadió un nuevo muro rígido). Este mecanismo es una forma de Control Indirecto (Rogers): reduce la carga de cálculo mental sin resolver el problema por el jugador, ya que solo muestra *dónde llegaría* el bloque, no si esa trayectoria es la correcta para resolver el nivel.

### Feedback multimodal (información posterior a la acción)

| Evento | Canal visual | Canal auditivo | Canal háptico (móvil) |
|---|---|---|---|
| Deslizamiento en curso | Animación fluida de traslado celda por celda | Sonido de "deslizamiento" continuo y sutil | Sin vibración (evento neutro) |
| Colisión con muro / bloque inerte | Destello breve en el punto de impacto | Sonido corto y seco de "freno" | Vibración corta de baja intensidad |
| Fusión cromática exitosa | Transición de color con partícula de mezcla | Tono ascendente de dos notas | Vibración media, doble pulso |
| Encaje correcto en meta | El bloque se ilumina y se transforma visualmente en muro rígido; pulso de luz que recorre el circuito conectado | Acorde de confirmación (tono de "logro") | Vibración firme, pulso único |
| Caída en abismo | El bloque se desvanece con partículas hacia el vacío | Sonido descendente de "pérdida de pieza" | Vibración larga de baja intensidad (señal de alerta, no de castigo) |
| Nivel completado | Iluminación total del circuito, transición de fondo oscuro a fondo cromático activo | Tema musical corto de cierre | Vibración de patrón ascendente |

La distinción deliberada entre la intensidad háptica de "caída en abismo" (alerta suave) y "colisión con muro" (evento neutro y frecuente) busca que el jugador perciba la diferencia entre un error recuperable sin fricción (Undo inmediato disponible) y una simple interacción normal del sistema, sin introducir una sensación de castigo que contradiga el pilar de "seguridad psicológica en la experimentación" definido en la Página 2 del documento.

### Canal de estado general ("Luz / Estado")

El indicador de "Luz / Estado" en la esquina inferior derecha del wireframe funciona como resumen de progreso del sector: su brillo aumenta proporcionalmente a la cantidad de metas ya encajadas, ofreciendo al jugador una referencia constante de avance sin necesidad de un contador numérico explícito, reforzando la lectura narrativa de "reactivación progresiva del módulo" definida en la Página 2.

---

# PÁGINA 10: MATRIZ DE RIESGOS, TRADE-OFFS Y VIABILIDAD TÉCNICA

### 1. Desglose de Riesgos Críticos del Proyecto

* **Riesgo 1: Deadlocks Silenciosos (Estados Irresolubles sin Notificación)**
  * *Tipo y Severidad:* Jugabilidad / Game Feel. Severidad Alta, Probabilidad Alta.
  * *Impacto:* El jugador desliza una pieza clave a una esquina muerta sin posibilidad de moverla ni impactarla. Si el juego no emite respuesta, el usuario pasa minutos buscando una solución inexistente (*Loss of Agency*).
  * *Mitigación y Validación:* Implementación de un Solver BFS (*Breadth-First Search*) en el pipeline de desarrollo. Todo nivel se valida verificando que no existan callejones sin salida accidentales o irresolubles. Respaldo directo en Undo inmediato.

* **Riesgo 2: Barrera de Accesibilidad por Discromatopsia**
  * *Tipo y Severidad:* Experiencia / Inclusión. Severidad Crítica, Probabilidad Media (~8% público masculino).
  * *Impacto:* Imposibilidad para jugadores daltónicos de diferenciar pares clave (Rojo/Verde o Azul/Púrpura), volviendo la mecánica de síntesis frustrante o injugable.
  * *Mitigación y Validación:* Codificación dual innegociable. Adición de glifos geométricos inscritos en alto contraste dentro de los bloques y metas (Círculo, Cuadrado, Triángulo, etc.). La lógica se sustenta simultáneamente en color y forma.

* **Riesgo 3: Complejidad Exponencial y Cuello de Botella en Level Design**
  * *Tipo y Severidad:* Producción / Alcance. Severidad Media, Probabilidad Alta.
  * *Impacto:* Diseñar a mano tableros que mantengan solución única, curva didáctica limpia y ausencia de soluciones triviales desborda el cronograma de 8 a 12 semanas.
  * *Mitigación y Validación:* Editor interno de niveles que ejecuta el solver en tiempo real dentro del motor. Muestra el número óptimo de movimientos (*par*) y advierte de inmediato si el puzle tiene atajos o es irresoluble.

---

### 2. Análisis de Trade-offs Explícitos

* **Decisión 1: Identidad Visual vs. Accesibilidad**
  * *Opción Descartada:* Pureza Hiper-Minimalista. Bloques de color plano puro sin ningún símbolo (estilo *KAMI* o abstracción pura).
  * *Opción Implementada:* Codificación Dual. Bloques y metas con glifos geométricos de alto contraste inscritos en su interior.
  * *Trade-off y Justificación:* Se sacrifica la pureza estética del color plano en favor de la inclusión universal, evitando la exclusión de usuarios con discromatopsias bajo estándares WCAG 2.1.

* **Decisión 2: Modelo Físico vs. Determinismo**
  * *Opción Descartada:* Física Continua (RigidBody2D). Desplazamiento por impulsos físicos y colisiones dinámicas de motor.
  * *Opción Implementada:* Matriz Discreta con Tweens. Lógica de posiciones enteras `[x][y]` con interpolaciones puramente visuales.
  * *Trade-off y Justificación:* Se renuncia al comportamiento orgánico de masas y rebotes para garantizar determinismo matemático absoluto, facilidad en la pila de Undo y cero bugs sub-píxel.

---

### 3. Justificación de Viabilidad para Producción en 3 Meses

* **Cero Dependencia de Activos Complejos:** No requiere modelado 3D, animaciones cuadro a cuadro complejas ni doblaje de voz; el apartado gráfico se resuelve mediante geometría vectorial, luces 2D y shaders mínimos.
* **Arquitectura Técnica Desacoplada:** La lógica del tablero corre sobre una matriz de datos bidimensional abstracta, permitiendo que la programación de reglas, el solver de verificación y la UI se desarrollen en paralelo sin dependencias bloqueantes.
* **Control Estricto de Alcance (*Zero Scope Creep*):** Se excluyen formalmente del MVP funciones secundarias como generación procedural, tablas de clasificación online, modos multijugador o microtransacciones estéticas.
---
---











# Kroma: Game Design Document (Summary)

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
