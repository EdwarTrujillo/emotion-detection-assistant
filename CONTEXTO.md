# CONTEXTO del proyecto

Archivo de continuidad entre sesiones. Se actualiza al cerrar cada fase.

## Stack
Python 3.11 (conda `emotion-ai`), Jupyter Notebook, Google Colab (entrenamiento con GPU),
TensorFlow/Keras 2.21.0, OpenCV, NumPy, pandas, scikit-learn, Matplotlib/Seaborn.
Más adelante: Gradio (interfaz) y Google Gemini (asistente).

## Decisiones vigentes
Ver `docs/adr.md`.

## Estado
- [x] Fase 1: entorno conda `emotion-ai` (Python 3.11, TF 2.21.0) como kernel de Jupyter; repo en GitHub;
      dataset FER-2013 en `data/fer2013/`; EDA en `notebooks/01_data_exploration.ipynb` (18 nov)
  - 35.887 imágenes (28.709 train / 7.178 test), todas 48x48 en grises
  - Desbalance 16,5 a 1 (happy 7.215 vs disgust 436)
  - Fuga detectada: 531 imágenes de test repetidas en train → se limpia train en la fase 2 (ADR-006)
- [ ] Fase 2: entrenamiento de los modelos base y mejorado en Colab
- [ ] Fase 3: detección en tiempo real con webcam
- [ ] Fase 4: interfaz con Gradio
- [ ] Fase 5: asistente con LLM, pruebas, README final
- [ ] Fase 6: reporte IEEE y diapositivas
- [ ] Fase 7: video y entrega (24 nov, en la noche)

## Próximos pasos
Fase 2 en Colab: limpiar train (ADR-006), separar validación, entrenar modelo base y mejorado, evaluar en test.
