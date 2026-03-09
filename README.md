# 📊 Telecom X: Predicción de Cancelación de Clientes (Customer Churn)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange.svg)
![Data Analysis](https://img.shields.io/badge/Data%20Analysis-Pandas%20%7C%20Seaborn-green.svg)

## 📖 Descripción del Proyecto
Este proyecto es una solución *End-to-End* de Ciencia de Datos aplicada a la industria de las telecomunicaciones. El objetivo principal es desarrollar un modelo predictivo de Machine Learning capaz de identificar qué clientes tienen un alto riesgo de cancelar su servicio (**Churn**), permitiendo a la empresa "Telecom X" tomar acciones preventivas de retención.

Dado que **adquirir un nuevo cliente es hasta 5 veces más caro que retener a uno existente**, este proyecto no solo se enfoca en la predicción matemática, sino en la extracción de *Insights* accionables para el negocio.

## 🎯 Objetivos
1. **Limpiar y preprocesar** una base de datos histórica de clientes.
2. **Explorar los datos (EDA)** para entender el comportamiento de los usuarios.
3. **Entrenar y evaluar modelos de Machine Learning** priorizando la capacidad de detectar clientes en riesgo (optimización del *Recall*).
4. **Interpretar las variables** para responder a la pregunta de negocio: *"¿Por qué se van los clientes?"*.
5. **Proponer estrategias de negocio** basadas en los resultados algorítmicos.

---

## 🛠️ Metodología y Fases del Proyecto

### Fase 1: Limpieza de Datos (Data Cleaning)
* Tratamiento de valores nulos (ej. clientes con 0 meses de permanencia y campos vacíos en `Cargos_Totales`).
* Conversión de tipos de datos (Strings a Floats).
* Creación de la variable objetivo estandarizada (`Abandono_Binario`: 1 = Cancela, 0 = Se queda).

### Fase 2: Preprocesamiento y Análisis Exploratorio (EDA)
* Análisis de correlación mediante Mapas de Calor (*Heatmaps*) y diagramas de dispersión (*Scatter plots*).
* Codificación de variables categóricas mediante **One-Hot Encoding** (`drop_first=True` para evitar multicolinealidad).
* División de datos en conjuntos de Entrenamiento y Prueba (80/20) evitando la fuga de datos (*Data Leakage*).
* Tratamiento del desbalanceo de clases aplicando **SMOTE** (Synthetic Minority Over-sampling Technique) estrictamente en el set de entrenamiento.
* Estandarización de variables numéricas con **StandardScaler**.

### Fase 3: Modelado de Machine Learning
Se entrenaron y compararon dos enfoques algorítmicos distintos:
1. **Regresión Logística:** Modelo lineal, interpretable, que requiere estandarización.
2. **Random Forest Classifier:** Modelo basado en ensambles de árboles, no lineal y robusto frente a la escala de datos.

**Métrica principal de evaluación:** **Recall (Sensibilidad)**. Se priorizó esta métrica debido a que, a nivel de negocio, el costo de un *Falso Negativo* (no detectar a un cliente que se va) es mucho mayor que el de un *Falso Positivo* (ofrecer un descuento a un cliente que pensaba quedarse).

---

## 📈 Resultados y Conclusiones del Modelado

* La **Regresión Logística** fue seleccionada como el mejor modelo para producción debido a su excelente capacidad de generalización y su alto nivel de *Recall*, capturando a la gran mayoría de los clientes en riesgo sin caer en *Overfitting* (sobreajuste), un problema que sí presentó el Random Forest en su configuración base.
* Se extrajeron los coeficientes del modelo y la importancia de variables (*Feature Importance*) para entender los motores de la cancelación.

### 🔑 Top 3 Factores que impulsan el Churn:
1. **Tiempo de contrato (Meses_Permanencia):** La mayoría de las deserciones ocurren en los primeros 6 meses.
2. **Tipo de Contrato:** Los contratos "Mes a Mes" (*Month-to-month*) facilitan la fuga rápida hacia la competencia.
3. **Cargos Mensuales:** Facturas elevadas sin una percepción clara de valor generan insatisfacción inmediata.

---

## 💼 Estrategias de Negocio Propuestas
A partir de las predicciones del modelo, se recomienda al equipo de Marketing y Ventas:

1. **Programa de Onboarding:** Fuerte enfoque en el soporte y fidelización durante el primer semestre del ciclo de vida del cliente.
2. **Migración de Contratos:** Campañas agresivas ofreciendo descuentos a cambio de pasar de contratos mensuales a contratos de 1 o 2 años.
3. **Downselling Preventivo:** Ofrecer planes más económicos a los clientes detectados en riesgo por facturación alta, antes de que decidan irse por completo.
4. **Automatización de Pagos:** Incentivar el pago con tarjeta de crédito/débito automático para reducir la "fricción" y la consciencia de pago mes a mes.

---

## 💻 Tecnologías Utilizadas
* **Lenguaje:** Python 3.x
* **Manipulación de Datos:** Pandas, Numpy
* **Visualización:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn (Modelos, Métricas, Preprocesamiento)
* **Balanceo de Datos:** Imbalanced-learn (SMOTE)

---

## 🚀 Cómo ejecutar este proyecto localmente

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tu-usuario/telecom-churn-prediction.git
   ```
2. Instala las dependencias necesarias:
   ```bash
   pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn
   ```
3. Ejecuta el Jupyter Notebook o el script de Python:
   ```bash
   jupyter notebook telecom_churn_analisis.ipynb
   # o
   python main.py
   ```

---
*Proyecto desarrollado por ciri-dev para AluraLatam.*
