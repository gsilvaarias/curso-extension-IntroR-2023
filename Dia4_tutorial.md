### Jueves, 21 de septiembre, 2023

# Introducción a Tidyverse


![tidyverse](./Images_markdown/tidyverse2.png)

El paquete **tidyverse** en realidad contiene otros paquetes (dplyr, ggplot2, etc.) y lo verás cuando cargues el paquete tidyverse usando `library()`. ¡Recuerde que el paquete debe estar instalado en su computador antes de que pueda ser cargado en sus bibliotecas! Para obtener ayuda sobre la instalación de paquetes, consulte el tutorial del [Dia 1](https://github.com/gsilvaarias/curso-extension-IntroR-2023/blob/main/Dia1_tutorialR.md).


También observará que hay algunas funciones que aparecen enmascaradas después de cargar tidyverse. Para entender lo que esto significa, echemos un vistazo a nuestra pestaña "Paquetes" en la ventana inferior derecha de RStudio.

Recordemos que **los paquetes consisten en una colección de funciones relacionadas con un propósito particular**. Sabemos que los paquetes deben cargarse en sus bibliotecas cada vez que se inicia una nueva sesión de RStudio e instalarse una vez por cada actualización de la versión de R ([Dia 1](https://github.com/gsilvaarias/curso-extension-IntroR-2023/blob/main/Dia1_tutorialR.md)). Cuando se carga un paquete (con la función `library()`), R importará todo el paquete (todas las funciones, documentación, conjuntos de datos incorporados) a su espacio de trabajo actual.

**¿Por qué R no mantiene todos los paquetes siempre cargados para empezar?** ¿Por qué tenemos que cargar las bibliotecas de paquetes en cada sesión de RStudio? La razón es simple: los paquetes a menudo tienen conflictos de nombres con otros paquetes. Aunque los autores de los paquetes intentan nombrar sus funciones de forma única, los nombres concisos y descriptivos son limitados y los conflictos de nombres con funciones de otros paquetes son inevitables. Por ejemplo, si ejecutas `?filter()` después de cargar el paquete tidyverse, aparecerán dos páginas de ayuda: una del paquete `dplyr` y otra del paquete `stats`. Estas funciones funcionan de forma diferente y es importante saber qué función estás utilizando en tu código.

**¿Cómo elige R qué definición de paquete utilizar para `filter()`?** Lo decide basándose en qué paquete se ha cargado más recientemente. El paquete `stats` es un paquete base de R precargado al principio de su sesión de R. Cuando carga el paquete tidyverse, que también carga el paquete `dplyr`, la definición de `filter()` cambia a la versión `dplyr.`

Para evitar el uso accidental de la función no deseada, algunos usuarios de R prefieren cargar funciones individuales en lugar de cargar una biblioteca completa. Si todo lo que necesita utilizar del paquete `dplyr` es la función `filter()`, podría ejecutar lo siguiente:


```{r}
## carga SOLO la función de filtro de dplyr
dplyr::filter()

## carga TODAS las funciones desde dplyr, luego usando filter()
library(dplyr)
filter()

## Atención!! Este bloque de código llama la función filter() del paquete dplyr sin ningún argumento solo para propósito de ver la función. Si se ejecuta como está dará un error porque la función necesita los datos de entrada.
```

> Ahora vamas a iniciar nuestra práctica usado el juego de datos de los pingüinos.

Para iniciar vamos a definir el directorio de trabajo. Como estamos trabajando en un cuaderno de Rmarkdown, debemos definir el directorio de trabajo en un bloque de código de tipo *setup*.

```{r setup, include=FALSE, echo=FALSE}
require("knitr")
opts_knit$set(root.dir = "~/Documents/GitHub/curso-extension-IntroR/")
```

## Cargar un archivo en R con tiduverse

Tidyverse tiene muchas de funciones útiles para leer datos desde el disco, una de estas es `read_csv()`.

```{r}
```

Cuando ejecuta `read_csv()`, imprime un mensaje que le indica el número de filas y columnas de datos, el delimitador utilizado y las especificaciones de las columnas (nombres de las columnas organizados por el tipo de datos que contiene la columna). También muestra información sobre cómo recuperar la especificación completa de la columna y cómo silenciar este mensaje. Este mensaje es una parte integral de `readr`.

Para silenciar el mensaje de la especificación de las columnas podemos incluir el argumento `col_types`. Con el cual explícitamente especificamos el tipo de datos que tiene cada columna. A este argumento hay que proveerle una lista de los tipos de elementos donde los nombres de cada elemento debe corresponder a los nombres de las columnas.

Adicionalmente podemos aprovechar para especificar el (los) caracteres usados para representar datos faltantes.


```{r}
```

A veces especificar los tipos de datos puede ser muy dispendioso. Si podemos corroborar que la función `read_csv()` hizo bien la inferencia del tipo de datos de cada columna, podemos usar la opción `show_col_types = FALSE` para silenciar el mensaje.

```{r}
```


---
**Otros tipos de archivos**

Una vez que domine read_csv(), el uso de otras funciones de readr es sencillo; sólo es cuestión de saber a qué función recurrir dependiendo del formato del archivo.

- `read_csv2()` lee archivos separados por punto y coma. Estos utilizan ; en lugar de , para separar los campos y son comunes en los países que utilizan , como marcador decimal.

- `read_tsv()` lee archivos delimitados por tabuladores.

- `read_delim()` lee archivos con cualquier delimitador, intentando adivinar automáticamente el delimitador si no se especifica.

- `read_table()` lee una variante común de los ficheros de anchura fija en la que las columnas están separadas por espacios en blanco.
---

---
Leer archivos de Excel directamente en R

Microsoft Excel es un programa de hojas de cálculo muy utilizado en el que los datos se organizan en hojas de trabajo dentro de archivos de hojas de cálculo.

Para esto necesitamos funciones del paquete **readxl**.

Este paquete no hace parte del núcleo de **tidyverse**, así que hay que cargarlo explícitamente, pero se instala automáticamente al instalar el paquete tidyverse.

- `read_xls()` lee archivos Excel con formato xls.
- `read_xlsx()` leer archivos Excel con formato xlsx.
- `read_excel()` can read files with both xls and xlsx format. It guesses the file type based on the input.

También esta disponible el paquete **writexl**, que nos permite crear hojas de cálculo Excel.
---


## Modificar información de la tabla de datos

Ahora que nuestros datos ya están disponibles en nuestro ambiente de trabajo, podemos hacerle algunas mejoras de formato. Por ejemplo, podemos usar la función `rename` del paquete `dplyr` para cambiar los nombres de las columnas.

```{r}
```

A menudo nos encontramos con la situación que nuetra tabla de datos necesita información asociada que se encuentra en una tabla anexa. Si en nuestro análisis de datos necesitamos esta información diponible en la misma tabla de datos. Entonces podemos crear una o mas columnas nuevas para incluir la información deseada. Para esto el paquete `dplyr` tiene la "familia" de funciones `join()` (`left_join()`, `inner_join()`, `right_join()`, `full_join()`, `semi_join()`, y `anti_join()`). Veamos un ejemplo sencillo quer busca agregar información cualitativa del tamaño de los pinguinos que está en una tabla diferente.

```{r}
```

Si observamos con cuidado, podemos notar que la variable tamaño es de tipo *caracter*. Esto es de esperar porque los datos que tiene son palabras (o cadenas de caracteres). Sin embargo sabemos que los valores "pequeño", "mediano" y "grande" tienen un significado que implica un orden. Para datos asi, existe un tipo de da to en R llamado **factores**. Para convertir el tipo de datos podemos usar la función `mutate()` del paquete `dplyr`.

```{r}
```

La función `mutate()` también nos permite agregar nuevas columnas usando los datos de la misma tabla. Veamos los ejemplos que ya trabajamos en el día 2.


```{r}
```

```{r}
```

Ahora que hemos terminado de completar nuestros datos, podemos asignar la tabla terminada a un nuevo elemento

```{r}
```


## Exploración de datos

Explorar los datos es una parte fundamental del análisis. Vamos a ver una funciones dentro del "Tidyverso" que son bastante ítiles para hacer exploraciones básicas de la tabla de datos. 

Esta sección le mostrará cómo utilizar algunas transformaciones para explorar los datos de forma sistemática, esto es un ciclo iterativo. Usted:

-Genera preguntas sobre sus datos.

- Busca respuestas sintetizando los datos.

- Utiliza lo que aprende para refinar sus preguntas y/o generar otras nuevas.

La exploración no es un proceso formal con un conjunto estricto de reglas. Más que nada, es curiosidad. Durante las fases iniciales de la exploración debe sentirse libre para investigar todas las ideas que se le ocurran. Algunas de estas ideas resultarán y otras serán callejones sin salida. A medida que continúes explorando, encontrarás algunas ideas especialmente productivas que acabarás escribiendo y comunicando a los demás.

La exploración de los datos es una parte importante de cualquier análisis de datos, incluso si las preguntas de investigación primarias están predefinidad, porque siempre hay que investigar la calidad de los datos. La limpieza de datos es sólo una de las aplicaciones de la exploración de los datos: se trata de preguntarse si los datos cumplen o no las expectativas. Para limpiar los datos, hay que utilizar todas las herramientas disponibles de exploración de datos.


- Podemos empezar por hacer conteos básicos usando la función `count()` de dplyr.

1. ¿Cuántas observaciones tenemos de cada especie?

```{r}

```

2. ¿Cuántas observaciones tenemos de cada especie dentro de las diferentes islas que visitamos?
```{r}

```

3. Ahora discriminado por sexo
```{r}

```

3. Ahora discriminado por sexo ignorando los datos faltantes en la variable sexo
```{r}

```

- Ahora podemos explorar las variables cuantitativas

1. Media y variación de la longitud del pico en las diferentes especies
```{r}

```

2. Media y variación de la longitud del pico entre sexos
```{r}

```

2. Media y variación del peso entre sexos
```{r}

```


```{r}

```


## Cambio de formato. Las tablas "tidy"

Es importante tener un forma coherente de organizar sus datos en R, una organización llamada datos "tidy". Poner tus datos en este formato requiere algo de trabajo inicial, pero ese trabajo merece la pena a largo plazo. Una vez que tenga los datos ordenados y las herramientas ordenadas proporcionadas por los paquetes del tidyverse, pasará mucho menos tiempo trasladando los datos de una representación a otra, lo que le permitirá dedicar más tiempo a las cuestiones analíticas que tenga entre manos.

Puede representar los mismos datos de múltiples maneras. Sin embargo en tidyverse, es importante que los datos presenten un formato organizado que permita que:

- Cada variable debe tener su propia columna.
    
- Cada observación debe tener su propia fila.
    
- Cada valor debe tener su propia celda.

![tidy-tables](./Images_markdown/tidy-tables.png)

Casi siempre tenemos nuestros datos en este formato, pero no siempre es asi. Vamos un ejemplo donde tomamos varias medidas en el tiempo sobre los mismos sujetos de observación.
```{r}

```

En este ejemplo simple, podemos ver que tenemos medidas de peso de 30 pingüinos de las tres especies diferentes tomados en dos periodos de tiempo (2007 y 2009). Sin embargo, aquí NO tenemos la variable tiempo en ninguna columna. Esto lo podemos arreglar con la función `pivot_longer()` del paquete tidyr.

```{r}

```

Ahora con una nueva columna para incluir la información de la variable "año de muestreo"" en nuestros análisis".




¿Los datos de los pingüinos necesita algún ajuste de formato?
 
```{r}

```



## Síntesis

- El meta-paquete tidyverse incluye un "universo" de paquetes que permiten hacer la mayor parte de análisis de datos.
- `readr` incluye las funciones para leer datos con diferentes formatos. Los nombres de las funciones son muy similares a las del paquete base de R.
- `dplyr` nos permite manipular los datos incluyendo el nombre de las variables, crear nuevas variables a partir de las operaciones entre los datos existentes, agrupar, sintetizar y filtrar datos .
- `tidyr` tiene dos funciones básicas para transformar el formato de los datos para hacerlos más eficientes o "tidy".














