# Emotion Detection Assistant

Proyecto de la materia de Inteligencia Artificial (Ingeniería de Sistemas, FUP), por **Edwar Trujillo**.

Sistema de visión computacional que detecta rostros por webcam, clasifica su expresión en 7 emociones
(angry, disgust, fear, happy, neutral, sad, surprise) con una red neuronal convolucional (CNN) en tiempo real,
e incluye un asistente conversacional al que se le puede preguntar cómo se siente la persona.

> 🚧 En desarrollo. Este README se completa en la fase 5 (instalación detallada, uso y resultados).

## Estructura

```
notebooks/        Notebooks de Jupyter, en orden de ejecución (01, 02, ...)
data/             Dataset FER-2013 (no se sube a GitHub; ver "Dataset")
models/           Modelos entrenados (.keras)
reports/figures/  Gráficas generadas (EDA, entrenamiento, evaluación)
reports/metrics/  Métricas exportadas
docs/adr.md       Decisiones de arquitectura
CONTEXTO.md       Estado actual del proyecto
```

## Requisitos

- Python **3.11** (entorno conda `emotion-ai`)
- Dependencias: `pip install -r requirements.txt`

## Dataset

FER-2013 desde Kaggle. Se descomprime en `data/fer2013/` de modo que queden las carpetas
`data/fer2013/train/` y `data/fer2013/test/`. (Instrucciones detalladas en la fase 1.)

## Privacidad

No se guardan imágenes ni video de la webcam. Al modelo de lenguaje solo se envían etiquetas de emoción
y porcentajes, nunca imágenes. La API key se guarda en `.env`, que no se sube al repositorio.
