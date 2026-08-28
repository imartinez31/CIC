# Propuesta Conceptual de Videojuego: *Kroma*

---

## 1. Propuesta
* **Título:** *Kroma*
* **Género:** Puzzle 2D  / Lógica espacial (tentativo).
* **Premisa:** En un tablero matricial limpio (cuadrícula de 5x5 a 8x8), el jugador desliza bloques elementales de color para combinarlos y encajarlos en sus
  casillas objetivo, estimulando de forma indirecta el pensamiento algorítmico, la planificación espacial y la autorregulación.

---

## 2. Elementos Formales del Juego

### A. Mecánica Principal (Verbo concreto)
* **Deslizar bloques (*Slide / Desplazar*):** El jugador arrastra bloques en cuatro direcciones cardinales (arriba, abajo, izquierda, derecha) sobre un tablero
  con casillas delimitadas.

### B. Objetivo del Jugador
* **Objetivo principal:** Llenar todas las casillas destino del tablero con el color y la figura solicitada en cada nivel.
* **Objetivo inmediato:** Calcular la trayectoria de los bloques para combinarlos entre sí (ej. Bloque Azul + Bloque Amarillo = Bloque Verde) y frenarlos usando
  obstáculos fijos en el tablero.

### C. Reglas Básicas
1. **Inercia continua:** Al deslizar un bloque, este no se detiene hasta chocar contra un muro, otro bloque o el borde del tablero.
2. **Fusión por contacto:** Si dos bloques de colores primarios compatibles colisionan, se fusionan automáticamente en un bloque de color secundario.
3. **Casilla meta:** Un bloque encaja en la casilla meta si coincide exactamente en color; una vez colocado, se bloquea y actúa como un nuevo obstáculo físico
   para los demás bloques.
5. **Entorno seguro (Sin fallo punitivo):** No existen cronómetros, vidas ni estados de derrota irreversibles; un botón de "deshacer" (*Undo*) y de "reiniciar nivel"
   permite revertir pasos al instante.

---

## 3. Experiencia Buscada (Estética)

### ¿Qué debe sentir el jugador?
* **Concentración serena y satisfacción analítica:** Sensación de control y orden mental libre de la ansiedad de fallar o de competir contra el tiempo.
* **Sensación de autoeficacia progresiva:** Motivación intrínseca al resolver problemas abstractos mediante el razonamiento lógico autónomo.

### ¿Por qué la mecánica genera esta experiencia?
* La física determinista de la inercia convierte cada nivel en un acertijo predecible. El jugador aprende a proyectar mentalmente los movimientos antes de
  deslizar el dedo/ratón, transformando la impulsividad inicial en un proceso reflexivo y estructurado.

---

## 4. Coherencia del Sistema (Modelo MDA)

```
[ MECÁNICAS ] ───► [ DINÁMICAS ] ───► [ ESTÉTICA / EXPERIENCIA ]
```

### A. Mecánica Principal (Verbo concreto)
* **Deslizar bloques (*Slide / Desplazar*):** El jugador arrastra bloques en cuatro direcciones cardinales (arriba, abajo, izquierda, derecha) sobre un tablero
  con casillas delimitadas.

### Mecánicas Secundarias de Soporte
* **Fusionar (*Merge*):** Provocar el impacto entre dos bloques primarios compatibles para sintetizar un nuevo bloque de color secundario.
* **Frenar / Bloquear (*Block*):** Utilizar muros fijos u otros bloques posicionados estratégicamente en la cuadrícula como topes para detener la inercia de una
  pieza en movimiento.
* **Encajar (*Slot / Match*):** Alinear y deslizar el bloque del color correspondiente dentro de la casilla meta para fijarlo de manera definitiva.
* **Revertir / Deshacer (*Undo*):** Retroceder un paso en la pila de movimientos sin límite de intentos ni penalización de puntaje.

