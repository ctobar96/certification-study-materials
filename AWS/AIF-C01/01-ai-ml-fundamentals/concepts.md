# Esquema de Estudio: Dominio 1 (20% del Examen)
https://sites.google.com/view/dominio1-esquemavisual/full-page-embed
## Fundamentos de Inteligencia Artificial y Machine Learning (AWS AIF-C01)

## Resumen del Dominio 1

El Dominio 1 cubre los conceptos clave, la taxonomía y las diferencias entre **Inteligencia Artificial (IA)**, **Machine Learning (ML)** y **Deep Learning (DL)**, los tipos de aprendizaje de máquinas, el ciclo de vida del ML tradicional, las métricas de evaluación de modelos, el preprocesamiento de datos y la selección del enfoque adecuado (ML tradicional vs. IA Generativa) utilizando servicios de AWS.

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
* **Dataset de Validación:** Datos no vistos durante el entrenamiento utilizados para ajustar hiperparámetros y evaluar el sobreajuste.
* **Dataset de Prueba (Test):** Datos no vistos para evaluar el rendimiento final generalizable antes de producción.
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

## Tarea 1.3: Ciclo de Vida del Machine Learning Tradicional y Preparación de Datos

```
[1. Definición del Problema] ➔ [2. Preparación & Feature Engineering]
                                               │
[5. MLOps & Monitoreo] ◄── [4. Evaluación] ◄── [3. Entrenamiento & Tuning]
```

### 1. Preparación de Datos y Feature Engineering (Profundización AIF-C01)

* **Limpieza e Imputación:**
  * *Manejo de Valores Nulos:* Sustitución por media/mediana (variables continuas) o moda (variables categóricas).
* **Transformación de Características:**
  * **One-Hot Encoding:** Convierte variables categóricas (ej. ["Rojo", "Verde", "Azul"]) en vectores binarios (0 y 1).
  * **Normalización / Escalado (Min-Max / Standard Scaling):** Ajusta las escalas numéricas para que características con rangos grandes (ej. ingresos de $10,000 a $1,000,000) no dominen sobre variables de rango pequeño (ej. edad de 18 a 65).
* **Fuga de Datos (Data Leakage):**
  * *Riesgo Crítico del Examen:* Ocurre cuando la información del dataset de prueba o datos del futuro se filtra inadvertidamente en el entrenamiento. Provoca una métrica irrealmente alta durante el entrenamiento pero falla gravemente en producción.
* **Desequilibrio de Clases (Class Imbalance):**
  * Ocurre cuando una clase representa la inmensa mayoría de los datos (ej. 99% transacciones normales vs 1% fraudes).
  * *Técnicas:* **Oversampling** (Duplicar casos minoritarios o crear datos sintéticos con SMOTE) y **Undersampling** (Reducir datos mayoritarios).

### 2. MLOps: Monitoreo y Derivas

* **Deriva de Datos (Data Drift):** Los datos de entrada en producción cambian estadísticamente en comparación con los datos de entrenamiento (ej. hábitos de compra post-pandemia).
* **Deriva de Concepto (Concept Drift):** La relación entre las variables de entrada y la variable objetivo cambia totalmente (ej. nuevos patrones de fraude que invalidan las reglas previas).

---

## Tarea 1.4: Métricas de Evaluación, Hiperparámetros y Dilemas de Ajuste

### 1. El Conflicto Entre Sobreajuste (Overfitting) y Subajuste (Underfitting)

| Estado | Descripción | Rendimiento en Entrenamiento | Rendimiento en Datos Nuevos (Test) | Solución Recomendada |
| ----- | ----- | ----- | ----- | ----- |
| **Underfitting (Subajuste)** | El modelo es demasiado simple (Alto Sesgo/Bias). | Bajo / Deficiente | Bajo / Deficiente | Aumentar complejidad del modelo, añadir más características. |
| **Modelo Óptimo** | El modelo generaliza correctamente patrones subyacentes. | Alto | Alto | Mantener balance con validación cruzada. |
| **Overfitting (Sobreajuste)** | El modelo memoriza el ruido (Alta Varianza/Variance). | Casi Perfecto (100%) | Deficiente / Error Alto | Regularización, reducir características, dropout, aumentar datos. |

### 2. Ajuste de Hiperparámetros (Hyperparameter Tuning) y Validación

* **Hiperparámetros:** Parámetros configurados manualmente *antes* de iniciar el entrenamiento (ej. Tasa de aprendizaje / *Learning Rate*, Número de épocas / *Epochs*, Tamaño del lote / *Batch Size*).
* **Parámetros del Modelo:** Pesos y sesgos que el algoritmo aprende automáticamente durante el entrenamiento.
* **Validación Cruzada (K-Fold Cross-Validation):** División del conjunto de entrenamiento en $K$ partes para entrenar e iterar $K$ veces, asegurando que todos los subconjuntos sirvan como validación. Minimiza el riesgo de sobreajuste.
* **Estrategias de Búsqueda:**
  * *Grid Search:* Probar todas las combinaciones posibles de forma exhaustiva.
  * *Random Search:* Probar combinaciones aleatorias (más rápido).
  * *Bayesian Optimization:* Ajuste inteligente basado en resultados de pruebas previas.

### 3. Métricas de Clasificación (Matriz de Confusión)

* **Verdaderos Positivos (TP) / Verdaderos Negativos (TN):** Predicciones correctas.
* **Falsos Positivos (FP - Error Tipo I):** Falsa alarma (ej. correo legítimo enviado a Spam).
* **Falsos Negativos (FN - Error Tipo II):** Ignorar un caso real positivo (ej. no detectar una enfermedad o transacción fraudulenta -> *El error más peligroso*).

#### Fórmulas e Interpretación:

* **Precisión (Precision):** $\frac{TP}{TP + FP}$ -> Mide cuántos de los elementos etiquetados como positivos eran realmente positivos. Usar cuando los Falsos Positivos son costosos.
* **Sensibilidad / Exhaustividad (Recall / Sensitivity):** $\frac{TP}{TP + FN}$ -> Mide la capacidad para detectar todos los casos positivos reales. Crucial cuando los Falsos Negativos son críticos (salud/fraude).
* **F1-Score:** Media armónica entre Precisión y Recall. La métrica ideal para datasets con clases desequilibradas.
* **Exactitud (Accuracy):** $\frac{TP + TN}{Total}$ -> Fracción total de predicciones correctas. Útil únicamente si el dataset está balanceado.

### 4. Métricas de Regresión

* **MAE (Mean Absolute Error):** Promedio de desviaciones absolutas. Fácil interpretación, robusto frente a valores atípicos.
* **MSE (Mean Squared Error):** Promedio de errores al cuadrado. Penaliza fuertemente los errores grandes u *outliers*.
* **RMSE (Root Mean Squared Error):** Raíz cuadrada del MSE. Retorna la métrica a las unidades originales de los datos.

---

## Tarea 1.5: Selección de Soluciones y Ecosistema AWS (ML Tradicional vs. IA Generativa)

### 1. Servicios Especializados de AWS para el Ciclo de Vida de ML Tradicional

* **Amazon SageMaker Data Wrangler:** Ingestión, limpieza, visualización y preparación de datos sin necesidad de escribir código complejo.
* **Amazon SageMaker Autopilot:** AutoML (Machine Learning Automatizado) para explorar, entrenar y evaluar automáticamente los mejores modelos tradicionales según el dataset suministrado.
* **Amazon SageMaker Canvas:** Interfaz visual no-code para usuarios de negocio e ingenieros que buscan generar predicciones sin programar.
* **Amazon SageMaker Clarify:** Identificación de sesgos (*bias*) en los datos de entrenamiento y explicabilidad del modelo (valores SHAP).
* **Amazon SageMaker Model Monitor:** Detección de la deriva de datos (*Data Drift*) y deriva de concepto (*Concept Drift*) en endpoints de producción.

### 2. Criterios de Selección Empresarial

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

### 3. Tabla Comparativa de Selección

| Criterio | ML Tradicional (Clásico) | IA Generativa (GenAI) |
| ----- | ----- | ----- |
| **Casos de Uso Típicos** | Predicción de ventas, detección de fraude, churn de clientes. | Redacción de correos, resúmenes de texto, chatbots, código. |
| **Entrada / Salida** | Tablas de datos, números, categorías definidas. | Texto libre, imágenes, audio, código fuente. |
| **Costo y Cómputo** | Relativamente bajo y predecible. | Alto consumo de GPU / Procesamiento basado en tokens. |
| **Determinismo** | Determinista (Misma entrada = Misma salida). | Probabilístico y No Determinista (Varía según temperatura). |
| **Servicio AWS Principal** | Amazon SageMaker AI, Amazon Forecast. | Amazon Bedrock, Amazon Q Developer. |