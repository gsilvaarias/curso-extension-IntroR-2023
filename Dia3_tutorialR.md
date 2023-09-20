---
title: "Estadistica en R"
date: "20/09/2023"
output: html_document

---
### Indice

- [Conceptos clave](#conceptos)
<<<<<<< HEAD
- [Estadistica Descriptiva](#estadistica_descriptiva)
- [Medidas de tendencia central](#Medidas_de_tendencia_central)
- [Moda](#Moda)
- [Media](#Media)
- [Mediana](#Mediana)
- [Uso de Trim](#Aplicacion_de_la_opcion_Trim)
- [Con datos faltantes](#Aplicacion_de_la_opcion_NA)
  - [Ejemplo](#Ejemplo_NA)
- [Medidas de dispersión](#Medidas_de_dispersion)
- [Rango](#Rango)
- [Variancia](#Variancia)
- [Desviación estandar](#Desviacion_estandar)
  - [Ejercicios](#Ejercicio_sd)
- [Prueba t](#Prueba_t)
  - [Ejercicio](#Ejercicio_t)
- [Regresión lineal](#Regresion_lineal)
- [Función lm](#Funcion_lm)
- [Función predict](#Funcion_predict)
  - [Ejercicio](#Ejercicio_pre)
- [Predicciones](#Hacer_predicciones)
- [Distribuición normal](#Distribuicion_normal)
- [Chi cuadrado](#Chi_cuadrado)
  - [Ejemplo](#Ejemplo_chi)
  - [Ejercicio](#Ejercicio_chi)
- [Coeficientes de correlación](#Coeficientes_correlacion)
  - [Ejemplo](#Ejemplo_cc)
  - [Valores NA](#Valores_NA)
  - [Ejercicio coeficiente correlación](#Ejercicio)
- [Escribiendo funciones propias](#funciones_propias)
=======
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



>>>>>>> refs/remotes/origin/main

# Dia 3 - Estadisitca en R

# Conceptos clave <a name = "conceptos"></a>
La estadistica es la disciplina que estudia la variabilidad, recolección, organización, análisis, interpretación y presentación de los datos, así como el proceso aleatorio que los genera siguiendo las leyes de la probabilidad.

Puede clasificarse en dos tipos, descriptiva e inferencial. La estad?stica descriptiva es la metodologia que se emplea para caracterizar un conjunto de datos. Sin embargo, no podemos extraer conclusiones debido a la variabilidad de las muestras. La estadistica inferencial complementa a la descriptiva permitiendo sacar conclusiones extrapolables a la poblacion gracias al empleo de metodos probabilisticos.

<<<<<<< HEAD
## Estadistica  descriptiva <a name = "estadistica_descriptiva"></a>
Es una disciplina que se encarga de recoger, almacenar, ordenar, realizar tablas o gráficos y calcular parámetros básicos sobre el conjunto de datos.

## Medidas de tendencia central <a name = "Medidas_de_tendencia_central"></a>
=======
# Estadistica  descriptiva <a name = "estadistica descriptiva"></a>
Es una disciplina que se encarga de recoger, almacenar, ordenar, realizar tablas o gráficos y calcular parámetros básicos sobre el conjunto de datos.

# Medidas de tendencia central <a name = "Medidas de tendencia central"></a>
>>>>>>> refs/remotes/origin/main
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
<<<<<<< HEAD

Para conocer  tamaño de la muestra empleamos la función `length()`
=======
\begin{itemize}
    \item Para conocer  tamaño de la muestra empleamos la funcion length()
\end{itemize}
>>>>>>> refs/remotes/origin/main

```{r presures, echo=FALSE}
?length
```
```{r presures, echo=FALSE}
length(x)
```

<<<<<<< HEAD
Una de las formas para determinar la moda es usando la función `mfv()`, instala el paquete "modeest" y lo cargue
=======
Para determinar la moda, podemos usar la funcion mfv(). Para esto, debes intalar el paquete "modeest" y cargarlo:

>>>>>>> refs/remotes/origin/main
```{r pressure, echo=FALSE}
install.packages("modeest")  #Comando para instalar el paquete "modeest"
library ("modeest")          #Comando para cargar el paquete "modeest"
```

Calcular la moda
```{r pressure, echo=FALSE}
mfv(x)
```
<<<<<<< HEAD
Para obtener la media o promedio de los datos utilizamos `mean()`
=======
Para obtener la media o promedio de los datos utilizamos la función mean()

>>>>>>> refs/remotes/origin/main
```{r pressure, echo=FALSE}
?mean()  
```
```{r pressure, echo=FALSE}
mean(x)  
```

## Aplicación de la opción Trim <a name = "Aplicacion_de_la_opcion_Trim"></a>
Cuando se suministra el parámetro trim, los valores del vector se ordenan y, a continuación, se elimina el numero necesario de observaciones del calculo de la media.

Cuando trim = 0.3, se eliminarán 3 valores de cada extremo de los cálculos para hallar la media.

En este caso, el vector ordenado es (-21, -5, 2, 3, 4.2, 7, 8, 12, 18, 54) y los valores eliminados del vector para calcular la media son (-21,-5,2) desde la izquierda y (12,18,54) desde la derecha.

- Crear un vector
```{r pressure, echo=FALSE}
x <- c(12,7,3,4.2,18,2,54,-21,8,-5)
```

- Encontrar la media
```{r pressure, echo=FALSE}
result.mean <-  mean(x,trim = 0.3)
```

## Aplicación de la opción NA <a name = "Aplicacion_de_la_opcion NA"></a>

Si faltan valores, la función media devuelve NA.

Para eliminar los valores que faltan del calculo, utilizar `na.rm = TRUE`, lo que significa eliminar los valores NA.

### Ejemplo <a name = "Ejemplo"></a>
Revisemos un ejemplo:

- Agregar valor NA en la posición 11 del vector x

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
result.mean <-  mean(x, na.rm = TRUE)
print(result.mean)
```

- La mediana podemos determinarla con la función `median()`

```{r pressure, echo=FALSE}
?median()
```
```{r pressure, echo=FALSE}
median(x)  
```

<<<<<<< HEAD
## Medidas de dispersion <a name = "Medidas_de_disperion"></a>
=======
# Medidas de dispersion <a name = "Medidas de disperion"></a>
>>>>>>> refs/remotes/origin/main
Las medidas de dispersión tratan, a través del cálculo de diferentes fórmulas, de arrojar un valor numérico que ofrezca información sobre el grado de variabilidad de una variable.

## Rango <a name = "Rango"></a>

El rango, el valor máximo y mínimo, la variabilidad y la desviación estándar son algunas de las medidas que empleadas habitualmente para describir la variabilidad de la muestra.
-El rango se usa para conocer la cobertura de nuestros datos, siendo la medida del esparcimiento entre el valor máximo y mínimo de nuestra muestra.

<<<<<<< HEAD
# Varianza <a name = "Variancia"></a>

-La varianza representa la variabilidad de una serie de datos respecto a su media.

# Desviación estándar <a name = "Desviacion_estandar"></a>
=======
## Varianza <a name = "Varianza"></a>

-La varianza representa la variabilidad de una serie de datos respecto a su media. 

## Desviacion estandar <a name = "Desviacion estandar"></a>
>>>>>>> refs/remotes/origin/main

-La desviación estándar es la raáz cuadrada del promedio de las distancias al cuadrado que van desde las observaciones a la media, es decir, la raíz cuadrada de la varianza.

Para determinar el rango en e cual se dispersa nuestra muestra, utilizamos la función `range()`

```{r pressure, echo=FALSE}

```

El rango se ve muy afectado por los valores máximos y mínimos. Para resolver este problema se utilizan los Quantiles (cuartiles, deciles, percentiles), que son medidas de localización, que tienen como función informar del valor de la variable que ocupara la posición (en tanto por cien) que nos interese respecto a todo el conjunto de datos. Es el resultado de dividir los datos en fracciones de igual tamaño. Nos ayudan a ver la concentración de datos, dependiendo de los parámetros de la función.

Para determinar cuantiles de la muestra utilizamos la función `quantile()`

```{r pressure, echo=FALSE}

```
utiliza la función `quantile()` y elimines los NA

```{r pressure, echo=FALSE}

```

variando el  valor de probabilidad podemos obtener cuartiles, deciles, percentiles. Por ejemplo:

```{r pressure, echo=FALSE}
quantile(x, probs=c(0, 0.2, 0.4, 0.6, 0.8, 1))  
```

Calculamos la varianza utilizando la función `var()`

```{r pressure, echo=FALSE}

```

Calculamos la desviación estándar usando la función `sd()`

```{r pressure, echo=FALSE}

```

Otra forma de calcular la desviación estandar, seria la siguiente:

```{r pressure, echo=FALSE}
sqrt_vec <- sqrt(var(x))  
sqrt_vec
```

### Ejercicios <a name = "Ejercicios"></a>
Ahora hagamos un ejercicio

**Cargar los datos**

Primero cargamos el set de datos desde el directorio de trabajo. Utilizamos `header=TRUE` para indicar que la primera fila del archivo corresponde al nombre de las variables.

```{r pressure, echo=FALSE}
penguins<-read.table("./CursoR_2023/Datos/penguins_matrix.txt", header=T)
penguins
```
Vamos a seleccionar una columna (bill_length_mm)

```{r presure, echo=FALSE}
bill_length <- penguins$bill_length_mm
```

¿Cual es el dato que más se repite?
¿Cual es el promedio de la muestra?
¿Cual es el valor central?
Calcular las medidas de dispersion

# Prueba t <a name = "Prueba_t"></a>

¿Que debemos hacer si queremos comparar la media de dos muestras?

Se utiliza la prueba t

Extraigamos los datos correspondientes a la longitud de la aleta y la masa corporal

```{r pressure, echo=FALSE}

```

## Continuamos con nuestra prueba t

Para realizar este tipo de prueba se puede usar la función `t.test`

Los argumentos a definir dentro de `t.test` para hacer la prueba son:
- x : vector numerico con los datos
- Alternative : tipo de hipótesis alterna. Los valores disponibles son "two.sided" cuando la hipótesis alterna es, "less" para el caso < y "greater" para el caso >.
- mu : valor de referencia de la prueba
- conf.level : nivel de confianza para reportar el intervalo de confianza asociado (opcional).

```{r pressure, echo=FALSE}
?t.test
```

Para una variable, realizar con "flipper_length"

```{r pressure, echo=FALSE}

```

Indicando el valor de la media
```{r pressure, echo=FALSE}
t.test(flipper_length, mu=200)
```

Indicando la hipótesis alternativa
```{r pressure, echo=FALSE}
t.test(flipper_length, mu=200, alternative="greater")
```

### Ejercicio <a name = "Ejercicio_t"></a>
Calcula el t-test para la variable "body_mass_g"

Entre dos variables, realizarlo para "flipper_length" y "body_mass"

```{r pressure, echo=FALSE}

```

# Regresión lineal <a name = "Regresion_lineal"></a>

El análisis de regresión es una herramienta estadística muy utilizada para establecer un modelo de relación entre dos variables. Una de estas variables se denomina variable predictora cuyo valor se obtiene mediante experimentos. La otra variable se denomina variable de respuesta cuyo valor se deriva de la variable predictora.

En la regresión lineal, estas dos variables se relacionan mediante una ecuación, en la que el exponente (potencia) de ambas variables es 1. Matemáticamente, una relación lineal representa una linea recta cuando se representa graficamente. Una relación no lineal en la que el exponente de cualquier variable no es igual a 1 crea una curva.

La ecuación matemática general para una regresión lineal es:

y = ax + b

y es la variable de respuesta.

x es la variable predictiva.

a y b son constantes denominadas coeficientes.

### Pasos para establecer una regresión
Un ejemplo sencillo de regresión es predecir el peso de una persona cuando se conoce su altura. Para ello necesitamos tener la relación entre la altura y el peso de una persona.

Los pasos para crear la relación son:
- Realizar el experimento de recoger una muestra de valores observados de altura y peso correspondiente.
- Crear un modelo de relación utilizando la función `lm()` en R.
- Hallar los coeficientes del modelo creado y crear la ecuación matemática con ellos.
- Obtener un resumen del modelo de relación para conocer el error medio en la predicción. También se denominan residuos.

Para predecir el peso de las nuevas personas, utilizar la función `predict()` en R.

### Datos de entrada
A continuación se presentan los datos de muestra que representan las observaciones

Valores de altura:

```{r pressure, echo=FALSE}
alt <- c(151, 174, 138, 186, 128, 136, 179, 163, 152, 131)
```

Valores de peso:
```{r pressure, echo=FALSE}
peso <- c(63, 81, 56, 91, 47, 57, 76, 72, 62, 48)
```

# Función `lm()` <a name = "Funcion_lm"></a>

Esta función crea el modelo de relación entre el predictor y la variable de respuesta.

La sintaxis básica de la función `lm()` en regresión lineal es
`lm(fórmula,datos)`
A continuación se describen los parámetros utilizados:
- formula es un símbolo que presenta la relación entre x e y.
- datos es el vector sobre el que se aplicara la formula.

Crear el modelo de relación y obtener los coeficientes
Aplicar la función `lm()` para peso~alt

```{r pressure, echo=FALSE}

```

# Función predict() <a name = "Funcion_predict"></a>

La sintaxis básica de `predict()` en regresión lineal es:
`predict(objeto, nuevos_datos)`
A continuación se describen los parámetros utilizados:
- objeto es la formula ya creada mediante la función `lm()`.
- nuevos_datos es el vector que contiene el nuevo valor de la variable predictora.
- El vector predictor es altura
- La variable de respuesta es peso

Hallar el peso de una persona de estatura 170 cm
```{r pressure, echo=FALSE}
a <- data.frame(alt = 170)
result <-  predict(relation,a)
result
```

### Ejercicio <a name = "Ejercicio_predict"></a>

Calculo de modelo lineal

Para este ejercicio vamos a crear un data frame combinando las variables "flipper_length_mm" y "body_mass_g"

```{r pressure, echo=FALSE}

```

Con el fin de conocer las relaciones existentes entre las variables podemos representar una matriz de diagramas de dispersion.

```{r pressure, echo=FALSE}

```

Ajuste del modelo lineal "flipper_length" "body_mass"

```{r pressure, echo=FALSE}

```

## Hacer predicciones <a name = "Hacer_predicciones"></a>

Crear un data frame con nuevos valores
```{r pressure, echo=FALSE}
nuevas_medidas <- data.frame("body_mass" = c(2665,2690,6325,6400,6339,2676))
```

Predicción de la longitud de las aletas

```{r pressure, echo=FALSE}

```

## Distribución normal <a name = "Distribucion_normal"></a>

En una colección aleatoria de datos procedentes de fuentes independientes, suele observarse que la distribución de los datos es normal. Es decir, al trazar un gráfico con el valor de la variable en el eje horizontal y el recuento de los valores en el eje vertical obtenemos una curva en forma de campana. El centro de la curva representa la media del conjunto de datos. En el gráfico, el cincuenta por ciento de los valores se situan a la izquierda de la media y el otro cincuenta por ciento a la derecha del gráfico.

R tiene cuatro funciones incorporadas para generar la distribución normal:

dnorm(x, media, sd) : guía de densidad
pnorm(x, media, sd) : presenta la función de distribuición
qnorm(p, media, sd) : presenta la función de quantil
rnorm(n, media, sd) : presenta desviaciones aleatorias

A continuación se describen los parámetros utilizados en las funciones descritas:
- x es un vector de números.
- p es un vector de probabilidades.
- n es el numero de observaciones (tamaño de la muestra).
- media es el valor medio de los datos de la muestra. Su valor por defecto es cero.
- sd es la desviación estandar. Su valor por defecto es 1.

### dnorm()
Esta función da la altura de la distribución de probabilidad en cada punto para una media y una desviación típica.

Crear una secuencia de numeros entre -10 y 10 incrementando de 0 en 0.
```{r pressure, echo=FALSE}
x <- seq(-10, 10, by = .1)
x
```

Elige la media como 2,5 y la desviación típica como 0,5.
```{r pressure, echo=FALSE}

```

# Prueba Chi Cuadrado <a name = "Chi_cuadrado"></a>
En estadística y estadística aplicada se denomina prueba χ² (pronunciado como «ji al cuadrado»1​ y a veces como «chi al cuadrado») a cualquier prueba en la que el estadístico utilizado sigue una distribución χ² si la hipótesis nula es cierta.

Para crear una prueba chi-cuadrado en R es:
`chisq.test(datos)`
A continuación se describen los parámetros utilizados:
- datos son los datos en forma de tabla que contienen el valor de recuento de las variables en la observación.

### Ejemplo <a name = "Ejemplo_chi"></a>

Tomaremos los valores del dataset "iris"
```{r presures, echo=FALSE}

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

# Coeficientes de correlación <a name = "Coeficientes_de_correlacion"></a>

El coeficiente de correlación de Pearson es una prueba que mide la relación estadística entre dos variables continuas. Si la asociación entre los elementos no es lineal, entonces el coeficiente no se encuentra representado adecuadamente.
El coeficiente de correlación puede tomar un rango de valores de +1 a -1. Un valor de 0 indica que no hay asociación entre las dos variables. Un valor mayor que 0 indica una asociación positiva. Es decir, a medida que aumenta el valor de una variable, también lo hace el valor de la otra. Un valor menor que 0 indica una asociación negativa, es decir, a medida que aumenta el valor de una variable, el valor de la otra disminuye.

Para realizar la prueba de Coeficiente de Correlación de Pearson se usa la función `cor.test()`.
```{r pressure, echo=FALSE}

```

# Ejemplo  <a name = "Ejemplo_cor"></a>
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

## Saber si existen valores NA   <a name = "valores_NA"></a>

```{r pressure, echo=FALSE}
which(is.na(penguins$flipper_length_mm))
```

# Ejercicio  <a name = "Ejercicio_cc"></a>

Correlacionar dos variables "bill_length_mm" y "bill_depth_mm"
```{r pressure, echo=FALSE}

```
# Escribiendo funciones propias <a name = "funciones_propias"></a>
(Material utilizado de: https://es.r4ds.hadley.nz/19-functions.html)

Una de las mejores maneras de lograr tener mayor alcance haciendo ciencia de datos es escribir funciones. Las funciones te permitirán automatizar algunas tareas comunes de una forma más poderosa y general que copiar-y-pegar. Escribir funciones tiene tres grandes ventajas sobre copiar-y-pegar:
- Puedes dar a la función un nombre evocador que hará tu código más fácil de entender.
- A medida que cambien los requerimientos, solo necesitarás cambiar tu código en un solo lugar, en vez de en varios lugares.
- Eliminas las probabilidades de errores accidentales cuando copias y pegas (por ej., al actualizar el nombre de una variable en un lugar, pero no en otro).

Deberías considerar escribir una función cuando has copiado y pegado un bloque de código más de dos veces (es decir, ahora tienes tres copias del mismo). Por ejemplo:

```
df <- data.frame(
 a = rnorm(10),
 b = rnorm(10),
 c = rnorm(10),
 d = rnorm(10)
)

df$a <- (df$a - min(df$a, na.rm = TRUE)) /
 (max(df$a, na.rm = TRUE) - min(df$a, na.rm = TRUE))
df$b <- (df$b - min(df$b, na.rm = TRUE)) /
 (max(df$b, na.rm = TRUE) - min(df$a, na.rm = TRUE))
df$c <- (df$c - min(df$c, na.rm = TRUE)) /
 (max(df$c, na.rm = TRUE) - min(df$c, na.rm = TRUE))
df$d <- (df$d - min(df$d, na.rm = TRUE)) /
 (max(df$d, na.rm = TRUE) - min(df$d, na.rm = TRUE))
```
Es posible que hayas podido descifrar que lo que hace es reescalar cada columna para que tenga un rango de 0 a 1. Pero **¿has encontrado el error?** Ocurrió copiando-y-pegando el código para `df$b`: Hemos olvidado de cambiar `a` a `b`. Extraer el código repetido en una función es una buena idea, ya que previene que cometas errores como este.

Para escribir una función, lo primero que necesitas hacer es analizar el código. ¿Cuantos inputs tiene?

Para hacer los inputs más claros, es buena idea reescribir el código usando variables temporales con nombres generales. Acá el código requiere un solo vector numérico, por lo que lo llamaremos `x`:
```
x <- df$a
(x - min(x, na.rm = TRUE)) / (max(x, na.rm = TRUE) - min(x, na.rm = TRUE))
```

Hay algo de duplicación en este código. Estamos computando el rango de datos tres veces, así que tiene sentido hacerlo en un solo paso:
```
rng <- range(x, na.rm = TRUE)
(x - rng[1]) / (rng[2] - rng[1])
```

Ahora que hemos simplificado el código y chequeado de que aún funciona, podemos convertirlo en una función:
```
rescale01 <- function(x) {
 rng <- range(x, na.rm = TRUE)
 (x - rng[1]) / (rng[2] - rng[1])
}

rescale01(c(1,2,3,NA,5))
```

Hay tres pasos claves para crear una función nueva:
1. Necesitas elegir un **nombre** para la función. Aquí hemos usado rescale01, ya que esta función reescala (rescale, en inglés) un vector para que se ubique entre 0 y 1.
2. Listar los inputs, o **argumentos**, de la función dentro de function. Aquí solo tenemos un argumento. Si tenemos más, la llamada se vería como `function(x, y, z)`.
3. Situar el código que has creado en el **cuerpo** de una función, un bloque de `{...}` que sigue inmediatamente a `function(...)`.

**Ten en cuenta el proceso general:** solo hemos creado la función después de darnos cuenta cómo funciona con un input simple. Es más fácil empezar con código que funciona y luego convertirlo en una función; es más difícil crear la función y luego tratar que funcione.

En este punto es una buena idea chequear tu función con algunos inputs diferentes.

>> Ejercicio 1:
>> - Prueba la función con inputs diferentes.
>> - Calcule para las diferentes columnas del df creado.

>> Ejercicio 2: Haga una función que retorne el valor mínimo y máximo de una variable (vector, columna...)
