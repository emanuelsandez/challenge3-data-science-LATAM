# challenge3-data-science-LATAM

# Proyecto de Análisis y Predicción de Churn para Telecom X

Este repositorio contiene el análisis exploratorio y el desarrollo de modelos predictivos para anticipar la cancelación de clientes (churn) en la empresa de telecomunicaciones **Telecom X**. El objetivo es identificar los factores más influyentes en la decisión de los clientes de darse de baja y construir un modelo que permita detectar tempranamente a aquellos con mayor riesgo, facilitando acciones de retención focalizadas.

---

## 📋 Contexto y Objetivos

Telecom X enfrenta una alta tasa de cancelación de clientes. A través de este proyecto se busca:

- Comprender las características demográficas, de servicios y de facturación que diferencian a los clientes que cancelan de los que permanecen.
- Desarrollar un modelo predictivo robusto que calcule la probabilidad de churn para cada cliente.
- Proporcionar recomendaciones de negocio basadas en los hallazgos para reducir la tasa de abandono.

---

## 📁 Estructura del Proyecto

```
.
├── TelecomX_2_LATAM_prueba.ipynb     # Notebook de modelado predictivo
├── datos_tratados.csv                 # Dataset limpio generado en el EDA (no incluido en el repo, se genera al ejecutar el primer notebook)
├── README.md                          # Este archivo

```

---

## ⚙️ Requisitos e Instalación

Para ejecutar los notebooks se necesita Python 3.8+ y las siguientes librerías:

- pandas
- numpy
- matplotlib
- seaborn
- plotly
- scikit-learn
- imbalanced-learn (para SMOTE)
- requests

Puedes instalarlas todas con:

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn imbalanced-learn requests
```


## 🚀 Uso

1. **Clona el repositorio**  
   ```bash
   git clone https://github.com/emanuelsandez/challenge3-data-science-LATAM
   cd TelecomX2_LATAM
   ```

2. **Ejecuta el notebook de modelado**  
   Abre `TelecomX2_LATAM.ipynb` y ejecuta las celdas. Este notebook carga `datos_tratados.csv`, prepara los datos, entrena varios modelos y evalúa su rendimiento.

---

## 📊 Resultados Principales

### Análisis Exploratorio (EDA)

- **Tasa de cancelación global:** 26,6% (1869 clientes).
- **Perfil de cliente que cancela:**
  - Contrato **mes a mes** (88,5% de los que cancelan).
  - Pago mediante **cheque electrónico** (57,3%).
  - Poca antigüedad (mediana de 10 meses vs 38 meses de los que permanecen).
  - Cargos mensuales más altos (mediana $80,75 vs $65,0).
  - Mayoría con **ambos servicios** contratados (internet + teléfono, 84,8%).

### Modelado Predictivo

Se evaluaron tres modelos:

| Modelo        | Accuracy | Precisión | Recall | F1‑score | Observaciones |
|---------------|----------|-----------|--------|----------|---------------|
| Dummy (base)  | 0.50     | —         | 0.00   | 0.00     | Clasificador trivial. |
| Random Forest | **0.82** | **0.78**  | **0.88**| **0.83** | Mejor equilibrio, generaliza bien. |
| KNN           | 0.77     | 0.72      | 0.88   | 0.79     | Recall similar, menor precisión. |

**Modelo seleccionado:** Random Forest, por su alto recall (88%) y buena estabilidad entre entrenamiento y prueba.

**Variables más importantes** (acumulan el 86% de la importancia):

1. **Contrato mensual** (23%) – 42,7% de churn.
2. **Antigüedad (tenure)** (19%) – mediana de 10 meses en cancelados.
3. **Internet de fibra óptica** (13%) – 41,9% de churn.
4. **Pago con cheque electrónico** (8%) – 45,3% de churn.
5. **Cargos mensuales** (6%) – mayores en cancelados.
6. Internet DSL (5%)
7. Pago por correo (5%)
8. Seguridad online (4%)
9. Soporte técnico (4%)
10. Facturación electrónica (3%)

---

## 💡 Estrategias de Retención Propuestas

1. **Migrar contratos mensuales a anuales**  
   Ofrecer descuentos (ej. 10%) o meses gratis a clientes con contrato mensual que se cambien a planes de mayor duración.

2. **Promover el pago automático**  
   Incentivar con pequeños descuentos mensuales el cambio de cheque electrónico a débito automático o tarjeta de crédito.

3. **Acompañar a clientes nuevos**  
   Implementar un programa de onboarding durante el primer año: llamadas de bienvenida, encuestas de satisfacción y ofertas personalizadas al cumplir 11 meses.

4. **Revisar la relación precio‑valor de la fibra óptica**  
   Evaluar si los precios son competitivos y mejorar la comunicación de los beneficios del servicio.

5. **Alertas tempranas con el modelo predictivo**  
   Integrar el modelo en un sistema que genere alertas diarias con clientes de alto riesgo, activando ofertas personalizadas o contactos proactivos.

---

## 🛠 Tecnologías Utilizadas

- **Python 3** – Lenguaje principal.
- **Pandas / NumPy** – Manipulación y análisis de datos.
- **Matplotlib / Seaborn / Plotly** – Visualizaciones.
- **Scikit-learn** – Modelos de machine learning (Random Forest, KNN, métricas, validación).
- **Imbalanced-learn** – SMOTE para balanceo de clases.
- **Requests** – Descarga del dataset.

---
