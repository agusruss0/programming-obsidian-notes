
---
## ¿Que es la cohesión?
Es una métrica para evaluar en un sistema, cuanto tiene que ver lo que un modulo hace con respecto a la responsabilidad del modulo. Si tengo una clase con $n$ métodos, cuanto tiene que ver los metodos con lo que hace esa clase.
Siempre buscamos que la cohesion sea alta. Si un clase tiene metodos que no tienen que ver con la tarea que realiza (por que no se supo donde ponerlos o por comodidad) se dice que es clase tiene una cohesion baja.

---
## Tipos de niveles de cohesion

### Tipos de cohesión aceptables
#### Cohesión Funcional
- Una clase con un solo método. No hay cohesion mas fuerte ya que todos sus métodos están relacionados con su tarea. Que sea un sistema con alta cohesion no garantiza un sistema de alta calidad.
#### Cohesión Secuencial
- Una clase que tiene metodos que deben hacerse en secuencia. Agrupo metodos que deban hacerse en cierto orden pero cumplen la tarea de la clase. Esto genera que si mas adelante tengo que cambiar alguno de los metodos o algoritmos dentro de esa clase, solo ella se ve afectada y no afecta al resto del sistema.
#### Cohesión Comunicacional
 - Todos los métodos de una clase trabajan sobre los mismos datos o mismo dominio. Es la mas usual. No tiene el nivel de cohesión mas alto pero si el que tiene mas sentido.
#### Cohesion Temporal
- Clases con metodos que se ejecutan en un momento particular y no necesariamente sobre la tarea de la clase. Al tener los metodos y el flujo de control dentro de la clase, eso reduce la cohesión.

### Tipos de cohesión no aceptables
#### Cohesión Procedural
- Las acciones o metodos de de una clase están relacionadas a través de un flujo de control por lo que tienen que ejecutarse en un orden especifico. Parecido al secuencial pero en esta existe  un método que decide como se ejecutan el resto de los métodos.
#### Cohesión Lógica
- Ejecuta metodos o no en función de un parámetro enviado cuando se instancie la clase. Si uno agrupa metodos dentro de una clase que se ejecutan por partes dependiendo de algun parametro. Es mejor dividir esos metodos en dos clases (pueden llegar a generar una cohesión temporal pero es mejor).
#### Cohesión Coincidental
- No existe una relación observable entre la clase y sus metodos o acciones. Tipica clase *utils*. Guarda metodos que se usan desde distintos lados. Lo problematico es que si cambiamos algo en los metodos o algoritmos corremos el riesgo de que algo se rompa.
