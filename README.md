 <p align="left">
   <img src="https://img.shields.io/badge/status-en%20desarrollo-green"> 
   <img src="https://img.shields.io/github/issues/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/github/forks/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/github/forks/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/github/license/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Ftwitter.com%2Fjdquiroga2410">
   <img src="https://img.shields.io/github/stars/camilafernanda?style=social">
   <img src="https://img.shields.io/badge/topic-seriesdetiempo-orange">

  </p>

 <h1 align="left"> Series de Tiempo </h1>

![Azul y Blanco Simple Farmacia Reapertura Comercial Horizontal Cartel](https://user-images.githubusercontent.com/87950040/200124555-b55fb8f0-4c57-41e6-af8c-7858efad08e0.png)

## Índice

* [Índice](#índice)

* [Descripción del proyecto](#descripción-del-proyecto)

* [¿Qué son las series de tiempo?](#series-de-tiempo)

* [Características](#características)

* [Manipulando una serie de tiempo](#manipulando-una-serie-de-tiempo)

* [Ventana Móvil](#ventana-móvil)

* [Bandas de Bollinger](#bandas-de-bollinger)

* [White Noise](#white-noise)

* [Randon Walk](#randon-walk)

* [Series de tiempo estacionarias](#Series-de-tiempo-estacionarias)

* [Autocorrelaciones](#autocorrelaciones)

* [Modelo ARIMA](#modelo-arima)

* [Tecnologías utilizadas](#tecnologías-utilizadas)

* [Datasets](#datasets)

* [Ejercicios](#ejercicios)
## Descripción del proyecto

Repositorio creado con el objetivo de identificar, describir y analizar <a href="https://es.wikipedia.org/wiki/Serie_temporal">series de tiempo</a> o series temporal profundizando en los conceptos básicos, en la aplicación en modelos de Machine Learning y en el uso del lenguaje de programación Python. 

## Series de tiempo

Las <a href="https://es.wikipedia.org/wiki/Serie_temporal">series de tiempo</a> se pueden definir como una colección de datos o valores, medidos en diferentes períodos y ordenados cronológicamente. Son distribuciones bidimensionales, donde $X$ corresponde a la variable tiempo (años, meses, días) y $Y$ a la variable que se estudia (ventas, precios, exportaciones, pasajeros de vuelos, etc.). 

![serie_tiempo (1)](https://user-images.githubusercontent.com/87950040/200134034-40557ec0-bef7-42ab-b184-25f643ef1aa8.png)

Las <a href="https://es.wikipedia.org/wiki/Serie_temporal">series de tiempo</a> tiene una gran importancia en las empresas u organismos de cualquier tipo ya que nos permite conocer el estado actual, el comportamiento en un período determinado y establecer la tendencia futura de una variable. Para la planeación de actividades de una empresa es muy importante la predicción de las variables relevantes de la actividad, como por ejemplo: la predicción de producción, de ventas, de desempleo, ingreso, población, precios, inflación, etc.

## Características

La <a href="https://es.wikipedia.org/wiki/Serie_temporal">series de tiempo</a> se caracterizan por:

* Son dependientes del tiempo.

* Tienen una tendencia: la tendncia son variaciones suaves y constantes que se suceden en un periodo de tiempo, por lo general largo. Debe ser largo para poder establecer una línea tendencia que sea representativa o significativa.

* <a href="https://todoeconometria.com/autocorrelacion-dw/">Autocorrelacionadas</a>: la mayoría de los procesos físicos presentan una inercia y no cambian tan rápidamente. Esto, combinado con la frecuencia del muestreo, a menudo hace que las observaciones consecutivas estén correlacionadas. Esta correlación entre observaciones consecutivas se llama autocorrelación. Cuando los datos están autocorrelacionados, la mayoría de los métodos estadísticos estándares basados en la suposición de observaciones independientes pueden arrojar resultados engañosos o incluso ser inútiles.

Revisa un <a href="series_de_tiempo.ipynb">primer ejemplo </a> de series de tiempo utilizando Python y el [Dataset](#datasets) #1

## Manipulando una serie de tiempo

A continuación vamos a ver como podemos manipular y analizar series de tiempo con la ayuda de Python y otras [tecnologías](#tecnologías-utilizadas). En este caso, vamos a trabajar con la información de los precios del dolar(USDCOP=X) de los últimos años.

Puede necesitar installar la siguiente dependencia:
```sh
!pip install --upgrade pandas
!pip install --upgrade pandas-datareader
!pip install yfinance
!pip install fix_yahoo_finance
```
* Primero se importan las librerías y recursos necesarios
```sh
#Importar modulos requeridos
import pandas_datareader as data
import pandas as pd
import numpy as np
#Importar librerias de visualización
import matplotlib.pyplot as plt
import seaborn as sns
```
* Cargamos los datos de la serie de tiempo
```sh
# Ejemplo serie de tiempo con Pandas
# Creando una serie de tiempo de los precios de dollar
ts = data.DataReader("USDCOP=X",
                     start='2017-1-1',
                     end='2022-11-3',
                     data_source='yahoo')['Adj Close']
```
* Visualizamos la serie de tiempo
```sh
ts.head()
```
```sh
Date
2017-01-02    2957.100098
2017-01-03    2950.699951
2017-01-04    2916.199951
2017-01-05    2891.100098
2017-01-06    2897.899902
Name: Adj Close, dtype: float64
```
Tambien podemos filtrar un periodo especifico. Puedes ver más filtros(<a href="manipulando_series_tiempo.ipynb">ver codigo</a>)
```sh
# filtrando sólo del 2022-01-01 al 2022-11-04
ts['2022-01-01':'2022-11-04']
```
```sh
Date
2022-01-03    4063.580078
2022-01-04    4063.080078
2022-01-05    4078.550049
2022-01-06    4026.919922
2022-01-07    4030.919922
                 ...     
2022-10-31    4833.259766
2022-11-01    4937.000000
2022-11-02    5002.250000
2022-11-03    5001.279785
2022-11-04    5067.109863
Name: Adj Close, Length: 220, dtype: float64
```
## Ventana Móvil
Una operación común en los datos de <a href="https://es.wikipedia.org/wiki/Serie_temporal">series de tiempo</a> es desplazar los valores hacia atrás y adelante en el tiempo, como por ejemplo para calcular el cambio porcentual de una muestra a otra. En Pandas podemos utilizar los métodos Series.rolling() y Series.shift().

<a href="ventana_móvil.ipynb">Ver código</a>

**Series.rolling()**

* Realizamos una revisón de la serie de tiempo:
```sh
ts.head(10)

Date
2017-01-02    2957.100098
2017-01-03    2950.699951
2017-01-04    2916.199951
2017-01-05    2891.100098
2017-01-06    2897.899902
2017-01-09    2865.699951
2017-01-10    2887.399902
2017-01-11    2888.800049
2017-01-12    2931.399902
2017-01-13    2877.899902
Name: Adj Close, dtype: float64
```

* Establecemos una ventana de 5, y vamos calculando el promedio de cada ventana a medida que se va desplazando:
```sh
#Utilizando Series.rolling()
media_movil = ts.rolling(window=5).mean()
media_movil.head(10)

Date
2017-01-02            NaN
2017-01-03            NaN
2017-01-04            NaN
2017-01-05            NaN
2017-01-06    2922.600000
2017-01-09    2904.319971
2017-01-10    2891.659961
2017-01-11    2886.179980
2017-01-12    2894.239941
2017-01-13    2890.239941
Name: Adj Close, dtype: float64
```
* Como podemos ver se calcula el promedio de los primeros 5 datos (en el dia 2017-01-06) y así sucesivamente:
```sh
ts['2017-01-02': '2017-01-06'].mean()

2922.6
```
**Series.shift()**

* Observamos como se desplaza los datos 1 posición o 1 día (podemos utilizarlo como un modelo de persistencia)
```sh
media_movil_sh= ts.shift(1)
media_movil_sh.head()

Date
2017-01-02            NaN
2017-01-03    2957.100098
2017-01-04    2950.699951
2017-01-05    2916.199951
2017-01-06    2891.100098
Name: Adj Close, dtype: float64
```
* Calculando el porcentaje de variación del día:
```sh
variacion_diaria = ts/ ts.shift(1) - 1
ts['var_diaria'] = variacion_diaria
ts['var_diaria'].head()

Date
2017-01-02 00:00:00         NaN
2017-01-03 00:00:00   -0.002164
2017-01-04 00:00:00   -0.011692
2017-01-05 00:00:00   -0.008607
2017-01-06 00:00:00    0.002352
Name: Adj Close, dtype: object
```

## Bandas de Bollinger

Las <a href="https://admiralmarkets.com/es/education/articles/forex-strategy/bandas-de-bollinger">bandas de Bollinger</a> son un indicador de inversión tendencial de tipo técnico, que se utiliza para predecir la evolución futura del precio de un instrumento financiero.

Está compuesto por tres bandas (superior, media e inferior) y permiten ver de forma dinámica cómo varía una serie de datos o precios en relación a la banda media. La distancia hacia arriba y hacia abajo respecto a los precios depende de la volatilidad de éstos.

En esta ocasión vamos a aplicar las ventanas móviles para determinar las <a href="https://admiralmarkets.com/es/education/articles/forex-strategy/bandas-de-bollinger">bandas de Bollinger</a> del comportamiento del <a href="bandas_bollinger.ipynb">precio del dollar</a>.

* Calculamos el promedio movil del precio del dollar en ventanas de 20 días:
```sh
media_movil = ts.rolling(window=20).mean()
```
* Calculamos la desviación standar movil de los datos:
```sh
std_movil = ts.rolling(window=20).std()
```
* Calculamos la banda superior:
```sh
banda_sup = media_movil + 2 * std_movil
```
* Calculamos la banda inferior:
```sh
banda_inf = media_movil - 2 * std_movil
```
* Visualizamos los datos:
```sh
ts["2022"].plot()
banda_sup["2022"].plot()
banda_inf["2022"].plot()
plt.show()
```
![bandas](https://user-images.githubusercontent.com/87950040/200143003-a15951ff-09bc-404a-85e8-7d8e2e772ceb.png)

* Para conocer con exactitud cuando el precio del dolar sobrepaso la banda superior:
```sh
ts["2022"][(ts["2022"] > banda_sup["2022"]).to_numpy()]
```
## White Noise

Un <a href="https://support.numxl.com/hc/es/articles/115001099806--C%C3%B3mo-comprobar-cu%C3%A1ndo-una-serie-de-tiempo-dada-es-s%C3%B3lo-ruido-blanco-">white noise</a> es un caso simple de los procesos estocásticos, donde los valores son independientes e idénticamente distribuidos a lo largo del tiempo con media cero, igual varianza (varianza constante) y no es <a href="https://todoeconometria.com/autocorrelacion-dw/">autocorrelacionada</a> , se denota por $\varepsilon_t$.

Si todas las series que observamos en la realidad fuesen <a href="https://ecab-estadistica.medium.com/ruido-blanco-white-noise-en-python-y-en-r-dbd87d4cd1fe">Ruido Blanco </a> serían impredecibles y no habría ningún modelo que proponer. Se trata de un proceso en el que todas sus variables son independientes.

```sh
import numpy as np
import matplotlib.pyplot as plt

y = np.random.normal(0, 3, 100)

plt.plot(y)
```
![whiteboise](https://user-images.githubusercontent.com/87950040/200144594-72479835-9a28-4d11-b661-cc1e23219150.png)

Vamos a ver un ejemplo en Python de cómo generar white noise comparandola con una serie de precios del mercado financiero:

* Primero importamos los recursos y módulos necesarios.
```sh
#Importar modulos requeridos
import pandas_datareader as data
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from math import sqrt
#Importar librerias de visualización
import matplotlib.pyplot as plt
import seaborn as sns
#Importamos los datos
df = pd.read_csv('https://raw.githubusercontent.com/ecabestadistica/curso-series-temporales/master/2.%20Serie%20temporal%20en%20R%20y%20Python/Python/Index2018.csv')
```
* Convertimos la variable fecha al tipo correspondiente, le asignamos una frecuencia de “business days” y rellenamos cualquier valor faltante.
```sh
df.date = pd.to_datetime(df.date, dayfirst = True)
df.set_index('date', inplace=True)
df=df.asfreq('b')
df=df.fillna(method='ffill')
```
* Generamos los datos de white noise, usando la misma media y varianza que los datos de SP500 que contiene el dataset.
```sh
wn = np.random.normal(loc = df.spx.mean(), scale = df.spx.std(), size = len(df))
df['wn'] = wn
```
* Visualizamos la serie de tiempo con white noise generada
```sh
df.wn.plot(figsize = (20,5))
plt.title('White Noise Time-Series', size= 24)
plt.show()
```
![whitenoise](https://user-images.githubusercontent.com/87950040/200146683-2d36d838-a21e-4dae-9719-5cf3e205bec4.png)

* Visualizamos la serie de tiempo  del SP500 que si tiene patrones.
```sh
df.spx.plot(figsize=(20,5))
plt.title('S&P Prices', size = 24)
plt.show()
```
![S P_Prices](https://user-images.githubusercontent.com/87950040/200146802-24baeb93-5e5c-49e0-a286-11b9752e787e.png)

## Randon Walk

El randon walk o camino al azar es un proceso estocástico $X_t$, donde la primera diferencia de este proceso estocástico es un <a href="https://support.numxl.com/hc/es/articles/115001099806--C%C3%B3mo-comprobar-cu%C3%A1ndo-una-serie-de-tiempo-dada-es-s%C3%B3lo-ruido-blanco-">white noise</a>, esto es $\triangledown X_t = \varepsilon_t$ .

## Series de tiempo estacionarias

## Autocorrelaciones


## Modelo ARIMA

```sh
ts.head()
```
## Tecnologías utilizadas

* **Python**
* **Statsmodels**
* **Pandas**

## Datasets

<a href="https://raw.githubusercontent.com/jesusdanielquiroga/Series-de-Tiempo/main/airline-passengers.csv"> Dataset 1: Passengers </a>

<a href="https://raw.githubusercontent.com/jesusdanielquiroga/Series-de-Tiempo/main/Amtrak.csv"> Dataset 2: Ridership </a>

<a href="https://raw.githubusercontent.com/ecabestadistica/curso-series-temporales/master/2.%20Serie%20temporal%20en%20R%20y%20Python/Python/Index2018.csv"> Dataset 3: Precios del mercado financiero, en específico, del SP500 </a>

## Ejercicios

**1.** Realizar un análisis del comportamiento anual del dólar desde enero de 2017 a la fecha.

* ¿Cuál es el año que tuvo mayor incremento?
* ¿Cuál es el año con mayor volatilidad? (Usar Boxplot)

**2.** Para la serie de amtrack y sp500(últimos 5 años)(símbolo: SPY).

* Dividir en train y test
* Revisar autocorrelaciones
* Determinar si la serie es ruido blanco
* determinar si la serie es random walk
* Descomponerla en trend, seasonality y residuos(usando la biblioteca)
* Determinar si la serie es estacionaria
* Si no lo es, intentar hacerla estacionaria con el método de diferencias

