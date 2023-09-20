---
title: "Estadística en R"
date: "20/09/2023"
output: html_document

---
### Indice

- [Conceptos clave](#conceptos)
- [Estadística Descriptiva](#estadística_descriptiva)
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


# Dia 3 - Estadística en R

# Conceptos clave <a name = "conceptos"></a>
La estadística es la disciplina que estudia la variabilidad, recolección, organización, análisis, interpretación y presentación de los datos, así como el proceso aleatorio que los genera siguiendo las leyes de la probabilidad.

Puede clasificarse en dos tipos, descriptiva e inferencial. La estad?stica descriptiva es la metodologia que se emplea para caracterizar un conjunto de datos. Sin embargo, no podemos extraer conclusiones debido a la variabilidad de las muestras. La estadística inferencial complementa a la descriptiva permitiendo sacar conclusiones extrapolables a la poblacion gracias al empleo de metodos probabilisticos.

# Estadística  descriptiva <a name = "estadística descriptiva"></a>
Es una disciplina que se encarga de recoger, almacenar, ordenar, realizar tablas o gráficos y calcular parámetros básicos sobre el conjunto de datos.

Comencemos definiendo una variable que contiene una secuencia de 34 numeros ¡Esta sera nuestra muestra!. Recuerda que para ingresar la secuencia en R debemos crear un vector, así:

```{r pressure, echo=FALSE}
x<-c(125, 126, 127, 128, 128, 129, 130, 131, 149, 132, 133, 134, 135, 136, 137, 138, 139, 140, 114, 142, 149, 143, 144, 145, 146, 147, 148, 133, 133, 133, 149, 150, 139, 152)
x
```
# Medidas de tendencia central <a name = "Medidas de tendencia central"></a>
Es un número ubicado hacia el centro de la distribución de los valores de una serie de observaciones. Las medidas de tendencia central mas utilizadas son:
            -la moda
            -la media
            -la mediana

# Moda <a name = "Moda"></a>           
La moda es el valor que tiene el mayor numero de ocurrencias en un conjunto de datos. Para determinar la moda, podemos usar la funcion mfv(). Para esto, primero debes intalar el paquete "modeest" y cargarlo:

```{r pressure, echo=FALSE}
install.packages("modeest")  #Comando para instalar el paquete "modeest"
library ("modeest")          #Comando para cargar el paquete "modeest"
```

Una vez hayas cargado el paquete "modeest" puedes calcular la moda así:
```{r pressure, echo=FALSE}
mfv(x)
```

# Media <a name = "Media"></a>
La media o promedio representa la distribucion equitativa de los datos si la suma total se repartiera por igual. Se calcula tomando la suma de los valores y dividiendola por el numero de valores de una serie de datos. 

Podemos calcular la media "manualmente", calculando la suma total de la muestra y dividiendo por su tamaño, como se indica a continuación:

Para conocer la suma total de la muestra, utilizamos la funcion sum()
```{r presures, echo=FALSE}
sum(x)
```
Para conocer  tamaño de la muestra empleamos la funcion length()
```{r presures, echo=FALSE}
length(x)
```
También se puede obtener la media de los datos utilizamos la función mean()

```{r pressure, echo=FALSE}
?mean()  
```
```{r pressure, echo=FALSE}
mean(x)  
```

## Aplicación del argumento Trim <a name = "Aplicacion de la opcion Trim"></a>
R tiene la capacidad de calcular la media recortada utilizando el argumento "trim". A través del argumento "trim", se especifica el porcentaje de valores que se deben recortar en cada extremo antes de calcular la media.

En este caso, si tenemos el vector ordenado es c(-21, -5, 2, 3, 4.2, 7, 8, 12, 18, 54), dependiendo del valor especificado en "trim", se pueden obtener los siguientes valores de promedio recortado: 

- Crear un vector
```{r pressure, echo=FALSE}
x1 <- c(-21, -5, 2, 3, 4.2, 7, 8, 12, 18, 54)  #Vector completo y ordenado
mean(x1)
x2 <- c(-5, 2, 3, 4.2, 7, 8, 12, 18)  # vector sin 2 valores extremos (un inferior - un superior)
mean(x2)
x3 <- c(2, 3, 4.2, 7, 8, 12)          # vector sin 4 valores extremos 
mean(x3)
x4 <- c(3, 4.2, 7, 8)                 # vector sin 6 valores extremos 
mean(x4)

mean(x1, trim=0.1)    #equivale al mean(x2)
mean(x1, trim=0.2)    #equivale al mean(x3)
mean(x1, trim=0.3)    #equivale al mean(x4)
```

## Aplicacion del argumento NA <a name = "Aplicacion de la opcion NA"></a>

Si faltan valores, la función media devuelve NA.

Para eliminar los valores faltantes del vector, se puede utilizar el argumento "na.rm = TRUE", lo que significa eliminar los valores NA del vector.

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

# Mediana <a name = "Mediana"></a>
La mediana es el valor central si todos los datos se ordenan de menor a mayor. El valor mas medio de una serie de datos se denomina mediana. La mediana podemos determinarla con la funcion median()
```{r pressure, echo=FALSE}
median(x)  
```
## Medidas de dispersion <a name = "Medidas_de_disperion"></a>
Las medidas de dispersión tratan, a través del cálculo de diferentes fórmulas, de arrojar un valor numérico que ofrezca información sobre el grado de variabilidad de una variable.

## Rango <a name = "Rango"></a>

El rango, el valor máximo y mínimo, la variabilidad y la desviación estándar son algunas de las medidas que empleadas habitualmente para describir la dispersión de la muestra. El rango se usa para conocer la cobertura de nuestros datos, siendo la medida del esparcimiento entre el valor máximo y mínimo de nuestra muestra. 

Podemos calcular el rango "manualmente", encontrando el dato máximo de los datos y restando el dato mínimo, así:

```{r pressure, echo=FALSE}
max() - min()
```

Si utilizamos la función `range()` nos mostrará el dato máximo y dato minimo de los datos, sin embago, debes tener en cuenta que esta función no encuentra la diferencia:

```{r pressure, echo=FALSE}
range()
```
## Varianza <a name = "Varianza"></a>

La varianza representa la variabilidad de una serie de datos respecto a su media. Calculamos la varianza utilizando la función `var()`

```{r pressure, echo=FALSE}
var()
```

# Desviación estándar <a name = "Desviacion_estandar"></a>
La desviación estándar es la raíz cuadrada del promedio de las distancias al cuadrado que van desde las observaciones a la media, es decir, la raíz cuadrada de la varianza. Calculamos la desviación estándar usando la función `sd()`

```{r pressure, echo=FALSE}
sd() 
```

Otra forma de calcular la desviación estandar, seria la siguiente:
```{r pressure, echo=FALSE}
sqrt_vec <- sqrt(var(x))  
sqrt_vec
```

## Medidas de localización <a name = "Medidas_de_disperion"></a>
Otras medidas muy utilizadas para describir los datos, son las medidas de localización donde se destacan los quantiles (cuartiles, deciles, percentiles), quienes tienen como función informar qué posición ocupará el dato de interés respecto a todo el conjunto de datos. Los cuantiles son el resultado de dividir los datos en fracciones de igual tamaño, de esta forma, si hablamos de cuartiles, significa que dividimos la muestra en cuatro; si hablamos de quintiles, significa que dividimos la muestra en cinco; si hablamos de deciles, en diez, y si hablamos de percentiles, en 100. variando el  valor de probabilidad podemos obtener cuartiles, deciles, percentiles. Para determinar cuantiles de la muestra utilizamos la función `quantile()`, por ejemplo:

```{r pressure, echo=FALSE}
p=0.25   #para cuartiles
p=0.20   #para quintiles
p=0.10   #para deciles
quantile(x, probs=c(seq(0,1,p))) 
```

### Ejercicios <a name = "Ejercicios"></a>
Ahora hagamos el siguiente ejercicio:

**Cargar los datos**

Primero cargamos el set de datos desde el directorio de trabajo. No olvides utilizar `header=TRUE` para indicar que la primera fila del archivo corresponde al nombre de las variables.

```{r pressure, echo=FALSE}
penguins<-read.table("./CursoR_2023/Datos/penguins_matrix.txt", header=T)
penguins
```
Vamos a seleccionar la columna (bill_length_mm)

```{r presure, echo=FALSE}
bill_length <- penguins$bill_length_mm
```

¿Cual es el dato que más se repite?
¿Cual es el promedio de la muestra?
¿Cual es el valor central?
Calcular las medidas de dispersion

# Prueba de comparación de medias - Prueba t <a name = "Prueba_t"></a>
¿Que debemos hacer si queremos comparar la media de una muestra con un valor estandar? ¿Qué debemos hacer si queremos comparar las medias de dos muestras? Se utiliza la prueba t. Para realizar este tipo de prueba se puede usar la función `t.test`

Los argumentos a definir dentro de `t.test` para hacer la prueba son:
- x : vector numerico con los datos
- Alternative : tipo de hipótesis alterna. Los valores disponibles son "two.sided" cuando la hipótesis alterna es "diferente a", "less" para el caso < y "greater" para el caso >.
- mu : valor de referencia de la prueba
- conf.level : nivel de confianza para reportar el intervalo de confianza asociado (opcional).

```{r pressure, echo=FALSE}
?t.test
```
Extraigamos los datos correspondientes a la longitud de la aleta (flipper_length) y la masa corporal (body_mass), así:

```{r presure, echo=FALSE}
flipper_length <- penguins$flipper_length
body_mass <- penguins$body_mass
```
### Ejercicio - Comparación de la media de una muestra con un valor estandar <a name = "Ejercicio_t1"></a>
Este ejercicio lo realizaremos con la variable "flipper_length" e indicando el valor estándar de la media, en este caso, mu=200:

```{r pressure, echo=FALSE}
t.test(flipper_length, mu=200)
```
Definición de la hipótesis alternativa:
```{r pressure, echo=FALSE}
t.test(flipper_length, mu=200, alternative="greater")
```
### Ejercicio - Comparación de las medias de dos muestras <a name = "Ejercicio_t2"></a>
Este ejercicio lo realizaremos con las variables, "flipper_length" y "body_mass"

```{r pressure, echo=FALSE}
alfa<-0.05
t.test(flipper_length,body_mass, var.equal = F, mu=200, conf.level = 1-alfa, alternative="greater")
```

# Regresión lineal <a name = "Regresion_lineal"></a>

El análisis de regresión es una herramienta estadística muy utilizada para establecer un modelo lineal de relación entre variables: las variables independientes (x) y la variable dependiente (y) que debe ser una variable continua. 

Nota aclaratoria: Hay dos tipos de variable: Continua y discreta. Una variable continua es aquella que admite decimales por naturaleza (Ejemplos: el pH, el peso, la masa). En cambio, una variable discreta es aquella que no tiene sentido escribirla con decimales, es decir, no podemos hablar de 2 personas y media.

El modelo matemático general para una regresión lineal es: y = b + ax
- x es la variable independiente.
- y es la variable dependiente o variable respuesta.
- a y b corresponden a la pendiente de la ecuación y al intercepto, respectivamente. Cuando se trabaja con varias variables independientes, aquellas constantes que acompañen a los x se llamarán coeficientes.

### Pasos para establecer una regresión
Un ejemplo sencillo de regresión es predecir el peso (variable dependiente - y) de una persona cuando se conoce su altura (variable independiente - x). Para ello necesitamos tener la relación entre la altura y el peso de una persona. Para hacer un modelo de regresión se utiliza la función `lm()` la cual crea el modelo de relación entre la variable independiente `x` y la variable de respuesta `y`, así:

### Ejemplo: 
```{r pressure, echo=FALSE}
alt <- c(151, 174, 138, 186, 128, 136, 179, 163, 152, 131)   # Ingreso de valores de altura
peso <- c(63, 81, 56, 91, 47, 57, 76, 72, 62, 48)            # Ingreso de valores de peso
fit <- lm(peso~alt)                                          # Generación del modelo
summary(fit)                                                 # Impresión y resumen del modelo
```
# Función predict() <a name = "Funcion_predict"></a>

La sintaxis básica de `predict()` en regresión lineal es: `predict(objeto, nuevos_datos)`
A continuación se describen los parámetros utilizados:
- objeto es la formula ya creada mediante la función `lm()`.
- nuevos_datos es el vector que contiene el nuevo valor de la variable predictora.
- El vector predictor es altura
- La variable de respuesta es peso

Ejemplo: Hallar el peso de una persona correspondiente a las estatura 190cm, 195cm, 200cm, 205cm y 210cm:
```{r pressure, echo=FALSE}
new <- data.frame(altura = seq(190, 210, 5))
pred <- predict(fit,new, interval = "confidence", level=0.90)
table <- cbind(data,pred)
```

### Ejercicio <a name = "Ejercicio_predict"></a>

1. Realiza un gráfico de dispersion con el fin de conocer las relaciones existentes entre las variables "flipper_length_mm" y "body_mass_g"
2. Calcula el modelo lineal para las variables "flipper_length_mm" (variable dependiente) y "body_mass_g" (variable independiente).
3. Haz una predicción de la longitud de las aletas: Crea un data frame con nuevos valores para "body_mass": `2665,2690,6325,6400,6339,2676`, así:
    
```{r pressure, echo=FALSE}
new <- data.frame("body_mass" = c(2665,2690,6325,6400,6339,2676))
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
La prueba χ² (se puede pronunciar como «ji al cuadrado» o «chi al cuadrado») se utiliza para analizar la relación entre dos variables categóricas en un conjunto de datos, como por ejemplo, en pruebas de independencia y bondad de ajuste al modelo.

Para crear una prueba chi-cuadrado en R es: `chisq.test(datos)`, primero crearemos una tabla con las características que vamos a comparar, así:

```{r pressure, echo=FALSE}
setosa <- iris %>% filter(Species == "setosa")
setosa_sepal_data <- data.frame("Sepal_length"=setosa$Sepal.Length, "Sepal_weidth"=setosa$Sepal.Width)
setosa_sepal_data
```

Ahora, procederemos a realizar la prueba χ²:

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

El coeficiente de correlación se utiliza para cuantificar la relación o asociación entre dos variables cuantitativas en un conjunto de datos. El coeficiente de correlación puede tomar un rango de valores de +1 a -1. Un valor de 0 indica que no hay asociación entre las dos variables. Un valor mayor que 0 indica una asociación positiva. Es decir, a medida que aumenta el valor de una variable, también lo hace el valor de la otra. Un valor menor que 0 indica una asociación negativa, es decir, a medida que aumenta el valor de una variable, el valor de la otra disminuye. Hay varios tipos de coeficientes de correlación, pero los dos más comunes son: 
- Coeficiente de correlación de Pearson (r) que se utiliza cuando la relación es lineal.
- Coeficiente de correlación de Spearman (ρ) aplicado cuando la relación no es lineal o los datos no tienen una distribución normal.
- Coeficiente de correlación de Kendal aplicado para evaluar la asociación entre dos variables ordenadas.

Para realizar la prueba de Coeficiente de Correlación de Pearson se usa la función `cor.test()`.

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
cor.test(penguins$flipper_length_mm, penguins$body_mass_g, method = "spearman", alternative = "greater")
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
