
---
## ¿Que es un diagrama de clases?
El **diagrama de clases** es uno de los diagramas incluidos en UML 2.5 clasificado dentro de los diagramas de estructura y, como tal, se utiliza para representar los elementos que componen un sistema de información desde un punto de vista estático.

El diagrama de clases es un **diagrama puramente orientado al modelo de programación orientado a objetos**, ya que define las clases que se utilizarán cuando se pase a la fase de construcción y la manera en que se relacionan las mismas.

---
## Elementos de un diagrama de clases
El diagrama de clases está formado por dos elementos: clases, relaciones e interfaces.
### Clases
Las clases son el elemento principal del diagrama y representa, como su nombre indica, una clase dentro del paradigma de la orientación a objetos. Representan conceptos o entidades del *negocio*.
Una clase define un __grupo de objetos__ que comparten características, condiciones y significado. __Resulta fundamental identificar de forma efectiva estas clases__.

Una clase esta compuesta por 3 elementos: __nombre de la clase, atributos, funciones__.
- Nombre de clase: identifica la clase. Si fuera un clase abstracta el nombre se escribe en _cursiva_
- Atributos: Atributos públicos, privados o protegidos.
- Funciones: funciones que ofrece la clase con sus respectivas visibilidades: públicos, privados o protegidos.
```mermaid
classDiagram
	class NombreDeClase{
	+Atributos
	+Funciones()
	}
```
Tanto los atributos como las funciones incluyen al principio de su descripción la visibilidad que tendrá. Esta visibilidad se identifica con un símbolo:
- **(+) Pública.** Representa que se puede acceder al atributo o función desde cualquier lugar de la aplicación.
- **(-) Privada.** Representa que se puede acceder al atributo o función únicamente desde la misma clase.
- **(#) Protegida.** Representa que el atributo o función puede ser accedida únicamente desde la misma clase o desde las clases que hereden de ella (clases derivadas).
### Relaciones
Una relación i**dentifica una dependencia**. Esta dependencia puede ser entre dos o más clases (más común) o una clase hacía sí misma (menos común, pero existen), este último tipo de dependencia se denomina _dependencia reflexiva_.
