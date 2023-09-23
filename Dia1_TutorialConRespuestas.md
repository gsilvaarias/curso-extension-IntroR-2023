
### Lunes, 18 de septiembre, 2023
# Introducción a Análisis en R para Datos Biológicos

## Bienvenidos al primer día de nuestro curso :)
Nosotros somos 3 profes y 2 monitores y esperamos poder compartir muchas experiencias en R con ustedes!  
Profes:
- Andréa Tonolli Thomaz (Dept. Biología - atonolli@unal.edu.co)
- Gustavo Silva (ICN - gasilvaa@unal.edu.co)
- Rosa Angelica Plata  (Dept. Biología - rplatar@unal.edu.co)

Monitores:
- Armando Ali Contreras Quesada (Dept. Biología - acontrerasq@unal.edu.co)
- Nathalia Cortes Duque (Dept. Estadística - ncortesd@unal.edu.co)

# Índice
- [Antes de empezar](#antes_empezar)
  - [Descargando los tutoriales de GitHub](#descargando-tutoriales)
  - [Slack](#slack)
  - [Materiales disponibles online](#Material)
- [R y RStudio](#R_RStudio)
  - [R](#R)
  - [RStudio](#RStudio)
  - [Salvar scripts](#Salvar)
  - [Configurar directorio de trabajo](#setwd)
  - [Gestión de proyectos en RStudio](#proyecto)
- [Introducción a la programación en R](#introR)
  - [Utilizar R como calculadora](#calculadora)
  - [Comparar cosas](#comparar)
- [Funciones y Paquetes](#funciones_paquetes)
  - [Funciones](#funciones)
  - [Paquetes](#paquetes)
- [Estructuras y tipos de datos](#datos)
  - [Variables](#variables)
  - [Datos básicos](#basico)
  - [Estructura de datos](#estructura)
- [Buenas prácticas para escribir código en R](#buenas)
- [Markdown](#markdown)
  - [¿Por qué utilizar Markdown?](#porque_markdown)
  - [Markdown Sintaxis Básica](#markdown_syntax)
  - [RMarkdown](#rmarkdown)

## Antes de empezar <a name = "antes_empezar"></a>
### Descargando los tutoriales de GitHub <a name = "descargando-tutoriales"></a>
Antes de empezar, nos gustaría de indicar donde el material del curso va a estar disponible. Tenemos una página en GitHub.
Github es un repositorio online gratuito que permite gestionar proyectos y controlar versiones de código. Es muy utilizado por desarrolladores para almacenar sus trabajos, dando así la oportunidad a millones de personas de todo el mundo para cooperar en ellos. Así, logramos compartir con ustedes de forma fácil el material del curso.  
1. Acceda al repositorio en [GitHub con el material](https://github.com/gsilvaarias/curso-extension-IntroR-2023.git)
2. Haga clic en el botón verde "Code" y luego "Download Zip". Esto guardará un archivo zip en su computadora.
3. Encuéntrelo y descomprímalo - se convertirá en una carpeta llamada "curso-extension-IntroR-2023". Nosotros vamos hacer el material disponible durante cada día de curso.
4. GitHub tiene muchos otros recursos chéveres, lamentablemente no tenemos tiempo en este curso. Pero si está interesade en aprender más sobre él, hay varios tutoriales disponibles online, como este [video](https://www.youtube.com/watch?v=hWglK8nWh60) y [este curso](https://swcarpentry.github.io/git-novice/).

### Slack <a name = "slack"></a>
Sabemos que el curso es presencial, pero es útil mantenernos comunicados durante el desarrollo para poder atender los requerimientos y dudas de todes. Además, todes podemos ayudarnos. Para esto creamos un canal de Slack, que es una herramienta que permite el trabajo colaborativo facilitando, entre otras cosas, el compartir archivos y snippets de código. [Este es el canal de slack del curso](https://join.slack.com/t/rparadatosbio-wii3581/shared_invite/zt-21kz4ammq-0RwsZ0fMADi080rUpqa7BA). Debes unirte al canal siguiendo los pasos que encuentras en [este enlace](https://slack.com/intl/es-co/help/articles/205239967-C%c3%b3mo-unirse-a-un-canal).
> **Aclaración importante:** Aunque existen aplicaciones de Slack para diferentes sistemas, no es necesario que descargues la aplicación en tus dispositivos. Basta con que te unas al canal usando la interfaz disponible en la web usando tu navegador.

### Materiales disponibles online <a name = "Material"></a>
Además, hay mucho material disponible en la internet de forma gratis, como libros, tutoriales y ayudas para problemas. Vamos a hablar un poco más de esto en el último día, pero acá nos gustaría compartir algunos que nos gusta con ustedes.

**Libros gratuitos** (en español y el inglés):
- [R para ciencias de datos - 1ed.](https://es.r4ds.hadley.nz/)
- [R for data Science - 2 ed.](https://r4ds.hadley.nz)
- [Hands-On Programming with R](https://rstudio-education.github.io/hopr/)
- [Statistical Thinking for the 21st Century - Español](https://statsthinking21.github.io/statsthinking21-core-spanish-site/)
- [An R companion to Statistical Thinking for the 21st Century](https://statsthinking21.github.io/statsthinking21-R-site/)
- [An Introduction to R and Python for Data Analysis](https://randpythonbook.netlify.app/)
- [Data Visualization](https://socviz.co/)

**Websites**
- [R Tutorial](https://www.tutorialspoint.com/r/index.htm)
- [@RforEcology](https://linktr.ee/rforecology)

**Cheat Sheets:**
- [R básico](https://github.com/rstudio/cheatsheets/blob/main/base-r.pdf)
- [RMarkdown](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)
- [dplyr y tidyr](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf)
- [ggplot](https://github.com/rstudio/cheatsheets/blob/main/data-visualization.pdf)
- [Un montón de otras](https://rforpoliticalscience.com/cheat-sheets-in-r/)

<center>Ahora estamos listos para empezar :smile:</center>

## Introducción a R y RStudio <a name = "R_RStudio"></a>
### R y CRAN <a name = "R"></a>
**R** es un software libre para cálculo estadístico y gráficos. Se compila y ejecuta en una amplia variedad de plataformas. Por esto, R ayuda a los analistas y científicos de datos a realizar muchas tareas relacionadas con los datos, como el almacenamiento, procesamiento y análisis de datos, y puede utilizarse para organizar, visualizar, analizar y hacer previsiones basados en diversos tipos de datos.  

Más específicamente en biología, tenemos muchos datos en diferentes formatos y hay una necesidad general de comprender los datos y hacer análisis estadísticos con estos datos. La mejor manera para comprender los datos es trabajando directamente con ellos y R posibilita esto. Además, permite los investigadores desarrollar un conocimiento básico de programación, que es muy útil actualmente.

Para descargar R debes acceder a **CRAN**, llamado así por sus siglas en inglés: the **c**omprehensive **R  a**rchive **n**etwork. CRAN está compuesto de una serie de servidores espejo repartidos alrededor del mundo y es utilizado para distribuir tanto R como los paquetes de R. No es necesario que intentes elegir un servidor que esté cerca tuyo: en su lugar, puedes utilizar el [servidor en la nube](https://cloud.r-project.org), que automáticamente lo identifica por ti.

Una vez al año sale una nueva versión importante de R y hay entre 2 y 3 ediciones menores en ese período. Es una buena idea actualizarlo, así evitas problemas con algunos paquetes que pueden no funcionar bien en versiones pasadas. El proceso puede ser un poco engorroso, porque requiere que reinstales todos los paquetes que ya tienes. Sin embargo, no hacerlo puede ser peor. Para este curso, asegúrate de tener la **versión 4.3.1. (Beagle Scouts)**. Es posible actualizar R directamente en el software, haciendo click en *R > Check for R updates.*

### RStudio <a name = "RStudio"></a>
Durante el curso no vamos a utilizar R directamente, utilizaremos **RStudio** que es un entorno de desarrollo integrado de R, gratuito y de código abierto. Proporciona un editor propio, funciona en todas las plataformas (incluido los servidores) y ofrece muchas ventajas, como la integración con el control de versiones y la gestión de proyectos. RStudio es una de las razones del porqué R se volvió tan popular en los últimos años y hace que el uso de R sea relativamente fácil para los nuevos usuarios.

Para hacer el [download de RStudio Desktop](https://posit.co/downloads/).

#### Layout básico:
Hay tres páneles principales:
- Consola de R (en la izquierda) - acá que escribimos el código (es igualito al ambiente en R)
- Ambiente/Historia (parte superior derecha)
- Archivos/Plots/Paquetes/Ayuda/Visor (parte inferior derecha)
![RStudio basico](../Images_markdown/RMarkdown_basic.png)
- Una vez abra, *File > New File > R script*, también se abrirá un panel de edición en la parte superior izquierda - esto posibilita gurdar nuestro código para ser reproducible
![RStudio basico editor](../Images_markdown/RMarkdown_basic2.png)

#### Flujo de trabajo en RStudio:
1. Escribir código en la consola interactiva de R (después si puede copiar el código en el script para ejecutarlo más tarde). Esto funciona bien cuando se hacen pequeñas pruebas y se empieza. Rápidamente se vuelve laborioso
2. Escribir en un archivo .R y utilizar las teclas de acceso directo de RStudio para el comando *Run* para ejecutar la línea actual, líneas seleccionadas o líneas modificadas a la consola interactiva de R. Esta es una gran manera de empezar; todo su código se guarda para más tarde. Podrás ejecutar el archivo siempre que quieres desde dentro de RStudio o usando la función `source()` de R.
![RunR](../Images_markdown/Run_command.png)

### Salvar scripts <a name = "Salvar"></a>
Para abrir una ventana para escribir **scripts**:
`File > New File > R Script`
Allí abrirá una pantalla arriba donde podemos escribir todos los comandos y salvar este archivo con la extensión .R y reabrir siempre que necesitamos :)

### Configurar directorio de trabajo <a name = "setwd"></a>
Siempre antes de empezar a trabajar en R, es buena práctica saber donde vamos a trabajar. Para esto, asignamos una carpeta, que en caso de salvar los scripts o generar algún archivo, vamos a saber donde la información está guardada.

Para saber la carpeta que estamos:
`getwd()`

![CarpetasWindows](../Images_markdown/carpetasWindows.png)

Hay dos maneras de setar la carpeta de trabajo. Una más fácil, otra más útil:
1. La más fácil se puede hacer con el cursor.  
`Session > Set Working Directory > Choose Directory`  
Allí se puede escoger la carpeta que se desee trabajar. El problema de hacer de esta forma es que no vas a guardar en el script el directorio que estas trabajando.

2. La segunda manera es hacer desde la línea de comando:  
`setwd("LA_CARPETA_DE_INTERES")`  
Para hacer esto, es necesario saber el camino donde está nuestra carpeta de interés.

### Gestión de proyectos en RStudio <a name = "proyecto"></a>
![Reproducibilidad](../Images_markdown/reproducibilidad.png)

En general, utilizar un sistema individual de organización de proyectos no es una buena idea porque puedes fácilmente perderse, por ejemplo: `Doc_FINAL.doc; Doc_FINAL_FINAL.doc; Doc_AHORA_SI_FINAL.doc` :/

Afortunadamente, existen herramientas y paquetes que pueden ayudarte a gestionar tu trabajo con eficacia.
Uno de los aspectos más potentes y útiles de RStudio es su función de gestión de proyectos, se puede utilizar crear un proyecto autocontenido y reproducible. Es especialmente interesante cuando un proyecto vas a tener muchos archivos y scripts.
`File > New Proyect > New Directory`. Una ventaja clave de un proyecto de RStudio es que siempre que abramos este proyecto en sesiones posteriores de RStudio, nuestro directorio de trabajo siempre será la carpeta del proyecto.

>> Ejercicio: Para nuestro curso, vamos a hacer de manera manual.
>> 1. vamos crear una carpeta con el nombre "CursoR_2023" en un sitio apropiado en el computador. En esta carpeta vamos a trabajar toda la semana.
>> 2. En RStudio vamos setar como directorio la carpeta que acabamos de crear, preferiblemente utilizando el comando en el script.
>> 3. Comprobemos nuestro directorio de trabajo utilizando el comando para esto.

#### Mejores prácticas para la organización de proyectos
1. **Tratar los datos como sólo lectura**: éste es probablemente el objetivo más importante. La recopilación de datos suele llevar mucho tiempo y/o ser costosa. Trabajar con ellos de forma interactiva (por ejemplo, en Excel), donde se pueden modificar, significa que nunca se está seguro de dónde proceden los datos o cómo se han modificado desde su recopilación. Por lo tanto, es una buena idea tratar los datos como **sólo lectura**.

2. **Limpieza de datos:** en muchos casos sus datos estarán "sucios" y necesitarán un pre-procesamiento significativo para obtener un formato que R (o cualquier otro lenguaje de programación) encuentre útil. Se resulta útil almacenar estos scripts de limpieza y crear una segunda carpeta de datos de "sólo lectura" para guardar los conjuntos de datos "limpios".

3. **Tratar los datos generados como desechable:** cualquier cosa generada por tus scripts debe ser tratada como desechable, esto es todo debe poder ser regenerado desde sus scripts. Hay muchas formas de gestionar esta salida, pero es una buena idea tener una carpeta de salida con diferentes subdirectorios para cada análisis.

4. **Mantener juntos los datos relacionados**

5. **Organice los scripts:** la creación de scripts R o documentos Rmarkdown independientes para las distintas fases de un proyecto maximizará la eficiencia. Para ejemplo, separar los comandos de descarga de datos evitará que vuelvas a descargar los datos innecesariamente.

6. **Mantener nombres coherentes:** por lo general, es mejor evitar cambiar el nombre de los datos descargados, de modo que se mantenga una conexión clara con el punto de verdad. De lo contrario, es posible que se pregunte si el `archivo_A` es realmente una copia de `Archivo_oficial_en_la_web` o no. Para los conjuntos de datos que genere, merece la pena dedicar tiempo a crear una convención de nomenclatura que funcione para su proyecto. Los nombres de los archivos no tienen por qué ser largos, solo tienen que ser lo suficientemente largos como para que se pueda saber de qué trata el archivo. La fecha de creación, el tema y si se trata de un producto intermedio o final son datos que conviene incluir en el nombre del archivo. Es una buena idea seguir un modelo ordenado (01, 02, 03 o por la fecha 2023-09-18).

**5 buenas prácticas para nombrar archivos:**
- Los nombres de los archivos deben ser cortos pero significativos.
- Utilice elementos coherentes y relevantes.
- Evite caracteres especiales (tildes) y espacios.
- Documente y comparta la convención de nomenclatura de archivos.
- Organización lógica de los archivos.

Para más info, [esta presentación tiene algunos consejos chéveres!](https://speakerdeck.com/jennybc/how-to-name-files?slide=12)

>> Ejercicio:
>> - Ahora podemos intentar salvar nuestro **script** inicial dentro de la carpeta del proyecto :)
>> - Además, vamos a generar una carpeta llamada `Datos`, donde mañana iremos salvar los datos que vamos a utilizar.

## Introducción a la programación en R <a name = "introR"></a>
Lo primero que verá en la consola de RStudio es un montón de información, seguida de un `>` y un cursor parpadeante. En muchos aspectos esto es similar al entorno "shell" y opera con la misma idea de un "Leer, evaluar, imprimir": usted escribe comandos, R intenta ejecutarlos y luego devuelve un resultado.

### Utilizar R como calculadora <a name = "calculadora"></a>
`1+100`

>> Ejercicio: intente hacer algunos otros cálculos para descubrir los símbolos matemáticos utilizados por R.

Utilice paréntesis () para agrupar operaciones con el fin de forzar el orden de evaluación, o para
dejar clara su intención.
```
3 + 5 * 2
(3 + 5) *2
```
Los números realmente pequeños o grandes reciben una notación científica
```
2/10000
5e3
```

**Comandos incompletos:** no te preocupes, puedes completar el comando o para cancelar solamente presione `Esc` o `Ctrl + C` (depende del computo).

**Comentarios:** todo texto que sigue después del # es ignorado por R cuando ejecuta el código y se denomina "comentario".

### Comparar cosas <a name = "comparar"></a>
También podemos hacer comparaciones en R:
```
1 == 1 #igualdad (observe dos signos de igual, que se leen como "es igual a")
1 != 2 # desigualdad (leído como "no es igual a")
1 < 2 # menor que
1 <= 1 # menor o igual que
1 > 0 # mayor que
1 >= -9 # mayor o igual que
```

## Funciones y Paquetes <a name = "funciones_paquetes"></a>
### Funciones <a name = "funciones"></a>
![function](https://www.rforecology.com/functions_image0_new.png)  
Una **función** es un conjunto de sentencias organizadas para realizar una tarea específica. R tiene un gran número de funciones incorporadas y el usuario puede crear sus propias funciones. Hoy vamos empezar a mirar las funciones ya existentes y más para el fin de la semana vamos a crear nuestra propia función.

En R, una función es un objeto, por lo que el intérprete de R es capaz de pasar el control a la función, junto con los argumentos que puedan ser necesarios para que la función realice las acciones. A su vez, la función realiza su tarea y devuelve el control al intérprete, así como cualquier resultado que pueda almacenarse en otros objetos.

Dos componentes de funciones son importantes conocer ahora:
1. **Nombre:** Este es el nombre real de la función. Se almacena en el entorno R como un objeto con este nombre.
2. **Argumentos:** Un argumento es un marcador de posición. Cuando se invoca una función, se pasa un valor al argumento. Los argumentos son opcionales; es decir, una función puede no contener argumentos. También los argumentos pueden tener valores por defecto.

#### Funciones ya existentes (built-in):
![built-in function](https://static.javatpoint.com/tutorial/r/images/r-built-in-functions.png)

R tiene muchas funciones incorporadas que se pueden llamar directamente en el programa sin definirlas primero.
Ejemplos sencillos de funciones incorporadas son `seq()`, `mean()`, `max()`, `sum(x)` y `paste(...)`, etc. Son llamadas directamente por los programas escritos por el usuario.

Algunos ejemplos:
```
seq(32,44)
sum(32,44)
sum(32:44)
mean(25:82)
```

**Ayuda:** es muy difícil recordarse de todo los argumentos que debemos poner en todas las funciones que utilizamos. Por esto R tiene una ventana de ayuda que es muy muy útil. Allí aparece todos los argumentos necesarios con una pequeña explanación.

### Paquetes <a name = "paquetes"></a>
![packages](https://miro.medium.com/v2/resize:fit:720/format:webp/0*0v6iYm6wH2uC6_jw.png)  

Los paquetes R son una colección de funciones R, código compilado y datos de ejemplo. Se almacenan en un directorio llamado *library* en el entorno de R. Por defecto, R instala un conjunto de paquetes durante la instalación. Más adelante se añaden más paquetes, cuando son necesarios para algún propósito específico. Cuando iniciamos la consola de R, sólo están disponibles por defecto los paquetes predeterminados (los básicos). Otros paquetes que ya están instalados tienen que ser cargados explícitamente para ser utilizados por el programa R que los va a utilizar.

Todos los paquetes disponibles en lenguaje R que están en CRAN están listados en *R Packages* de RStudio.

A continuación se muestra una lista de comandos que se deben utilizar para comprobar, verificar y utilizar los paquetes de R.
- Obtener la ubicación de los paquetes de R: `.libPaths()` - puedes variar dependiendo de las configuraciones de cada computo.
- Obtener la lista de todos los paquetes instalados: `library()`
- Obtener todos los paquetes cargados actualmente en el entorno R: `search()`

#### Instalar paquetes
![instalar](https://static.javatpoint.com/tutorial/r/images/r-packages.png)

La principal manera de instalar un paquete es instalando directamente desde el directorio CRAN. El siguiente comando obtiene los paquetes directamente de la página web de CRAN e instala el paquete en el entorno de R. Se le pedirá que elija el ""mirror".
`install.packages("NOMBRE_PAQUETE")`  

Otra opción es en *Packages*, hacer click en *Install*. Allí es posible buscar todos los paquetes en CRAN.

Además de CRAN, hay algunos otras maneras que se puede instalar paquetes:
- **Archivo .zip**: también es posible hacer la instalación directamente de un archivo. En el website de CRAN se puede descargar el paquete necesario. Guarde el paquete como archivo .zip en una ubicación adecuada del sistema local y ejecute el comando `install.packages(CAMINO_ARCHIVO, repos = NULL, type = "source")`.
- **GitHub**: necesita tener el paquete ["devtools"](https://www.projectpro.io/recipes/install-packages-devtools-r) instalado para hacer download de paquetes disponibles en GitHub. Devtools es un paquete bastante chévere que facilita en desarrollo de nuevos paquetes en R.
- **[Bioconductor](https://www.bioconductor.org/)**: Hay muchos paquetes relacionados con genómica.

>> Ejercicio: hacer el download del paquete que vamos a necesitar durante nuestro curso: `tidyverse`. Importante tener en cuenta que este paquete ya hace automáticamente el download de un montón de otros paquetes que vamos a necesitar.

#### Abrir paquetes
Antes de poder utilizar un paquete en el código, debe cargarse en el entorno R actual. También es necesario cargar un paquete que ya esté instalado previamente pero que no esté disponible en el entorno actual. Es una buena práctica siempre cargar todos los paquetes que vamos a utilizar en el inicio de nuestro script.

Un paquete se carga utilizando el siguiente comando:
`library("NOMBRE_PAQUETE")`

>> Ejercicio: cargar el paquete que acabamos de hacer el download.

## Estructuras y tipos de datos <a name = "datos"></a>
Para sacar el máximo de R, es necesario conocer a fondo los tipos de datos y estructuras de datos básicos y saber cómo operar con ellos.

Es muy importante entender las estructuras de datos porque estos son los objetos que manipulará día a día en R. Tratar con conversiones de objetos es una de las fuentes más comunes de frustración para los principiantes.

**Todo en R es un objeto.**

### Variables <a name = "variables"></a>
Una variable es un símbolo que representa otro valor (como "X" en álgebra). Podemos almacenar valores en variables utilizando el operador de asignación `<-`, así:
```
x <- 1/40
y <- (5*6)^2
```
Observa que la asignación no imprime un valor. En su lugar, lo almacenamos para más tarde en algo llamado **variable**.
>> También es posible utilizar el operador `=` para la asignación, pero recomendamos utilizar `<-`

Busque la pestaña *Environment* en uno de los paneles de RStudio, y verá que ha aparecido `x` y su valor. Nuestra variable `x` puede utilizarse en lugar de un número en cualquier cálculo:
`log(x)`

Observa también que las variables pueden ser reasignadas:
`x <- 100`

Los valores de asignación pueden contener la variable a la que se asigna:
`x <- x+1`

>> Ejercicio: crie dos variables numéricas y haga comparaciones entre ellas.

Además de mirar en *Environment* las variables, es posible listarlas utilizando el comando `ls()`. Se puede remover las variables utilizando `rm()`. Utilizando estos dos comandos juntos, se remove todas las variables en el ambiente R `rm(ls())`.

Los **nombres de las variables** pueden contener letras, números, guiones bajos y puntos. No pueden empezar por un número ni contener espacios. Cada persona utiliza una convención diferente para los nombres largos de las variables, por ejemplo:
- punto.entre.palabras
- guion_entre_palabras
- MaiusculaParaSeparar

**Lo que utilices depende de ti, pero sé coherente.**

### Datos básicos <a name = "basico"></a>
R tiene 5 tipos de datos básicos:
- **carácter:** "a", 'hola'(comillas simples o doble)
- **numérico (decimal = "double"):** 2, 15.5 (siempre utilizar .)
- **entero:** 2L (la L indica que lo almacene como un entero)
- **lógico:** TRUE, FALSE
- **complejo:** 1+4i (números complejos con partes reales e imaginarias)

![data_types](https://intellipaat.com/blog/wp-content/uploads/2021/10/Different-Data-Types-in-R-Programming.jpg)

No importa lo complicado que se sea los datos y análisis, todos los datos en R se interpretan como una clase de datos específica. Además, para datos faltantes, siempre usamos **NA**.

>> Ejercicio: juegue un poco creando variables nuevas para diferente tipos de datos y haga una prueba con la función `class()`.

### Estructura de Datos <a name = "estructura"></a>
Los datos básicos pueden combinarse para formar estructuras de datos. R tiene muchas estructuras de datos, son ellas:
- **Vector atómico**
- **Matriz**
- **Arreglos (arrays)**
- **Lista (vectores recursivos)**
- **Data frame**
- **Factores**

![data_structure](https://techvidvan.com/tutorials/wp-content/uploads/sites/2/2020/01/R-data-strucutres.jpg)

#### Vectores
Un vector es la estructura de datos más común y básica en R y es prácticamente el caballo de batalla de R. En general es una colección de elementos carácter, lógico, entero o numérico. Llamamos un vector de atómico porque **sólo contiene datos de un único tipo**.

Es posible crear vectores especificando directamente su contenido. R adivinará entonces el modo de almacenamiento apropiado para el vector. Por ejemplo:
`x <- c("a", "b", "c")`

Las funciones `length()`, `class()`, `str()` y `nchar()` proporcionan información útil sobre sus vectores y objetos R en general.

>> Ejercicio: utilize las funciones arriba para descubrir lo que hacen.

La función **c()** (para combinar) también puede utilizarse para añadir elementos a un vector.
`x <- c(x, "d")`

**Vectores numéricos:**
```
x <- c(1, 2, 3)
class(x)
```
Vectores en secuencia numérica:
```
x <- seq(1:10)
y <- seq(from = 1, to = 10, by = 0.1)
```

- Podemos especificar elementos de un vector utilizando el índice de la posición dentro de []. Es importante tener en cuenta que, diferente de otras lenguajes de programación, el **índice en R empieza en 1** (y no en 0): `y[1]`.

- Podemos hacer cálculos entre vectores existentes: `x + y`. Importante tener en cuenta que los dos vectores deben tener el mismo tamaño y ser del mismo tipo de dato o R genera un *Warning* o un *Error*.

**Datos faltantes:**
R admite datos faltantes en vectores. Se representan como NA (No Disponible) y se pueden utilizar para todos los tipos de vectores cubiertos en esta lección:
`x <- c(1.2, NA, 0.7)`
La función `is.na()` indica los elementos de los vectores que representan datos que faltan, y la función `anyNA()` devuelve TRUE si el vector contiene algún valor que falta.

>> Ejercicio: Genere un vector con dato faltante e intente utilizar las dos funciones.

**¿Qué ocurre cuando se mezclan tipos dentro de un vector?**
R creará un vector resultante con un modo que pueda acomodar más fácilmente todos los elementos que contiene. Esta conversión entre modos de almacenamiento se denomina "coerción". Cuando R convierte el modo de almacenamiento basándose en su contenido, se denomina "coerción implícita".

>> Ejercicio: Intente crear vectores con tipos mezclados y intente adivinar que pasa utilizando la función `class()`.

También puede controlar cómo se coaccionan los vectores explícitamente utilizando las funciones `as.<nombre_clase>()`

**Vectores vacíos:** Se puede crear un vector vacío con `vector()` (por defecto, el modo es lógico). Es más común utilizar constructores directos como `character()`, `numeric()`, etc.

Podemos asegurarnos que estamos trabajando con vectores utilizando `is.vector()`.

#### Matrices
En R, las matrices son una extensión de los vectores numéricos o de caracteres. No son un tipo de objeto separado, sino simplemente un vector atómico con dimensiones; el número de filas y columnas. Como ocurre con los vectores atómicos, los elementos de una matriz deben ser del mismo tipo de datos.
```
m <- matrix(nrow= 2, ncol=2)
m
dim(m) #para las dimensiones de la matrix
```
Para crear una matrix con datos, podemos hacer:
`m <- matrix(c(1:6), nrow=2, ncol =3)`
En este ejemplo es posible observas que las matrices en R se **rellenan por columnas**. Para ser por fila utilizamos `byrow = TRUE`.

Acá tenemos una diferencia en `class(m)` y también podemos utilizar `typeof()`, depende lo que queremos.
>> Ejercicio: Pruebe para la matrix que acabamos de hacer estas dos funciones y mire la diferencia.

Hay algunas otras maneras de generar matrizes, por ejemplo, crear un vector y lo transforma en una matriz de 2 filas y 5 columnas.
```
m <- 1:10
dim(m) <- c(2,5)
```
Otra forma es vincular columnas o filas utilizando `rbind()` y `cbind()` ("row bind" y "column bind", respectivamente). Estas dos funciones son muy útiles en general para manipulación de datos, pero es importante estar seguro que los vectores tienen el mismo tamaño:
```
x <- 1:3
y <- 10:12
mc <- cbind(x, y)
mc
mr <- rbind(x, y)
mr
```
- Los elementos de una matriz pueden referenciarse especificando el índice a lo largo de cada dimensión (por ejemplo, "fila" y "columna"), siempre entre corchetes simples: `mr[2,3]`.

#### Arreglos (arrays)
Un *array* es una estructura de datos que puede contener datos multidimensionales. Por ejemplo, en matrices cuadradas puede contener dos filas y dos columnas. Las matrices pueden almacenar los valores que tienen sólo un tipo similar de tipos de datos.
```
vector1 <-  c(5, 10, 15, 20)
vector2 <-  c(25, 30, 35, 40, 45, 50, 55, 60)
arreglo <- array(c(vector1, vector2),dim =c(4,4,3))
arreglo
class(x)
```
En realidad arreglos no son utilizados muy frecuentemente y en este curso vamos nos enfocar en las otras estructuras de datos, pero se necesitan más info de arreglos, este [website](https://www.datacamp.com/tutorial/arrays-in-r) puede ayudar.

#### Listas
En R, las **listas** actúan como contenedores. A diferencia de los vectores atómicos, el contenido de una lista **NO está restringido a un único tipo de dato** y puede abarcar cualquier mezcla. Las listas se denominan a veces vectores genéricos, porque los elementos de una lista pueden ser de cualquier tipo de objeto R, incluso listas que contengan más listas. Esta propiedad las diferencia fundamentalmente de los vectores atómicos.

Una lista es un tipo especial de vector. Cada elemento puede ser de un tipo diferente.

Las listas pueden ser extremadamente **útiles dentro de las funciones**. Dado que las funciones en R sólo pueden devolver un único objeto, puede "grapar" muchos tipos diferentes de resultados en un único objeto que una función puede devolver.

Una lista no se imprime en la consola como un vector. En su lugar, cada elemento de la lista comienza en una nueva línea.

Cree listas utilizando `list()` o convierta otros objetos a listas utilizando `as.list()`. Vamos crear una lista ejemplo:
`l <- list(1, "a", TRUE, 1+4i)`

Como podemos mirar en el ejemplo, el contenido de los elementos de una lista puede recuperarse utilizando corchetes dobles `x[[1]]`. Los corchetes simples devolverán otra lista.

>> Ejercicio: Evalúe la posición [1] y [[1]] de la lista creada con la función `class()`. ¿Cómo difieren??

Los elementos de una lista pueden tener nombre (es decir, las listas pueden tener el atributo `names`):
```
xlist <- list(a = "Hola", b = 1:10)
names(xlist)
```
Si los elementos de una lista tienen nombre, se puede hacer referencia a ellos mediante la notación **$** (es decir, `xlist$a`).

>> Ejercicio: ¿Cuál es el tamaño y la estructura de la lista creada? Use funciones apropiadas como `length()` y `str()`.

#### Data Frames
Un *data frame* es un tipo de datos muy importante en R. Es la estructura más utilizada para datos tabulares y lo que utilizamos para las estadísticas. Es un tipo especial de lista donde cada elemento de la lista tiene la misma longitud (es decir, es una **lista "rectangular"**).

Los *data frames* pueden tener atributos adicionales, como `rownames()`, que pueden ser útiles para anotar datos, como *IDs*.

Información adicional sobre los *data frames*:
- Normalmente se crean mediante `read.csv()` y `read.table()`, es decir, al importar los datos a R - vamos hablar de esto mañana!!
- Suponiendo que todas las columnas de un *data frame* son del mismo tipo, se puede convertir en una matriz con `data.matrix()` o `as.matrix()`. De lo contrario, se aplicará la coerción de tipos y los resultados no siempre serán los esperados.
- También puede crear un *data frame* manualmente con la función `data.frame()`.
- Encuentre el número de filas y columnas con `nrow()` y `ncol()`, respectivamente.
- Los nombres de las filas pueden generarse automáticamente y se parecen a 1, 2, ..., n. La coherencia en la numeración de los nombres de las filas puede no respetarse cuando las filas se reorganizan.

Por ejemplo, vamos crear un *data frame* manualmente:
```
dat <- data.frame(id = letters[1:10],
                  x = 1:10,
                  y = 11:20)
dat
```
Algunas funcionas de *data frames* importantes:
```
# nombres
names(dat)
colnames(dat)
rownames(dat)

#subset
head(dat)
tail(dat)

#tamaño y estructura
dim(dat)
nrow(dat)
ncol(dat)
str(dat)
sapply(dat, class)

#tipo de dato
is.list(dat)
is.data.frame(dat)
class(dat)
```

Dado que los *data frames* son rectangulares, se puede hacer referencia a los elementos del marco de datos especificando la fila y el índice de columna entre corchetes simples (similar a la matriz) `dat[1,2]` o a columnas o filas `dat$y`, `dat[,1]`, `dat[1,]`.

>> Ejercicio: adicione una nueva columna al data frame dat que ya creamos. ¿Cómo podemos hacer esto?

#### Factores:
Los factores se parecen a los datos de caracteres, pero se utilizan para representar **información categórica**. Los factores pueden estar ordenados o no y son una clase importante para el análisis estadístico y para hacer gráficos.

Los factores se almacenan como números enteros y tienen etiquetas únicas asociadas a estos números. Aunque los factores parecen (y a menudo se comportan) como vectores de caracteres, en realidad son enteros y hay que tener cuidado al tratarlos como cadenas.

Una vez creados, los factores sólo pueden contener un conjunto predefinido de valores, conocidos como niveles (*levels*). Por defecto, R siempre ordena los niveles por orden alfabético.

Por ejemplo, hagamos un vector con observaciones por concentración de alguna sustancia:
```
conc <- c("Bajo", "Alto", "Medium", "Bajo", "Medio")
conc
str(conc)
class(conc)
fac_conc <- factor(conc)
fac_conc
str(fac_conc)
class(fac_conc)
levels(fac_conc)
nlevels(fac_conc)
```

A veces, el orden de los factores no importa, otras veces puede querer especificar el orden porque es significativo (por ejemplo, "bajo", "medio", "alto") o porque lo requiere un tipo de análisis concreto. Además, especificar el orden de los niveles nos permite comparar niveles:
```
levels(fac_conc)
fac_conc <- factor(fac_conc, levels = c("Bajo", "Medium", "Alto"), ordered = TRUE)
levels(fac_conc)
min(fac_conc)
```
Vamos trabajar con factores más adelante en el curso...

>> Ejercicio: compare como recuperar elementos específicos para diferentes estructuras de datos.

# Buenas prácticas para escribir código en R <a name = "buenas"></a>
- Inicia cada programa con una descripción de lo que hace.
- A continuación, cargue todos los paquetes necesarios.
- Tenga en cuenta en qué directorio de trabajo se encuentra cuando cree un script.
- Utilice comentarios para marcar secciones de código.
- Asigne un nombre y un estilo coherentes al código.
- Divida el código en partes pequeñas y discretas.
- Factorice las operaciones comunes en lugar de repetirlas.
- Guarde todos los archivos fuente de un proyecto en un mismo directorio y utilice rutas relativas para acceder a ellos.
- Empiece siempre con un entorno limpio en lugar de guardar el espacio de trabajo.
- Haz que otra persona revise tu código.  

# Markdown <a name = "markdown"></a>

[Markdown](https://www.markdownguide.org/getting-started/) es un lenguaje que
puede usar para agregar elementos de formato a documentos de texto sin formato.
En una aplicación como Word, haces clic en los botones para formatear palabras y
frases, y los cambios son visibles de inmediato. Markdown no es así. Cuando se
crea un archivo con formato de Markdown (`.md` o `.Rmd` en el caso de R), se agrega la sintaxis de
Markdown al texto para indicar qué palabras y frases deben verse diferentes.

Por ejemplo, para indicar un encabezado, agregue un signo de número antes de él
(por ejemplo, # Encabezado uno). O para poner una frase en negrita, agregue dos
asteriscos antes y después (por ejemplo, **este texto está en negrita**).

## ¿Por qué utilizar Markdown? <a name = "porque_markdown"></a>

Quizás se pregunte por qué la gente usa Markdown en lugar de un editor "normal".
¿Por qué escribir con Markdown cuando puede presionar botones en una interfaz
para formatear su texto? Resulta que hay un par de razones importantes por las
que la gente usa Markdown:
- Se puede utilizar para todo. La gente lo usa para crear sitios web,
  documentos, notas, libros, presentaciones, mensajes de correo electrónico y
  documentación técnica.
- Es portátil. Los archivos que contienen texto con formato Markdown se pueden
  abrir utilizando prácticamente cualquier aplicación.
- Es independiente de la plataforma. Puede crear texto con formato Markdown en
  cualquier dispositivo que ejecute cualquier sistema operativo.
- Puede convertir en varios tipos de archivos, como .pdf, .HTML y muchos otros.

Aquí usaremos **RMarkdown** para editar los tutoriales con nuestras propias notas y
al final los exportaremos a diferentes formatos, por ejemplo: pdf y html.

## Markdown Sintaxis Básica <a name = "markdown_syntax"></a>
Hay varias Markdown *cheat sheets* disponibles, algunas interesantes para mirar son: [esta](https://www.markdownguide.org/cheat-sheet/) y [esta](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf).  

Aquí veremos la sintaxis básica que usamos para hacer estos tutoriales.

Los comandos básicos para recordar son:  
- Encabezamiento: `# H1 ## H2 ### H3`
- Negrita: `**bold**` o `__bold__`
- Itálica: `*itálico*` o `_itálico_`
- Cita en bloque: `>` o `>>`
- Lista no ordenada:
  - lalala
  - lala
- Lista ordenada:
  1. lalala
  2. lalala
- Código: `lalala`
- Regla horizontal: ---
- Link: `[alguna-palabra](https://www.example.com)`
- Imagen:
  - de un archivo: `![texto](ruta_de_la_imagen.png)`

  - de la internet: `![texto](https://LINK_PARA_LA_IMAGEN.png)`

Para empezar, vamos a hacer [esto ejercício](https://www.markdowntutorial.com/es/).  

Si olvida la sintaxis, ¡no hay lío! Puede escribir como si fuera un archivo de texto 😉

## RMarkdown <a name = "rmarkdown"></a>

<figure> <p align="center"> <img src = "https://bookdown.org/yihui/rmarkdown/images/hex-rmarkdown.png" width="200"> </p></figure>

Durante el curso vamos a utilizar (**R Markdown**)[https://bookdown.org/yihui/rmarkdown/].
Los documentos de R Markdown son completamente reproducibles y soportan docenas de formatos de salida tales como PDFs, archivos de Word, presentaciones y más.

Los archivos R Markdown están diseñados para ser usados de tres maneras:
1. Para comunicarse con quienes toman decisiones, que desean enfocarse en las conclusiones, no en el código que subyace al análisis.
2. Para colaborar con otras personas que hacen ciencia de datos (¡incluyendo a tu yo futuro!), quienes están interesados tanto en tus conclusiones como en el modo en el que llegaste a ellas (es decir, el código).
3. Como un ambiente en el cual hacer ciencia de datos, como si fuera un notebook de laboratorio moderno donde puedes capturar no solo que hiciste, sino también lo que estabas pensando cuando lo hacías.

Para esto necesitamos el paquete `rmarkdown`. En realidad ya lo instalamos cuando cuando hicimos la instalación de `tidyverse`, porque es una de sus dependencias.

Para empezar vamos en `File > New File > R Markdown`. Esto abrirá una ventana que se puede poner datos generales (opcional). Ahora podemos empezar a escribir nuestro código utilizando los comandos de Markdown. Este archivo debe tener la estensión `.Rmd`.

Contiene tres tipos importantes de contenido:
- Un encabezado YAML (opcional) rodeado de ---
- Bloques de código de R rodeados de ` ```{r} ``` `.
- Texto mezclado con formateos de texto simple como `# Encabezado` e `_itálicas_`.

![pantalla](../Images_markdown/Pantalla_markdown.png)

Cuando abres un archivo .Rmd, obtienes una interfaz de notebook donde el código y el output están intercalados. Puedes ejecutar cada bloque de código haciendo clic en el ícono ejecutar (se parece a un botón de reproducir en la parte superior del bloque de código), o presionando Cmd/Ctrl + Shift + Enter. RStudio ejecuta el código y muestra los resultados incustrados en el código.
![](https://es.r4ds.hadley.nz/rmarkdown/tamanio-diamantes-cuadernillo.png)

Para producir un reporte completo que contenga todo el texto, código y resultados, haz clic en “Knit”.
![](https://es.r4ds.hadley.nz/rmarkdown/tamanio-diamantes-reporte.png)

Cuando haces knit el documento (knit significa tejer en inglés), R Markdown envía el .Rmd a knitr (http://yihui.name/knitr/) que ejecuta todos los bloques de código y crea un nuevo documento markdown (.md) que incluye el código y su output. El archivo markdown generado por knitr es procesado entonces por pandoc (http://pandoc.org/) que es el responsable de crear el archivo terminado. La ventaja de este flujo de trabajo en dos pasos es que puedes crear un muy amplio rango de formatos de salida, como aprenderás en [Formatos de R markdown ].
![](https://es.r4ds.hadley.nz/images/RMarkdownFlow.png)

>> Ejercicio: Crea un nuevo documento R Markdown con File > New File > R Markdown… Haz clic en el icono apropiado de Knit, salva y genere un archivo html.

#### Opciones para Bloques
La salida de los bloques puede personalizarse con options, que son argumentos suministrados en el encabezado del bloque. Knitr provee casi 60 opciones que puedes usar para personalizar tus bloques de código. Aquí cubriremos las opciones de bloques más importantes que usarás más frecuentemente. Puedes ver la lista completa en http://yihui.name/knitr/options/.

El conjunto más importante de opciones controla si tu bloque de código es ejecutado y qué resultados estarán insertos en el reporte final:
- **eval = FALSE** evita que el código sea evaluado. (Y, obviamente, si el código no es ejecutado no se generaran resultados). Esto es útil para mostrar códigos de ejemplo, o para deshabilitar un gran bloque de código sin comentar cada línea.

- **include = FALSE** ejecuta el código, pero no muestra el código o los resultados en el documento final. Usa esto para código de configuración que no quieres que abarrote tu reporte.

- **echo = FALSE** evita que se vea el código, pero sí muestra los resultados en el archivo final. Utiliza esto cuando quieres escribir reportes enfocados a personas que no quieren ver el código subyacente de R.

- **message = FALSE** o warning = FALSE evita que aparezcan mensajes o advertencias en el archivo final.

- **results = 'hide'** oculta el output impreso; fig.show = 'hide' oculta gráficos.

Cosas que no hay derechamente en Markdown, se puede utilizar lenguaje **html** y **latex**. Además, para opciones más avanzadas de RMarkdown, podemos mirar [acá](https://es.r4ds.hadley.nz/27-rmarkdown.html).  
<br>
<p align="center">
FIN del día 1 :smile:
</p>
