# Predicción de Victimización Territorial en Chile: Un Enfoque de Machine Learning

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0%2B-orange.svg)](https://scikit-learn.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-Latest-green.svg)](https://xgboost.readthedocs.io)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📋 Descripción del Proyecto

Este proyecto desarrolla un modelo predictivo de victimización personal basado en características individuales y territoriales, utilizando datos de la **Encuesta Nacional Urbana de Seguridad Ciudadana (ENUSC) 2023** de Chile. El objetivo es identificar patrones de riesgo que permitan focalizar políticas públicas de seguridad ciudadana de manera eficiente.

### 🎯 Pregunta de Investigación

*¿Qué zonas de Chile presentan mayor riesgo de victimización, según las características individuales y del entorno urbano, estimadas a partir de modelos de aprendizaje automático?*

## 👥 Autores

- **Catalina Aránguiz** - [caranguizc@estudiante.uc.cl](mailto:caranguizc@estudiante.uc.cl)
- **Maykol Medrano** - [mmedrano@uc.cl](mailto:mmedrano@uc.cl)

**Institución:** Instituto de Economía, Pontificia Universidad Católica de Chile  
**Curso:** EAE3709 - Aplicaciones de Machine Learning en Economía  
**Semestre:** Primer Semestre 2025

## 🔍 Características Principales

- **Análisis multiterritorial**: Evaluación de robustez predictiva across 16 regiones de Chile
- **Feature engineering psicométrico**: Construcción de índices compuestos validados con Cronbach's Alpha
- **Comparación algorítmica**: SVM, Random Forest y XGBoost con optimización de hiperparámetros
- **Explicabilidad SHAP**: Análisis de importancia territorial y dependencias no-lineales
- **Validación estratificada**: Train/test split que preserva distribuciones regionales

## 📊 Metodología

### 1. Datos y Variables

- **Fuente**: ENUSC 2023 (Instituto Nacional de Estadísticas + Ministerio del Interior)
- **Muestra**: Población urbana chilena con filtro Kish para independencia
- **Variables**: 68 features organizados en 6 categorías:
  - Sociodemográficas (edad, sexo, educación, NSE)
  - Territoriales (región, antigüedad, presencia institucional)
  - Perceptuales (desórdenes, incivilidades, exposición)
  - Organizacionales (medidas comunitarias, cohesión social)
  - Confianza institucional (evaluación Carabineros)
  - **Target**: Victimización personal binaria (0/1)

### 2. Preprocesamiento

- **Índices compuestos**: Agregación psicométrica de variables correlacionadas
- **Encoding estratificado**: Variables binarias (0/1) y dummy encoding para categóricas
- **Imputación robusta**: Mediana para continuas, moda para categóricas
- **Validación territorial**: Split estratificado región×victimización (80/20)

### 3. Modelado

- **Algoritmos**: SVM Lineal, Random Forest, XGBoost
- **Optimización**: GridSearchCV con validación cruzada estratificada (5-fold)
- **Métrica primaria**: F1-Score (balance precision-recall para datos desbalanceados)
- **Balanceo**: Class weights y scale_pos_weight según ratio empírico (3.58:1)

### 4. Evaluación

- **Performance territorial**: Score combinado que penaliza variabilidad regional
- **Explicabilidad SHAP**: Importancia global y heterogeneidad territorial
- **Métricas múltiples**: F1, AUC-ROC, Balanced Accuracy, Sensibilidad, Especificidad

## 🚀 Instalación y Uso

### Requisitos

```bash
pip install -q pyreadstat pingouin factor_analyzer pandas pyarrow
pip install -q scikit-learn xgboost imbalanced-learn
pip install -q matplotlib seaborn missingno
pip install -q shap lime
