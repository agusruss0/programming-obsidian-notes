
---
## ¿Que es el Aprendizaje Estadístico?
En general el aprendizaje estadístico refiere a un conjunto de encares para estimar una función predictora $f$. Esta función recibirá uno o mas inputs, llamadas variables independientes o predictores, denotado como $X$, y devolverá un variable de output, llamada variable dependiente o respuesta, denotada como $Y$. Lo que queremos encontrar a través de estas variables es si existe alguna asociación entre alguna de las variables predictoras y el output. Para eso, el objetivo es desarrollar un modelo preciso que pueda ser usado para predecir esos resultados.

Mas formalmente, tenemos una respuesta cuantitativa $Y$ y $p$ diferentes predictores, $X_{1},X_{2},\dots,X_{p}$. Se asume que existe alguna relación entre $Y$ y $X=(X_{1},X_{2},\dots,X_{p})$, que se puede escribir de la siguiente forma:
$$
Y=f(X)+\epsilon
$$
Acá $f$ es una función fija desconocida de $X_{1},X_{2},\dots,X_{p}$ y $\epsilon$ es un __término de error__ random que es independiente de $X$ y tiene [[media]] igual a 0. En esta formula $f$ representa la información *sistemática* que $X$ provee a $Y$.
## ¿Porqué estimar $f$ ?
Existen dos razone por las cuales queremos estimar $f$ : *predicción* e *inferencia*.
### Predicción
En muchas situaciones, los inputs $X$ pueden estar fácilmente disponibles, pero $Y$ es difícil de obtener. Por lo tanto, como el término de error promedia 0, podemos predecir $Y$ usando:
$$
\hat{Y} = \hat{f}(X)
$$
donde $\hat{f}$ representa un estimado para $f$, y $\hat{Y}$ representa la predicción resultante de $Y$. A $\hat{f}$ se la trata como una _caja negra_, en el sentido de que no nos interesa la forma exacta de $\hat{f}$ , siempre y cuando se obtengan predicciones precisas para $Y$.

La precisión de $\hat{Y}$ como predicción de $Y$ depende de dos cantidades, llamadas __error reducible__ y __error irreducible__. En general, $\hat{f}$ no va ser estimada perfectamente para $f$, y esta imprecisión va a introducir algo de error. Este es un error reducible ya que potencialmente podemos mejorar la precisión de $\hat{f}$$ usando mejores técnicas estadísticas para estimar $f$ . Aun así, aunque estimemos perfectamente $f$, por lo que nuestra formula tomaría la forma de $\hat{Y}=f(X)$, nuestra predicción aun tendría algo de error. Esto es porque $Y$ es también una función de $\epsilon$, que por definición no puede ser predicho usando $X$. Esto se conoce como error irreversible, ya que no importa lo bien que estimemos $f$ , no podemos reducir el error que agrega $\epsilon$.

El error irreducible $\epsilon > 0$. La cantidad de $\epsilon$ puede también contener variables no medidas que sirven para predecir $Y$. Como no se miden, $f$ no puede usarlas para sus predicciones. La cantidad $\epsilon$ también contiene variación no medida.

Considerar una función estimada $\hat{f}$ y un conjunto de predictores $X$, que producen la predicción $\hat{Y} = \hat{f}(X)$. Asumamos que $\hat{f}$ y $X$ están fijas por lo que la única variación la obtenemos de $\epsilon$. Entonces:
$$\begin{array}{l}
E(Y-\hat{Y})^{2} = E[f(X) + \epsilon -\hat{f}(X)]^{2} \\
\qquad\qquad\quad= \underbrace{ [f(X)-\hat{f}(X)]^{2}} + \underbrace{Var(\epsilon)} \\
\qquad\qquad\qquad\quad\mathrm Reducible \qquad Irreducible
\end{array}
$$
donde $E(Y-\hat{Y})^{2}$ representa el promedio, o el _valor esperado_, de la diferencia de cuadrados entre lo predicho y el actual valor de $Y$, y $Var(\epsilon)$ representa la varianza asociada con el termino de error $\epsilon$.

