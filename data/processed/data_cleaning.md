# 1. Procedimiento de limpieza de datos

Vamos a realizar la limpieza, normalización y agrupación de los datos recogidos.

## 1.1 Descripción de los métodos utilizados para la limpieza de datos
   
1. **Eliminación de filas duplicadas**: Se eliminan posibles duplicados del dataset para evitar redundancia en el análisis.
   
2. **Manejo de valores nulos**: Se identificaron valores nulos y se sustituyeron por valores en el mismo formato. Por ejemplo, las columnas 'tweet_texts' y 'sentiments' contienen listas de textos y listas de sentimientos respectivamente. Se sustituyen los valores NaN por listas vacías.

3. **Conversión de tipos de datos**: Se convirtieron los tipos de datos de las columnas según su contenido y uso en el análisis.

4. **Agrupación de datos**: Se agruparon los datos de los dos datasets en uno solo para facilitar su análisis y visualización.

5. **Selección de columnas relevantes**: Se seleccionaron únicamente las columnas necesarias para el análisis, eliminando aquellas que no aportaban valor.
   - Columnas seleccionadas: `['datetime', 'temp', 'precip', 'preciptype', 'conditions', 'tweet_texts', 'sentiments', 'icon', 'number_tweets', 'hour']`.

   - La columna preciptype tiene valores nulos cuando no llueve y el string 'rain' cuando hay precipitaciones. Lo usaremos para saber los momentos en los que ha         llovido

6. **División del dataset**: Se divide el dataset completo en tres partes para diferentes usos, manteniendo un enfoque balanceado mediante el uso de la función `sample(frac=1)` para barajar los datos antes de dividirlos.

## 1.2 Justificación de las decisiones tomadas durante el proceso de limpieza

- **Selección de columnas**: Se eliminaron aquellas columnas que consideramos redundantes o irrelevantes para el análisis, lo cual simplifica el dataset y facilita la interpretación de los resultados. Por ejemplo, nos quedamos con columnas como conditions o icon que muestran el tipo de clima que hace en cada momento.

- **Eliminación de duplicados**: Mantener solo registros únicos ayuda a evitar sesgos en los resultados, asegurando que cada punto de datos tenga la misma importancia.

- **División del dataset**: Dividir el conjunto de datos en partes para poder subirlo al repositorio de GitHub, ya que el tamaño del dataset completo supera el límite permitido.
