# Análisis Predictivo y Exploratorio – GDSC Dataset (Genomics of Drug Sensitivity in Cancer)

Este proyecto forma parte de la formación profesional en ciencia de datos aplicada a bioinformática, como parte del programa de mentoría de Salud Analytics. El análisis utiliza datos del GDSC (Genomics of Drug Sensitivity in Cancer) con el objetivo de predecir la sensibilidad a drogas en líneas celulares de cáncer, a partir de características moleculares.

---

## Objetivo General

Explorar y modelar la relación entre perfiles genómicos de líneas celulares cancerígenas y su respuesta a tratamientos farmacológicos, medida por valores de **LN_IC50**, **AUC** y **Z-SCORE**.  
Además, se incorporan datos funcionales de las drogas (targets y pathways) para realizar un análisis de enriquecimiento biológico.

---

## Dataset

- **GDSC_DATASET.csv**: matriz consolidada de sensibilidad farmacológica y variables genómicas (expresión, metilación, CNA, MSI).
- **Compounds-annotation.csv**: metadatos de drogas, incluyendo nombres, targets y rutas biológicas.

---

## Estructura del Análisis

### 1. Carga, limpieza y transformación
- Conversión de columnas categóricas binarias (‘Y’/’N’) a numéricas (1/0).
- Generación de variable binaria para MSI.
- Eliminación de valores nulos en la variable dependiente (`LN_IC50`).

### 2. Análisis exploratorio
- Histogramas de las distribuciones de `LN_IC50`, `AUC`, `Z_SCORE`.
- Correlaciones de Spearman entre variables genómicas y respuestas a drogas.

### 3. Análisis estadístico
- Prueba de Mann-Whitney U para comparar `LN_IC50` entre líneas MSI-H vs MSS/MSI-L.

---

## Modelado Predictivo

### 4. LASSO Regression
- Entrenamiento con `LassoCV` para predicción de `LN_IC50`.
- Evaluación con RMSE y R².
- Visualización de importancia de coeficientes (magnitud).

### 5. XGBoost Regressor
- Entrenamiento con `XGBRegressor` (100 árboles, learning rate 0.1).
- Métricas: R², RMSE, MAE.
- Visualización del top 20 de variables más importantes por importancia de Gini.

---

## Feature Engineering y Análisis Funcional

### 6. Anotaciones funcionales
- Filtrado de drogas de interés y obtención de targets moleculares y vías (`TARGET_PATHWAY`) desde `Compounds-annotation.csv`.

### 7. Enrichment Analysis con gseapy
- Lista de targets utilizada para análisis de enriquecimiento con bases de datos Reactome y KEGG.
- Resultados: pathways significativamente enriquecidos (p-ajustada < 0.05).

### 8. Visualización en red (genes ↔ pathways)
- Construcción de red bipartita `Gene-Term` usando `networkx`.
- Colores diferenciados por tipo de nodo.
- Disposición tipo fuerza de resorte (`spring_layout`).

---

## Herramientas Utilizadas

- **Lenguaje**: Python (pandas, seaborn, matplotlib, scipy, sklearn, xgboost, networkx, gseapy)
- **Entorno**: Google Colab
- **Visualización**: seaborn, matplotlib, networkx




# Predictive-Modeling-of-Drug-Sensitivity-using-GDSC-Dataset
