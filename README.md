# Proyecto Final: De los Datos al Conocimiento

## 1. Objetivo del proyecto
Aplicar un flujo completo de ciencia de datos sobre el conjunto `styles.csv`, incluyendo:
- Preparación y análisis exploratorio de datos.
- Modelado supervisado.
- Modelado no supervisado.
- Optimización de hiperparámetros.
- Evaluación y comparación de resultados.

## 2. Dataset
Se utilizó el archivo `styles.csv`.

Nota técnica: el dataset contiene al menos una fila con formato inconsistente. Para evitar errores de lectura, en el notebook se usa:
`pd.read_csv('styles.csv', engine='python', on_bad_lines='skip')`

## 3. Preparación y análisis exploratorio
Decisiones aplicadas:
- Revisión de dimensiones, muestra inicial y nulos.
- Visualización de distribución por género.
- Visualización de categorías principales (top 10).
- Selección de variables simples para mantener el flujo entendible.

## 4. Modelado supervisado
- Problema: clasificación multiclase.
- Variable objetivo: `articleType`.
- Variables predictoras: `gender`, `masterCategory`, `subCategory`, `baseColour`, `season`, `year`, `usage`.
- Preprocesamiento: eliminación de nulos y codificación con `pd.get_dummies`.
- Modelo base: `RandomForestClassifier`.

Resultado principal:
- Precisión modelo base: **0.7837**.

## 5. Modelado no supervisado
- Método: K-Means.
- Preprocesamiento: codificación de variables categóricas y escalado.
- Reducción de dimensionalidad: PCA a 2 componentes para visualización.

Resultado principal:
- Silueta: **0.4941**.

## 6. Optimización de hiperparámetros
Se aplicó `GridSearchCV` sobre el modelo Random Forest con una grilla pequeña para mantener simplicidad:
- `n_estimators`: [100, 150]
- `max_depth`: [None, 20]
- `min_samples_split`: [2, 5]

Mejores hiperparámetros encontrados:
- `max_depth = 20`
- `min_samples_split = 5`
- `n_estimators = 100`

Resultado:
- Precisión optimizada: **0.7822**.

## 7. Evaluación y comparación
Comparación final de modelos supervisados:
- Modelo base: **0.7837**
- Modelo optimizado: **0.7822**

Conclusión:
- En este caso, la optimización no mejoró la precisión respecto al modelo base.
- El modelo base ya presentaba buen desempeño para una versión simple del flujo.

## 8. Visualizaciones clave incluidas
- Distribución por género.
- Top 10 de categorías principales.
- Dispersión de clusters (PCA + K-Means).
- Matriz de confusión para 10 clases frecuentes.

## 9. Justificación metodológica
- Se priorizó un enfoque simple y reproducible.
- Se seleccionaron variables de negocio directas para facilitar interpretación.
- Se incluyó modelado supervisado y no supervisado para cumplir requerimientos académicos.
- Se reportaron métricas claras para comparación objetiva.

## 10. Archivos de entrega
- Notebook: `data_analysis.ipynb`
- Informe: `README.md`
- Presentación: `Presentacion_Proyecto_Final.pptx` (basada en plantilla de estudiantes)
