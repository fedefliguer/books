_[Statistical Rethinking: A Bayesian Course with Examples in R and Stan. Richard McElreath](https://github.com/rmcelreath/statrethinking_winter2019)_

## 0. Prefacio

* Este libro busca ayudar a aumentar el conocimiento y la confianza en el modelado estadístico. Se entiende como un andamio, uno que permitirá construir el muro de la materia. En este proceso, se realiza trabajo 'inconveniente' como el paso a paso de algunos algoritmos que luego serán calculados automáticamente.
* El libro busca que el lector esté listo para intentar hacer inferencia estadística sin p-valores.
* El libro cuenta con cuadros 'rethinking' (aluden a conexiones con otros enfoques, proporcionan antecedentes históricos o llaman
malentendidos comunes) y cuadros 'overthinking' (proporcionan más detalles de explicaciones de código o matemáticas).

``` r
install.packages(c("rstan","coda","mvtnorm","devtools"))
library(devtools)
devtools::install_github("rmcelreath/rethinking")
```

## 1. EL GOLEM DE PRAGA: *modelos estadísticos*

* _Referencia: El golem es un robot de arcilla conocido en el folklore judío, construido a partir de polvo, fuego y agua. Se le da vida al inscribir emet, "verdad", en su frente. Animado en verdad, pero sin voluntad propia, un golem siempre hace exactamente lo que se le dice. Esto es afortunado porque el golem es increíblemente poderoso, capaz de resistir y lograr más de lo que Los creadores podrían. Sin embargo, su obediencia también trae peligro, como instrucciones descuidadas o inesperadas. los eventos pueden convertir a un golem en contra de sus creadores. Su abundancia de poder se corresponde con su falta de sabiduría._
* Del mismo modo, los modelos estadístico comparten gran parte de esto. La preocupación por la verdad les da vida, pero en sí mismos no so son ni verdaderos ni falsos, ni profetas ni charlatanes. Más bien son construcciones diseñadas para algún propósito. Estas construcciones
son increíblemente poderosas, cumpliendo diligentemente sus cálculos programados. Los modelos también son robots sin intención propia, que se mueven de acuerdo con las instrucciones miopes que ellos encarnan. No hay sabiduría en el golem. No discierne cuando el contexto es inapropiado por sus respuestas. Simplemente conoce su propio procedimiento, nada más. Simplemente hace lo que se le dice.
* Las estadísticas tienden a ser inflexibles y frágiles. Por inflexible, quiero decir que tienen muy formas limitadas de adaptarse a contextos de investigación únicos. Por frágil, quiero decir que fallan en impredecibles formas cuando se aplica a nuevos contextos. He leído personalmente cientos de usos de la prueba exacta de Fisher en revistas científicas, pero aparte del uso original de Fisher, nunca he visto que se use adecuadamente. Incluso un procedimiento como la regresión lineal ordinaria, que es bastante flexible en muchos sentidos, pudiendo codificar una gran diversidad de hipótesis interesantes, a veces es frágil.
¡Estoy <span style="font-family:Papyrus; font-size:4em;">ENAMORADO!</span>
