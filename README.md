 <p align="left">
   <img src="https://img.shields.io/badge/status-en%20desarrollo-green"> 
   <img src="https://img.shields.io/github/issues/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/github/forks/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/github/forks/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/github/license/jesusdanielquiroga/model-api">
   <img src="https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Ftwitter.com%2Fjdquiroga2410">
   <img src="https://img.shields.io/github/stars/camilafernanda?style=social">
  </p>

 <h1 align="left"> Series de Tiempo </h1>

![Azul y Blanco Simple Farmacia Reapertura Comercial Horizontal Cartel](https://user-images.githubusercontent.com/87950040/200124555-b55fb8f0-4c57-41e6-af8c-7858efad08e0.png)

## Índice

* [Índice](#índice)

* [Descripción del proyecto](#descripción-del-proyecto)

* [¿Qué son las series de tiempo?](#series-de-tiempo)

* [Características](#características)

* [Manipulando una serie de tiempo](#manipulando-una-serie-de-tiempo)

* [White Noise](#white-noise)

* [Randon Walk](#randon-walk)

* [Modelo ARIMA](#modelo-arima)

* [Tecnologías utilizadas](#tecnologías-utilizadas)

* [Datasets](#datasets)

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

## White Noise

## Randon Walk

## Modelo ARIMA

```sh
cd game
python3 main.p
```
## Tecnologías utilizadas

* **Python**
* **Statsmodels**
* **Pandas**

## Datasets

<a href="https://raw.githubusercontent.com/jesusdanielquiroga/Series-de-Tiempo/main/airline-passengers.csv"> Dataset 1: Passengers </a>

<a href="https://raw.githubusercontent.com/jesusdanielquiroga/Series-de-Tiempo/main/Amtrak.csv"> Dataset 2: Ridership </a>



