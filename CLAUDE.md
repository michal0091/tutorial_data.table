# CLAUDE.md - Proyecto de Libro Corto en Quarto R

## Descripción del Proyecto

Este proyecto utiliza **Quarto** para crear un libro corto que combina texto narrativo con código R ejecutable. Quarto es un sistema de publicación científica y técnica que permite crear documentos reproducibles de alta calidad.

## Estructura del Proyecto

```
mi-libro-quarto/
├── _quarto.yml           # Configuración principal del proyecto
├── index.qmd            # Página de inicio/prefacio
├── intro.qmd            # Capítulo de introducción
├── capitulo-01.qmd      # Primer capítulo
├── capitulo-02.qmd      # Segundo capítulo
├── conclusion.qmd       # Conclusiones
├── references.bib       # Bibliografía (opcional)
├── _freeze/            # Carpeta de cache (generada automáticamente)
├── _book/              # Salida del libro (generada automáticamente)
└── data/               # Carpeta para datos
    └── ejemplo.csv
```

## Configuración Inicial

### 1. Archivo `_quarto.yml` (Configuración Principal)

```yaml
project:
  type: book
  output-dir: _book

book:
  title: "Mi Libro Corto"
  subtitle: "Un análisis con R y Quarto"
  author: "Tu Nombre"
  date: today
  chapters:
    - index.qmd
    - intro.qmd
    - capitulo-01.qmd
    - capitulo-02.qmd
    - conclusion.qmd

format:
  html:
    theme: cosmo
    toc: true
    toc-depth: 2
    code-fold: true
    code-tools: true
  pdf:
    documentclass: scrbook
    toc: true
```

### 2. Archivo `index.qmd` (Página de Inicio)

```markdown
# Prefacio {.unnumbered}

Este libro presenta...

## Sobre este libro

## Requisitos previos

- R (versión 4.0 o superior)
- RStudio
- Quarto

## Estructura del libro
```

## Comandos Útiles

### Renderizar el libro completo
```bash
quarto render
```

### Previsualizar en modo desarrollo
```bash
quarto preview
```

### Renderizar solo un capítulo
```bash
quarto render capitulo-01.qmd
```

### Limpiar archivos generados
```bash
quarto clean
```

## Configuración de Chunks de Código R

### Opciones globales recomendadas
```r
#| echo: true
#| warning: false
#| message: false
#| fig-width: 8
#| fig-height: 6
```

### Ejemplos de chunks útiles

#### Carga de librerías
```r
#| label: setup
#| include: false

library(tidyverse)
library(ggplot2)
library(knitr)
library(DT)
```

#### Figura con caption
```r
#| label: fig-ejemplo
#| fig-cap: "Gráfico de dispersión de ejemplo"

ggplot(mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  theme_minimal()
```

#### Tabla interactiva
```r
#| label: tabla-ejemplo

DT::datatable(head(mtcars), options = list(pageLength = 5))
```

## Mejores Prácticas

### 1. Organización de Archivos
- Un archivo `.qmd` por capítulo
- Nombres descriptivos para los archivos
- Carpeta `data/` para conjuntos de datos
- Carpeta `images/` para imágenes estáticas

### 2. Código R
- Usar nombres descriptivos para los chunks: `#| label: nombre-descriptivo`
- Configurar opciones de chunk apropiadas
- Comentar el código adecuadamente
- Usar el pipe nativo `|>` de R 4.1+

### 3. Texto y Formato
- Un párrafo por idea
- Usar headers jerárquicos (##, ###, ####)
- Aprovechar las referencias cruzadas: `@fig-ejemplo`, `@tbl-datos`
- Incluir captions descriptivos en figuras y tablas

### 4. Reproducibilidad
- Fijar semillas para números aleatorios: `set.seed(123)`
- Documentar versiones de paquetes
- Incluir información de sesión al final

## Extensiones Útiles

### Callouts (Cajas de texto)
```markdown
::: {.callout-note}
Esta es una nota importante.
:::

::: {.callout-warning}
¡Cuidado con este código!
:::

::: {.callout-tip}
Consejo útil para el lector.
:::
```

### Referencias Cruzadas
```markdown
Como vemos en @fig-grafico-importante...
Los resultados se muestran en @tbl-resultados...
```

### Bibliografía
```markdown
Según @autor2023, los resultados muestran...
```

## Comandos de Git Recomendados

```bash
# Inicializar repositorio
git init

# Archivo .gitignore recomendado
echo "_book/
_freeze/
.Rproj.user/
*.Rproj" > .gitignore

# Primer commit
git add .
git commit -m "Configuración inicial del proyecto Quarto"
```

## Recursos Adicionales

- [Documentación oficial de Quarto](https://quarto.org/docs/books/)
- [Guía de Quarto Books](https://quarto.org/docs/books/book-basics.html)
- [Ejemplos de libros en Quarto](https://quarto.org/docs/gallery/#books)
- [R for Data Science (2e)](https://r4ds.hadley.nz/) - Ejemplo de libro hecho con Quarto

## Solución de Problemas Comunes

### Error: "Quarto not found"
```bash
# Verificar instalación
quarto --version

# Reinstalar si es necesario desde https://quarto.org/docs/get-started/
```

### Problemas de renderizado
1. Verificar que todos los paquetes R estén instalados
2. Revisar la sintaxis YAML en `_quarto.yml`
3. Comprobar que no hay chunks de código con errores

### Cache issues
```bash
# Limpiar cache
quarto clean
```

## Checklist para Publicación

- [ ] Todos los capítulos renderizan sin errores
- [ ] Las referencias cruzadas funcionan correctamente
- [ ] Las figuras tienen captions apropiados
- [ ] El índice se genera correctamente
- [ ] Los links externos funcionan
- [ ] La bibliografía está completa (si aplica)
- [ ] El formato PDF se ve correcto
- [ ] El formato HTML es responsive

---

**Fecha de creación:** `r Sys.Date()`  
**Versión de Quarto:** `r system("quarto --version", intern = TRUE)`  
**Versión de R:** `r R.version.string`








# Fuente de la información del USUARIO

Tema: paquete data.table


## Estructura

Módulo 1: Fundamentos y Sintaxis Esencial (El "Porqué" y el "Cómo")
# --- 1. Introducción a data.table ----
¿Qué es un data.table y en qué se diferencia de un data.frame?
La filosofía de data.table: velocidad, eficiencia de memoria y sintaxis concisa.
Creación de un data.table: data.table() y as.data.table().
El operador <- vs. := (una primera mirada a la modificación por referencia).
# --- 2. La Sintaxis General: DT[i, j, by] ----
Desglose de la estructura: DT[i, j, by] como el corazón de data.table.
i: Selección/filtrado de filas. Uso de expresiones lógicas y el alias .N.
j: Selección y transformación de columnas. El papel de .() y list().
by: Agrupación y operaciones por grupo. La base de la computación eficiente.

Módulo 2: Manipulación de Datos Intermedia
# --- 3. Encadenamiento de Operaciones (Chaining) ----
La sintaxis DT[...] [...] [...] como alternativa legible al anidamiento de funciones.
Comparativa con el pipe (%>% o |>) de dplyr. Ventajas y desventajas.
# --- 4. Uniones de Datos (Joins) ----
Estableciendo "llaves" con setkey(). ¿Por qué y cuándo es crucial para el rendimiento?
Tipos de joins: merge(), DT[X], y el uso de on = .().
Joins de actualización (update joins) usando :=.

Módulo 3: Técnicas Avanzadas y Funciones Especiales
# --- 5. El Poder de := (Modificación por Referencia) ----
Entendiendo a fondo la modificación por referencia y sus implicaciones en la memoria.
Crear, actualizar y eliminar columnas con :=.
El uso de copy() para evitar efectos secundarios no deseados.
Caso de estudio: ¿Cuándo te puede "morder" la modificación por referencia si no tienes cuidado?
# --- 6. Los Símbolos Especiales: .SD, .SDcols, .I, .GRP ----
.SD (Subset of Data): Aplicar funciones a un subconjunto de columnas por grupo.
Uso de .SDcols para especificar las columnas sobre las que actúa .SD.
Casos de uso avanzados con lapply(.SD, ...).
Otros símbolos útiles: .I (índices de fila), .GRP (identificador de grupo), etc.
# --- 7. Joins Avanzados: No-Equi Joins y Rolling Joins ----
Non-equi joins: Unir tablas basadas en desigualdades (>=, <, etc.).
Rolling joins: Una característica estrella para series temporales (ej. roll = TRUE, roll = "nearest").
# --- 8. Remodelación de Datos: melt y dcast ----
De formato ancho a largo (melt).
De formato largo a ancho (dcast).
Funciones de agregación dentro de dcast.

Módulo 4: Optimización y Buenas Prácticas
# --- 9. Optimización del Rendimiento ----
Uso de setkey() y setindex() para acelerar filtros y joins.
Buenas prácticas de escritura de código para maximizar la velocidad.
Configuración de hilos con setDTthreads() y getDTthreads().
# --- 10. Do's y Don'ts (Los Mandamientos de data.table) ----
Errores comunes y cómo evitarlos.
Consejos prácticos extraídos directamente de la comunidad y la documentación oficial.

Módulo 5: Integración con el Ecosistema R
# --- 11. data.table con ggplot2, shiny y tidymodels ----
Flujos de trabajo eficientes para la visualización y modelado.
El paquete dtplyr: una traducción de la sintaxis dplyr a data.table. ¿Cuándo usarlo?



## referencias y fuentes de la información

https://franknarf1.github.io/r-tutorial/_book/index.html#getting-started-with-r
https://cran.r-project.org/web/packages/data.table/vignettes/datatable-intro.html
https://rdatatable.gitlab.io/data.table/reference/data.table.html#examples
https://raw.githubusercontent.com/rstudio/cheatsheets/master/datatable.pdf
https://cran.r-project.org/web/packages/data.table/data.table.pdf
https://github.com/Rdatatable/data.table/wiki
https://github.com/Rdatatable/data.table/wiki/Articles
https://arelbundock.com/posts/dt_tb_df/index.html
https://stata2r.github.io/data_table/
https://anirban166.github.io/data%20table/data.table.threads/
https://rdatatable-community.github.io/The-Raft/posts/2024-10-17-duckdb_polars_reshape-toby_hocking/



https://github.com/Rdatatable/data.table/wiki/Do%27s-and-Don%27ts



## boceto del tutorial

---

### # --- 1. Introducción a `data.table` ----

#### ¿Qué es un `data.table`?

Imagina un `data.frame` de R que ha pasado un tiempo en el gimnasio y ha estudiado ingeniería de software. Un `data.table` **es** un `data.frame`, pero mejorado. Hereda toda la estructura de `[fila, columna]` que ya conoces, pero le añade superpoderes en velocidad, manejo de memoria y una sintaxis más directa para operaciones complejas.

La clave es que no es un objeto completamente nuevo y extraño; es una evolución. Esto significa que la mayoría de las funciones que esperan un `data.frame` (como las de `ggplot2` o muchos paquetes de modelado) funcionarán sin problemas con un `data.table`.

---

#### La Filosofía de `data.table`

`data.table` se construyó con tres objetivos principales en mente:

1.  **Velocidad 🚀:** Las operaciones internas están escritas en C y altamente optimizadas. Para conjuntos de datos grandes (cientos de miles o millones de filas), la diferencia de tiempo con `dplyr` o R base puede ser de segundos a minutos, o incluso horas.
2.  **Eficiencia de Memoria 🧠:** Su característica más distintiva es la **modificación por referencia**. Cuando usas el operador especial `:=`, `data.table` no crea una copia del objeto en memoria para añadir o cambiar una columna, sino que lo modifica directamente. Esto es radicalmente diferente al comportamiento de "copiar al modificar" de R base y `dplyr`.
3.  **Sintaxis Concisa y Consistente ✍️:** Casi todo lo que necesitas hacer se puede expresar dentro de los corchetes `[ ]` con la estructura `DT[i, j, by]`, lo que hace el código más corto y, una vez que te acostumbras, más legible.

---

#### Creando un `data.table`

Vamos a ver el código. Primero, asegúrate de tener la librería instalada y cargada.

```R
# install.packages("data.table") # Si no lo tienes
library(data.table)

# Convertimos el data.frame 'iris' a un data.table
iris_dt <- as.data.table(iris)

# También podemos crearlo desde cero
mi_dt <- data.table(
  ID = c("A", "B", "C", "A", "B"),
  Valor = 1:5,
  Categoria = factor(c("Tipo1", "Tipo2", "Tipo1", "Tipo1", "Tipo2"))
)

# Imprime el data.frame original
iris

# Imprime el data.table
iris_dt
```

La salida de `data.table` es más limpia: muestra las primeras y últimas filas y te informa del número total de filas, lo cual es muy práctico para data sets grandes.

#### El Operador `<-` vs. `:=` (Un Vistazo Inicial)

Esta es probablemente la diferencia conceptual más importante. En R base, `<-` crea una copia en memoria para modificar un objeto. `:=` de `data.table` modifica el objeto original directamente, sin crear copias, lo que lo hace mucho más eficiente.

```R
# --- Enfoque data.table (Modificación por Referencia) ---
iris_dt[, NuevaColumna := Sepal.Length * 2]
```
Profundizaremos en esto más adelante, pero es la piedra angular de la eficiencia de `data.table`.

---
---

### # --- 2. La Sintaxis General: `DT[i, j, by]` ----

Pensemos en esto como si fuera una pregunta que le haces a tus datos. La estructura `DT[i, j, by]` se traduce a:

"Toma mi `data.table` (`DT`), filtra las filas **donde** (`i`) se cumple una condición, luego **haz** (`j`) este cálculo o selección, **agrupando por** (`by`) esta variable".

]

#### **`i`**: El Filtro de Filas (El "Dónde")

Aquí es donde le dices a `data.table` qué filas te interesan. Usas expresiones lógicas.

```R
# Filas donde Species es "setosa"
iris_dt[Species == "setosa"]

# Múltiples condiciones: Species es "virginica" Y Petal.Width > 2
iris_dt[Species == "virginica" & Petal.Width > 2]

# .N es un símbolo especial para el número total de filas.
# Selecciona la última fila del data.table.
iris_dt[.N]
```

#### **`j`**: La Selección/Cálculo (El "Qué Hacer")

Aquí es donde seleccionas columnas o realizas cálculos sobre ellas. La sintaxis clave aquí es usar `.()`, que es un alias para `list()`. Le dice a `data.table`: "quiero que me devuelvas un nuevo `data.table` con estos resultados".

```R
# Seleccionar solo la columna Sepal.Length
iris_dt[, .(Sepal.Length)]

# Crear una nueva columna sobre la marcha (el resultado es un nuevo data.table)
iris_dt[, .(Area.Sepalo = Sepal.Length * Sepal.Width)]
```
**Importante:** Lo que hacemos en `j` con `.()` **devuelve un resultado**, no modifica `iris_dt`.

#### **`by`**: La Agrupación (El "Agrupado Por")

Esta es la respuesta de `data.table` al `group_by()` de `dplyr`. Le dices a `data.table` que ejecute la expresión `j` para cada grupo único definido en `by`.

```R
# Calcular la media de Sepal.Length PARA CADA Species
iris_dt[, .(Media.Sepal.Length = mean(Sepal.Length)), by = .(Species)]
```

#### **Ejercicio 1:**
Usando el `data.table` `iris_dt`, ¿cómo le pedirías la **media de `Petal.Width`** solo para la especie **"versicolor"**?

#### **Solución al Ejercicio 1:**
El código `iris_dt[Species == "versicolor", mean(Petal.Width)]` es funcional y da el resultado numérico correcto. Sin embargo, una pequeña mejora sigue la "filosofía `data.table`" y es mucho más potente para flujos de trabajo.

```R
# Tu código (funciona y es correcto para un vistazo rápido)
iris_dt[Species == "versicolor", mean(Petal.Width)]

# La forma idiomática de data.table (más robusta)
iris_dt[Species == "versicolor", .(Media_Petal_Width = mean(Petal.Width))]
```
La diferencia es sutil pero clave:
* La primera versión devuelve un **vector numérico** simple.
* La segunda versión, usando `.()` y nombrando la columna, devuelve un **nuevo `data.table`**, que es mucho más útil para seguir trabajando con él.

---
---

### # --- 3. Encadenamiento de Operaciones (Chaining) ----

El "chaining" o encadenamiento es simplemente la idea de realizar una operación justo después de otra sobre el resultado de la anterior, todo en una sola línea de código fluida. La sintaxis es `DT[...] [...] [...]`.

**Ejemplo:**
1.  **Filtrar** `iris_dt` para quedarnos solo con "versicolor" y "virginica".
2.  Luego, sobre ese resultado, **agrupar** por `Species` y **calcular** la media de `Sepal.Length`.

```R
# Paso 1: Filtro  ->  Paso 2: Agrupación y cálculo
iris_dt[Species %in% c("versicolor", "virginica")][, .(Media_Sepal_Length = mean(Sepal.Length)), by = Species]
```

#### **Ejercicio 2:**
¿Cómo encadenarías dos operaciones para encontrar la `Petal.Length` **máxima** de la especie con el `Sepal.Width` **promedio más alto**?

#### **Solución al Ejercicio 2:**
La solución `iris_dt[Species == iris_dt[, .(mean_Sepal.Width = mean(Sepal.Width)), Species][which.max(mean_Sepal.Width), Species], .(max_Petal.Length = max(Petal.Length)), Species]` es una forma impresionante y correcta de resolverlo usando una subconsulta. Es potente y atómica.

Una forma alternativa que usa encadenamiento con `order()` y puede ser más legible es la siguiente:

```R
# Paso 1: Calcular la media y ordenar los resultados en orden descendente.
result_ordenado <- iris_dt[, .(Media_Sepal_Width = mean(Sepal.Width)), by = Species][order(-Media_Sepal_Width)]

# Paso 2: Extraer el nombre de la especie superior (que ahora está en la primera fila)
top_species <- result_ordenado[1, Species]

# Paso 3: Usar ese nombre para filtrar la tabla original y obtener el resultado final
iris_dt[Species == top_species, .(Max_Petal_Length = max(Petal.Length))]
```
Ambos métodos son válidos. El primero es un "one-liner" potente, el segundo es más explícito en sus pasos.

---
---

### # --- 4. Uniones de Datos (Joins) ----

`data.table` ofrece dos formas principales de unir tablas: usando **llaves (`keys`)** (el método más rápido para uniones repetitivas) o el argumento **`on`** (más flexible para uniones puntuales).

#### Estableciendo "Llaves" con `setkey()` 🔑
`setkey()` ordena físicamente la tabla por una columna, permitiendo búsquedas y uniones casi instantáneas. Modifica la tabla por referencia.

```R
# Tablas de ejemplo
transacciones_dt <- data.table(transaction_id = 1:6, product_id = c("A", "B", "A", "C", "B", "C"), cantidad = c(10, 5, 8, 15, 6, 12))
productos_dt <- data.table(product_id = c("A", "B", "C"), nombre_producto = c("Manzana", "Naranja", "Pera"), precio = c(1.2, 0.8, 1.5))

# Establecemos la llave en la columna común
setkey(transacciones_dt, product_id)
setkey(productos_dt, product_id)
```

#### Sintaxis de Join: `DT1[DT2]`
Con las llaves establecidas, la sintaxis de join es trivial.
```R
# Unir 'transacciones_dt' a 'productos_dt' (Equivalente a un Left Join)
productos_dt[transacciones_dt]
```

#### Joins Flexibles con `on =`
Para uniones puntuales sin modificar la tabla, se usa `on`.
```R
# Hacemos el mismo join usando 'on'
productos_dt[transacciones_dt, on = .(product_id)]
```

#### **Ejercicio 3:**
Usando el método `on =`, ¿cómo unirías las dos tablas y añadirías una nueva columna llamada `ingreso_total` que sea el resultado de `cantidad * precio`?

#### **Solución al Ejercicio 3:**
La solución `productos_dt[transacciones_dt, on = .(product_id)][, ingreso_total := cantidad * precio]` es perfecta. Es idiomática y eficiente.

1.  `productos_dt[transacciones_dt, on = .(product_id)]`: Primero realizas el join. Esto crea en memoria un nuevo `data.table` que contiene todas las columnas de ambas tablas.
2.  `[, ingreso_total := cantidad * precio]`: Luego, encadenas una operación `:=` sobre ese resultado para crear la nueva columna de forma súper eficiente.

Una alternativa avanzada es el **"Update Join"**, que modifica una de las tablas originales directamente.

```R
# "Update join": une y actualiza en un solo paso
transacciones_dt[productos_dt, on = .(product_id), ingreso_total := i.precio * cantidad]

# Ahora la tabla 'transacciones_dt' original ha sido modificada
print(transacciones_dt)
```
El prefijo `i.` se usa para referirse a las columnas de la tabla de "dentro" del join (`productos_dt` en este caso).

---
---

### # --- 5. El Poder de `:=` (Modificación por Referencia) ----

El operador `:=` modifica el `data.table` original directamente en la memoria. Es como escribir con un bolígrafo sobre el documento original.

* **R Base / `dplyr` (`<-` o `mutate`)**: Fotocopia, modifica la copia, reemplaza el original.
* **`data.table` (`:=`)**: Edita el original directamente.



#### Usos Principales de `:=`

```R
# Recrear tabla para ejemplos
transacciones_dt <- data.table(transaction_id = 1:6, product_id = c("A", "B", "A", "C", "B", "C"), cantidad = c(10, 5, 8, 15, 6, 12))

# 1. Añadir MÚLTIPLES columnas a la vez
transacciones_dt[, `:=`(stock_bajo = cantidad < 10, cliente_id = c(101, 102, 101, 103, 102, 103))]

# 2. Actualizar columnas condicionalmente
transacciones_dt[cantidad > 10, es_pedido_grande := TRUE]

# 3. Eliminar columnas
transacciones_dt[, c("stock_bajo", "es_pedido_grande") := NULL]
```

#### La "Zona de Peligro" y la Función `copy()`

Asignar un `data.table` con `<-` NO crea una copia. `dt_alias <- dt_original` solo crea un nuevo nombre que apunta a los mismos datos en memoria. Para crear una copia real e independiente, se debe usar `copy()`.

```R
dt_original <- data.table(x = 1:3)
dt_copia <- copy(dt_original) # Copia independiente
dt_copia[, y := x * 2]

# dt_original permanece intacto
print(dt_original)
```

#### **Ejercicio 4:**
1.  Crea una copia de nuestra `transacciones_dt` actual y llámala `transacciones_analisis`.
2.  En `transacciones_analisis`, crea una nueva columna `prioridad`.
3.  Establece el valor de `prioridad` a **"Alta"** para las transacciones cuyo `product_id` sea "A" o "C".
4.  Finalmente, elimina la columna `cliente_id` de `transacciones_analisis`.

#### **Solución al Ejercicio 4:**
```R
# Estado de la tabla original para el ejercicio
transacciones_dt <- data.table(
  transaction_id = 1:6, product_id = c("A", "B", "A", "C", "B", "C"),
  cantidad = c(10, 5, 8, 15, 6, 12), cliente_id = c(101, 102, 101, 103, 102, 103)
)

# 1. Crear una copia independiente
transacciones_analisis <- copy(transacciones_dt)

# 2 & 3. Crear la columna y actualizarla condicionalmente
transacciones_analisis[, prioridad := "Normal"] # Asignar valor por defecto primero
transacciones_analisis[product_id %in% c("A", "C"), prioridad := "Alta"]

# 4. Eliminar la columna 'cliente_id'
transacciones_analisis[, cliente_id := NULL]

# --- Verificación Final ---
print("Tabla Original:")
print(transacciones_dt)
print("Tabla de Análisis:")
print(transacciones_analisis)
```

---
---

### # --- 6. Los Símbolos Especiales: `.SD`, `.SDcols`, `.I`, `.GRP` ----

#### `.SD`: El Subconjunto de Datos (Subset of Data)

`.SD` es una mini-tabla temporal que contiene los datos del grupo actual en una operación `by`. Su uso más común es con `lapply()` para aplicar una función a varias columnas a la vez.

#### `.SDcols`: Especificando las Columnas

Por defecto, `.SD` contiene todas las columnas excepto las de agrupación. Para controlar qué columnas se incluyen, se usa `.SDcols`, lo cual es más limpio y eficiente.

```R
# Calcular la media de todas las columnas de medidas para cada Species
columnas_a_calcular <- c("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width")
iris_dt[, lapply(.SD, mean), by = Species, .SDcols = columnas_a_calcular]
```

#### **Ejercicio 5:**
Usando `.SD` y `.SDcols` sobre el `iris_dt`, ¿cómo calcularías el **valor máximo** (`max`) de las columnas que **empiezan con "Petal"**, agrupando por `Species`?

#### **Solución al Ejercicio 5:**
La forma más directa es especificando las columnas manualmente. Una forma más programática y robusta usa la función `patterns()` de `data.table`.

```R
# Solución usando patterns() para seleccionar columnas dinámicamente
iris_dt[
  ,
  lapply(.SD, max),
  by = Species,
  .SDcols = patterns("^Petal") # Elige columnas que empiecen (^) con "Petal"
]
```
---
---

### # --- 7. Joins Avanzados: No-Equi Joins y Rolling Joins ----

#### Non-Equi Joins (Uniones por Desigualdad)
Permiten unir tablas basadas en un rango de valores, no en una coincidencia exacta.

```R
# Ejemplo: Asignar pacientes a un rango de riesgo por su nivel de glucosa
pacientes_dt <- data.table(paciente_id = c("A", "B", "C", "D"), glucosa = c(85, 130, 105, 190))
riesgo_dt <- data.table(glucosa_min = c(70, 100, 126), glucosa_max = c(99, 125, 200), riesgo = c("Normal", "Elevado", "Alto"))

# El Non-Equi Join
riesgo_dt[pacientes_dt, on = .(glucosa_min <= glucosa, glucosa_max >= glucosa), .(paciente_id, riesgo)]
```

#### Rolling Joins (Uniones Rodantes) ↔️
Característica estrella para series temporales. Une cada fila a la última observación ocurrida en o antes de su marca de tiempo en la otra tabla.

```R
# Ejemplo: Asignar a cada venta el precio vigente en ese momento
cotizaciones_dt <- data.table(tiempo = as.POSIXct(c("2025-08-20 10:00:00", "2025-08-20 10:05:00", "2025-08-20 10:15:00")), precio = c(100.5, 100.8, 100.7))
ventas_dt <- data.table(tiempo = as.POSIXct(c("2025-08-20 10:02:00", "2025-08-20 10:05:00", "2025-08-20 10:18:00")), cantidad = c(10, 5, 20))
setkey(cotizaciones_dt, tiempo) # Requiere llave en la columna de tiempo

# Rolling Join: Para cada venta, encuentra la última cotización
cotizaciones_dt[ventas_dt, roll = TRUE]
```
---
---

### # --- 8. Remodelación de Datos: `melt` y `dcast` ----

`melt()` y `dcast()` sirven para pivotar datos, pasando de formato "ancho" a "largo" y viceversa.

* `melt()`: "Derrite" una tabla ancha, convirtiendo columnas en filas.
* `dcast()`: "Moldea" una tabla larga, convirtiendo filas en columnas.

#### **Ejercicio 6:**
1.  **`melt`**: Transforma `iris_dt` a un formato largo. La única columna identificadora (`id.vars`) debe ser `Species`.
2.  **`dcast`**: Sobre la tabla larga que acabas de crear, calcula la **media** de cada `Metrica` para cada `Species` y vuelve a ponerla en un formato ancho. (Pista: necesitarás `fun.aggregate = mean`).

#### **Solución al Ejercicio 6:**
Una solución elegante combina los pasos. Primero se "derrite", luego se agrega, y finalmente se "moldea".
```R
resultado_final <- melt(
  iris_dt,
  id.vars = "Species",
  measure.vars = patterns("Sepal|Petal"),
  variable.name = "Metrica",
  value.name = "Valor"
)[, 
  .(Media_Valor = mean(Valor)), # Agregamos los datos en formato largo
  by = .(Species, Metrica)
][, 
  dcast(.SD, Species ~ Metrica, value.var = "Media_Valor") # Reestructuramos a formato ancho
]

print(resultado_final)
```
---
---

### # --- 9. Optimización del Rendimiento ----

Para escribir código rápido, hay que entender cómo piensa el paquete.
* **`setkey()`**: Tu herramienta principal. Reordena físicamente los datos para filtros y joins ultra-rápidos.
* **`setindex()`**: Una alternativa ligera a `setkey`. Crea un índice para acelerar filtros sin reordenar la tabla. Ideal para "llaves secundarias".
* **`setDTthreads()`**: Controla el número de núcleos de CPU que `data.table` utilizará para operaciones paralelizadas.
* `options(datatable.verbose = TRUE)`: Activa un modo detallado que muestra qué optimizaciones está usando `data.table` internamente. Es excelente para aprender y depurar.

---
---

### # --- 10. Do's y Don'ts (Los Mandamientos de `data.table`) ----

#### Qué HACER ✅
1.  **HAZ `:=` tu principal herramienta de modificación.**
2.  **HAZ de `fread()` tu lector de archivos por defecto.** Es increíblemente rápido e inteligente.
3.  **HAZ uso de `setkey()` y `setindex()` en tablas grandes.** La diferencia de rendimiento es espectacular.
4.  **HAZ que tu salida sea un `data.table` usando `.()` en `j`.**
5.  **HAZ `copy()` explícitamente cuando necesites un objeto independiente.**

#### Qué NO HACER ❌
1.  **NO uses números de fila en `i` (como `DT[100:200, ]`).** Está optimizado para búsquedas lógicas y por llave.
2.  **NO uses `dplyr` u otros verbos directamente sobre un `data.table` (sin `dtplyr`)**. Puede forzar copias y destruir el rendimiento.
3.  **NO uses bucles `for` para operar por grupos.** Usa el argumento `by`.
4.  **NO uses `apply(DT, 1, ...)` para operar por filas.** Piensa siempre en operaciones vectorizadas por columnas.
5.  **NO olvides el prefijo `i.` en los joins de actualización.**

---
---

### # --- 11. Integración con el Ecosistema R ----

Un `data.table` **es** un `data.frame`, por lo que se integra de forma nativa con la mayoría de paquetes.

* **`ggplot2` 📊**: Haz todo el trabajo pesado de preparación de datos en `data.table` primero. El `data.table` final, limpio y agregado, se pasa directamente a `ggplot()` sin necesidad de conversiones.
* **`shiny` ✨**: Es el motor perfecto para apps de Shiny rápidas y responsivas. La velocidad de `data.table` en las expresiones reactivas mejora drásticamente la experiencia del usuario.
* **`tidymodels` 🤖**: Usa `data.table` para la ingeniería de características a alta velocidad (crear variables, unir fuentes de datos). El `data.table` final con todas las variables se pasa directamente a `initial_split()` y `recipe()`.

---


## Estilo

A la hora de escribir utiliza el tema personalizado de estilos llamado "Mi estilo academico" (se definió para claiude) en vez de "Normal" predeterminado 