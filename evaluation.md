# 1. Evaluación

Las métricas que se emplearon en la anterior entrega han sido relevantes para evaluar la validez de nuestras hipótesis.

Nuestro proyecto se centra en dividir los datos en día y noche y comparar si aspectos como el estado del cielo o la temperatura afectan a el número de tweets. O si el estado del cielo afecta al sentimiento (positivo o negativo) en los tweets.

## 1.1. Descripción de las Métricas Utilizadas

### 1.1.1. ANOVA

El análisis de varianza (ANOVA) se utiliza para comparar las medias de tres o más grupos y determinar si existen diferencias significativas entre ellos. Se basa en la variabilidad de los datos dentro de cada grupo y entre los grupos para evaluar si las diferencias observadas son mayores que las que podrían ocurrir por azar.

E análisis de varianza (ANOVA) fue útil en este caso porque permitió evaluar si existen diferencias significativas en el número de tweets en función del estado del cielo, tanto durante el día como durante la noche. Dado que los datos incluyen varias categorías de estado del cielo (nublado, despejado, parcialmente nublado) y dos períodos del día con comportamientos potencialmente diferentes, ANOVA permitió comparar estas categorías y determinar si el estado del cielo influye de manera significativa en la actividad de los tweets. Esta herramienta fue adecuada para analizar las variaciones entre múltiples grupos y entender mejor los factores que afectan la publicación de tweets en diferentes momentos del día.

### 1.1.2. Correlación de Pearson y de Spearman 

El análisis de correlación de Pearson mide la relación lineal entre dos variables, mientras que la correlación de Spearman evalúa relaciones monótonas, es decir, cómo varían las variables de forma consistente, sin necesidad de ser lineales. Ambas métricas son útiles en este caso para identificar y cuantificar la relación entre la temperatura y el número de tweets, ya que nos permiten entender si existe alguna tendencia o patrón consistente entre estas dos variables. La combinación de ambos enfoques proporciona una visión más completa, considerando tanto relaciones lineales como no lineales.


### 1.1.3. Log Likelihood y Perplexity
     
Log likelihood: representa cuán probable es que el modelo haya generado los datos observados. Un valor más alto (menos negativo) significa que el modelo se ajusta mejor a los datos, explica mejor los datos, o que captura bien las distribuciones subyacentes. Es relevante para evaluar los resultados ya que nos permite ver qué periodo entre los datos diurnos y nocturnos tiene patrones más consistentes o predecibles.

Perplexity: es una métrica derivada de log likelihood, y mide la incertidumbre del modelo al predecir los datos. Valores más bajos de perplexity indican un modelo más seguro y enfocado; valores más altos, un modelo más disperso y general. En este caso, comparar la perplexity de los datos diurnos y nocturnos puede dar información adicional sobre la naturaleza de los temas, si son más generales o específicos por ejemplo.

La diferencia clave entre estos dos es que mientras la log likelihood mide cómo el modelo ajusta los datos observados, la perplexity evalúa la calidad de las predicciones del modelo.

### 1.1.4. U_mass y C_v

Las métricas de coherencia como u_mass y c_v son herramientas utilizadas para evaluar la calidad de los modelos de tópicos al analizar cómo de bien están relacionadas semánticamente las palabras dentro de un tópico. Estas métricas ayudan a interpretar y comparar diferentes configuraciones de modelos.

- u_mass: Es una métrica basada en la probabilidad conjunta de las palabras dentro de un tópico, calculada a partir de un corpus de referencia. Utiliza las frecuencias de aparición de las palabras en los documentos para evaluar la relación entre ellas. Es intrínseca, ya que se calcula únicamente con los datos del modelo y no requiere información externa. Los valores suelen ser negativos y más cercanos a 0 indican mayor coherencia.

- c_v: Es una métrica basada en las co-ocurrencias de palabras, que utiliza un enfoque de ventana deslizante para evaluar qué tan a menudo las palabras aparecen juntas en un corpus de texto. Esta métrica combina datos estadísticos con información semántica extraída de un corpus externo. Es extrínseca, ya que evalúa las palabras del modelo en función de un corpus externo, lo que puede aumentar su interpretabilidad. Sus valores están en un rango positivo (generalmente entre 0 y 1), donde valores más altos indican una mejor coherencia. Es más robusta y confiable que u_mass cuando el modelo está diseñado para temas complejos o corpus grandes.

### 1.1.5. P valor variables exógenas

En el análisis se utilizó el p-valor para evaluar la significancia estadística de las variables exógenas en el modelo SARIMAX. El p-valor mide la probabilidad de obtener un resultado al menos tan extremo como el observado, asumiendo que la hipótesis nula es verdadera. En este caso, la hipótesis nula establece que la variable exógena no tiene un efecto significativo sobre la serie temporal. Un p-valor bajo (generalmente menor a 0.05) indica que es poco probable que la relación observada sea fruto del azar, lo que justifica incluir la variable en el modelo. Esta métrica es útil porque permite identificar qué factores exógenos tienen un impacto real en la dinámica del número de tweets, asegurando la validez estadística de las conclusiones del modelo.

## 1.2. Resultados de las Evaluaciones

### 1.2.1. Relación entre estado del cielo y número total y sentimiento de tweets

En un primer análisis visual descubrimos que, durante la noche, las horas con mayor número de tweets pertenecen a un cielo nublado. Pero esto no implica que por está nubado vayan a haber un gran número de tweets, ya que las horas nubladas también constan de un número de tweets bajo. De hecho, durante el día los mayores picos pertenecen a cielo despejado. Ya que esta visualización no es muy concluyente realizamos un análisis anova. El motivo de dividir entre día y noche es que el etiquetamiento de los datos de estados del cielo tiene diferentes etiquetas para un mismo estado si pertenece a día o noche, y consideramos que estaba bien dejarlo así y no juntar esas etiquetas en una categoría.

Con el uso del Anova intentamos ver con una métrica si hay una diferencia significativo entre el estado del cielo y el número de tweets de cada uno. Los grupos son partly cloudy, clear y cloudy. Se divide tambien entre día y noche. 

Observando el número de tweets durante el día, no existen diferencias estadísticamente significativas entre los grupos de estados del cielo (p = 0.1977). Esto sugiere que, dando igual si el cielo está despejado, parcialmente nublado o nublado, esto no afecta al nnúmero de tweets en cada hora. Pero en la noche, el valor p (p = 0.0098) indica que sí hay diferencias entre los estados del cielo (lo consideramos así al superar por debajo el umbral de 0.05). Estos resultados apoyan la hipótesis de que el estado del cielo durante la noche influye en la cantidad de tweets publicados, apoyando el análisis realizado anteriormente, donde se observaron mayores niveles de actividad en condiciones de cielo nublado.

Diferenciando entre solo tweets con sentimientos positivos, durante el día no se ven diferencias entre los estados del cielo (p = 0.0922), aunque este valor se aproxima al umbral comúnmente aceptado, que es de 0.05. Esto sugiere una tendencia que no podemos catalogar como concluyente. Pero otra vez, durante la noche, los resultados muestran diferencias entre los estados del cielo (p = 0.0436), lo cual indica que el estado del cielo influye en el número de tweets positivos.

Por último, para los tweets negativos, de nuevo durante el día vemos una ausencia de diferencias significativas (p = 0.2187). Sin embargo, durante la noche, volvemos a ver diferencias entre los grupos de estados del cielo (p = 0.0177).

Los resultados que nos ha dado el ANOVA en cada caso indica que el estado del cielo tiene un impacto durante la noche en el número total de tweets, así como en la cantidad de tweets positivos y negativos durante esta etapa, pero no durante el día. Se apoya la observación inicial de una mayor actividad en condiciones de cielo nublado durante la noche, e indica que podría estar relacionado con patrones específicos de comportamiento en redes sociales durante la noche.

### 1.2.2. Relacion entre temperatura y número total y sentimiento de tweets 

Para empezar este análisis de correlación entre la temperatura y el número de tweets se obtiene tanto un gráfico mostrando la tendencia de la temperatura media a lo largo de las horas, diferenciando entre día y noche, como la cantidad de tweets publicada por hora.

En los gráficos se aprecia claramente durannte el día que ambas variables presentan un comportamiento similar. Sin embargo, durante la noche, esta relación visual no es tan clara, ya que las tendencias muestran mayores diferencias, pareciendose más a una relación indirecta.

Posteriormente, se va a comprobar, más profundamente, si existe una relación entre la temperatura y los tweets.

Para visualizar la correlación entre la temperatura con los tweets, se hace un análisis por separado del día y de la noche y otro análisis de los sentimientos.

La correlación entre temperatura y número de tweets es positiva pero moderada (Pearson: 0.21, Spearman: 0.26). Al separar por períodos, durante el día (Pearson: 0.37, Spearman: 0.32) y la noche (Pearson: 0.33, Spearman: 0.34), ambas son significativas pero aún son moderadas como para destacarlas.

En el análisis de sentimientos, se observa una correlación moderada entre temperatura y tweets positivos (Pearson y Spearman: 0.32), mientras que no hay relación alguna con los tweets negativos (Pearson: 0.02, Spearman: 0.01).

Podría haber una relación positiva entre temperatura y actividad en redes sociales, especialmente durante el día y en tweets con sentimientos positivos, pero consideramos los resultados como demasiado débiles. 

Incluso si los resultados hubieran sido altos, es importante destacar que este análisis no es concluyente. Una aparente relación entre dos variables, como la temperatura y el número de tweets, no implica causalidad. Existen otros factores externos que pueden influir en esta relación, como las horas del día en las que las personas tienen mayor tiempo libre para publicar en redes sociales.

### 1.2.3. Análisis de topics en día y noche con LDA

Con el modelo Latent Dirichlet Allocation (LDA) analizamos los temas de los tweets durante el día y la noche. 

El Log Likelihood en la noche es de -24,736,576.43 y en el día es de -17,235,406.66, lo que indica un mejor ajuste del modelo durante el día, posiblemente porque los tweets diurnos siguen patrones más regulares (temas más generales y predecibles). 

Sin embargo, la Perplexity es más baja en la noche (4805.89) en comparación con el día (5740.83), sugiriendo que los temas nocturnos son más coherentes y específicos, es decir, hay menos incertidumbre en las predicciones del modelo para los tweets nocturnos.

Podríamos concluir que los temas diurnos son más generales y comunes, lo que explica la mayor log likelihood y perplexity. Los temas nocturnos, aunque menos frecuentes, son más específicos, lo que se refleja en una perplexity más baja.

Esto a pesar de no ser métricas significativas, resalta diferencias en la naturaleza de los temas según el momento del día.

### 1.2.4. Modelo dinámico de tópicos por mes

En un modelo dinámico de tópicos, los valores obtenidos reflejan las probabilidades de que cada palabra aparezca en los documentos asociados a un tópico específico. Un valor más alto indica que la palabra es más relevante para describir ese tópico. Estos valores se utilizan para identificar y etiquetar los tópicos en función de las palabras más representativas.

Dado que estos valores no son métricas de evaluación, vamos a emplear medidas de coherencia como u_mass y c_v para analizar el rendimiento del modelo.

Para el modelo 1, los resultados de coherencia obtenidos para el modelo dinámico de tópicos son los siguientes:

#### Análisis de u_mass:

- Mes 0: -0.0203
- Mes 1: -0.0212
- Mes 2: -0.0155

Los valores son negativos, algo común para esta métrica, ya que no está normalizada. Así, un valor cercano a 0 indica una mejor coherencia entre las palabras del tópico. Se puede observar una mejora ligera en el mes 2, sugiriendo una mayor relación semántica entre las palabras en los tópicos de este mes en comparación con los otros meses.

#### Análisis de c_v:

- Mes 0: 0.2686
- Mes 1: 0.2648
- Mes 2: 0.2550

Los valores disminuyen progresivamente del Mes 0 al Mes 2, lo que sugiere que la coherencia entre palabras dentro de los tópicos tiende a reducirse a lo largo del tiempo.

Ambos indicadores muestran valores moderados, lo que indica que los tópicos tienen una coherencia razonable pero no excepcional. La variación entre meses es pequeña en ambas métricas, lo que sugiere que el modelo es bastante estable y que los cambios temporales en los tópicos son moderados. En general, los resultados reflejan un modelo dinámico de tópicos que mantiene una coherencia moderada a lo largo del tiempo, aunque con ligeras variaciones en función de la métrica utilizada.

Para el modelo 2, los resultados de coherencia obtenidos para el modelo dinámico de tópicos son los siguientes:

#### Análisis de u_mass:

- Mes 0: -0.0255
- Mes 1: -0.0170
- Mes 2: -0.0132

Los valores son negativos al igual que en el modelo 1. Los valores se vuelven progresivamente menos negativos, con una diferencia significativa entre el Mes 0 y el Mes 2.

#### Análisis de c_v:

- Mes 0: 0.2654
- Mes 1: 0.2605
- Mes 2: 0.2561

El valor de c_v desciende ligeramente con el tiempo, lo que indica que las palabras más representativas dentro de los tópicos presentan menor coherencia en términos de co-ocurrencia en los meses posteriores.

Mientras que u_mass indica una mejora en la cohesión semántica de los tópicos con el tiempo, c_v muestra una ligera disminución en la coherencia basada en co-ocurrencias. Esta divergencia podría deberse a diferencias en cómo cada métrica evalúa la coherencia, con u_mass favoreciendo relaciones probabilísticas y c_v priorizando patrones observados en el corpus. A pesar de las pequeñas variaciones, el modelo se mantiene relativamente estable en términos de coherencia, lo cual es esperable en un modelo dinámico que captura cambios graduales en el tiempo.


Los resultados del modelo 2 muestran una mayor mejora en la coherencia semántica (u_mass), especialmente hacia el Mes 2, aunque parten de valores iniciales más bajos. Por otro lado, c_v tiene una ligera reducción en todos los meses en comparación con los resultados del modelo 1, pero sigue mostrando una tendencia decreciente similar.

### 1.2.5. P valor de variables exógenas

Los resultados del análisis indican que el p-valor para la variable exógena día o noche es 0.530, lo que sugiere que no tiene un efecto estadísticamente significativo sobre la serie temporal, ya que supera el umbral típico de 0.05. Por otro lado, el p-valor para la variable que representa los días de la semana es 0.000, lo que indica una relación altamente significativa con la serie temporal. Esto implica que el patrón semanal tiene un impacto relevante en la dinámica del número de tweets, mientras que la distinción entre día y noche no parece influir en este caso.


## 1.3. Limitaciones en la Evaluación

La principal limitación fue algo que nos hizo cambiar el enfoque del proyeto, ya que el primer análisis iba a ser sobre cómo afecta la precipitación a el número o sentimiento de los tweets. El problema es que, a pesar de que el dataset cuenta con un gran número de tweets, durante tres meses, los datos no son consistentes y hay horas e incluso días enteros que no tienen datos. La mala suerte que tuvimos fue que ya que trata de datos de verano, los pocos días que llovío, estaban arecándose justamente a las últimas fehcas del dataset, que es cuando mayor inconsistencia de datos hay. Por tanto, al no tener datos de tweets en los días de lluvia tuvimos que cambiar el enfoque a el estado del cielo, ya que si que se cuenta con bastantes horas parcialmente nubldo o nublado gracias a la columna icon que tiene estas categorías.

La ausencia de datos en ciertas horas de los tweets afecta la calidad del análisis ya que estas lagunas pueden sesgar las conclusiones. El modelo no tiene información completa para ciertos períodos, lo que podría llevar a una interpretación incorrecta de las tendencias. Además, los valores ausentes pueden alterar la distribución temporal de los datos y reducir la precisión de las correlaciones y análisis de los factores relacionados, como el clima o los sentimientos.

El hecho de que no se conozca la ubicación exacta de los tweets ni si provienen de una población específica, añadido a la falta de información sobre las edades de los usuarios, introduce un sesgo en el análisis. Sin detalles geográficos ni demográficos, es difícil saber si los datos representan a toda la población de Portugal o solo estamos investigando a un grupo particular, lo que limita la generalización de los resultados o ver cómo afectan ciertas variables ajenas al estudio. Este sesgo puede influir en la interpretación de las tendencias, ya que ciertos comportamientos podrían estar influenciados por factores regionales o de edad no explicados en el dataset.
