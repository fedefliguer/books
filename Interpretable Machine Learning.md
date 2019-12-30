_[Interpretable Machine Learning: A Guide for Making Black Box Models Explainable. Christoph Molnar](https://christophm.github.io/interpretable-ml-book/)_

## 1. Introducción

* El libro busca hacer que los modelos ML sean fáciles de interpretar. Por lo tanto, la organización de los diferentes modelos que hay será por su capacidad de ser interpretados.
* ML: conjunto de métodos que usan las computadoras para hacer y mejorar predicciones o comportamientos basados en datos.
* El libro se ocupa del aprendizaje supervisado. La serie de pasos es la siguiente:
  1. Recoger datos pasados con el target.
  2. Llevar esos datos a un algoritmo ML.
  3. Integrar el resultado de ese algoritmo a un producto o proceso.

## 2. Interpretabilidad

* La interpretabilidad es el grado en que un humano puede comprender la causa de una decisión.
* Es posible que algunos modelos no requieran explicaciones porque se usan en un entorno de bajo riesgo, lo que significa que un error no tendrá consecuencias graves (por ejemplo, un sistema de recomendación de películas) o que el método ya ha sido ampliamente estudiado y evaluado (por ejemplo, reconocimiento óptico de caracteres). La necesidad de interpretabilidad surge cuando no es suficiente obtener la predicción (el qué), sino que el modelo también debe explicar cómo llegó a la predicción (el por qué).
* Además de eso, la interpretabilidad es importante en ciertas circunstancias particulares:
  1. En ciertas circunstancias, las personas no se conforman con el qué sino que su curiosidad o su necesidad hace que necesiten saber cómo funcionan ciertas cosas.
  2. En algunos casos, el algoritmo es utilizado por una disciplina científica que busca agregar conocimiento al mundo. En ese caso, no es la predicción lo que interesa sino directamente el algoritmo, es decir que es imprescindible interpretarlo.
  3. Los algoritmos pueden tener sesgos, en particular en contra de ciertas minorías. La aceptabilidad social de un algoritmo depende de su interpretabilidad.
  4. Los modelos solo pueden ser inspeccionados y auditados cuando son interpretables.
* Por el contrario, la interpretabilidad no es necesaria cuando el modelo tiene un riesgo muy bajo al equivocarse, cuando el problema está muy estudiado y hay muchos años de experiencia en el tema, o bien cuando las personas conociendolo podrían modificar su comportamiento para alterar el resultado.
* La interpretabilidad intrínseca se refiere a los modelos de aprendizaje automático que se consideran interpretables debido a su estructura simple, como árboles de decisión cortos o modelos lineales dispersos. La interpretabilidad post hoc se refiere a la aplicación de métodos de interpretación después del entrenamiento modelo.
* Un método de interpretación puede tener múltiples resultados: estadísticos de resumen, visualización de los atributos, elementos internos del modelo, ejemplos con datos reales. La interpretación también puede ser propia del modelo (como los coeficientes de la regresión) o general (pares de entrada y salida).
* Alcance de la interpretabilidad: Preguntas en las que valdría la pena detenerse.
  1. ¿Cómo crea el algoritmo el modelo? Esto requiere conocimiento del algoritmo, y no sólo de los datos.
  2. ¿Cómo hace predicciones el modelo entrenado? Entender cómo, a través de las variables y los pesos, se pueden generar las predicciones
  3. ¿Cómo afectan partes del modelo a las predicciones? Entender los pesos, a veces son contraintuitivos.
  4. ¿Por qué el modelo hizo una cierta predicción para una instancia?
  5. ¿Por qué el modelo hizo predicciones específicas para un grupo de instancias?

## 3. Modelos
* Un modelo es lineal si la asociación entre features y target se modela linealmente.
* Un modelo con restricciones de monotonicidad asegura que la relación entre una característica y el resultado objetivo siempre vaya en la misma dirección en todo el rango de la feature: un aumento en el valor de la característica siempre conduce a un aumento o siempre a una disminución en el objetivo 
* Algunos modelos pueden incluir automáticamente interacciones entre características para predecir el resultado objetivo.
<p align="center"> <img src="https://github.com/fjf-arg/books/blob/master/images/3.1.png"> </p>

### 1. Regresión lineal
En este modelo, el resultado previsto de una instancia es una suma ponderada de sus características p. Las betas (β) representan los pesos o coeficientes de las características aprendidas. El primer peso en la suma (β0) se llama intercepción y no se multiplica con una característica. El épsilon (ϵ) es el error que cometemos, la diferencia entre la predicción y el resultado real. Se supone que estos errores siguen una distribución gaussiana centrada en torno al 0, lo que significa que cometemos muchos errores en direcciones negativas y positivas, muchos pequeños y pocos grandes. Los pesos estimados vienen con intervalos de confianza. Un intervalo de confianza es un rango para la estimación de peso que cubre el peso "verdadero" con una cierta confianza. Si el modelo es el modelo "correcto" depende de si las relaciones en los datos cumplen ciertos supuestos:
  * Linealidad: La predicción debe ser una combinación lineal de características. Los efectos lineales son fáciles de cuantificar y describir. Son aditivos, por lo que es fácil separar los efectos. 
  * Normalidad: Se supone que la esperanza del target condicionada a los features incluidos en la regresión sigue una distribución normal. Si se viola esta suposición, los intervalos de confianza estimados de los pesos de las características no son válidos.
Homocedasticidad (varianza constante): Se supone que la varianza del término de error es constante en todo el espacio de features. Esta suposición a menudo se viola en la realidad. 
  * Independencia: Se supone que cada observación es independiente de cualquier otra. 
  * Características fijas: Las features de entrada se consideran fijas, lo que implica que están libres de errores de medición. 
  * Ausencia de multicolinealidad: No desea características fuertemente correlacionadas, porque esto arruina la estimación de los pesos. 
 
En una situación en la que dos características están fuertemente correlacionadas, se vuelve problemático estimar los pesos porque los efectos de la característica son aditivos y se vuelve indeterminable a cuál de las características correlacionadas atribuir los efectos. El peso de las variables se interpreta por la magnitud de sus beta, pero su importancia por su estimador t, que divide ese beta por el desvío estándar: la intuición es que una variable será más importante cuanto más grande sea el beta pero también cuánto más seguro estemos que ese es el valor real (o sea, más chico el desvío estándar). El R2 es la proporción de la variabilidad del target que el modelo explica en los datos usados para modelar, y el R2 ajustado es una medida similar pero que considera la cantidad de variables: ![R^2_{adj} = R^2 * (1-R^2) * \frac{n-1}{n-p-1}](https://render.githubusercontent.com/render/math?math=R%5E2_%7Badj%7D%20%3D%20R%5E2%20*%20(1-R%5E2)%20*%20%5Cfrac%7Bn-1%7D%7Bn-p-1%7D) (para knitear la fórmula ayudó _[esto](https://www.latex4technics.com/)_ y _[esto](https://alexanderrodin.com/github-latex-markdown/)_). Las formas de visualizar el valor de los coeficientes puede ser con una especie de boxplot por variable donde cada barra esté centrada en el coeficiente y tenga la amplitud de su desvío estándar (weight plot), o con un boxplot real por variable, donde cada valor de la variable en la muestra se multiplica por el coeficiente estimado y entonces se grafica en forma de boxplot los efectos reales de la variable sobre el target (effect plot). En este último gráfico podría señalarse, por ejemplo, con un color el valor de una observación particular en cada variable para entender, en ese caso, cuál es el valor predicho.
<p align="center"> <img src="https://github.com/fjf-arg/books/blob/master/images/3.2.png"> </p>

A juzgar por lo que debe considerarse como una buena explicación ML, los modelos lineales no crean las mejores explicaciones. Son contrastables, pero el valor de referencia sobre el cual tienen interpretación los pesos es un caso en el que todas las características numéricas son cero y, en forma arbitraria, las categóricas están en sus basales. Ese caso no suele ser real. En ocasiones las variables se centran en torno de la media, para que el valor de referencia sea ‘el caso típico’. Esto también podría ser un punto de datos inexistente, pero al menos podría ser más probable o más significativo. Los modelos lineales crean explicaciones verdaderas, siempre que la ecuación lineal sea un modelo apropiado para la relación entre características y resultados. Cuantas más no linealidades e interacciones haya, menos preciso será el modelo lineal y menos sinceras serán las explicaciones.

Si la interpretabilidad crece cuando las variables son menos, se vuelven útiles métodos como Lasso, que realiza la selección de características y la regularización de los pesos de las características seleccionadas. Este modelo incorpora un término de penalización por los valores de los coeficientes, cosa que hace que muchos se ajusten a 0. El parámetro lambda de penalización dirá qué tanto se penalizará por cada peso: cuanto más grande sea, cada vez menos características reciben una estimación de peso diferente de cero.

<p align="center"> <img src="https://github.com/fjf-arg/books/blob/master/images/3.3.png"> </p>

A la izquierda del gráfico, el parámetro de penalización es muy chico y por lo tanto muchas variables (12) tienen un peso distinto de cero, por eso hay muchas líneas. En cuanto se incrementa el parámetro, más variables van hacia 0. El valor óptimo de lambda se elige muchas veces con validación cruzada. Lasso no es el único medio para reducir la cantidad de features, sino que hay otros como la selección manual, el umbral de correlación (sólo variables que correlacionan en cierta forma con el target) o el forward o backward selection (empezar con una sola o con todas las features, e ir recortando o agregando nuevas y viendo el impacto sobre el R2).

En conclusión, el modelo de regresión lineal es muy usado, por lo que en general es aceptado para el modelado predictivo y hacer inferencia. Matemáticamente es sencillo estimar los pesos y tiene la garantía de encontrar pesos óptimos (siempre y cuando los datos cumplen con los supuestos). Junto con los pesos se obtienen intervalos de confianza sustentados por una sólida espalda estadística. Como ventaja, el modelo sirve como base para muchas extensiones, como GLM. Sin embargo, los modelos de regresión lineal solo pueden representar relaciones lineales, es decir, una suma ponderada de las features de entrada. Cada no linealidad o interacción debe ser hecha a mano y definida explícitamente al modelo como una característica de entrada. Como vimos, además, la interpretación de un coeficiente en particular puede ser contraintuitiva, porque es en el contexto del modelo y depende de todas las demás características.
