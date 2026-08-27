# Actividad 4: Lectura y discusión de modelos heurísticos
Analizar cómo los modelos teóricos pueden complementar las ideas previas sobre qué hace que un videojuego funcione.


INSTRUCCIONES
Leer los modelos GAP y PLAY.

Discutir en equipo:
- Ideas previas sobre qué hace bueno a un videojuego
- Conceptos nuevos que aportan los modelos
- Posibles aplicaciones al diseño
- Registrar conclusiones individuales en un documento dentro de su carpeta personal en GitHub.

---

## 1. Ideas Previas sobre qué Hace Bueno a un Videojuego
Tradicionalmente, la noción común sobre qué hace funcional y atractivo a un videojuego suele sustentarse en percepciones intuitivas y subjetivas del jugador y del diseñador:
* **Jugabilidad empírica:** Se asume que un buen juego es aquel que resulta "divertido", con gráficos llamativos, buena ambientación sonora y una curva de dificultad
  percibida de forma intuitiva.
* **Diseño guiado por la intuición (*Unassisted Intuition*):** Históricamente, las mecánicas y tutoriales se diseñan a partir de la experiencia propia del desarrollador
  ("diseñar para uno mismo"), asumiendo que el usuario entenderá la lógica de interacción por sentido común.
* **Dificultad como reto plano:** Creencia de que el reto continuo o la penalización estricta son suficientes para retener la atención, sin discriminar entre fricción
  mecánica y reto cognitivo.
* **Tutoriales tardíos:** Tendencia recurrente en la industria de relegar el diseño de los primeros niveles y tutoriales al final del ciclo de producción,
  tratándolos como manuales interactivos en lugar de sistemas de aprendizaje integrados.

---

## 2. Conceptos Nuevos que Aportan los Modelos Teóricos
Los marcos formales de investigación en interacción humano-computadora (HCI) y teorías del aprendizaje (Desurvire & Wiberg; Gee; Bandura)  
estructuran formalmente la experiencia del jugador:

### A. Diferenciación de Dificultad (*Usability Difficulty* vs. *Strategy & Challenge*)
* **Usabilidad e Interfaz:** La fricción en los controles, la navegación y la claridad de la interfaz debe minimizarse al máximo (baja dificultad de usabilidad).
* **Reto Estratégico:** El desafío debe provenir exclusivamente de la toma de decisiones, la maestría mecánica y la estrategia (*positive game challenge*),
* no de lidiar con controles torpes o información confusa.

### B. Principios de Aproximabilidad (*Game Approachability Principles - GAP*)
* **Autoeficacia (*Self-Efficacy*):** Fomentar la creencia y confianza del jugador en que es capaz de dominar el sistema antes de exponerlo a fallos críticos.
* **Entorno Seguro (*Sandbox without consequence*):** Espacios donde el usuario puede experimentar y practicar mecánicas aprendidas sin penalizaciones severas de pérdida
  o muerte del avatar.
* **Andamiaje (*Scaffolding*):** Asistencia graduada que se presenta de lo general a lo específico según el jugador lo requiera, evitando la frustración y el abandono.
* **Información bajo demanda y a tiempo (*Information On Demand and In Time* / *System Thinking*):** La instrucción debe entregarse exactamente cuando es aplicable y
  mantenerse consultable en lugar de saturar al inicio con texto que desaparece.

### C. Heurísticas de Jugabilidad (*PLAY & HEP Frameworks*)
* **Recompensas significativas:** Premiar al jugador aumentando sus capacidades de acción y personalización en el mundo, reforzando la inmersión.
* **Consistencia del mundo (*Game World Persistence*):** El entorno debe reaccionar y recordar el paso del jugador, validando su agencia e impacto en el sistema.
* **Paseo y primeros minutos (*First 10-20 minutes rule*):** Los primeros minutos deben garantizar acciones claras con retroalimentación inmediata y gratificante
  para enganchar a jugadores casuales y novatos.

---

## 3. Posibles Aplicaciones al Diseño
La incorporación sistemática de estos modelos transforma la metodología de desarrollo de videojuegos:

1. **Diseño Proactivo de Niveles de Aprendizaje:** Integrar las heurísticas GAP desde la fase conceptual del *Game Design Document* (GDD), concibiendo el tutorial
   como parte intrínseca de la narrativa y mecánicas iniciales, no como un agregado de último minuto.
3. **Evaluaciones Heurísticas Tempranas (Pre-User Testing):** Aplicar listas estructuradas (PLAY/GAP) durante prototipos tempranos para identificar fallas de usabilidad,
   inconsistencias en controles y oportunidades de mejora antes de invertir en pruebas empíricas extensivas.
5. **Flujos de Información Contextual (HUD & Tooltips):** Diseñar interfaces no intrusivas que mantengan los objetivos activos en pantalla o
   accesibles mediante un menú de consulta rápida cuando se introducen mecánicas complejas.
7. **Diseño de Curvas de Dificultad Dinámicas y Adaptativas:** Modular la inteligencia artificial (IA) y el ritmo de los encuentros para alternar tensión y descanso,
   evitando la penalización repetitiva por un mismo fallo.

---

## 4. Conclusión Individual
* **Superación del sesgo del desarrollador:** Los modelos teóricos sustituyen la intuición no asistida por criterios objetivos y medibles, permitiendo anticipar
  barreras de accesibilidad que los jugadores experimentados suelen pasar por alto.
* **Complementariedad metodológica:** La evaluación heurística (GAP/PLAY) y las pruebas con usuarios (*User Testing*) no son excluyentes; la heurística predice
  y estructura el diseño conceptual, mientras que las pruebas empíricas validan la carga emocional, el ritmo real y la diversión efectiva.
* **El valor del aprendizaje invisible:** Un videojuego exitoso es aquel que enseña sus sistemas complejos de forma orgánica, donde el jugador adquiere maestría
  sintiendo que progresa por habilidad propia gracias a un andamiaje y autoeficacia cuidadosamente construidos.

