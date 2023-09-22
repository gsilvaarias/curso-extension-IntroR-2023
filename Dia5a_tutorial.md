### Lunes, 18 de septiembre, 2023
# Introducción a Análisis en R para Datos Biológicos
# Día 5 - Errores comunes

## Índice
- [Errores de sintaxis](#sintaxis)
- [Errores de semánticos](#semantica)
- [Recursos](#recursos)


R es conocido por producir mensajes de error que son difíciles de entender. Sin embargo con la experiencia uno comienza a interpretar con mayor facilidad los mensajes y encontrar la solución mas rápido.

Hay algunos errores comunes que todo principiante tiene problemas para entender. Hoy mostraremos cómo descifrar algunos de los errores más comunes que se ven y cómo solucionarlos.

**La mayoría de los errores en R se deben a buscar algo que no está ahí.**


Hay dos tipos principales de errores en el código R:

- Los errores de **sintaxis** son el resultado de sentencias de código inválidas que R no entiende. Los errores de sintaxis siempre dan lugar a mensajes de error.

- Los errores **semánticos** son el resultado de código válido que se ejecuta correctamente pero produce resultados no deseados.


## Errores de sintaxis <a name = "sintaxis"></a>

Si obtiene un error de sintaxis, entonces ha introducido un comando que R no puede entender. Esos son normalmente recogidos por R y obtendrás mensajes de error recordándote que revises tu código y los corrijas. Generalmente el mensaje de error logra señalar el punto aproximado del comando donde se encuentra el error.

Los errores más comunes son errores de sintaxis:

- Olvidar un símbolo

*Error: unexpected symbol in ...*
```{r}
x = c(1,2,3,4,5,6,7,8)
2 x
```
- Corchete abierto pero sin cerrar

Símbolo **+** en la consola (en vez de **>**)

```{r}
x = c(1,2,3,4,5,6,7,8
x[
```

- Nombre de un objeto o ruta de archivo mal escrito


*Error: object 'X' not found*
<br>
Por lo general, podrá darse cuenta fácilmente de que cometió un error tipográfico porque recibirá un error de *objeto no encontrado*. Recuerde que R también **distingue entre mayúsculas y minúsculas**.
<br>
También puede estar faltando comillas.
```{r}
Datos_pinguinos
```

```{r}
rep(y, 5)
```


*Error : cannot open the connection*
<br>
Un archivo/conexión no puede abrirse porque R no puede encontrarlo (principalmente debido a un error en la ruta).
```{r}
datos_pinguinos <- read_csv("datasets/penguins_matrix2.txt")
```


- Tipo incorrecto de corchete de cierre (por ejemplo, un corchete cuadrado de apertura pero un paréntesis de cierre).

*Error: unexpected ']' in "x(3]"*
```{r}
x(3]
```


- Un paquete no se ha cargado en R, por lo que R no sabe dónde encontrar la función especificada

*Error: could not find function*
<br>
Es un buen hábito utilizar las funciones *library()* para todos los paquetes que va a utilizar en la parte superior R chunk en su archivo R Markdown. A este *chunk* normalmente se le da el nombre *setup*.

*could not find function "read_csv"*
<br>
No se ha cargado el paquete
```{r}
datos_pinguinos <- read_csv("../datasets/penguins_matrix2.txt")
```


- Problemas con las dimensiones del objeto

*Error in ... : subscript out of bounds*
<br>
Errores causados por intentar acceder a un elemento o dimensión que no existe.

```{r}
x = matrix(0,5,7)
x[6,1]
```

*Error : replacement has X rows, data has Y*
<br>
Este error se produce cuando se intenta asignar un vector de valores a un subconjunto de un objeto existente y las longitudes no coinciden.
```{r}
data <- data.frame(x1 = c(1, 1, 2, 3, 4),
                   x2 = "x")

data$x3 <- rep("y", 5)
```




- Mezclar datos en formato numérico con datos en formato carácter

*Error in ... : non-numeric argument to a binary operator*
<br>
Este es un error sencillo de descifrar. Esto ocurre cuando mezclamos diferentes valores vectoriales en el cálculo.

```{r}
vec1 <- 1:3
vec2 <- c("esto", "es", "vector")
vec1 + vec2
```

## Errores semánticos <a name = "semantica"></a>

Un error semántico se produce cuando una sentencia es sintácticamente válida, pero no hace lo que el programador pretendía. El código en sí es correcto, pero el resultado de esa línea de código no lo es.

No ignore los *Warnings*.



## Recursos <a name = "recursos"></a>

- [Errores comunes](https://epirhandbook.com/es/common-errors.html), N. Batra.

- [errores-comunes-rstudio-knit](https://gist.github.com/rocarvaj/0cdd45ad48f3754335a059d0e3cca1bd), R. Carvajal.

- [Errores más comunes programando en R](https://programacion-en-r.webnode.es/errores-comunes/).

- [How to: Interpret Common Errors in R](https://warin.ca/posts/rcourse-howto-interpretcommonerrors/), Thierry Warin.

- [Deciphering Common R Errors](https://ismayc.github.io/rbasics-book/6-errors.html), C. Ismay y P. C. Kennedy.

- [Common errors and debugging R code](https://www.tylerclavelle.com/code/2018/debug/), T. Clavelle.

- [Impatient R](https://www.burns-stat.com/documents/tutorials/impatient-r/), P. Burns.

- [R Error Message Cheat Sheet](http://varianceexplained.org/courses/errors/), D. Robinson 

- [I’ve got 99 problems, but dependencies ain’t one by Noam Ross](https://github.com/noamross/zero-dependency-problems)

- [Stackoverflow](https://stackoverflow.com/)






