
**Zigzag Run**

1. Definición del perfil de jugador
   
1.1 Tipo de jugador (motivaciones y estilo de juego)

Aplicando la taxonomía de Bartle, el jugador objetivo es predominantemente un Triunfador (Achiever): su motivación central es el desafío y la superación constante de metas (puntaje, tiempo, monedas). Como motivación secundaria aparece un componente de Asesino (Killer), expresado no en competencia directa contra otros sino en la búsqueda de dominar el sistema y superar su propio récord.

Bajo el modelo de los 8 placeres de LeBlanc (MDA), el placer dominante es el Reto (dominio de problemas y obstáculos) y el placer secundario es la Sensación (retroalimentación audiovisual inmediata: sonidos, partículas, vibración). Se sacrifica deliberadamente la Narrativa y el Descubrimiento profundo, ya que ampliarlos entraría en conflicto con sesiones cortas y un core loop ágil.

En términos de las 28 dimensiones de motivación (McKechnie et al., 2024), el jugador se ubica alto en Competencia, medio-alto en Sensación/Estímulo, y bajo en Narrativa y en Compañerismo (Fellowship), pues el juego es principalmente de un solo jugador y no depende de la cooperación social.

1.2 Plataforma objetivo

Dispositivos móviles (smartphones, Android/iOS), con controles táctiles simplificados (un solo dedo o gestos básicos: tocar para saltar, deslizar para esquivar/atacar). Esto condiciona el diseño de controles, la interfaz y la duración de las partidas.

1.3 Tipo de sesiones

Sesiones cortas, de aproximadamente 1 a 5 minutos, con la posibilidad de detenerse y retomar en cualquier punto sin perder el progreso. El juego debe ofrecer "unidades de diversión" completas (un nivel, una carrera, un intento) que quepan en momentos breves de la vida diaria del jugador.

1.4 Nivel de experiencia

Jugador casual a intermedio: no necesariamente experimentado en videojuegos de acción, pero dispuesto a mejorar sus habilidades a través de la repetición. El juego debe seguir el principio de "fácil de aprender, difícil de dominar", con una barrera de entrada baja y techo de habilidad alto para retener tanto a jugadores ocasionales como a los que buscan optimizar su desempeño.

2. Relación del perfil con la estructura del juego
2.1 Núcleo del juego y loop principal (core loop)

Siguiendo el esquema núcleo del juego → dinámicas → desafíos → metas, las mecánicas del núcleo se definen como abstractas (en el sentido de Pac-Man, no representacionales como un simulador): reglas simples de salto, esquive y recolección, elegidas porque un jugador Triunfador/placer de Reto necesita entender el sistema de inmediato para poder dominarlo, sin la carga de aprender una simulación realista.

El loop principal resultante es: avanzar → saltar/esquivar obstáculo → recolectar objeto → resultado (meta o fallo) → retroalimentación inmediata vía interfaz (puntaje, sonido, vibración) → reintentar. Este ciclo de 30 segundos a 3 minutos concreta las metas y desafíos que exige el placer de Reto, mientras la interfaz entrega el placer de Sensación mediante feedback audiovisual instantáneo.

2.2 Interfaz, modelo de cámara y estructura general del juego

El modelo de cámara elegido es la cámara estática de scroll lateral, señalada como la opción clásica para juegos de plataformas por ofrecer un punto de vista fijo y predecible. El modelo de interacción es táctil de un solo dedo (tocar = saltar, deslizar = esquivar), coherente con jugar "entre actividades" en un móvil.

La estructura general usa niveles discretos en progresión lineal (no mundo abierto), porque el mundo abierto exige un modo de exploración con mayor carga de memoria espacial y sesiones largas — un ajuste que corresponde al placer de Descubrimiento, no al de Reto que aquí es dominante. Se define un único modo de juego principal (evitar múltiples sistemas de interfaz/acción simultáneos), con pantallas de suspensión (pausa, reinicio) que permiten interrumpir la partida sin perder progreso, ideal para sesiones cortas e interrumpibles.

2.3 Ritmo y dificultad (demanda cognitiva del género)

De acuerdo con la evidencia de Dobrowolski et al. (2015) sobre género y efectos cognitivos, los juegos de acción/plataformas exigen predominantemente una visión egocéntrica: reacción rápida ante pocos objetos simultáneos, a diferencia de géneros de estrategia (RTS) que requieren visión alocéntrica y planificación ejecutiva sobre múltiples objetos. Esta demanda cognitiva —reacción veloz, bajo número de elementos a rastrear— es precisamente la que mejor ajusta (fit) con un jugador casual-intermedio de sesiones cortas, que no busca ni puede sostener la carga ejecutiva de un género alocéntrico.

El ritmo es entonces ágil desde el primer segundo, con dificultad ascendente gradual (un obstáculo nuevo a la vez) y reinicio instantáneo tras el fallo, para mantener al jugador dentro del canal de flow: ni tan fácil que aburra, ni tan exigente en carga cognitiva que genere ansiedad o abandono.

3. Justificación teórica

Jesse Schell (2008, cap. 8-9) — el punto de partida es la idea de que el juego no es lo que se ve en pantalla, sino la experiencia que ocurre en la mente del jugador. Esto justifica diseñar primero el perfil (quién es, qué necesita sentir) y solo después las mecánicas. El concepto de canal de flow —equilibrio entre el desafío del juego y la habilidad del jugador— respalda directamente la curva de dificultad ascendente gradual y el reinicio instantáneo: el objetivo es mantener al jugador entre el aburrimiento y la ansiedad.

Dobrowolski et al. (2015) — esta lectura aporta evidencia empírica de que el género de un juego determina demandas cognitivas específicas: los juegos de acción exigen visión egocéntrica y reacción veloz ante pocos objetos, mientras géneros de estrategia exigen visión alocéntrica y rastreo de múltiples objetos (planificación ejecutiva). Elegir un género de plataformas/acción para un jugador casual-móvil es una decisión de ajuste (fit) entre el perfil cognitivo del jugador y la mecánica estructural del juego, evitando imponerle una carga ejecutiva que no busca ni puede sostener en sesiones cortas.

Scott Rogers (2010, Level Up!, Level 2) — su planteamiento sobre identificar con precisión al público objetivo y sus motivaciones antes de diseñar respalda por qué el perfil de jugador (plataforma, tipo de sesión, experiencia) se definió antes que cualquier mecánica. De ahí también se deriva la estructura de niveles discretos con metas claras por nivel, en vez de un sistema abierto que diluye el objetivo frente a un público que busca logro medible.

LeBlanc / MDA y Bartle (marco complementario) — el modelo MDA recuerda que la diversión no es accidental sino resultado de las reglas (mecánicas → dinámicas → estética), lo que justifica trabajar el diseño desde el núcleo del juego hacia la experiencia percibida. La taxonomía de Bartle y la síntesis de los 8 placeres permiten declarar explícitamente qué tipo de jugador se prioriza (Triunfador, placer de Reto y Sensación) y qué se sacrifica conscientemente (Narrativa, Descubrimiento, Compañerismo), evitando que el diseño quede ambiguo.
