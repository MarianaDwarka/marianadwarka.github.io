---
title: "Algorithmic trading"
description: "An overview of SQLAlchemy, a Python library for interacting with relational databases using an Object-Relational Mapping (ORM) approach. It also compares SQLAlchemy with MySQL Connector"
pubDate: "May 27 2024"
heroImage: "/blogImages/algorithmictrading.png"
---

**Algorithmic trading**, also known as automated trading, is a method of executing buy and sell orders in financial markets using algorithms and computer programs. These algorithms are designed to make trading decisions based on a series of predefined parameters and rules, without direct human intervention.

<a class="btn btn-outline ml-5" href="https://github.com/MarianaDwarka/Trading_Algoritmico" target="_blank">CHECK OUT THE PROJECT REPOSITORY</a> 

### **Objective**:
The project's objective is to develop an algorithmic trading system that emulates the lifecycle of market data, from its extraction to its analysis and real-time execution of trades, specifically working with the EUR/USD currency pair. This system connects to a broker (OANDA) through an API to obtain market data, process it in a virtual machine hosted on Azure, and execute automatic trades based on a simple moving average (SMA) crossover strategy. The resulting data is stored in a MySQL database in Azure, allowing for later adjustment of strategy parameters using Python.

First, we will explain the data lifecycle, that is, the stages data goes through from its creation to its visualization.

### **Data Lifecycle**

![](/blogImages/ciclodato.png)

The cycle consists of five main phases:

1. **Data Source**: 
   In this initial stage, data is collected or identified from various sources. These sources may include databases, files, sensors, APIs, among others. It is crucial that the quality and accuracy of the data are verified from this first step.

2. **Processing**:
   Here the data undergoes processes of **preparation, organization, and transformation**. This involves cleaning the data (removing errors or inconsistencies), properly structuring it, and converting it into a format that is useful for further analysis.

3. **Storage**:
   Processed data is **stored** in appropriate storage systems such as relational databases, data warehouses, or cloud solutions. Storage ensures that the data is accessible for future analysis.

4. **Analysis**:
   In this phase, the stored data is analyzed to **extract insights, patterns, and trends**. Analytical techniques such as statistics, machine learning, or data mining are used to obtain valuable information that can be used for decision-making.

5. **Visualization**:
   The results of the analysis are represented graphically or visually through **dashboards, charts, or reports**. This facilitates the understanding of the extracted information and helps communicate the findings clearly and effectively for decision-making.

This data lifecycle describes a continuous and cyclical process, as data can be updated, or new data can be incorporated into the cycle at any time.

For the proposed example in this project, we would have the following diagram illustrating the process through which the data passes from extraction from the broker to trade execution:

![](/blogImages/esquematrading.png)

### **System Components (Algorithmic Trading)**:
1. **Data Source and Extraction**:
   - **Broker API (OANDA)**: The OANDA API is used to obtain real-time market data, which serves as the basis for analysis and trade execution.
   - **`tpqoa` Library**: Facilitates the connection and manipulation of data coming from OANDA in Python.
  
2. **Processing in Azure**:
   - **Virtual Machine (Azure VM1)**: All data processing occurs on a virtual machine running Python. At this stage, the data is cleaned and structured for further analysis.
   - **Preprocessing**: Data is prepared for technical analysis, working with both historical data for backtesting and real-time data for trade execution.

   - **Implementation of the Trading Strategy**:
      - **Simple Moving Average Crossover (SMA 50/200)**: The primary strategy is based on the crossover of moving averages over different periods (50 and 200) to generate buy and sell signals.
      - **TA-Lib**: The `TA-Lib` library is used for technical analysis on financial data, facilitating the calculation of indicators like moving averages.
      - **Backtesting**: The strategy is retrospectively tested with historical data using the `backtesting` library. 100 days of data with one-hour granularity are used, including a 0.15% commission to simulate a realistic environment.
   
   - **Parameter Tuning**:
      - **Optimization**: After the initial backtesting, the moving averages' parameters are optimized to improve strategy performance. These adjusted parameters are tested again for comparison with the original results.
  
3. **Storage in MySQL**:
   - **MySQL Database on Azure**: All processed data is stored in a MySQL database in Azure for future analysis. This database is accessible from a local computer via MySQL Workbench. The `sqlalchemy` library is used to connect to the database.
   - **Real-time Data Storage**: Data is continuously stored, allowing immediate access for strategy parameter adjustments.

4. **Real-Time Execution**:
   - **Trade Execution**: Once the data is processed, the strategy executes trades in real-time using the OANDA API. The signals generated by the strategy trigger the buying or selling of assets.
   - **Data Streaming**: The `tpqoa` library facilitates continuous access and handling of real-time data from the broker.

5. **Visualization**:
   - **Python for Visualization**: The results and key metrics of the executed trades, along with the data stored in the database, are visualized and analyzed using Python, allowing for further parameter and strategy adjustments.

---

This flow allows not only the automatic execution of trades in real-time but also continuous adjustment based on retrospective analysis of the data stored in the MySQL database. This creates a continuous improvement cycle that optimizes the trading strategy based on the results obtained.

## Conclusions:

* A system that emulates the complete algorithmic trading cycle was successfully implemented, from extracting real-time market data, processing it, executing automatic trades, and storing and visualizing results. This flow demonstrates how different technologies (API, Azure, MySQL, Python) can be integrated into an automated environment.
* This project provided a comprehensive view of the algorithmic trading process and real-time data management, as well as the importance of technological infrastructure in automating financial decisions.
* Future iterations could explore other financial indicators, implement machine learning techniques, or improve strategy optimization through more complex analysis.

---

Español

---
# Trading Algorítmico

El trading algorítmico, también conocido como trading automatizado, es un método de ejecutar órdenes de compra y venta en los mercados financieros utilizando algoritmos y programas de computadora. Estos algoritmos están diseñados para tomar decisiones de trading basadas en una serie de parámetros y reglas predefinidas, sin intervención humana directa.

<a class="btn btn-outline ml-5" href="https://github.com/MarianaDwarka/Trading_Algoritmico" target="_blank">Revisar repositorio del proyecto</a> 


### **Objetivo**:
El objetivo del proyecto es desarrollar un sistema de trading algorítmico que emule el ciclo de vida de los datos de mercado, desde su extracción hasta su análisis y ejecución de operaciones en tiempo real, el particular se trabajará con el par de divisasEUR/USD. Este sistema se conecta a un broker (OANDA) mediante una API para obtener datos de mercado, procesarlos en una máquina virtual alojada en Azure y ejecutar trades automáticos basados en una estrategia de cruces de medias móviles simples (SMA's). Los datos resultantes son almacenados en una base de datos MySQL en Azure, permitiendo ajustes posteriores de los parámetros estratégicos utilizando Python.

Antes que nada, comenzaremos explicando el ciclo de vida de los datos, es decir, las etapas por las que pasan los datos desde su creación hasta su visualización.

### **Ciclo de vida de los datos**

![](/blogImages/ciclodato.png)

El ciclo se compone de cinco fases principales:

1. **Fuente de datos**: 
   En esta etapa inicial, los datos son recolectados o identificados desde diversas fuentes. Estas fuentes pueden ser bases de datos, archivos, sensores, APIs, entre otros. Es crucial que la calidad y precisión de los datos se verifiquen desde este primer paso.

2. **Tratamiento**:
   Aquí los datos pasan por procesos de **preparación, organización y transformación**. Esto implica limpiar los datos (eliminando errores o inconsistencias), estructurarlos adecuadamente y convertirlos en un formato que sea útil para su posterior análisis.

3. **Almacenamiento**:
   Los datos tratados son **almacenados** en sistemas de almacenamiento adecuados, como bases de datos relacionales, almacenes de datos o soluciones en la nube. El almacenamiento asegura que los datos estén accesibles para su análisis en el futuro.

4. **Análisis**:
   En esta fase, los datos almacenados son analizados para **extraer conocimientos, patrones y tendencias**. Se utilizan técnicas analíticas como estadísticas, aprendizaje automático o minería de datos para obtener información valiosa que puede ser utilizada para la toma de decisiones.

5. **Visualización**:
   Los resultados del análisis se representan de manera gráfica o visual mediante **tableros, gráficos o informes**. Esto facilita la comprensión de la información extraída y ayuda a comunicar los hallazgos de manera clara y efectiva para la toma de decisiones.

Este ciclo de vida del dato describe un proceso continuo y cíclico, ya que los datos pueden ser actualizados o nuevos datos pueden ser incorporados en el ciclo en cualquier momento.

Entonces, para el ejemplo propuesto en este proyecto, se contaría con el siguiente esquema que ilustra el proceso por el cual van pasando los datos desde que se extraen del broker hasta que se ejecuta el trade:

![](/blogImages/esquematrading.png)

### **Componentes del Sistema (Trading Algorítmico)**:
1. **Fuente de Datos y Extracción**:
   - **API de Broker (OANDA)**: Se utiliza la API de OANDA para obtener datos de mercado en tiempo real, que son la base para el análisis y ejecución de las operaciones.
   - **Biblioteca `tpqoa`**: Para facilitar la conexión y manipulación de los datos provenientes de OANDA en Python.
  
2. **Procesamiento en Azure**:
   - **Máquina Virtual (Azure VM1)**: Todo el procesamiento de los datos ocurre en una máquina virtual que ejecuta Python. En esta fase, los datos se limpian y estructuran para el análisis posterior.
   - **Preprocesamiento**: Los datos se preparan para análisis técnico, y se trabaja tanto con datos históricos para backtesting como con datos en tiempo real para la ejecución de trades.

   - **Implementación de la Estrategia de Trading**:
      - **Cruce de Medias Móviles (SMA 50/200)**: La estrategia principal se basa en el cruce de medias móviles de diferentes periodos (50 y 200) para generar señales de compra y venta.
      - **TA-Lib**: Utilización de la biblioteca `TA-Lib` para realizar análisis técnico sobre los datos financieros. Esta librería facilita el cálculo de indicadores como las medias móviles.
      - **Backtesting**: Se realiza una prueba retrospectiva de la estrategia con datos históricos, usando la biblioteca `backtesting`. Se utilizan 100 días de datos con granularidad de una hora y se incluyen comisiones del 0.15% para simular un entorno realista.
   
   - **Ajuste de Parámetros**:
      - **Optimización**: Tras el backtesting inicial, se optimizan los parámetros de las medias móviles para mejorar el rendimiento de la estrategia. Estos parámetros ajustados son probados nuevamente para compararlos con los resultados originales.
  
3. **Almacenamiento en MySQL**:
   - **Base de Datos MySQL en Azure**: Todos los datos procesados se almacenan en una base de datos MySQL en Azure para su posterior análisis. Esta base de datos es accesible desde una computadora local mediante MySQL Workbench. Se utiliza la biblioteca `sqlalchemy` para la conexión con la base de datos.
   - **Real-time Data Storage**: Los datos son almacenados de forma continua, permitiendo un acceso inmediato para ajustar los parámetros de la estrategia.

4. **Ejecución en Tiempo Real**:
   - **Ejecución de Trades**: Una vez procesados los datos, la estrategia ejecuta trades en tiempo real utilizando la API de OANDA. Las señales generadas por la estrategia disparan la compra o venta de activos.
   - **Streaming de Datos**: La biblioteca `tpqoa` facilita el acceso y manejo continuo de los datos en tiempo real desde el broker.

5. **Visualización**:
   - **Python para Visualización**: Los resultados y métricas clave de los trades ejecutados, junto con los datos almacenados en la base de datos, se visualizan y analizan mediante Python, lo que permite ajustes adicionales en los parámetros y la estrategia.

---


Este flujo permite no solo la ejecución automática de trades en tiempo real, sino también el ajuste continuo basado en el análisis retrospectivo de los datos almacenados en la base de datos MySQL. Esto crea un ciclo de mejora continua que optimiza la estrategia de trading en función de los resultados obtenidos.

## Conclusiones:

* Se logró implementar un sistema que emula el ciclo completo de trading algorítmico, desde la extracción de datos de mercado en tiempo real, su procesamiento, la ejecución de operaciones automáticas y el almacenamiento y visualización de resultados. Este flujo demuestra cómo se pueden integrar diferentes tecnologías (API, Azure, MySQL, Python) en un entorno automatizado.
* Este proyecto ha permitido obtener una visión integral del proceso de trading algorítmico y el manejo de datos en tiempo real, así como la importancia de la infraestructura tecnológica en la automatización de decisiones financieras.
* En futuras iteraciones, se podrían explorar otros indicadores financieros, implementar técnicas de aprendizaje automático, o mejorar la optimización de la estrategia a través de análisis más complejos.
