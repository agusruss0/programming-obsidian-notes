
---
## ¿Que es la cohesión?
Es una métrica para evaluar en un sistema, cuanto tiene que ver lo que un modulo hace con respecto a la responsabilidad del modulo. Si tengo una clase con $n$ métodos, cuanto tiene que ver los metodos con lo que hace esa clase.
Siempre buscamos que la cohesion sea alta. Si un clase tiene metodos que no tienen que ver con la tarea que realiza (por que no se supo donde ponerlos o por comodidad) se dice que es clase tiene una cohesion baja.

---
## Tipos de niveles de cohesion
Para el [[paradigma estructurado]].
### Tipos de cohesión aceptables
#### Cohesión Funcional
- Una clase con un solo método. No hay cohesion mas fuerte ya que todos sus métodos están relacionados con su tarea. Que sea un sistema con alta cohesion no garantiza un sistema de alta calidad.
#### Cohesión Secuencial
- Una clase que tiene metodos que deben hacerse en secuencia. Agrupo metodos que deban hacerse en cierto orden pero cumplen la tarea de la clase. Esto genera que si mas adelante tengo que cambiar alguno de los metodos o algoritmos dentro de esa clase, solo ella se ve afectada y no afecta al resto del sistema.
#### Cohesión Comunicacional
 - Todos los métodos de una clase trabajan sobre los mismos datos o mismo dominio. Es la mas usual. No tiene el nivel de cohesión mas alto pero si el que tiene mas sentido.


### Tipos de cohesión no aceptables
#### Cohesion Temporal
- Clases con metodos que se ejecutan en un momento particular y no necesariamente sobre la tarea de la clase. Al tener los metodos y el flujo de control dentro de la clase, eso reduce la cohesión.
#### Cohesión Procedural
- Las acciones o metodos de de una clase están relacionadas a través de un flujo de control por lo que tienen que ejecutarse en un orden especifico. Parecido al secuencial pero en esta existe  un método que decide como se ejecutan el resto de los métodos.
#### Cohesión Lógica
- Ejecuta metodos o no en función de un parámetro enviado cuando se instancie la clase. Si uno agrupa metodos dentro de una clase que se ejecutan por partes dependiendo de algún parámetro. Es mejor dividir esos metodos en dos clases (pueden llegar a generar una cohesión temporal pero es mejor).
#### Cohesión Coincidental
- No existe una relación observable entre la clase y sus metodos o acciones. Típica clase *utils*. Guarda metodos que se usan desde distintos lados. Lo problemático es que si cambiamos algo en los metodos o algoritmos corremos el riesgo de que algo se rompa.

---
## Cohesión en [[OOP]]
En OOP se trasladan los conceptos de cohesión, [[Acoplamiento|acoplamiento]] como así también el tratamiento para otros atributos de calidad en el diseño (como la [[OOP#Cambiabilidad|cambiabilidad]], y la [[OOP#Reusabilidad|reusabilidad]]).
Para estos atributos en algunos casos, también se aplican prácticas y procesos usados establecidos en paradigmas anteriores (como el estructurado o el orientado a eventos).
La cohesión y el acoplamiento en OOP, suele tener visiones diferentes de acuerdo a distintos autores.

Podemos pensar el alcance a la cohesión en OOP desde tres puntos de vista:
#### Cohesión del objeto respecto de sus responsabilidades
- Hablamos de alta cohesión de un objeto cuando hay alto grado de relación en __la semántica del objeto respecto de las responsabilidades que desarrolla__. En la medida que el objeto implemente exclusivamente las responsabilidades que le corresponde mayor será el nivel de cohesión.
#### Cohesión en cada método del objeto
- Pensando que lo anterior se cumple, podemos estudiar la especificidad y segregación de los métodos (públicos o privados) y su interrelación
#### Cohesión dentro del paquete que contiene a las clases
- Se aplica el concepto de cohesión a la relación que guardan las clases dentro de un paquete que las contiene.