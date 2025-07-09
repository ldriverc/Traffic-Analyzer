# Traffic Analyzer - Sistema de Análisis de Tráfico Vehicular con Machine Learning

[![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)](https://www.python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🚦 Descripción

Traffic Analyzer es un sistema avanzado de análisis de tráfico vehicular que utiliza técnicas de Machine Learning para procesar, analizar y predecir patrones de tráfico. El sistema está diseñado para trabajar con datos de sensores de tráfico almacenados en archivos Excel, proporcionando insights valiosos para la gestión del tráfico urbano.

## 🎯 Características Principales

### 📊 Análisis Exploratorio
- **Carga automática de datos**: Procesamiento recursivo de archivos Excel desde múltiples carpetas
- **Preprocesamiento inteligente**: Limpieza de datos, detección de valores atípicos y normalización
- **Análisis temporal**: Identificación de patrones por hora, día de la semana y estacionalidad
- **Detección de horas punta**: Identificación automática de períodos de alta congestión

### 🤖 Machine Learning
- **Modelos predictivos**: Random Forest para predicción de flujo vehicular y ocupación
- **Detección de anomalías**: Isolation Forest para identificar datos atípicos
- **Análisis de clustering**: K-means para identificar patrones de tráfico similares
- **Ingeniería de características**: Extracción automática de features temporales y categóricas

### 📈 Visualizaciones
- **Dashboards interactivos**: Visualizaciones comprensivas con matplotlib y seaborn
- **Heatmaps temporales**: Análisis de patrones por hora y día de la semana
- **Análisis comparativo**: Comparación entre diferentes períodos (2024 vs 2025)
- **Métricas de rendimiento**: Visualización de la importancia de características

### 🔮 Predicción
- **Predicción en tiempo real**: Estimación de flujo y ocupación para condiciones específicas
- **Análisis de tendencias**: Identificación de cambios significativos en el tráfico
- **Clustering de patrones**: Agrupación de comportamientos similares de tráfico

## 🛠️ Instalación

### Requisitos Previos
- Python 3.7 o superior
- Jupyter Notebook
- Google Colab (opcional)

### Dependencias
```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn
pip install openpyxl xlrd
```

### Configuración en Google Colab
1. Abrir el notebook en Google Colab
2. Montar Google Drive para acceder a los archivos de datos
3. Ejecutar las celdas de instalación de dependencias

## 📁 Estructura de Datos

### Formato de Entrada
El sistema espera archivos Excel con la siguiente estructura:

| Columna | Descripción | Tipo |
|---------|-------------|------|
| `Fecha` | Fecha de la medición | DateTime |
| `Hora` | Hora de la medición | Time |
| `Pista` | Identificador de la pista | Integer |
| `Flujo` | Número de vehículos | Float |
| `Ocupación` | Tiempo de ocupación en ms | Float |

### Estructura de Carpetas
```
/content/drive/MyDrive/Mediciones/
├── 2024/
│   ├── enero/
│   │   ├── medicion_01.xlsx
│   │   └── medicion_02.xlsx
│   └── febrero/
└── 2025/
    └── enero/
        └── medicion_01.xlsx
```

## 🚀 Uso

### Ejecución Básica
```python
# Inicializar el analizador
analyzer = TrafficAnalyzer()

# Cargar todos los archivos Excel
analyzer.load_all_excel_files()

# Ejecutar análisis completo
analyzer.generate_comprehensive_report()
```

### Análisis Específicos

#### 1. Análisis Comparativo de Horas Punta
```python
# Comparar tráfico entre 2024 y 2025
results = analyzer.analyze_peak_hours_comparison()
```

#### 2. Predicción con Machine Learning
```python
# Entrenar modelos predictivos
rf_flujo, rf_ocupacion, features = analyzer.ml_traffic_prediction()

# Realizar predicción
flujo_pred, ocupacion_pred = predict_traffic(
    analyzer, rf_flujo, rf_ocupacion, features,
    hora=8, pista=1, dia_semana=1, mes=7
)
```

#### 3. Análisis de Clustering
```python
# Identificar patrones de tráfico
patterns, kmeans_model = analyzer.clustering_analysis()
```

## 📊 Resultados y Métricas

### Métricas de Rendimiento
- **R² Score**: Coeficiente de determinación para evaluar la calidad del modelo
- **MAE (Mean Absolute Error)**: Error absoluto medio
- **RMSE (Root Mean Square Error)**: Raíz del error cuadrático medio

### Outputs Generados
1. **Visualizaciones temporales**: Gráficos de flujo y ocupación por hora/día
2. **Heatmaps**: Mapas de calor que muestran patrones de tráfico
3. **Clusters de comportamiento**: Agrupaciones de patrones similares
4. **Predicciones**: Estimaciones de tráfico futuro
5. **Reportes estadísticos**: Resúmenes numéricos y comparativos

## 🔧 Configuración Avanzada

### Personalización de Horas Punta
```python
analyzer = TrafficAnalyzer()
analyzer.peak_hours_morning = (6, 10)  # 6 AM - 10 AM
analyzer.peak_hours_evening = (16, 21)  # 4 PM - 9 PM
```

### Ajuste de Parámetros de ML
```python
# Personalizar Random Forest
rf_flujo = RandomForestRegressor(
    n_estimators=200,
    max_depth=15,
    random_state=42
)

# Personalizar detección de outliers
iso_forest = IsolationForest(
    contamination=0.05,  # 5% de outliers esperados
    random_state=42
)
```

## 📈 Casos de Uso

### 1. Gestión de Tráfico Urbano
- Identificación de cuellos de botella
- Optimización de semáforos
- Planificación de rutas alternativas

### 2. Análisis de Infraestructura
- Evaluación de la capacidad de las vías
- Planificación de ampliaciones
- Estudios de impacto de nuevas construcciones

### 3. Predicción y Planificación
- Estimación de tráfico futuro
- Planificación de eventos especiales
- Gestión proactiva de congestiones

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Para contribuir:

1. Fork el repositorio
2. Crear una rama feature (`git checkout -b feature/AmazingFeature`)
3. Commit los cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir un Pull Request

## 📝 Licencia

Este proyecto está licenciado bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 🙏 Agradecimientos

- Desarrollado para análisis de tráfico vehicular urbano
- Utiliza bibliotecas de código abierto de la comunidad Python
- Inspirado en metodologías de ingeniería de tráfico moderna

## 📞 Contacto

Para preguntas, sugerencias o soporte técnico, por favor contacta al equipo de desarrollo.

---

**Nota**: Este sistema está optimizado para trabajar con Google Colab y requiere acceso a Google Drive para la carga de archivos de datos.
