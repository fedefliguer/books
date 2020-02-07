_[Statistical Rethinking: A Bayesian Course with Examples in R and Stan. Richard McElreath](https://github.com/rmcelreath/statrethinking_winter2019)_

## 0. Prefacio

* Este libro busca ayudar a aumentar el conocimiento y la confianza en el modelado estadístico. Se entiende como un andamio, uno que permitirá construir el muro de la materia. En este proceso, se realiza trabajo 'inconveniente' como el paso a paso de algunos algoritmos que luego serán calculados automáticamente.
* El libro busca que el lector esté listo para intentar hacer inferencia estadística sin p-valores.
* El libro cuenta con cuadros 'rethinking' (aluden a conexiones con otros enfoques, proporcionan antecedentes históricos o llaman
malentendidos comunes) y cuadros 'overthinking' (proporcionan más detalles de explicaciones de código o matemáticas).

install.packages(c("rstan","coda","mvtnorm","devtools"))
library(devtools)
devtools::install_github("rmcelreath/rethinking")
