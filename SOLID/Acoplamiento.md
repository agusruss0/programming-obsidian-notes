
---
## ¿Que es el acoplamiento?
Es la métrica que mide la dependencia que hay entre dos metodos o clases. A diferencia de la [[Cohesión|cohesión]], que mide cuanto tienen que ver los metodos con las tareas y responsabilidades de una clase, el acoplamiento mide cuanto depende un método de otro. Siempre se busca que el acoplamiento sea lo mas bajo posible.

---
## Tipos de acoplamiento
En el [[paradigma estructurado]]
### Acoplamiento aceptable
#### Acoplamiento de Datos
La menor dependencia que se puede conseguir es cuando lo que le manda un método a otro por parámetro es un valor escalar o ningún parámetro. Si tenemos un método $A$ que llama a otro método $B$, $B$ no tiene que saber nada de $A$ para funcionar. Puede funcionar sin saber nada de donde se llamo.
#### Acoplamiento Estampado
Acá el parámetro que se manda no es un escalar sino un objeto. Por ende necesito conocer las propiedades de ese objeto para poder usarlo.
### Acoplamiento no aceptable
#### Acoplamiento por Control
En este caso lo que se manda por parámetro (un ```bool```, un ```int```, etc) definirá que parte del código se ejecuta. Si tengo un método $A$ que utiliza al método $B$. $A$ debe conocer como funciona $B$ para saber que mandar para que se realize lo deseado. La solución a este problema es dividir a $B$ en dos metodos distintos $B_{1}, B_{2}$ y que $A$ llame al que cumple con su requisito.
#### Acoplamiento Común
Utilizacion de variables globales. Al ser accesible desde cualquier lugar, se corre el riesgo de perder el valor que se había guardado. Mejor crear una clase y guardar ahí ese valor.
#### Acoplamiento Patológico
Un método usa parte del código de otro. En [[OOP]] no se ve mucho pero en lenguajes estructurados se podía dependiendo del input ir a un línea de código especifica.

---
## Acoplamiento en OOP
Se lo describe como el nivel de relación, conocimiento o dependencia que tienen objetos, clases y paquetes entre si. Se toma como consigna principal y objetivo que el sistema tenga componentes __lo mas independientes posibles__.
Esto implica que cada objeto/clase tenga __metodos de pocos argumentos, claramente definidos__ con el __menor acoplamiento__ posible.

Una bien implementada OPP conduce a la creación de componentes en un sistema __débilmente acoplados__.

Además de interfaces estrechas, es fundamental que la estructura interna de un objeto este oculta dentro del objeto. __No respetar el [[OOP|encapsulamiento]] genera mas acoplamiento__.

Un sistema bien diseñado __no necesita compartir su estado interno__. Los valores de los atributos de cada objeto son de cada objeto.

Si se divide __erróneamente una clase altamente cohesiva__, las clases resultantes estarán __fuertemente acopladas__.
Si se integran dos clases con __bajo acoplamiento__ la clase resultante no será __altamente cohesiva__.

Si se diseñan las clases como una colección de datos, con un conjunto de operaciones que solo gestionan los mismo, __no hay garantías sobre el nivel de acoplamiento obtenido__.

Las interacciones (por estructura o por llamadas entre metodos) entre objetos/clases, y por ende el tipo de relación, __condicionan el acoplamiento__.

Cada tipo de relación tiene mas o menos acoplamiento respecto de las otras relaciones. 

La __relación mas leve es la dependencia (o uso)__, ya que la relación es efímera mientras se ejecuta el método en el método usado. El objeto no depende del que lo usa.

En el caso de la asociación, la navegabilidad entre objetos/clases condiciona también el tipo de acoplamiento. Una asociación navegable en un sentido, es menos acoplada que si es navegable en los dos sentidos.

Las __agregaciones son mas acopladas que las asociaciones__, debido a que tiene la __contención física__ de los objetos agregados.

La composición, __es la relación de asociación mas acoplada de todas__. Por eso es una relación que en lo posible se trata de evitar, debido a su uso tan exclusivo y el costo en términos de esfuerzo de desarrollo y mantenimiento debido a su alto acoplamiento.

La generalización/especialización, tiene también un tipo de acoplamiento: __el acoplamiento de clases.



