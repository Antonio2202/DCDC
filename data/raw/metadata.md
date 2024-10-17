# 1. Recogida de datos complejos

[Repositorio GitHub](https://github.com/Antonio2202/DCDC)

## 1.1 Fuente de los datos

Se dispone de cuatro archivos que contienen **tweets** publicados en Portugal entre el 1 de agosto de 2018 y el 20 de octubre de 2018, obtenidos de
[Kaggle](https://www.kaggle.com/datasets/augustop/portuguese-tweets-for-sentiment-analysis) debido a la
imposibilidad de acceder a los datos mediante la API de X por limitaciones de pago. Estos archivos se clasifican de la siguiente manera:
1. Tweets con Tema, que incluyen alrededor de 60,000 tweets recogidos utilizando aproximadamente 100 términos políticos junto con emoticonos positivos y negativos.
2. Tweets sin Tema, que contienen cerca de 780,000 tweets obtenidos únicamente a partir de emoticonos positivos y negativos. Este CSV, a su vez, ha sido dividido en 5 partes para que sea posible añadirlo a GitHub, pues solo es posible subir archivos de máximo 25 MB.
3. Tweets Neutrales de Hashtags, que suman alrededor de 15,000 tweets recolectados mediante hashtags.
4. Tweets Neutrales de Cuentas de Noticias, que incluyen aproximadamente 35,000 tweets recopilados directamente de cuentas de noticias populares.

Adicionalmente, se cuenta con **datos meteorológicos** de Portugal obtenidos de la API de [Visual Crossing](https://www.visualcrossing.com/weather-api), que abarcan las mismas fechas. Estos datos están divididos en tres archivos distintos debido a limitaciones de la API que solo permitía descargar un archivo por mes. Estos datos se unirán en un único archivo para su análisis.

## 1.2 Fecha de recogida

Todos los datos, tanto los **tweets** como los **meteorológicos**, fueron obtenidos el 3 de octubre de 2024.

## 1.3 Formato de los datos

Ambos datasets están en el mismo formato, CSV.

## 1.4 Licencia de uso

- La licencia de uso bajo la que se encuentran los datos de **tweets** es [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.en).

- La licencia de uso bajo la que se encuentran los **datos meteorológicos** es [Términos de uso](https://www.visualcrossing.com/weather-services-terms).

## 1.5 Descripción de las variables o atributos

El dataset de **tweets** contiene las siguientes variables o atributos:

- id: Identificador único de cada tweet.
- tweet_text: Texto del tweet.
- tweet_date: Fecha y hora en que se publicó el tweet.
- sentiment: Sentimiento asociado al tweet.
- query_used: Indica el término de búsqueda que se utilizó para recopilar el tweet.


El dataset de **datos meteorológicos** contiene las siguientes variables o atributos:

- name: Nombre del lugar o región (en este caso, Portugal).
- datetime: Fecha y hora del registro (en formato ISO 8601).
- temp: Temperatura medida en grados Celsius.
- feelslike: Temperatura de sensación térmica en grados Celsius.
- dew: Punto de rocío en grados Celsius.
- humidity: Humedad relativa en porcentaje.
- precip: Precipitación acumulada en milímetros.
- precipprob: Probabilidad de precipitación en porcentaje.
- preciptype: Tipo de precipitación (por ejemplo, lluvia, nieve), si aplica.
- snow: Cantidad de nieve caída en milímetros.
- snowdepth: Profundidad de la nieve en milímetros.
- windgust: Ráfaga de viento más fuerte registrada, en kilómetros por hora.
- windspeed: Velocidad del viento en kilómetros por hora.
- winddir: Dirección del viento en grados (0° corresponde al norte).
- sealevelpressure: Presión atmosférica al nivel del mar en hPa (hectopascales).
- cloudcover: Cobertura nubosa en porcentaje.
- visibility: Visibilidad en kilómetros.
- solarradiation: Radiación solar medida en W/m².
- solarenergy: Energía solar acumulada en MJ/m².
- uvindex: Índice ultravioleta (UV).
- severerisk: Riesgo de condiciones meteorológicas severas (probabilidad).
- conditions: Condiciones meteorológicas descriptivas (ej. "Clear" - despejado).
- icon: Ícono asociado con las condiciones meteorológicas (ej. "clear-night").
- stations: Códigos de las estaciones meteorológicas que contribuyeron al registro.
