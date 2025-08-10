# 🚀 Challenge TelecomX - Modelo Predictivo de Churn

**Autor**: [Marely Cárcamo Quisto]  
**Fecha**: [Agosto-2025]  
**Repositorio**: [Enlace a GitHub/GitLab]  

## 📖 Índice
1. [Descripción del Proyecto](#-descripción-del-proyecto)
2. [Misión y Objetivos](#-misión-y-objetivos)
3. [Instalación y Uso](#-instalación-y-uso)
4. [Flujo de Trabajo](#-flujo-de-trabajo)
5. [Hallazgos Clave](#-hallazgos-clave)
6. [Estructura del Repositorio](#-estructura-del-repositorio)
7. [Contribución](#-contribución)
8. [Licencia](#-licencia)

---

## 📌 **Descripción del Proyecto**
Análisis predictivo de cancelación de clientes (Churn) para TelecomX, identificando factores clave y proponiendo estrategias de retención basadas en datos. El proyecto incluye:

- Limpieza y preparación de datos
- Análisis exploratorio (EDA)
- Modelado predictivo con machine learning
- Interpretación de resultados y recomendaciones estratégicas

**Entregables**:
- `Challenge1.ipynb`: Notebook de limpieza y EDA
- `Challenge2.ipynb`: Notebook de modelado predictivo
- `datos_tratados.csv`: Dataset procesado
- `informe_churn.pdf`: Informe ejecutivo con conclusiones

---

## 🧠 **Misión y Objetivos**

### Misión
Desarrollar modelos predictivos capaces de prever qué clientes tienen mayor probabilidad de cancelar sus servicios, permitiendo a TelecomX anticiparse al problema de la cancelación mediante un pipeline robusto para esta etapa inicial de modelado.

### Objetivos
✔ **Preparación de datos**:  
   - Tratamiento de valores faltantes/anómalos  
   - Codificación y normalización de variables  

✔ **Análisis exploratorio**:  
   - Correlación entre variables  
   - Selección de características  

✔ **Modelado predictivo**:  
   - Entrenamiento de modelos de clasificación  
   - Evaluación con métricas (F1-Score, Recall, Precision)  

✔ **Interpretación**:  
   - Importancia de variables en las predicciones  
   - Conclusiones estratégicas sobre factores de churn  

---

## 🛠️ **Instalación y Uso**

### Requisitos
[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/downloads/release/python-3110/)
[![Pandas](https://img.shields.io/badge/Pandas-2.2.2-150458.svg)](https://pandas.pydata.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.4.0-orange.svg)](https://scikit-learn.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.0-11557c.svg)](https://matplotlib.org/)
[![Plotly](https://img.shields.io/badge/Plotly-5.24.1-276EF1.svg)](https://plotly.com/python/)
[![Imbalanced-Learn](https://img.shields.io/badge/Imbalanced_Learn-0.12.0-yellow.svg)](https://imbalanced-learn.org/)

```bash
# Instalar dependencias
pip install -r requirements.txt
```

### Datos Originales
🔗 [Dataset en formato JSON](https://github.com/ingridcristh/challenge2-data-science-LATAM/blob/main/TelecomX_Data.json)

### Ejecución
```bash
jupyter notebook Challenge2.ipynb
```

---

## 🔍 **Flujo de Trabajo**

### 1. Preprocesamiento (`Challenge1.ipynb`)
- Limpieza de datos (ej: `"No internet service" → "No"`)
- Creación/eliminación de variables (ej: `tiene_Fibra_Optica`)
- Análisis exploratorio (EDA)

### 2. Visualización y Gráficos Relevantes 

#### Gráfico 1. Distribución de la Cancelación
<img width="500" height="500" alt="newplot_proporcion_churn" src="https://github.com/user-attachments/assets/1765250c-cc23-419f-912d-1c7c835568a8" />

#### Gráfico 2. Tiempo Contrato X Cancelación
<img width="900" height="500" alt="newplot_tiempoContrato_X_cancelacion" src="https://github.com/user-attachments/assets/82fabe8e-1e32-434c-8d13-7538883726a2" />

#### Gráfico 3. Gasto Total X Cancelación
<img width="900" height="500" alt="newplot_gastoTotal_X_cancelacion" src="https://github.com/user-attachments/assets/a5c30560-ae31-411e-8267-16ae8c18e3ce" />

#### Gráfico 4. Correlación de Variables Categóricas
<img width="1000" height="1000" alt="newplot_correlacion" src="https://github.com/user-attachments/assets/b7885039-f7c6-45f9-aeeb-bf6ccaf7b84d" />

#### Gráfico 5. Importancia de Variables
<img width="900" height="500" alt="newplot_importancia_variables" src="https://github.com/user-attachments/assets/f0cf064b-1396-44dd-a6a3-ebac2d070fc6" />






### 3. Modelado Predictivo (`Challenge2.ipynb`)
```python
# Pipeline completo
pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('model', RandomForestClassifier())
])
```
- Balanceo de clases con **SMOTE**
- Entrenamiento de modelos (Árbol de Decisión + Random Forest)
- Evaluación con métricas:
   - F1-Score: 0.84 (Random Forest)
   - Recall: 83% 

---

## 📊 **Hallazgos Clave**
| Factor | Impacto en Churn | Estrategia Propuesta |
|--------|------------------|----------------------|
| Contrato mensual | 3× más riesgo | Ofertas anuales con 2 meses gratis |
| Primeros 6 meses | 70% cancelaciones | Onboarding personalizado |
| Gasto <$50 | 60% más churn | Paquetes "Básico Plus" |
| Pago con cheque electrónico | 25% más cancelaciones | Descuentos por pago automático |

---

## 📂 **Estructura del Repositorio**
```
.
├── data/
│   ├── raw/                    # Datos originales (JSON)
│   └── processed/              # datos_tratados.csv
├── notebooks/
│   ├── Challenge1.ipynb        # Limpieza y EDA
│   └── Challenge2.ipynb        # Modelado predictivo
├── reports/
│   └── informe_churn.pdf       # Análisis ejecutivo
├── requirements.txt            # Dependencias
└── README.md                   # Este archivo
```

---

## 🤝 **Contribución**
1. Haz fork del proyecto
2. Crea tu rama (`git checkout -b feature/nueva-mejora`)
3. Haz commit de tus cambios (`git commit -m 'Add some feature'`)
4. Haz push a la rama (`git push origin feature/nueva-mejora`)
5. Abre un Pull Request

---

## 📄 **Licencia**
[MIT](https://choosealicense.com/licenses/mit/)

---



