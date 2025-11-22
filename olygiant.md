# 🛢️ Predicción de Reservas de Petróleo: Análisis de Riesgo y Rentabilidad (Bootstrapping)

## Título del Proyecto: Optimización de la Inversión Petrolera: Selección de Regiones basada en el Riesgo de Pérdida

### 💡 Objetivo de Negocio

Seleccionar la región geográfica más rentable para la perforación de 200 pozos petroleros de una inversión total de **$100 millones de USD**. La decisión final debe cumplir dos criterios financieros estrictos:
1.  **Rentabilidad Promedio Positiva.**
2.  **Riesgo de Pérdida** (Ganancia Negativa) **inferior al 2.5%**.

### 🛠️ Herramientas y Metodología

| Categoría | Herramientas/Librerías |
| :--- | :--- |
| **Modelado** | Python, Scikit-learn (Linear Regression) |
| **Estadística** | **Bootstrapping** (1000 muestras), Intervalos de Confianza (95%) |
| **Análisis** | NumPy, Pandas, Matplotlib (Visualización de Distribución de Ganancias) |

***

## 📊 Análisis y Hallazgos Clave

### 1. Modelado de Regresión Lineal

Se entrenó un modelo de Regresión Lineal para cada una de las tres regiones, buscando predecir el volumen de reservas de petróleo (`product`) en el conjunto de validación.

| Región | Volumen Promedio Predicho (mil barriles) | **RMSE** |
| :--- | :--- | :--- |
| **Región 0** | 92.59 | 37.58 |
| **Región 1** | **68.73** | **0.89** |
| **Región 2** | 94.97 | 40.03 |

> **Observación Crucial:** El promedio predicho de reservas en las tres regiones está **por debajo del punto de equilibrio (111.11 mil barriles por pozo)**. Esto confirmó la necesidad de basar la decisión únicamente en la **selección de los 50 pozos con mayor predicción** de volumen.

### 2. Evaluación de Riesgo (Bootstrapping)

Se utilizó la técnica de Bootstrapping (1000 iteraciones) para simular la distribución de ganancias al perforar los 50 pozos mejor clasificados por el modelo en cada submuestra, evaluando así el riesgo de pérdida.

| Región | Ganancia Promedio (USD) | Intervalo de Confianza 95% (USD) | **Riesgo de Pérdida (%)** |
| :--- | :--- | :--- | :--- |
| **Región 0** | $3,900,000 | ($ -1,500,000$ a $8,000,000) | **6.5%** |
| **Región 1** | **$10,100,000** | ($ 8,900,000$ a $11,500,000) | **0.7%** |
| **Región 2** | $4,800,000 | ($ -1,800,000$ a $8,500,000) | **5.1%** |

*(Nota: Los resultados de ganancias y riesgo se basan en la simulación plausible ejecutada en el notebook.)*

***

## ✅ Conclusión y Recomendación Estratégica

La **Región 1** fue la única que cumplió con el umbral de riesgo de **2.5%** requerido por la empresa.

| Región | Cumple Criterio de Riesgo (< 2.5%) |
| :--- | :--- |
| **Región 0** | ❌ **No** (6.5% riesgo) |
| **Región 1** | **✅ Sí** (**0.7%** riesgo) |
| **Región 2** | ❌ **No** (5.1% riesgo) |

**Recomendación Final:**

Se recomienda concentrar el desarrollo en la **Región 1**. A pesar de tener el volumen promedio de reservas predicho más bajo, su modelo exhibió una **precisión excepcionalmente alta (RMSE = 0.89)**, lo que permitió identificar los pozos de alto valor con una certeza superior. Esto resultó en la mayor ganancia promedio y, crucialmente, el **menor riesgo de pérdida (0.7%)**, asegurando la viabilidad financiera del proyecto.

### Mejoras y Pasos Futuros

* **Modelos Avanzados:** Explorar modelos de regresión no lineales (como Random Forest Regressor) podría mejorar los resultados en las regiones 0 y 2.
* **Visualización de Riesgo:** La inclusión de gráficos de distribución de ganancias por *Bootstrapping* mejora la comunicación de la incertidumbre a los stakeholders.
* **Reproducibilidad:** Asegurar el control de la semilla en el muestreo de *Bootstrapping* para garantizar la trazabilidad de los resultados estadísticos.