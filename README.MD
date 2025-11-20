# Proyecto EDA – Análisis Exploratorio de Datos

## Descripción del proyecto
Este proyecto forma parte del módulo **Python for Data**.  
El objetivo es realizar un Análisis Exploratorio de Datos (EDA) utilizando dos datasets relacionados con campañas de marketing telefónico de una institución bancaria portuguesa:

- **bank-additional.csv** — Información de campañas y características del cliente.  
- **customer-details.xlsx** — Datos demográficos y comportamiento de clientes en diferentes años.

---

## Estructura del repositorio

```
Proyecto-EDA
│
├── data
│   ├── bank-additional.csv
│   ├── customer-details.xlsx
│   ├── bank_clean.csv
│   ├── customers_combined.csv
│   └── merged.csv
│
├── notebooks
│   ├── eda.ipynb
│   ├── limpieza_transformacion.ipynb
│   └── modelo_predictivo.ipynb
│
├── modelos
│   ├── logistic_model.pkl
│   ├── results.json
│   ├── roc_curve.png
│   └── confusion_matrix.png
│
└── README.md
```

---

##  1. Transformación y limpieza de los datos

### Dataset **bank-additional.csv**
- Eliminación de duplicados.  
- Limpieza del formato numérico (comas → puntos).  
- Conversión de *y* a binario (`yes = 1`, `no = 0`).  
- Tratamiento de nulos:
  - Numéricos → mediana.
  - Categóricos → "unknown".
- Conversión y estandarización de fechas.
- Análisis de valores atípicos.

### Dataset **customer-details.xlsx**
- Lectura de las 3 hojas y unión en un solo DataFrame.  
- Limpieza de fechas y normalización.  
- Comprobación de ausencia de nulos.  
- Preparación para *merge* con `id`.

---

## 2. Análisis descriptivo
Incluyó:
- Distribución de variables numéricas (edad, duración, campaña…).  
- Análisis de profesiones, educación, estado civil, métodos de contacto.  
- Comparación entre clientes que convierten y los que no.  
- Estadísticas: media, mediana, desviación, percentiles.  
- Matriz de correlación.

---

## 3. Visualización de datos
Se generaron gráficos utilizando **matplotlib** y **seaborn**:
- Histogramas  
- Gráficos de barras  
- Boxplots  
- Heatmap de correlaciones  
- Curva ROC del modelo predictivo  

---

##  4. Modelo predictivo supervisado
Se aplicó una **Regresión Logística** para estimar la probabilidad de conversión (`y=1`).

###  Pipeline de preprocesamiento
- `StandardScaler()` para numéricos  
- `OneHotEncoder()` para categóricos  
- `SimpleImputer()` para nulos

###  Métricas evaluadas
- Accuracy  
- Precision  
- Recall  
- F1-score  
- ROC AUC  
- Matriz de confusión  
- Curva ROC  

Los resultados, gráficos y el modelo (`logistic_model.pkl`) están en la carpeta **/modelos**.

---

##  5. Ejecución del proyecto

###  Instalar dependencias
```
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl joblib pypandoc
```

###  Ejecutar los notebooks
```
jupyter notebook
```

---

##  6. Informe del análisis
El informe contiene:
- Explicación de la estructura de los datos.  
- Proceso de limpieza y justificación.  
- Visualizaciones clave.  
- Insights relevantes sobre el comportamiento de los clientes.  
- Evaluación e interpretación del modelo predictivo.  
- Conclusiones para mejorar la estrategia de marketing.

---

##  7. Conclusiones principales
- El dataset está **fuertemente desbalanceado** (muy pocos “sí”).  
- La **duración de la llamada** es una variable muy predictiva.  
- Las variables macroeconómicas influyen en la conversión.  
- El uso de `class_weight="balanced"` mejora la detección de positivos.  
- El modelo permite asignar un **score de conversión** útil para priorizar contactos.

---



