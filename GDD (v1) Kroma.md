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

# PÁGINA 2

---

# PÁGINA 3

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
 



# PÁGINA 7

---

# PÁGINA 8

---

# PÁGINA 9

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
