# SCY1101-EV3-CarSeats

## Proyecto: Análisis y Predicción de Ventas de Sillas para Autos (Car Seats)

**Asignatura:** SCY1101 - Programación para la Ciencia de Datos  
**Evaluación:** Parcial N°3

---

## Integrantes

- Felipe Araya
- Antonia Muñoz
- Sofia Cortese

---

## Descripción

Proyecto de análisis de datos y machine learning aplicado al dataset **Car Seats**, que contiene información de ventas de sillas infantiles para autos en 400 tiendas de EE.UU.

Se implementa un pipeline ETL completo con extracción desde CSV y API REST (tipo de cambio USD→CLP), análisis exploratorio de datos (EDA), y se comparan dos modelos supervisados de clasificación (**Árbol de Decisión** y **Regresión Logística**) para predecir si una tienda tendrá ventas altas (`HighSales`). Finalmente se construye un **Dashboard interactivo con Plotly Dash** para la visualización de los resultados.

---

## Estructura del proyecto

```
SCY1101-EV3-CarSeats/
├── data/
│   ├── raw/
│   │   └── dataset_car_seats.csv          # Dataset original
│   └── processed/
│       └── dataset_car_seats_clean.csv    # Dataset preprocesado generado por el notebook
├── notebooks/
│   └── EV3CarsSeat_final.ipynb            # Notebook principal
└── README.md
```

---

## Contenido del Notebook

El notebook sigue el flujo ETL + ML definido en la pauta:

1. **Extracción** — Carga del CSV y obtención del tipo de cambio USD/CLP desde API REST (`dolarapi.com`)
2. **Transformación** — Conversión de columnas monetarias a CLP y creación de la variable objetivo `HighSales`
3. **EDA** — Estadísticas descriptivas, boxplots por variable, histogramas, scatter plots y matriz de correlación
4. **Preparación** — Label Encoding (`Urban`, `US`), get_dummies (`ShelveLoc`), estandarización con `StandardScaler` antes de la división
5. **Carga** — Guardado del dataset limpio como `dataset_car_seats_clean.csv`
6. **Modelado** — Árbol de Decisión y Regresión Logística con `GridSearchCV`, métricas por clase y matriz de confusión
7. **Dashboard** — Dashboard interactivo con Plotly Dash accesible vía cloudflared

---

## Dependencias

```
pandas
numpy
matplotlib
seaborn
scikit-learn
requests
dash
plotly
```

---

## Cómo reproducir

1. Abrir `notebooks/EV3CarsSeat_final.ipynb` en **Google Colab**
2. Subir `data/raw/dataset_car_seats.csv` al entorno de Colab
3. Ejecutar las celdas en orden
4. Al llegar a la última celda, se generará automáticamente una URL pública con **cloudflared** para acceder al dashboard

---

## Variables del Dataset

| Variable | Descripción |
|---|---|
| `Sales` | Ventas unitarias en miles (variable objetivo base) |
| `HighSales` | 1 si Sales > 8 mil unidades, 0 si no (variable objetivo ML) |
| `CompPrice` | Precio del competidor (CLP) |
| `Income` | Ingreso de la comunidad (CLP) |
| `Advertising` | Presupuesto publicidad local (CLP) |
| `Population` | Tamaño de la población |
| `Price` | Precio de las sillas en la tienda (CLP) |
| `ShelveLoc` | Calidad de ubicación en estantería (Good/Medium/Bad) |
| `Age` | Edad promedio de la población |
| `Education` | Nivel educacional promedio |
| `Urban` | ¿Tienda en zona urbana? (Yes/No) |
| `US` | ¿Tienda en EE.UU.? (Yes/No) |
