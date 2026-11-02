# Esquema de Estudio Detallado: Dominio 1 (20% del Examen)
## Fundamentos de Inteligencia Artificial y Machine Learning (AWS AIF-C01)

---

## Resumen del Dominio 1
El Dominio 1 cubre los conceptos clave, la taxonomía y las diferencias entre **Inteligencia Artificial (IA)**, **Machine Learning (ML)** y **Deep Learning (DL)**, los tipos de aprendizaje de máquinas, el ciclo de vida del ML tradicional, las métricas de evaluación de modelos y la selección del enfoque adecuado (ML tradicional vs. IA Generativa) para resolver problemas empresariales en AWS.

---

## Tarea 1.1: Conceptos Básicos y Taxonomía de IA/ML

### 1. Jerarquía y Relación de Conceptos
* **Inteligencia Artificial (IA):** Campo amplio de la informática dedicado a crear sistemas capaces de realizar tareas que simulan el razonamiento humano (sistemas basados en reglas, lógica formal, IA/ML).
* **Machine Learning (ML):** Subconjunto de la IA en el que los algoritmos aprenden patrones directamente a partir de datos estructurados o no estructurados sin ser programados explícitamente.
* **Deep Learning (DL):** Subconjunto del ML basado en **Redes Neuronales Artificiales (ANN)** con múltiples capas (profundas), óptimo para datos no estructurados como imágenes, audio y texto.
* **IA Generativa (GenAI):** Subconjunto especializado del Deep Learning enfocado en crear nuevo contenido sintético (texto, imagen, código, audio) en lugar de clasificar o predecir valores.

### 2. Vocabulario y Definiciones Esenciales para el Examen
* **Feature (Característica/Variable de Entrada):** Atributo individual medible utilizado como entrada para realizar una predicción (ej. metros cuadrados de una casa).
* **Label / Target (Etiqueta/Variable Objetivo):** La respuesta correcta o el valor objetivo que el modelo intenta predecir (ej. precio final de la casa).
* **Dataset de Entrenamiento:** Conjunto de datos utilizado por el algoritmo para aprender patrones.
* **Dataset de Validación y Prueba (Validation & Test):** Datos no vistos durante el entrenamiento, utilizados para evaluar el rendimiento generalizable del modelo.
* **Inferencia:** El proceso en el cual un modelo entrenado genera predicciones sobre nuevos datos de entrada en producción.

---

## Tarea 1.2: Tipos de Aprendizaje Automático (ML Paradigms)

### 1. Aprendizaje Supervisado (Supervised Learning)
* **Definición:** El algoritmo se entrena con datos etiquetados (*Inputs + Correct Labels*).
* **Principales Tareas:**
  * **Clasificación:** Predicción de categorías discretas o etiquetas de clase.
    * *Binaria:* Sí/No, Fraudulento/Legítimo.
    * *Multiclase:* Clasificar un correo en Spam, Social o Promociones.
  * **Regresión:** Predicción de valores numéricos continuos (ej. pronóstico de ingresos, estimación de temperatura).

### 2. Aprendizaje No Supervisado (Unsupervised Learning)
* **Definición:** El algoritmo analiza datos sin etiquetas predefinidas para encontrar estructuras o patrones ocultos.
* **Principales Tareas:**
  * **Agrupamiento (Clustering):** Segmentación de elementos similares (ej. agrupamiento de clientes por hábitos de compra con K-Means).
  * **Reducción de Dimensionalidad:** Compresión de un número elevado de características a un espacio menor sin perder información esencial (ej. PCA - Principal Component Analysis).
  * **Detección de Anomalías:** Identificación de puntos atípicos en transmisiones de datos.

### 3. Aprendizaje por Refuerzo (Reinforcement Learning - RL)
* **Definición:** Un **agente** aprende a tomar decisiones dentro de un **entorno** dinámico mediante prueba y error para maximizar una **recompensa acumulada**.
* **Conceptos Clave:** Agente, Entorno (Environment), Estado (State), Acción (Action), Recompensa (Reward).
* **Casos de Uso Empresarial:** Optimización de rutas logísticas, robótica industrial, comercio financiero automatizado y AWS DeepRacer.

---

## Tarea 1.3: Ciclo de Vida del Machine Learning Tradicional

```
[1. Definición del Problema] ➔ [2. Recopilación y Preparación de Datos]
                                       │
[5. Despliegue y Monitoreo] ◄── [4. Evaluación] ◄── [3. Entrenamiento]
```

1. **Definición del Problema Empresarial:** Identificación de los KPIs y conversión a una tarea de ML.
2. **Ingestión y Preparación de Datos (Data Engineering):**
   * *Limpieza:* Manejo de valores nulos o duplicados.
   * *Feature Engineering:* Transformación de datos brutos en variables representativas (ej. normalización, codificación one-hot).
   * *Split de Datos:* División en 70-80% entrenamiento, 10-15% validación y 10-15% prueba.
3. **Entrenamiento del Modelo (Model Training):** Ajuste de hiperparámetros y optimización de funciones de pérdida.
4. **Evaluación:** Verificación del rendimiento frente a los requisitos empresariales antes del despliegue.
5. **Despliegue y Monitoreo (MLOps):** Medición de deriva de datos (*Data Drift*) y deriva de concepto (*Concept Drift*).

---

## Tarea 1.4: Métricas de Evaluación y Dilemas de Ajuste

### 1. El Conflicto Entre Sobreajuste (Overfitting) y Subajuste (Underfitting)

| Estado | Descripción | Rendimiento en Entrenamiento | Rendimiento en Datos Nuevos (Test) | Solución Recomendada |
| :--- | :--- | :--- | :--- | :--- |
| **Underfitting (Subajuste)** | El modelo es demasiado simple; no capta los patrones básicos. | Bajo / Deficiente | Bajo / Deficiente | Aumentar complejidad del modelo, añadir más características. |
| **Modelo Óptimo** | El modelo generaliza correctamente patrones subyacentes. | Alto | Alto | Mantener balance con validación cruzada. |
| **Overfitting (Sobreajuste)** | El modelo memoriza el ruido del conjunto de entrenamiento. | Casi Perfecto (100%) | Deficiente / Error Alto | Regularización, reducir características, aumentar datos de entrenamiento. |

### 2. Métricas de Clasificación (Matriz de Confusión)
* **Verdaderos Positivos (TP) / Verdaderos Negativos (TN):** Predicciones correctas.
* **Falsos Positivos (FP - Error Tipo I):** Dar una alarma falsa (ej. clasificar correo legítimo como Spam).
* **Falsos Negativos (FN - Error Tipo II):** Ignorar un caso real (ej. clasificar una transacción fraudulenta como legítima -> *El error más peligroso en salud/seguridad*).

#### Fórmulas e Interpretación para AWS AIF-C01:
* **Precisión (Precision):** $\frac{TP}{TP + FP}$ -> Mide cuántos de los elementos etiquetados como positivos eran realmente positivos. Crucial cuando los falsos positivos son costosos.
* **Sensibilidad / Exhaustividad (Recall / Sensitivity):** $\frac{TP}{TP + FN}$ -> Mide la capacidad del modelo para capturar todos los casos positivos reales. Crucial en diagnóstico médico y fraude.
* **F1-Score:** Media armónica entre Precisión y Recall. Ideal cuando hay clases desequilibradas.
* **Exactitud (Accuracy):** $\frac{TP + TN}{Total}$ -> Fracción total de predicciones correctas. Útil únicamente si el dataset está balanceado.

### 3. Métricas de Regresión
* **MAE (Mean Absolute Error):** Promedio de las diferencias absolutas entre predicciones y valores reales. Fácil de interpretar.
* **MSE (Mean Squared Error):** Promedio de los errores al cuadrado. Penaliza fuertemente los errores grandes o valores atípicos (*outliers*).
* **RMSE (Root Mean Squared Error):** Raíz cuadrada del MSE. Retorna la métrica a las unidades originales de los datos.

---

## Tarea 1.5: Selección de Soluciones: ML Tradicional vs. IA Generativa en AWS

### Criterios de Selección Empresarial

```
                         ¿El problema requiere generar contenido totalmente nuevo?
                                           │
                        ┌──────────────────┴──────────────────┐
                       SÍ                                    NO
                        │                                     │
                        ▼                                     ▼
        【IA Generativa (LLMs / FMs)】            ¿Tiene datos estructurados/etiquetados
         Amazon Bedrock / Titan                  y busca predecir valores o categorías?
                                                              │
                                                        ┌─────┴─────┐
                                                       SÍ          NO
                                                        │           │
                                                        ▼           ▼
                                                 【ML Tradicional】 【Analítica/Reglas】
                                                 Amazon SageMaker   Servicios Clásicos AWS
```

### Tabla Comparativa de Selección

| Criterio | ML Tradicional (Clásico) | IA Generativa (GenAI) |
| :--- | :--- | :--- |
| **Casos de Uso Tipicos** | Predicción de ventas, detección de fraude, churn de clientes. | Redacción de correos, resúmenes de texto, chatbots, código. |
| **Entrada / Salida** | Tablas de datos, números, categorías definidas. | Texto libre, imágenes, audio, código fuente. |
| **Costo y Cómputo** | Relativamente bajo y predecible. | Alto consumo de GPU / Procesamiento basado en tokens. |
| **Determinismo** | Determinista (Misma entrada = Misma salida). | Probabilístico y No Determinista (Varía según temperatura). |
| **Servicio AWS Principal** | Amazon SageMaker AI, Amazon Forecast. | Amazon Bedrock, Amazon Q Developer. |