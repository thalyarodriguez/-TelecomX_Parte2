# 📊 Telecom X - Parte 2

## 🔮 Predicción de Cancelación de Clientes (Churn)

## 🎯 Propósito del Proyecto

El objetivo principal de este análisis es desarrollar modelos predictivos capaces de anticipar la cancelación de clientes (churn) en la empresa Telecom X.

A través de técnicas de machine learning, se busca identificar qué clientes tienen mayor probabilidad de cancelar el servicio, utilizando variables relevantes como el tiempo de permanencia, tipo de contrato, nivel de gasto y servicios contratados.

Este modelo permite a la empresa implementar estrategias preventivas de retención y reducir la pérdida de clientes.

# 📁 Estructura del Proyecto

```
Telecom-X-Parte-2/
│
├── TelecomX_Parte2.ipynb        # Cuaderno principal con todo el análisis
├── datos_tratados.csv           # Dataset limpio y preparado (Parte 1)
├── README.md                    # Documentación del proyecto

```

# 🗂 Dataset Utilizado

El proyecto utiliza el archivo:

```
datos_tratados.csv
```

Este archivo corresponde a los datos previamente limpiados y organizados en la Parte 1 del desafío.

Contiene únicamente variables relevantes, con valores corregidos y estandarizados.

⚠ Es necesario que este archivo esté ubicado en el mismo directorio que el cuaderno principal para su correcta ejecución.


# 🔧 Preparación de los Datos

## 📌 1. Clasificación de Variables

Las variables fueron clasificadas en:

### 🔹 Variables Numéricas

* tenure
* Charges.Monthly
* Charges.Total
* Cuentas_Diarias
* SeniorCitizen

### 🔹 Variables Categóricas

* gender
* Contract
* InternetService
* PaymentMethod
* StreamingTV
* StreamingMovies
* OnlineSecurity
* TechSupport
* PaperlessBilling
* MultipleLines
* Dependents
* PhoneService


## 🔄 2. Encoding

Las variables categóricas fueron transformadas a formato numérico mediante:

* **One-Hot Encoding**

Esto permitió que los algoritmos de machine learning pudieran procesarlas correctamente.


## 📏 3. Normalización

Se aplicó **StandardScaler** únicamente para el modelo de Regresión Logística, ya que:

* Modelos lineales son sensibles a la escala de los datos.
* La estandarización evita que variables con mayor magnitud dominen el modelo.

El modelo Random Forest no requirió normalización, ya que los modelos basados en árboles no son sensibles a la escala.


## ✂ 4. Separación de Datos

Los datos fueron divididos en:

* 80% entrenamiento
* 20% prueba

Esto permitió evaluar el desempeño del modelo en datos no vistos previamente.


# 🤖 Modelos Implementados

Se desarrollaron dos modelos de clasificación:

### 🔹 1. Regresión Logística

* Requiere normalización.
* Se utilizó `class_weight="balanced"` para manejar el desbalance de clases.
* Mejor desempeño en detección de churn (Recall = 81%).

### 🔹 2. Random Forest

* No requiere normalización.
* Mayor exactitud general.
* Presentó sobreajuste (overfitting).


# 📊 Evaluación de Modelos

Las métricas utilizadas fueron:

* Accuracy
* Precision
* Recall
* F1-score
* Matriz de Confusión

El modelo seleccionado fue **Regresión Logística**, ya que presentó:

* Mejor recall para churn
* Buena estabilidad (sin overfitting)
* Mayor capacidad de generalización


# 📈 Análisis Exploratorio (EDA) e Insights

Durante el análisis exploratorio se identificaron patrones importantes:

## 🔥 1. Tiempo de permanencia (tenure)

Clientes nuevos presentan mayor probabilidad de cancelar.

## 📄 2. Tipo de contrato

Los contratos mensuales están más asociados al churn.
Contratos de uno y dos años reducen significativamente la cancelación.

## 💰 3. Nivel de gasto

El gasto total acumulado influye en la probabilidad de cancelación.

## 🌐 4. Tipo de servicio

Clientes con fibra óptica presentan mayor riesgo de churn.

Se utilizaron gráficos como:

* Boxplots
* Histogramas
* Gráficos de barras comparativos
* Matriz de correlación

# 🚀 Estrategias Propuestas

Con base en los hallazgos, se recomiendan:

* Programas de fidelización para clientes nuevos.
* Incentivar contratos de largo plazo.
* Seguimiento especial a clientes de alto gasto.
* Implementación de un sistema de alerta temprana basado en el modelo predictivo.


# 🛠 Instrucciones para Ejecutar el Proyecto

## 1️⃣ Instalar bibliotecas necesarias

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```


## 2️⃣ Ejecutar el cuaderno

Abrir el archivo:

```
TelecomX_Parte2.ipynb
```

Asegurarse de que el archivo:

```
datos_tratados.csv
```

esté en el mismo directorio.


## 3️⃣ Cargar los datos

Dentro del notebook:

```python
import pandas as pd

df = pd.read_csv("datos_tratados.csv")
```

Luego ejecutar las celdas en orden secuencial.

# 📌 Conclusión General

La cancelación de clientes no es un fenómeno aleatorio, sino que está fuertemente influenciada por:

* Antigüedad del cliente
* Tipo de contrato
* Nivel de gasto
* Tipo de servicio contratado

El modelo de Regresión Logística permite anticipar el churn con alta capacidad de detección, convirtiéndose en una herramienta estratégica para mejorar la retención y rentabilidad de la empresa.

