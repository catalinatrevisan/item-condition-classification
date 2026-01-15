# Clasificación de condición de productos (Nuevo vs Usado)

## Contexto
Este proyecto fue desarrollado en el marco de una **competencia de Kaggle** como parte de la materia **Análisis Predictivo**.  
El objetivo es predecir si un producto publicado es **nuevo o usado**, utilizando información estructurada y textual.

## Objetivo
Desarrollar un modelo de clasificación binaria capaz de:
- Identificar correctamente la condición del producto
- Generalizar a datos no vistos
- Obtener un desempeño competitivo en un entorno real (Kaggle)

## Dataset
- Conjunto de entrenamiento: 70.000 registros × 45 variables  
- Conjunto de test: 30.000 registros × 44 variables  
- Luego del feature engineering se generaron **156 variables**

## Feature Engineering
- **Numéricas**: log(precio), ratios de precio, unidades vendidas  
- **Temporales**: duración del anuncio, fechas de publicación y actualización  
- **Textuales**: longitud del título, proporción de mayúsculas y dígitos, detección de palabras clave  
- **Vendedor y atributos del producto**: reputación, envío, garantía, cantidad de imágenes  
- **Interacciones**: combinaciones de variables para capturar relaciones no lineales  

## Enfoque de Modelado
- Validación adversarial para verificar similitud entre train y test (AUC = 0.63)
- Validación cruzada estratificada (10 folds)
- Modelos entrenados:
  - LightGBM
  - XGBoost
  - CatBoost

## Ensemble de modelos
Se utilizó un **ensemble ponderado**:
- LightGBM: 35%
- XGBoost: 35%
- CatBoost: 30%

## Resultados
- AUC promedio en validación: **≈ 0.9985**
- Score público Kaggle: **0.90700**
- Score privado Kaggle: **0.90911**
- Accuracy tras optimización de umbral: **≈ 98%**

## Técnicas Avanzadas
- Pseudo-labeling para ampliar el dataset de entrenamiento
- Optimización del threshold para maximizar F1-score
- Entrenamiento con múltiples semillas para mayor robustez

## Posibles Mejoras
- Búsqueda más exhaustiva de hiperparámetros
- Stacking con un meta-modelo
- Análisis de interpretabilidad (SHAP values)

## Herramientas
Python, Pandas, Scikit-learn, LightGBM, XGBoost, CatBoost, TF-IDF
