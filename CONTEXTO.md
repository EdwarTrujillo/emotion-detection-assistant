# CONTEXTO del proyecto

Archivo de continuidad entre sesiones. Se actualiza al cerrar cada fase.

## Stack
Python 3.11 (conda `emotion-ai`), Jupyter Notebook, Google Colab (entrenamiento con GPU),
TensorFlow/Keras 2.21.0, OpenCV, NumPy, pandas, scikit-learn, Matplotlib/Seaborn.
Más adelante: Gradio (interfaz) y Google Gemini (asistente).

## Decisiones vigentes
Ver `docs/adr.md`.

## Estado
- [x] Fase 1a: entorno conda `emotion-ai` con Python 3.11 y TensorFlow 2.21.0, registrado como kernel de Jupyter (18 nov)
- [x] Fase 1b: repositorio en GitHub con la estructura de carpetas (18 nov)
- [ ] Fase 1c: dataset FER-2013 y EDA (`notebooks/01_data_exploration.ipynb`)
- [ ] Fase 2: entrenamiento de los modelos base y mejorado en Colab
- [ ] Fase 3: detección en tiempo real con webcam
- [ ] Fase 4: interfaz con Gradio
- [ ] Fase 5: asistente con LLM, pruebas, README final
- [ ] Fase 6: reporte IEEE y diapositivas
- [ ] Fase 7: video y entrega (24 nov, en la noche)

## Próximos pasos
Crear la cuenta de Kaggle, descargar FER-2013 en `data/fer2013/` y ejecutar el notebook de EDA.
