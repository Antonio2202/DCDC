# 1. Métodos

El proyecto comenzó con la idea de analizar si existe relación entre las horas en las que hayan precipitaciones y la cantidad de tweets publicados durante ese tiempo. La hipótesis plantea que la lluvia podría influir no solo en la actividad en redes sociales si no también en las emociones expresadas en dichas publicaciones. Se realizó un cruce entre los datos de precipitaciones y las marcas temporales de los tweets en el dataset. Sin embargo, se identificó el hecho de que no había datos de tweets para todas las horas incluidas en el rango temporal de lluvia. Esta falta de información impidió llevar a cabo el análisis inicialmente propuesto.

Se decidió replantear el enfoque del análisis y centrarse en otras variables meteorológicas del dataset. Se propuso investigar el impacto de tanto la temperatura como el estado del cielo (columna *icon*) en el número y el sentimiento de los tweets. En este caso, la variable *icon* no solo proporciona información sobre el estado del cielo, diferenciando entre despejado, nublado y lluvioso, sino que también clasifica estos estados según el momento del día, distinguiendo entre día y noche. Esto permitió incorporar al análisis una dimensión temporal adicional.

## 1.1. Análisis de la condición meteorológica y el número de tweets en función del día y la noche

El proceso comenzó con la segmentación de los datos en dos categorías principales: día y noche. A partir de esta clasificación, se analizaron los efectos que las variables de estado del cielo podrían tener sobre la cantidad de tweets, diferenciando entre las dos franjas temporales.

Para llevar a cabo este análisis, se emplearon técnicas que permitieron observar la presencia de relación entre las variables meteorológicas y los datos de tweets. 

Primero, se aplicó una visualización de los datos sobre los datos únicamente de día y luego se realizó el mismo proceso sobre los datos de noche. En el eje *x* se visualiza el tiempo y en el *y* el número de tweets, resaltando las horas en las que ha estado nublado y despejado, con el objetivo de ver si los días con más tweets pertenencen a una de las categorías. 

Además, se calculó este número de horas con mayores tweets filtrando por un número cercano al máximo y contando la cantidad de ocurrencias de cada tipo de *estado del cielo*.

## 1.2. Análisis de Varianza (ANOVA)

Para calcular la relación entre número de tweets y condición meteorológica de manera más clara, se aplicó el **Análisis de Varianza (ANOVA)**, que es una técnica estadística que permite comparar las medias de tres o más grupos para determinar si al menos uno es significativamente diferente. En este caso, se utilizó para analizar si las diferentes categorías de la variable meteorológica icon (e.g., *clear-day*, *partly-cloudy-day*) tienen un impacto significativo en el número de tweets (*number_tweets*). Usando la función *f_oneway* de SciPy, se evaluaron las diferencias entre grupos, calculando el p-valor. Un p-valor cercano a 0 indicaría que las condiciones meteorológicas afectan significativamente la cantidad de tweets.

Además, se realizó este mismo análisis, pero realizandolo por separado entre sentimientos positivos y negativos.

## 1.3. Análisis de correlacion de variables (Temperatura y Número de Tweets)

Se hizo un análisis de los datos de horas de día (entre 7am y 7pm), creando un gráfico con la media de temperatura por hora, y otro gráfico del número de tweets por horas. Estos gráficos se parecían, por tanto, investigamos una posible relación entre la temperatura y el número de tweets.

Para ello, realizamos un análisis obteniendo tanto el valor de la **correlación de Pearson** (relación lineal) como la de **Spearman** (relación monotónica). Además, para cada valor de correlación, obtenemos su respectivo p-valor, que ayuda a determinar si existe suficiente evidencia para concluir que hay una correlación real entre dos variables o si esa relación podría haber ocurrido fruto de la casualidad. Además de la relación entre la temperatura y el número de tweets durante el día, también se realiza el mismo análisis durante la noche y también teniendo en cuenta el día entero. 

Por otra parte, también se ha analizado la correlacion entre la temperatura y el número de tweets positivos y negativos independientemente, en ambas quitando los valores de número de tweets nulos.

## 1.4. Análisis de topics en día y noche con LDA

Aprovechando que se había hecho un análisis distinguiendo entre datos de día y noche, se realiza un estudio de los temas que se tratan en los tweets durante ambos momentos. Existe una lista de tweets por cada una de las horas, por lo que se tuvo que aplanar estos datos. Además, se vectoriza cada tweet con un máximo de 50.000 palabras y eliminando *stopwords*, se genera el *bag of words*, con un vocabulario distinto entre día y noche. Estos topics se estudiarán con **Latent Dirichlet Allocation (LDA)**. Este modelo se entrena con los siguientes hiperparámetros: 

- 3 topics
- Alpha = 0.1 (*doc_topic_prior*)
- Beta = 0.05 (*topic_word_prior*)


## 1.5. Modelo dinámico de tópicos por mes

Como LDA es estático, o asume significado estático aunque nuestros datos no lo fueran, no captura cambios en tendencias,y por lo tanto, perdemos información en el análisis. Entonces se utiliza el modelo **Dynamic Topic Models**, que ofrece una evolución natural y suave y preserva la coherencia temporal. Usando DTM de la librería Gensim, se entrenan dos modelos con distintos hiperparámetros. 

#### Modelo 1

En el primero se define el número de topics en 5, sobre un *time_slice* de 3 representando los 3 meses que tiene el dataset. Además, también se define el *chain_variance* como 0.1 para controlar la suavidad de la evolución temporal.

#### Modelo 2

En el segundo modelo se define el número de topics en 3, sobre un *time_slice* de 3 representando los 3 meses que tiene el dataset. Además, se cambia el valor de *chain_variance* a 0.3 para intentar topics más diferentes entre ellos.