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

# PÁGINA 5

---

# PÁGINA 6

---

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
