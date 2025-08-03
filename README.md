
# 📊 Análisis de Evasión de Clientes (Churn) - Telecom X 📉

## Índice
- [Introducción](#introducción)
- [Objetivo](#objetivo)
- [Fases del Proyecto](#fases-del-proyecto)
- [Origen de Datos y Descripción](#origen-de-datos-y-descripción)
- [Diccionario de Datos](#diccionario-de-datos)
- [Proceso de Limpieza y Transformación](#proceso-de-limpieza-y-transformación)
- [Visualización y Gráficos Relevantes](#visualización-y-gráficos-relevantes)
- [Hallazgos](#hallazgos)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)
- [Cierre del Documento](#cierre-del-documento)

## Introducción 🚀 🚀

Este proyecto se enfoca en el análisis de datos de clientes de Telecom X, una empresa que enfrenta una alta tasa de cancelaciones. El objetivo principal es comprender los factores que influyen en la decisión de los clientes de dejar la empresa (churn). A través del procesamiento y análisis de datos, se busca extraer información valiosa que sirva de base para el equipo de Data Science, permitiéndoles desarrollar modelos predictivos y estrategias efectivas para reducir la evasión de clientes.

## Objetivo 🎯 🎯

El objetivo de este proyecto es realizar un análisis exploratorio y descriptivo del conjunto de datos de clientes de Telecom X para identificar los principales factores y patrones asociados a la evasión de clientes (churn). Los resultados de este análisis se utilizarán para informar al equipo de Data Science y guiar la implementación de estrategias de retención de clientes.

## Fases del Proyecto 🏗️ 🏗️

### Instalación de Dependencias 🛠️

Para replicar este análisis, necesitarás instalar las siguientes bibliotecas de Python. Puedes hacerlo utilizando pip:

```bash
pip install pandas numpy matplotlib plotly requests
```

### Versiones Utilizadas 🐍📦

### Versiones Utilizadas 🐍📦
[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/downloads/release/python-3110/)
[![Pandas](https://img.shields.io/badge/Pandas-2.2.2-150458.svg)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.0-11557c.svg)](https://matplotlib.org/)
[![Plotly](https://img.shields.io/badge/Plotly-5.24.1-276EF1.svg)](https://plotly.com/python/)
[![Requests](https://img.shields.io/badge/Requests-2.32.3-222222.svg)](https://docs.python-requests.org/en/latest/)


## Versiones Utilizadas 🐍📦

Este proyecto fue desarrollado utilizando las siguientes versiones de Python y bibliotecas:

-   🐍 **Python**: 3.11.13
-   🐼 **Pandas**: 2.2.2
-   🔢 **Numpy**: 2.0.2
-   📈 **Matplotlib**: 3.10.0
-   📊 **Plotly**: 5.24.1
-   🌐 **Requests**: (No se muestra versión específica en la celda, se asume versión compatible)

## Origen de Datos y Descripción 📁 📁

Los datos utilizados en este proyecto provienen de un archivo JSON disponible a través de una URL de GitHub. Este conjunto de datos contiene información detallada sobre clientes de Telecom X, incluyendo datos demográficos, servicios contratados (teléfono, internet y servicios adicionales) e información de la cuenta (tipo de contrato, facturación y cargos).

El archivo original es un JSON anidado que fue aplanado en un DataFrame de pandas para facilitar el análisis tabular.

- **Fuente:** [URL del archivo JSON](https://raw.githubusercontent.com/marelycarcamo/challenge2-TelecomX/refs/heads/main/TelecomX_Data.json)

## Diccionario de Datos 📖 📖

A continuación se presenta el diccionario de datos con la descripción de cada columna en el dataset:

-   `customerID`: número de identificación único de cada cliente
-   `Churn`: si el cliente dejó o no la empresa
-   `customer_gender`: género (masculino y femenino)
-   `customer_SeniorCitizen`: información sobre si un cliente tiene o no una edad igual o mayor a 65 años
-   `customer_Partner`: si el cliente tiene o no una pareja
-   `customer_Dependents`: si el cliente tiene o no dependientes
-   `customer_tenure`: meses de contrato del cliente
-   `phone_PhoneService`: suscripción al servicio telefónico
-   `phone_MultipleLines`: suscripción a más de una línea telefónica
-   `internet_InternetService`: suscripción a un proveedor de internet
-   `internet_OnlineSecurity`: suscripción adicional de seguridad en línea
-   `internet_OnlineBackup`: suscripción adicional de respaldo en línea
-   `internet_DeviceProtection`: suscripción adicional de protección del dispositivo
-   `internet_TechSupport`: suscripción adicional de soporte técnico, menor tiempo de espera
-   `streaming_TV`: suscripción de televisión por cable
-   `streaming_Movies`: suscripción de streaming de películas
-   `account_Contract`: tipo de contrato
-   `account_PaperlessBilling`: si el cliente prefiere recibir la factura en línea
-   `account_PaymentMethod`: forma de pago
-   `account_Charges_Monthly`: total de todos los servicios del cliente por mes
-   `account_Charges_Total`: total gastado por el cliente
-   `tiene_Fibra_Optica`: variable binaria creada que indica si el cliente tiene servicio de Fibra Óptica (1) o no (0)
-   `Cuentas_Diarias`: variable numérica creada que indica el promedio de gasto diario del cliente

## Proceso de Limpieza y Transformación ✨🧼🧼

Se realizaron los siguientes pasos para limpiar y transformar el dataset:

1.  **Carga y Aplanamiento:** Los datos JSON anidados fueron cargados y aplanados en un DataFrame tabular utilizando `pd.json_normalize()`.
2.  **Primer Vistazo y Tipos de Datos:** Se realizó una inspección inicial con `.head()`, `.info()` y `.sample()` para entender la estructura, tipos de datos y identificar posibles problemas como valores nulos o vacíos.
3.  **Corrección de Nombres:** Se corrigieron algunos nombres de columnas que contenían errores tipográficos o inconsistencias.
4.  **Manejo de Valores Vacíos:** Se identificaron y manejaron celdas con valores vacíos (`''`), particularmente en las columnas `Churn` y `account_Charges_Total`. Los registros con valores vacíos en `Churn` fueron eliminados, y la columna `account_Charges_Total` se convirtió a tipo numérico, manejando los valores vacíos restantes como `NaN` (y luego eliminados implícitamente al convertir a numérico en el paso siguiente).
5.  **Conversión de Tipos de Datos:** La columna `account_Charges_Total`, que inicialmente era de tipo `object`, fue convertida a tipo numérico (`float64`) utilizando `pd.to_numeric`.
6.  **Conversión a Variables Binarias:** Columnas con respuestas binarias ('Yes'/'No') como `customer_Partner`, `customer_Dependents`, `phone_PhoneService`, `account_PaperlessBilling` y la columna objetivo `Churn` (después de eliminar los vacíos) fueron mapeadas a valores numéricos (1/0).
7.  **Normalización de Columnas Multivalor:** Columnas de servicios adicionales con valores 'Yes', 'No', y 'No internet service' o 'No phone service' (`internet_OnlineSecurity`, `internet_OnlineBackup`, `internet_DeviceProtection`, `internet_TechSupport`, `internet_StreamingTV`, `internet_StreamingMovies`, `phone_MultipleLines`) fueron normalizadas reemplazando los valores 'No service' por 'No', y luego convertidas a binario (1/0).
8.  **Creación de Nuevas Características:**
    *   Se creó la columna `tiene_Fibra_Optica` (binaria) para identificar a los clientes con servicio de Fibra Óptica.
    *   Se creó la columna `Cuentas_Diarias` calculando el promedio de los cargos mensuales dividido por 30.

## Visualización y Gráficos Relevantes 📊📈👁️👁️

Se generaron diversas visualizaciones interactivas utilizando Plotly Express para explorar la relación entre las diferentes características de los clientes y la tasa de evasión (`Churn`). Los gráficos principales incluyen histogramas que muestran la distribución de clientes con y sin evasión para cada variable categórica y numérica relevante.

Los gráficos clave generados fueron:

-   **Distribución de Evasión:** Un gráfico de pastel que muestra el porcentaje total de clientes que han evadido.
-   **Evasión por Duración de Contrato:** Histograma que compara las tasas de evasión entre los diferentes tipos de contrato (mes a mes, un año, dos años).
-   **Evasión por Método de Pago:** Histograma que muestra la distribución de evasión por cada método de pago.
-   **Evasión por Método de Facturación:** Histograma que compara la evasión entre facturación tradicional y electrónica.
-   **Evasión por Meses de Permanencia:** Histograma que visualiza la tasa de evasión en función de la antigüedad del cliente (`customer_tenure`).
-   **Evasión por Cuentas Diarias:** Histograma que muestra la distribución de evasión según el promedio de gasto diario.
-   **Evasión por Gasto Total de Cuentas:** Histograma que relaciona la evasión con el gasto total acumulado por el cliente.
-   **Evasión por Género:** Histograma que compara la tasa de evasión entre hombres y mujeres.
-   **Evasión por Grupo Etario:** Histograma que muestra la evasión en clientes mayores y menores de 65 años.
-   **Evasión por Relación de Pareja y Dependientes:** Histogramas que analizan la evasión según si el cliente tiene pareja o dependientes.
-   **Evasión por Tipo de Servicio de Internet:** Histograma que compara la evasión entre clientes con DSL, Fibra Óptica o sin servicio de internet.
-   **Evasión por Servicios Adicionales de Internet:** Histogramas individuales para Seguridad Online, Copia de Seguridad Online, Protección de Dispositivos, Soporte Técnico, Streaming TV y Streaming de Películas, mostrando la evasión para clientes con y sin cada servicio.
-   **Evasión por Servicio de Múltiples Líneas Telefónicas:** Histograma que compara la evasión para clientes con una o múltiples líneas telefónicas.
-   **Matriz de Correlación:** Un heatmap de la matriz de correlación para variables numéricas, incluyendo las características binarias creadas, para identificar relaciones lineales entre ellas.

Estos gráficos permitieron identificar visualmente los factores con mayor impacto en la probabilidad de que un cliente evada.

## Hallazgos 🕵🏻‍♂️💡💡

Basándonos en el análisis exploratorio de los datos, se identificaron los siguientes hallazgos clave relacionados con la evasión de clientes:

-   **Tipo de Contrato:** Los clientes con **contratos mes a mes** presentan una tasa de evasión significativamente más alta en comparación con aquellos con contratos de uno o dos años.
-   **Método de Pago:** El uso de **cheque electrónico** como método de pago está fuertemente asociado con una mayor probabilidad de evasión.
-   **Facturación Electrónica:** Los clientes que optan por la **facturación electrónica** muestran una mayor propensión a evadir.
-   **Antigüedad del Cliente (Tenure):** La **baja antigüedad** en la empresa es un predictor importante de evasión; la tasa de abandono disminuye considerablemente a medida que aumenta el tiempo que el cliente lleva con el servicio.
-   **Servicios Adicionales de Internet:** La **ausencia de servicios de seguridad y soporte en línea** (como Seguridad Online, Copia de Seguridad Online, Protección de Dispositivos y Soporte Técnico) está correlacionada con una mayor tasa de evasión.
-   **Tipo de Servicio de Internet:** Los clientes con servicio de **Fibra Óptica** tienen una tasa de evasión notablemente más alta que los clientes con DSL o sin servicio de internet.
-   **Servicios de Streaming (TV y Películas):** Los clientes que tienen servicios de **streaming** tienden a evadir ligeramente más.
-   **Líneas Telefónicas:** Tener **múltiples líneas telefónicas** también muestra una ligera correlación con una mayor tasa de evasión.
-   **Demografía:** El **género** no parece ser un factor determinante. Los **ciudadanos senior** tienen una tasa de evasión ligeramente mayor, mientras que tener **pareja o dependientes** se asocia con una menor evasión.
-   **Cargos (Mensuales y Totales):** Los clientes con **cargos mensuales y totales más altos** (frecuentemente asociados con el servicio de Fibra Óptica) tienden a tener una mayor tasa de evasión. Esto podría sugerir problemas de percepción de valor o satisfacción con el costo del servicio.

En resumen, los factores más críticos asociados a la evasión son los **contratos a corto plazo, el método de pago electrónico, la facturación electrónica, la baja antigüedad, la falta de servicios de seguridad y soporte en internet, y el tipo de servicio de Fibra Óptica**, así como potencialmente los **cargos más elevados**.

## Conclusiones ✅

El análisis confirma que el churn es un problema multifactorial en Telecom X, con una clara concentración de evasión en segmentos específicos de clientes. Los clientes con **contratos a corto plazo** (mes a mes), que utilizan **métodos de pago electrónicos**, optan por la **facturación electrónica** y tienen una **baja antigüedad** son los más propensos a evadir. La **calidad y percepción de valor de los servicios de internet**, particularmente la **Fibra Óptica** y la **falta de servicios de seguridad/soporte**, son factores críticos que impulsan la evasión. Los cargos más altos, a menudo asociados con estos servicios, también parecen jugar un papel.

## Recomendaciones 👍

Basado en los hallazgos, se sugieren las siguientes recomendaciones estratégicas para Telecom X:

1.  **Revisar la Estrategia de Contratos Mes a Mes:** Implementar incentivos significativos para que los clientes con contratos mes a mes migren a planes de mayor duración (uno o dos años). Comunicar claramente los beneficios de los contratos a largo plazo (ej: estabilidad de precio, descuentos).
2.  **Investigar la Satisfacción con Pago Electrónico:** Analizar por qué los usuarios de cheque electrónico tienen mayor churn. Podría haber problemas con el proceso, la seguridad percibida, o quizás este método sea preferido por clientes menos comprometidos. Considerar incentivos para otros métodos de pago automático.
3.  **Optimizar la Experiencia de Fibra Óptica y Servicios Adicionales:** Mejorar la calidad del servicio de Fibra Óptica y promover activamente la adopción de servicios de seguridad y soporte. Estos servicios parecen ser "stickers" para la retención. Ofrecer paquetes que incluyan estos servicios o períodos de prueba gratuitos.
4.  **Programas de Retención para Clientes Nuevos y de Corta Antigüedad:** Implementar programas proactivos para contactar y ofrecer soporte adicional a los clientes en sus primeros meses, cuando el riesgo de evasión es más alto. Monitorear de cerca la satisfacción de estos clientes.
5.  **Comunicación de Valor:** Asegurarse de que los clientes, especialmente aquellos con planes de mayor costo (como Fibra Óptica), entiendan el valor que reciben por su dinero. Destacar los beneficios de velocidad, fiabilidad y servicios adicionales.
6.  **Análisis Adicional de Facturación Electrónica:** Aunque práctico, su correlación con churn merece más investigación. Podría estar relacionado con un segmento demográfico más joven y menos estable, o con problemas en la interfaz o comunicación.
7.  **Desarrollar Modelos Predictivos:** Utilizar este análisis exploratorio como base para construir modelos de machine learning que predigan la probabilidad de churn para cada cliente, permitiendo intervenciones de retención personalizadas.

## Cierre del Documento 👋

Este análisis proporciona una base sólida para entender el churn en Telecom X. Los hallazgos identificados son puntos de partida clave para que el equipo de Data Science profundice con modelos predictivos y para que las áreas de negocio implementen estrategias de retención dirigidas a los segmentos de mayor riesgo. La monitorización continua de estos factores será esencial para evaluar la efectividad de las acciones tomadas.
