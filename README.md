# 🌍 ML-Predicción-Sismicidad-Global

Modelo de Machine Learning para predecir si un terremoto será significativo (magnitud ≥ 6.0) a partir de su ubicación geográfica y profundidad.

---

## 📋 Descripción del problema

Los terremotos son uno de los fenómenos naturales más destructivos del planeta, pero no todos tienen el mismo impacto. La evidencia muestra que la ubicación geográfica y la profundidad del sismo son factores clave para determinar su gravedad.

El objetivo de este proyecto es entrenar un modelo de clasificación que, dado un terremoto con sus coordenadas geográficas y profundidad, prediga si será significativo (magnitud ≥ 6.0) o no. Esto tiene aplicaciones directas en gestión de riesgos y sistemas de alerta temprana.

---

## 📊 Dataset utilizado

- **Nombre:** Global Natural Disasters 2000–2025
- **Fuente:** USGS (United States Geological Survey) — Dataset público
- **Registros:** 46.419 terremotos
- **Período:** 2000 – 2025
- **Acceso:** El dataset completo está disponible en Kaggle. En este repositorio se incluye una muestra en `src/data_sample/`

---

## 🤖 Solución adoptada

Se ha planteado un problema de **clasificación binaria supervisada**. A partir de la magnitud Richter se ha creado la variable target `es_severo`:

| Valor | Significado | Criterio |
|-------|-------------|----------|
| `1` | Terremoto significativo | Magnitud ≥ 6.0 |
| `0` | Terremoto leve/moderado | Magnitud < 6.0 |

El dataset presenta un fuerte desbalanceo de clases (91.7% vs 8.3%), por lo que las métricas principales de evaluación son **F1-Score y ROC-AUC**. Se han comparado varios algoritmos de clasificación y se ha optimizado el mejor mediante búsqueda de hiperparámetros.

---

## 📁 Estructura del repositorio

```
ML-Predicción-Sismicidad-Global/
├── src/
│   ├── data_sample/    --> Muestra del dataset original
│   ├── img/            --> Imágenes y gráficas del proyecto
│   ├── models/         --> Modelo final guardado en formato pickle
│   ├── notebooks/      --> Notebooks de desarrollo y pruebas
│   └── utils/          --> Funciones auxiliares
├── main.ipynb          --> Notebook final del pipeline de ML
├── Presentacion.pdf    --> Documento soporte de la exposición
├── requirements.txt    --> Dependencias del proyecto
└── README.md
```

---

## 🔧 Tecnologías utilizadas

- Python 3.8+
- pandas
- numpy
- scikit-learn
- imbalanced-learn (SMOTE)
- matplotlib
- seaborn
- joblib

---

## ▶️ Instrucciones de reproducción

1. Clona el repositorio:
```bash
git clone https://github.com/usuario/ML-Predicción-Sismicidad-Global.git
```

2. Instala las dependencias:
```bash
pip install -r requirements.txt
```

3. Descarga el dataset completo desde Kaggle y colócalo en `src/data_sample/`

4. Ejecuta el notebook principal:
```bash
jupyter notebook main.ipynb
```

---

## 📈 Principales resultados

| Métrica | Valor |
|---------|-------|
| Modelo seleccionado | Decision Tree (optimizado con GridSearchCV) |
| Técnica de balanceo | SMOTE |
| F1-Score (test) | 0.2276 |
| Recall clase severo (test) | 59% |
| Umbral de decisión | 0.5 (prioriza recall sobre precisión) |

> La decisión de priorizar el recall sobre el F1 responde al contexto de negocio: en un sistema de alerta temprana es preferible una falsa alarma a no detectar un terremoto severo.

---

## 🔗 Proyecto relacionado

Este proyecto es la continuación del análisis exploratorio realizado en [EDA-Sismicidad-Global](https://github.com/pmoranmacho-hue/EDA-Sismicidad-Global.git).

---

## 👥 Autores

- [Pablo Moran](@pmoranmacho-hue)
- [Enrique Algarra](@Enrique-Algarra)
- [Ana Belén Escobar](@Abem-ds)
