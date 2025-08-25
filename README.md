# 💧 Pump It Up: Predicción del estado de bombas de agua en Tanzania

**Concurso de ciencia de datos de DrivenData**:  
🔗 [Pump It Up - DrivenData](https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/)
Este proyecto tiene como objetivo construir un modelo predictivo que determine el estado de funcionamiento de las bombas de agua rurales en Tanzania.

---

## Entorno de trabajo

El entorno virtual está definido en el archivo `Environment.yml`, el cual incluye todas las dependencias necesarias. Para activarlo:

```bash
conda env create -f Environment.yml
conda activate pumpitup
```

---

## Librerías principales

El análisis utiliza las siguientes librerías para procesamiento de datos, visualización y modelado:

- `pandas`, `numpy`, `scipy`
- `matplotlib`, `seaborn`, `plotly`
- `scikit-learn`, `xgboost`, `imbalanced-learn`
- `feature_engine`, `nbformat`

---

## Estructura del proyecto

```
PUMPITUP_DATAMININGTHEWATERTABLES/
│
├── 📂 Datasets/ # Los datos de la competición no están incluidos (reglas de DrivenData). Puedes conseguir los datos participando en el concurso.
│
├── 📂 Notebooks/
│   └── PumpItUp_DataMiningTheWaterTables.ipynb
│
├── Environment.yml
├── .gitignore
├── LICENSE.txt
└── README.md
```

---

## 🧹 Análisis exploratorio y preprocesamiento del conjunto de entrenamiento

Se realizó un análisis exploratorio detallado y preprocesamiento del conjunto `train.csv`, con los siguientes pasos clave:

- **Tipología de variables**: clasificación de las variables en numéricas y categóricas.
- **Exploración de valores únicos**: identificación de columnas con alta cardinalidad y posibles redundancias.
- **Detección de valores mal codificados**: análisis para identificar entradas erróneas o inconsistentes.
- **Detección de valores atípicos**: uso del coeficiente de asimetría y estadísticas descriptivas (`describe`) para identificar outliers.
- **Tratamiento de valores faltantes**:
  - Variables numéricas imputadas con la media o mediana.
  - Variables categóricas tratadas como una clase adicional.
- **Análisis de colinealidad y correlación**:
  - Mapa de calor de correlaciones con la variable objetivo para variables numéricas.
  - V de Cramer para evaluar la asociación entre variables categóricas y la variable objetivo.
- **Conversión de variables categóricas a numéricas**: aplicación de `LabelEncoder` para preparar los datos para modelos de clasificación.

---

## 🤖 Modelado y evaluación

### Modelos explorados:

- `DecisionTreeClassifier`
- `RandomForestClassifier`
- `XGBoostClassifier` 
- Ensemble de modelos `GradientBoostingClassifier` y `RandomForestClassifier` mediante `StackingClassifier`

### Técnicas utilizadas:

- Selección de características con `RFE`.
- Validación cruzada con `StratifiedKFold`.
- Balanceo de clases con `SMOTE`.
- Optimización de hiperparámetros con `GridSearchCV` y `RandomizedSearchCV`.

### Métricas:

- Accuracy
- Matriz de confusión
- Reporte de clasificación (Precision, Recall, F1-score)

---
