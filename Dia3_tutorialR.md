---
title: "Estadistica en R"
date: "20/09/2023"
output: html_document

---
### Indice 

- [Conceptos clave](#conceptos)
- [Estadistica](#estadistica descriptiva)
- [Estadistica](#Medidas de tendencia central)
- [Estadistica](#Moda)
- [Estadistica](#Media)
- [Estadistica](#Mediana)
- [Estadistica](#Aplicacion de la opcion Trim)
- [Estadistica](#Aplicacion de la opcion NA)
- [Estadistica](#Ejemplo)
- [Estadistica](#Medidas de dispersion)
- [Estadistica](#Rango)
- [Estadistica](#Varianza)
- [Estadistica](#Desviacion estandar)
- [Estadistica](#Ejercicios)
- [Estadistica](#Prueba t)
- [Estadistica](#Ejercicio)
- [Estadistica](#Regresion lineal)
- [Estadistica](#Funcion lm)
- [Estadistica](#Funcion predict)
- [Estadistica](#Ejercicio)
- [Estadistica](#Hacer predicciones)
- [Estadistica](#Distribuicion normal)
- [Estadistica](#Chi cuadrado)
- [Estadistica](#Ejemplo)
- [Estadistica](#Ejercicio)
- [Estadistica](#Coeficientes de correlacion)
- [Estadistica](#Ejemplo)
- [Estadistica](#Valores NA)
- [Estadistica](#Ejercicio)




# Dia 3 - Estadisitca en R

# Conceptos clave <a name = "conceptos"></a>
La estadistica es la disciplina que estudia la variabilidad, recolección, organización, análisis, interpretación y presentación de los datos, así como el proceso aleatorio que los genera siguiendo las leyes de la probabilidad.

Puede clasificarse en dos tipos, descriptiva e inferencial. La estad?stica descriptiva es la metodologia que se emplea para caracterizar un conjunto de datos. Sin embargo, no podemos extraer conclusiones debido a la variabilidad de las muestras. La estadistica inferencial complementa a la descriptiva permitiendo sacar conclusiones extrapolables a la poblacion gracias al empleo de metodos probabilisticos.

# Estadistica  descriptiva <a name = "estadistica descriptiva"></a>
Es una disciplina que se encarga de recoger, almacenar, ordenar, realizar tablas o gráficos y calcular parámetros básicos sobre el conjunto de datos.

# Medidas de tendencia central <a name = "Medidas de tendencia central"></a>
Es un número ubicado hacia el centro de la distribución de los valores de una serie de observaciones. Las medidas de tendencia central mas utilizadas son:
            -la moda
            -la media
            -la mediana

# Moda <a name = "Moda"></a>           
La moda es el valor que tiene el mayor numero de ocurrencias en un conjunto de datos.

# Media <a name = "Media"></a>
La media representa la distribucion equitativa de los datos si la suma total se repartiera por igual. Se calcula tomando la suma de los valores y dividiendola por el numero de valores de una serie de datos. 

# Mediana <a name = "Mediana"></a>
La mediana es el valor central si todos los datos se ordenan de menor a mayor. El valor mas medio de una serie de datos se denomina mediana. 

# Ejemplo - Medidas de tendencia central></a>
Comencemos definiendo una variable que contiene una secuencia de 34 numeros ¡Esta sera nuestra muestra!. Recuerda que para ingresar la secuencia en R debemos crear un vector, así:

```{r pressure, echo=FALSE}
x<-c(125, 126, 127, 128, 128, 129, 130, 131, 149, 132, 133, 134, 135, 136, 137, 138, 139, 140, 114, 142, 149, 143, 144, 145, 146, 147, 148, 133, 133, 133, 149, 150, 139, 152)
x
```
\begin{itemize}
    \item Para conocer  tamaño de la muestra empleamos la funcion length()
\end{itemize}

```{r presures, echo=FALSE}
?length
```
```{r presures, echo=FALSE}
length(x)
```

Para determinar la moda, podemos usar la funcion mfv(). Para esto, debes intalar el paquete "modeest" y cargarlo:

```{r pressure, echo=FALSE}
install.packages("modeest")  #Comando para instalar el paquete "modeest"
library ("modeest")          #Comando para cargar el paquete "modeest"
```

Calcular la moda
```{r pressure, echo=FALSE}
mfv(x)
```
Para obtener la media o promedio de los datos utilizamos la función mean()

```{r pressure, echo=FALSE}
?mean()  
```
```{r pressure, echo=FALSE}
mean(x)  
```

## Aplicación de la opcion Trim <a name = "Aplicacion de la opcion Trim"></a>
Cuando se suministra el parametro trim, los valores del vector se ordenan y, a continuacion, se elimina el numero necesario de observaciones del calculo de la media.

Cuando trim = 0.3, se eliminarán 3 valores de cada extremo de los calculos para hallar la media.

En este caso, el vector ordenado es (-21, -5, 2, 3, 4.2, 7, 8, 12, 18, 54) y los valores eliminados del vector para calcular la media son (-21,-5,2) desde la izquierda y (12,18,54) desde la derecha.

- Crear un vector
```{r pressure, echo=FALSE}
x <- c(12,7,3,4.2,18,2,54,-21,8,-5)
```

- Encontrar la media
```{r pressure, echo=FALSE}
result.mean <-  mean(x,trim = 0.3)
```

## Aplicacion de la opcion NA <a name = "Aplicacion de la opcion NA"></a>

Si faltan valores, la función media devuelve NA.

Para eliminar los valores que faltan del calculo, utilizar na.rm = TRUE, lo que significa eliminar los valores NA.

# Ejemplo <a name = "Ejemplo"></a>
Revisemos un ejemplo:

- Agregar valor NA en la posicion 11 de vector x

```{r pressure, echo=FALSE}
x[11] <- NA
```
```{r pressure, echo=FALSE}
x
```

- Encontremos la media
```{r pressure, echo=FALSE}
result.mean <-  mean(x)
print(result.mean)
```

- Encontremos la media quitando los valores NA

```{r pressure, echo=FALSE}
result.mean <-  mean(x,na.rm = TRUE)
print(result.mean)
```

- La mediana podemos determinarla con la funcion median()

```{r pressure, echo=FALSE}
?median()
```
```{r pressure, echo=FALSE}
median(x)  
```

# Medidas de dispersion <a name = "Medidas de disperion"></a>
Las medidas de dispersión tratan, a través del cálculo de diferentes fórmulas, de arrojar un valor numérico que ofrezca información sobre el grado de variabilidad de una variable.

## Rango <a name = "Rango"></a>

El rango, el valor mximo y minimo, la variabilidad y la desviacion estandar son algunas de las medidas que empleadas habitualmente para describir la variabilidad de la muestra.
-El rango se usa para conocer la cobertura de nuestros datos, siendo la medida del esparcimiento entre el valor maximo y minimo de nuestra muestra. 

## Varianza <a name = "Varianza"></a>

-La varianza representa la variabilidad de una serie de datos respecto a su media. 

## Desviacion estandar <a name = "Desviacion estandar"></a>

-La desviacion estandar es la raiz cuadrada del promedio de las distancias al cuadrado que van desde las observaciones a la media, es decir, la raiz cuadrada de la varianza.


Para determinar el rango en e cual se dispersa nuestra muestra, utilizamos la funcion range()

```{r pressure, echo=FALSE}
 
```

El rango se ve muy afectado por los valores maximos y minimos. Para resolver este problema se utilizan los Quantiles (cuartiles, deciles, percentiles), que son medidas de localizacion, que tienen como funcion informar del valor de la variable que ocupara la posicion (en tanto por cien) que nos interese respecto a todo el conjunto de datos. Es el resultado de dividir los datos en fracciones de igual tamaño. Nos ayudan a ver la concentracion de datos, dependiendo de los parametros de la funcion.

Para determinar cuantiles de la muestra utilizamos la funcion quantile()

```{r pressure, echo=FALSE}

```
utiliza la funcion quantile () y elimines los N.A

```{r pressure, echo=FALSE}

```

variando el  valor de probabilidad podemos obtener cuartiles, deciles, percentiles. Por ejemplo: 

```{r pressure, echo=FALSE}
quantile(x, probs=c(0, 0.2, 0.4, 0.6, 0.8, 1))  
```

Calculamos la varianza utilizando la funcion var()

```{r pressure, echo=FALSE}

```

Calculamos la desviacion estandar usando la funcion sd()

```{r pressure, echo=FALSE}
 
```

Otra forma de calcular la desviacion estandar, seria la siguiente:

```{r pressure, echo=FALSE}
sqrt_vec <- sqrt(var(x))  
sqrt_vec
```

# Ejercicios <a name = "Ejercicios"></a>
Ahora hagamos un ejercicio


## Cargar los datos

Primero Cargamos el set de datos desde el directorio de trabajo. Utilizamos header=TRUE para indicar que la primera fila del archivo corresponde al nombre de las variables.

```{r pressure, echo=FALSE}
penguins<-read.table("./CursoR_2023/Datos/penguins_matrix.txt", header=T)
penguins
```
Vamos a seleccionar una columna (bill_length_mm)

con el comado names(penguins) mostramos el nombre de cada variable, correspondiente a los headers de cada columna

```{r pressure, echo=FALSE}

```

```{r presure, echo=FALSE}
bill_length <- penguins$bill_length_mm
```

¿Cual es el dato que mas se repite?
¿Cual es el promedio de la muestra?
¿Cual es el valor central?
Calcular las medidas de dispersion


# Prueba t <a name = "Prueba t"></a>

¿Que debemos hacer si queremos comparar la media de dos muestras? 

Se utiliza la prueba t

Extraigamos los datos correspondientes a la longitud de la aleta y la masa corporal

```{r pressure, echo=FALSE}

```

## Continuamos con nuestra prueba t

Para realizar este tipo de prueba se puede usar la funcion "t.test"

Los argumentos a definir dentro de "t.test" para hacer la prueba son:

x : vector numerico con los datos
Alternative : tipo de hipotesis alterna. Los valores disponibles son "two.sided" cuando la hipotesis alterna es, "less" para el caso < y "greater" para el caso >.
mu : valor de referencia de la prueba
conf.level : nivel de confianza para reportar el intervalo de confianza asociado (opcional).
 

```{r pressure, echo=FALSE}
?t.test
```

Para una varible realizar con "flipper_length"

```{r pressure, echo=FALSE}

```

Indicando el valor de la media

```{r pressure, echo=FALSE}
t.test(flipper_length, mu=200)
```

Indicando la hipotesis alternativa
```{r pressure, echo=FALSE}
t.test(flipper_length, mu=200, alternative="greater")
```

# Ejercicio <a name = "Ejercicio"></a>
Calcula el t-test para la variable "body_mass_g"


Entre dos variables, realizarlo para "flipper_length" "body_mass"

```{r pressure, echo=FALSE}

```

Como establecer un modelo lineal?

## Regresion lineal <a name = "Regresion lineal"></a>

El analisis de regresion es una herramienta estadistica muy utilizada para establecer un modelo de relacion entre dos variables. Una de estas variables se denomina variable predictora cuyo valor se obtiene mediante experimentos. La otra variable se denomina variable de respuesta cuyo valor se deriva de la variable predictora.

En la regresion lineal, estas dos variables se relacionan mediante una ecuacion, en la que el exponente (potencia) de ambas variables es 1. Matemáticamente, una relación lineal representa una linea recta cuando se representa graficamente. Una relacion no lineal en la que el exponente de cualquier variable no es igual a 1 crea una curva.

La ecuación matemática general para una regresión lineal es:

y = ax + b

y es la variable de respuesta.

x es la variable predictiva.

a y b son constantes denominadas coeficientes.


# Pasos para establecer una regresion
Un ejemplo sencillo de regresion es predecir el peso de una persona cuando se conoce su altura. Para ello necesitamos tener la relacion entre la altura y el peso de una persona.

Los pasos para crear la relacion son:

- Realizar el experimento de recoger una muestra de valores observados de altura y peso correspondiente.

- Crear un modelo de relación utilizando las funciones lm() en R.

- Hallar los coeficientes del modelo creado y crear la ecuacion matematica con ellos.

- Obtener un resumen del modelo de relacion para conocer el error medio en la prediccion. También se denominan residuos.

Para predecir el peso de las nuevas personas, utilizar la funcion predict() en R.


# Datos de entrada
A continuacion se presentan los datos de muestra que representan las observaciones

Valores de altura

```{r pressure, echo=FALSE}
alt <- c(151, 174, 138, 186, 128, 136, 179, 163, 152, 131)
```

Valores de peso

```{r pressure, echo=FALSE}
peso <- c(63, 81, 56, 91, 47, 57, 76, 72, 62, 48)
```

# Funcion lm() <a name = "Funcion lm"></a>

Esta funcion crea el modelo de relacion entre el predictor y la variable de respuesta.

La sintaxis básica de la función lm() en regresión lineal es

lm(fórmula,datos)
A continuacion se describen los parametros utilizados:

- formula es un simbolo que presenta la relacion entre x e y.

- datos es el vector sobre el que se aplicara la formula.


Crear el modelo de relación y obtener los coeficientes

Aplicar la función lm() peso~alt

```{r pressure, echo=FALSE}

```

# Función predict() <a name = "Funcion predict"></a>

La sintaxis basica de predict() en regresion lineal es:

predict(objeto, nuevos_datos)

A continuación se describen los parámetros utilizados:

objeto es la formula ya creada mediante la funcion lm().

nuevos_datos es el vector que contiene el nuevo valor de la variable predictora.

-El vector predictor es altura
-La variable de respuesta es peso

Hallar el peso de una persona de estatura 170 cm

```{r pressure, echo=FALSE}
a <- data.frame(alt = 170)
result <-  predict(relation,a)
result
```

# Ejercicio <a name = "Ejercicio"></a>

Calculo de modelo lineal

Para este ejercicio vamos a crear un dataframe combinando las variables "flipper_length_mm" y "body_mass_g" 

```{r pressure, echo=FALSE}

```

Con el fin de conocer las relaciones existentes entre las variables podemos representar una matriz de diagramas de dispersion. 

```{r pressure, echo=FALSE}

```

Ajuste del modelo lineal "flipper_length" "body_mass"

```{r pressure, echo=FALSE}

```

## Hacer predicciones <a name = "Hacer predicciones"></a>

Crear un dataframe con nuevos valores
```{r pressure, echo=FALSE}
nuevas_medidas <- data.frame("body_mass" = c(2665,2690,6325,6400,6339,2676))
```

Prediccion de la longitud de las aletas

```{r pressure, echo=FALSE}

```

## Distribucion normal <a name = "Distribucion normal"></a>

En una coleccion aleatoria de datos procedentes de fuentes independientes, suele observarse que la distribucion de los datos es normal. Es decir, al trazar un grafico con el valor de la variable en el eje horizontal y el recuento de los valores en el eje vertical obtenemos una curva en forma de campana. El centro de la curva representa la media del conjunto de datos. En el grafico, el cincuenta por ciento de los valores se situan a la izquierda de la media y el otro cincuenta por ciento a la derecha del grafico. 

R tiene cuatro funciones incorporadas para generar la distribucion normal:

dnorm(x, media, sd) : guia de densidad
pnorm(x, media, sd) : presenta la funcion de distribuicion
qnorm(p, media, sd) : presenta la funcion de quantil
rnorm(n, media, sd) : presenta desviaciones aleatorias

A continuación se describen los parámetros utilizados en las funciones descritas

x es un vector de numeros.

p es un vector de probabilidades.

n es el numero de observaciones (tamaño de la muestra).

media es el valor medio de los datos de la muestra. Su valor por defecto es cero.

sd es la desviacion estandar. Su valor por defecto es 1.

# dnorm()
Esta función da la altura de la distribucion de probabilidad en cada punto para una media y una desviacion tipica.

- Crea una secuencia de numeros entre -10 y 10 incrementando de 0 en 0.
```{r pressure, echo=FALSE}
x <- seq(-10, 10, by = .1)
x
```

- Elige la media como 2,5 y la desviacion tipica como 0,5.
```{r pressure, echo=FALSE}

```

Como sabemos si nuestros datos estan correlacionados

## Prueba Chi Cuadrado <a name = "Chi cuadrado"></a>

En estadística y estadística aplicada se denomina prueba χ² (pronunciado como «ji al cuadrado»1​ y a veces como «chi al cuadrado») a cualquier prueba en la que el estadístico utilizado sigue una distribución χ² si la hipótesis nula es cierta.

Para crear una prueba chi-cuadrado en R es:

chisq.test(datos)
A continuación se describen los parametros utilizados:

- datos son los datos en forma de tabla que contienen el valor de recuento de las variables en la observacion.

# Ejemplo <a name = "Ejemplo"></a>

Tomaremos los valores del dataset "iris" 
```{r presures, echo=FALSE}

```
```

# Crear una base de datos a partir del conjunto de datos principales

```{r pressure, echo=FALSE}
setosa <- iris %>% filter(Species == "setosa")
setosa_sepal_data <- data.frame("Sepal_length"=setosa$Sepal.Length, "Sepal_weidth"=setosa$Sepal.Width)
setosa_sepal_data
```
 

# Realizar la prueba Chi-cuadrado
```{r pressure, echo=FALSE}
chisq.test(setosa_sepal_data)
``` 

# Ejercicio <a name = "Ejercicio"></a>
Calcular el chi cuadrado entre dos variables de set de datos penguins, retirando los datos N.A

```{r pressure, echo=FALSE}
chisq.test(na.omit(penguins$body_mass_g))
``` 

## Coeficientes de correlacion <a name = "Coeficientes de correlacion"></a>
## Test de correlacion

El coeficiente de Correlacion de Pearson es una prueba que mide la relaci?n estadistica entre dos variables continuas. Si la asociacion entre los elementos no es lineal, entonces el coeficiente no se encuentra representado adecuadamente.
El coeficiente de correlacion puede tomar un rango de valores de +1 a -1. Un valor de 0 indica que no hay asociacion entre las dos variables. Un valor mayor que 0 indica una asociacion positiva. Es decir, a medida que aumenta el valor de una variable, tambien lo hace el valor de la otra. Un valor menor que 0 indica una asociacion negativa, es decir, a medida que aumenta el valor de una variable, el valor de la otra disminuye.


Para realizar la prueba de Coeficiente de Correlacion de Pearson se usa la funcion cor.test()

```{r pressure, echo=FALSE}

```

# Ejemplo  <a name = "Ejemplo"></a>
A seguir algunos ejemplos

```{r pressure, echo=FALSE}
cor.test(penguins$flipper_length_mm, penguins$body_mass_g, method = "pearson", alternative = "greater")
```

Forma de acceder a los resultados
```{r pressure, echo=FALSE}
cor.test(penguins$flipper_length_mm, penguins$body_mass_g, method = "pearson", alternative = "greater")$estimate 
```

```{r pressure, echo=FALSE}
cor.test(penguins$flipper_length_mm, penguins$body_mass_g, method = "spearm", alternative = "greater")
```

```{r pressure, echo=FALSE}
cor.test(penguins$flipper_length_mm, penguins$body_mass_g, method = "kendall", alternative = "greater")
```

## Saber si existen valores NA   <a name = "valores NA"></a>

```{r pressure, echo=FALSE}
which(is.na(penguins$flipper_length_mm))
```

# Ejercicio   <a name = "Ejercicio"></a>

Correlacionar dos variables "bill_length_mm" y "bill_depth_mm"

```{r pressure, echo=FALSE}

```



This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

```

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

