# HAR-iPhone — Edge Impulse

Reconocimiento de actividad humana (Human Activity Recognition) a partir de datos de movimiento capturados con dos iPhones, en cinco clases: `bajarescaleras`, `caminar`, `correr`, `quieto`, `subirescaleras`.

## Dataset

Datos adquiridos con dos iPhones (sensores de movimiento del dispositivo).

| Clase | Duración training | Duración test | Split |
|---|---|---|---|
| Bajarescaleras | 4m 19s | 1m 20s | 76% / 24% |
| Caminar | 6m 24s | 1m 36s | 80% / 20% |
| Correr | 4m 17s | 1m 4s | 80% / 20% |
| Quieto | 4m 49s | 1m 12s | 80% / 20% |
| Subirescaleras | 4m 58s | 1m 12s | 81% / 19% |

## Resultados (validation set)

| Métrica | Valor |
|---|---|
| Accuracy | 91.8% |
| Loss | 0.21 |
| Area under ROC Curve | 0.99 |
| Weighted avg Precision | 0.92 |
| Weighted avg Recall | 0.92 |
| Weighted avg F1 score | 0.92 |

**F1 por clase**

| Clase | F1 |
|---|---|
| Bajarescaleras | 0.95 |
| Caminar | 0.97 |
| Correr | 0.87 |
| Quieto | 0.95 |
| Subirescaleras | 0.80 |

**Confusion matrix**

| | Bajarescaleras | Caminar | Correr | Quieto | Subirescaleras |
|---|---|---|---|---|---|
| **Bajarescaleras** | 92.6% | 0% | 1.9% | 0% | 5.6% |
| **Caminar** | 1.1% | 96.6% | 0% | 0% | 2.3% |
| **Correr** | 0% | 0% | 93.3% | 0% | 6.7% |
| **Quieto** | 0% | 0% | 5.4% | 94.6% | 0% |
| **Subirescaleras** | 0% | 4% | 12% | 6% | 78% |

La clase con más error es `subirescaleras` (F1 0.80), confundida principalmente con `correr` (12%) y en menor medida con `quieto` (6%) y `caminar` (4%) — consistente con que subir escaleras comparte patrones de aceleración con esas actividades. El resto de clases se mantiene por encima de 0.87 de F1.

## On-device performance

_Pendiente de completar con los datos de la pestaña Deployment (latencia, RAM, flash) para el target final._

## Estructura del repo

```
.
├── README.md
├── deployment/       # librería exportada desde Edge Impulse (según target final)
├── scripts/          # scripts/notebooks de preprocesamiento de datos de acelerómetro/giroscopio
└── docs/             # capturas del dashboard, notas de diseño del impulse
```
