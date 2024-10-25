# 1. Motivación

## 1.1 Objetivo General del Proyecto

Este análisis busca explorar la relación entre las condiciones climátológicas (principalmente temperatura, precipitaciones y estado del cielo) y la actividad en las redes sociales en Portugal durante el periodo del 1 de agosto al 20 de octubre de 2018. El objetivo es determinar cómo los cambios en el clima influyen tanto en términos de la cantidad de tweets publicados como del sentimiento positivo o negativo expresado en los mismos. Este análisis puede proporcionar una idea de cómo factores meteorológicos como las altas temperaturas, la lluvia o el cielo nublado pueden influir en el comportamiento y las emociones compartidas en las redes sociales.

## 1.2 Preguntas de Investigación o Hipótesis

- Todas las hipótesis formuladas en este análisis se refieren exclusivamente a Portugal y al período comprendido entre el 1 de agosto de 2018 y el 20 de octubre de 2018. Los resultados estarán limitados a esta región y rango temporal específico, y las conclusiones se interpretarán dentro de este contexto geográfico y temporal.

1. Los días de temperaturas más extremas se publican más tweets que en días de clima moderado

2. En dias lluviosos o nublados, la cantidad de tweets con sentimiento negativo es mayor que en días soleados

3. La lluvia y las bajas temperaturas están asociadas con un aumento en el número total de tweets.

4. El clima soleado está asociado con un aumento en los tweets con sentimiento positivo

5. Los cambios climáticos bruscos (por ejemplo, de un día soleado a lluvioso) aumentan la variabilidad en los sentimientos expresados en los tweets.

## 1.3 Justificación de los Datos Seleccionados

### Variabilidad

- El rango de valores para la temperatura, las precipitaciones y las condiciones del cielo durante el período de estudio proporciona una buena base para analizar cómo diferentes escenarios climáticos impactan en el comportamiento en redes sociales.

### Periocidad y Temporalidad

- Los datos abarcan un período continuo de casi tres meses, lo que permite detectar patrones repetitivos o cambios en la conducta social relacionados con el clima.

- Los datos de tweets coinciden temporalmente con los datos climatológicos, permitiendo un análisis sincrónico entre el clima y el comportamiento en redes sociales. Esta alineación temporal es esencial para responder a las preguntas de investigación planteadas.

### Geolocalización

- Ambos datasets (climatológico y de tweets) están centrados en una misma ubicación geográfica, lo que permite una comparación directa entre el clima experimentado en esa área y la actividad social registrada. Esto elimina la variabilidad de otros factores geográficos o climáticos que podrían afectar los resultados.

- Portugal es una región con una variedad moderada de condiciones climáticas durante el período de estudio, lo que facilita observar cómo cambios en las condiciones meteorológicas impactan en las interacciones sociales.

### Riqueza en Datos Textuales

- Los tweets representan expresiones espontáneas y cotidianas de las personas, permitiendo evaluar cómo el clima puede influir en su actividad en redes sociales. Dado que el sentimiento de los tweets está etiquetado como positivo o negativo, es posible analizar la influencia del clima en el estado emocional.

### Conclusiones

Estos datos son adecuados para responder a las preguntas de investigación planteadas porque permiten establecer conexiones directas entre las condiciones meteorológicas y las expresiones emocionales y conductuales en redes sociales. Además, la riqueza temporal, geográfica y emocional que ofrecen los datos facilita la exploración de cómo las variaciones climáticas influyen en la vida digital de las personas.

## 1.4 Desafios Potenciales con los Datos Limpiados

### Datos Faltantes o Incompletos:

- Los datos climatológicos están completos. Sin embargo, puede haber días o períodos en los que el número de tweets sea insuficiente para un análisis estadístico robusto.

### Ruido en los Tweets

- El texto de los tweets puede contener información irrelevante o fuera de contexto respecto al clima, como discusiones políticas, eventos deportivos, u otros temas no relacionados con el análisis.

- Además, el análisis de los sentimientos puede no ser perfecto y pueden clasificar erróneamente el tono emocional de un tweet, especialmente en casos de sarcasmo o ambigüedad.

### Sesgo de Localización

- Algunos tweets pueden estar marcados como provenientes de Portugal, pero en realidad podrían haber sido enviados por usuarios de otras partes. Esto introduce un sesgo que puede distorsionar las conclusiones sobre la relación entre el clima y el comportamiento social.

- Los datos climatológicos pueden representar promedios generales para toda Portugal, lo que puede no reflejar con precisión el clima experimentado por usuarios en ubicaciones específicas dentro del país.
 
### Balanceo de Clases

- Es probable que haya más tweets con sentimiento positivo o negativo dependiendo del contexto general. Si el dataset está desbalanceado en cuanto a sentimientos o cantidad de tweets en días específicos (por ejemplo, más tweets en días soleados que en días lluviosos), esto podría sesgar los resultados y dificultar el análisis

### Datos muy Homogéneos o Variados

- Si los datos meteorológicos son muy similares puede ser difícil detectar diferencias notables en la cantidad o el sentimiento de los tweets.

- Esto también puede ocurrir en el caso contrario, si hay demasiadas fluctuaciones extremas que dificulten establecer patrones claros.

### Correlación no implica Causalidad

- Aunque es posible encontrar correlaciones entre las condiciones climáticas y los tweets, esto no implica necesariamente una relación causal directa. Otros factores, como eventos sociales o culturales, podrían estar influyendo simultáneamente en la actividad en redes sociales.



