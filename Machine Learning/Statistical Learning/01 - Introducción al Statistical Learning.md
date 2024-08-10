
---
## ¿Que es el Aprendizaje Estadístico?
En general el aprendizaje estadístico refiere a un conjunto de encares para estimar una función predictora $f$. Esta función recibirá uno o mas inputs, llamadas variables independientes o predictores, denotado como $X$, y devolverá un variable de output, llamada variable dependiente o respuesta, denotada como $Y$. Lo que queremos encontrar a través de estas variables es si existe alguna asociación entre alguna de las variables predictoras y el output. Para eso, el objetivo es desarrollar un modelo preciso que pueda ser usado para predecir esos resultados.

Mas formalmente, tenemos una respuesta cuantitativa $Y$ y $p$ diferentes predictores, $X_{1},X_{2},\dots,X_{p}$. Se asume que existe alguna relación entre $Y$ y $X=(X_{1},X_{2},\dots,X_{p})$, que se puede escribir de la siguiente forma:
$$
Y=f(X)+\epsilon
$$
Acá $f$ es una función fija desconocida de $X_{1},X_{2},\dots,X_{p}$ y $\epsilon$ es un __término de error__ random que es independiente de $X$ y tiene [[media]] igual a 0. En esta formula $f$ representa la información *sistemática* que $X$ provee a $Y$.
![[error-term.png|700]]
---
## ¿Porqué estimar $f$ ?
Existen dos razones por las cuales queremos estimar $f$ : *predicción* e *inferencia*.
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
### Inferencia
Siempre estamos interesados en entender lam asociación entre $Y$ y $X_{1},X_{2},\dots,X_{p}$. Queremos estimar $f$ pero no solo para hacer predicciones para $Y$, si no también para conocer $\hat{f}$ en su forma exacta para responder las siguientes preguntas:
- ___¿Que predictores están asociados a la respuesta?___ Identificar las variables importantes entre un gran data set de posibles variables puede ser muy util.
- ___¿Cuál es la relación entre la respuesta y cada predictor?___ Algunos predictores pueden tener una relación positiva con $Y$, pueden estar asociados grandes valores de un predictor a grandes valores en $Y$. La relación puede ser opuesta 
- ___¿Puede la relación entre $Y$ y cada predictor ser adecuadamente modelada con una ecuación lineal, o es la relación mas compleja?___ En la mayoría de los casos los métodos para estimar $f$ terminan en una forma lineal. Pero sucede que la verdadera relación es mas complicada por lo que un modelo lineal deja de ser una representación precisa de la relación
---
## ¿Como estimar $f$ ?
Asumiremos que vamos a trabajar con un dataset de $n$ __observaciones o data points__. Estas observaciones se llaman __data de entrenamiento__ por que serán la data que utilicemos para entrenar nuestro modelo.

Sea $x_{ij}$ el valor del $j$-esimo predictor para la observación $i$, donde $i=1,2,\dots,n$ y $j=1,2,\dots,p$. Correspondientemente sea $y_{i}$ variable de respuesta de la $i$-esima observación. Entonces nuestra data de entrenamiento consiste de $\{ (x_{1},y_{1}),(x_{2},y_{2}),\dots,(x_{n},y_{n}) \}$ donde $x_{i}=(x_{i1},x_{i2},\dots,x_{ip})^{T}$.

El objetivo es aplicar un método de aprendizaje estadístico a la data de entrenamiento para poder estimar $\hat{f}$ talque $Y \approx \hat{f}(X)$ para toda observación $(X,Y)$.

La mayoría de métodos de aprendizaje estadístico para esta tarea se pueden caracterizar entre *paramétricos* o *no paramétricos*.
### Métodos Paramétricos
Los métodos paramétricos implican un enfoque basado en modelos de dos pasos.
1. Primero podemos asumir sobre la forma de la función $f$. Por ejemplo podemos decir que $f$ es lineal en $X$. 
$$
f(X)=\beta_{0}+\beta_{1}X_{1}+\beta_{2}X_{2}+\dots+\beta_{p}X_{p}
$$
Este es un [[modelo lineal]].  Ahora, en vez de tener que estimar una función arbitraria $p$-dimensional $f(X)$, solo tenemos que estimar los $p+1$ coeficientes $\beta_{0},\beta_{1},\dots,\beta_{p}$ .

![[linear-model.png|600]]

2. Una vez que hayamos elegido el modelo, necesitamos un procedimiento para usar la data de entrenamiento para entrenar el modelo. En el caso del modelo lineal tenemos que estimar los parámetros $\beta_{0},\beta_{1},\dots,\beta_{p}$ tal que:
$$
Y \approx \beta_{0}+\beta_{1}X_{1}+\beta_{2}X_{2}+\dots+\beta_{p}X_{p}
$$
El encare mas común para ajustar este modelo se conoce como [[mínimos cuadrados]].

Este enfoque basado en modelos se denomina paramétrico y nos permite reducir el problema de la estimación de $f$ a la estimación de un conjunto de parámetros. La desventaja de del encare paramétrico es que el modelo que elijamos no igualara la verdadera forma de $f$. Si el modelo elegido esta muy lejos de la verdadera forma de $f$, nuestra estimación sera pobre. Podemos elegir un modelo mas *flexible* que nos permita ajustar mas el modelo, pero también requeriría estimar una mayor cantidad de parámetros. Estos modelos mas complejos pueden derivar en un fenómeno llamado *[[overfitting]]*, que significa que siguen el ruido o el error muy de cerca.
### Métodos no paramétricos
Los métodos no paramétricos no asumen explícitamente la forma funcional de $f$. En cambio buscan una estimación de $f$ que se acerque lo mas que pueda a las observaciones sin ser muy estricto o muy laxo. La ventaja en comparación a los métodos paramétricos es que se evita asumir un forma particular de $f$, tiene el potencial de ajustar un grand rango de posibles formas de $f$ con precisión. La mayor desventaja de estos métodos es que no reducen el problema de estimar $f$ a un pequeño numero de parámetros, por lo que necesitan de un gran numero de observaciones para obtener una estimación precisa de $f$.

![[Pasted image 20240721214511.png|600]]

---
## Precisión de la predicción vs. Interpretabilidad del modelo
Entre los métodos que podemos encontrar, existen algunos mas restrictivos y otros mas flexibles. Por ejemplo,  la [[regresion lineal]] es mucho mas restrictiva que el método de thin-plate spline, ya que uno genera funciones lineales ya sean líneas o planos, y la otra puede ajustar de manera mas suave como una manta.
![[Pasted image 20240721220554.png|600]]

Para decidir si necesitamos un método mas restrictivo o uno mas flexible, tenemos que tener en cuenta que queremos obtener del modelo. Por ejemplo, si lo que buscamos es inferencia, un modelo restrictivo es mucho mas interpretable. Así podremos entender mejor la relación que hay entre $Y$ y $X_{1},X_{1},\dots,X_{p}$ . Si el objetico es la predicción, la interpretabilidad no nos interesa por lo que podemos optar por un modelo mas flexible que cumpla únicamente en generar predicciones precisas.

---
## Supervisado vs No Supervisado
La mayoría de los problemas de aprendizaje estadístico entran en dos categorías: *supervisado* y *no supervisado*.
### Aprendizaje Supervisado
En el aprendizaje supervisado tenemos que para cada observación de las medidas del predictor $x_{i}, i=1,\dots,n$ hay una medida de respuesta asociada $y_{i}$. Queremos ajustar un modelo  que relacione la respuesta con los predictores, con la esperanza de predecir con precisión la respuesta para futuras observaciones (predicción) o entender mejor la relación entre la respuesta y los predictores (inferencia).
### Aprendizaje No Supervisado
El aprendizaje no supervisado describe la situación algo mas compleja en la que para cada observación $i=1,\dots,n$, vemos un vector de medidas $x_{i}$ pero ninguna respuesta asociada $y_{i}$. Es decir no existe variable de respuesta a predecir, estamos trabajando a ciegas, ya que al no tener esta variable no podemos supervisar nuestro análisis.
Podemos intentar entender las relaciones entre las variables o entre las observaciones. Una de las herramientas mas comunes para estos casos es el _análisis de cluster_ o *clustering*. El objetivo de esta herramienta es la de comprobar, en función de $x_{1},\dots,x_{n}$, si alguna de las observaciones se dividen en grupos relativamente distintos.

![[Pasted image 20240721234529.png|600]]

Muchas veces no es claro si un análisis deberia ser considerado supervisado o no supervisado. Por ejemplo, si tenemos un dataset de $n$ observaciones. Por $m$ de las observaciones, con $m<n$, tenemos medidas del predictor y medidas de la respuesta. Para las restantes $n-m$ observaciones, tenemos las medidas de predicción pero nos las de respuesta. Este escenario puede darse cuando los costos de medición de los predictores son relativamente bajos, pero las correspondientes a la repuesta con mucho mas costosas de recopilar. Nos referimos a esta configuración como un problema de _aprendizaje semi-supervisado_. Queremos un método de aprendizaje estadístico que nos permita utilizar las $m$ observaciones para las cuales las medidas de repuesta están disponibles como también las $n-m$ para las cuales no.

---
## Regresión vs Clasificación
