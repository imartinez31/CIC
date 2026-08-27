# Propuesta Conceptual de Videojuego: Estantería de Libros

## 1. Idea general

**Estantería de Libros** es un videojuego de puzzle de organización, en la línea de *Water Sort Puzzle*, donde el jugador debe ordenar libros de colores en estanterías de altura variable, respetando restricciones tanto de color como de espacio físico.

---

## 2. Mecánica principal

El jugador mueve libros entre estantes. Cada estante está dividido en espacios de distinta altura (bajo, medio, alto), y cada libro tiene dos atributos: un **color** (grosor del lomo) y una **altura** (tamaño del libro). Un libro solo puede colocarse en un espacio si:

1. El espacio disponible tiene la altura adecuada para ese libro.
2. El libro queda apilado sobre otro del mismo color (o el espacio está vacío).

El jugador gana el nivel cuando todos los libros de cada color están agrupados en estantes completos, sin mezclas de color y respetando la altura de cada espacio.

---

## 3. Objetivo del jugador

Reorganizar completamente el desorden inicial de libros, logrando que cada estante contenga únicamente libros de un mismo color, colocados en los espacios de altura correspondiente, usando el menor número de movimientos posible (o dentro de un límite de movimientos según el nivel).

---

## 4. Reglas básicas

- Solo se puede mover un libro a la vez.
- Un libro no puede colocarse en un espacio de altura menor a la suya.
- Un libro solo puede apilarse sobre otro libro del mismo color, o en un espacio vacío compatible con su altura.
- No hay límite de tiempo; el desafío es puramente de planificación.
- El nivel se completa cuando cada estante queda ocupado por libros de un solo color, correctamente distribuidos según su altura.

---

## 5. Experiencia buscada

El juego busca generar una sensación de **orden y satisfacción visual progresiva**: a medida que el jugador resuelve el puzzle, el caos inicial de colores y tamaños mezclados se transforma en una estantería visualmente armónica. Esta sensación se sostiene en dos capas de tensión mental:

- La tensión de **color** (clásica de Water Sort): saber qué libro va con qué color.
- La tensión de **espacio** (el elemento nuevo): saber si hay un lugar físico disponible para ese libro, aunque el color coincida.

Esta doble restricción genera momentos de "bloqueo aparente" —el jugador identifica la solución de color correcta pero no tiene dónde colocarla— que obligan a replanificar toda la secuencia de movimientos. Ese instante de frustración momentánea, seguido de la resolución, es el corazón de la experiencia: el placer de un rompecabezas que parecía trabado y de pronto encaja.

La estética cálida (madera, lomos de colores, una biblioteca ordenada) refuerza emocionalmente esa sensación de logro, apelando a una satisfacción muy identificable y cotidiana: la de "poner orden" en algo tangible.

---

## 6. Justificación de la coherencia del diseño (marco MDA)

El modelo **MDA (Mecánicas, Dinámicas, Estética)** de Hunicke, LeBlanc y Zubek permite explicar por qué los elementos formales de Estantería de Libros están alineados entre sí:

### Mecánicas
Las reglas base son simples: mover libros, respetar color y altura. Esta simplicidad es intencional: un sistema de reglas mínimo que, combinado, genera complejidad emergente (igual que en Water Sort, cuya profundidad no viene de reglas numerosas sino de sus combinaciones).

### Dinámicas
De esas mecánicas surge un comportamiento de juego específico: el jugador debe pensar varios movimientos por adelantado, porque cada movimiento reduce las opciones futuras. La restricción de altura introduce una dinámica que no existe en el Water Sort original: el jugador ya no solo pregunta "¿este color va aquí?" sino "¿tengo espacio físico para moverlo?". Esto produce la dinámica de "bloqueo aparente y desbloqueo" descrita en la sección anterior, que es el motor central de la experiencia de juego.

### Estética
La combinación de esas dinámicas genera la experiencia estética buscada: satisfacción por el orden, tensión mental sostenida sin presión de tiempo, y una sensación de logro visual muy tangible al completar cada estante.

**Coherencia del diseño:** cada elemento formal está diseñado para reforzar la experiencia final. Si se eliminara la restricción de altura, el juego perdería su capa de tensión espacial y se reduciría a un clon directo de Water Sort sin identidad propia. Si se añadiera un límite de tiempo, se rompería la naturaleza contemplativa y reflexiva de la experiencia buscada, sustituyendo la satisfacción de "pensar con calma" por ansiedad, algo incoherente con la estética cálida y pausada que se busca transmitir. Por eso, la ausencia de temporizador, la doble restricción (color + altura), y la estética visual de biblioteca no son elementos aislados, sino decisiones de diseño que se sostienen mutuamente para producir una experiencia consistente de orden, calma y logro progresivo.
