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

