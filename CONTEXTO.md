# CONTEXTO del proyecto

Archivo de continuidad entre sesiones. Se actualiza al cerrar cada fase.

## Stack
Python 3.11 (conda `emotion-ai`), Jupyter Notebook, Google Colab (entrenamiento con GPU),
TensorFlow/Keras 2.21.0, OpenCV, NumPy, pandas, scikit-learn, Matplotlib/Seaborn.
Más adelante: Gradio (interfaz) y Google Gemini (asistente).

## Decisiones vigentes
Ver `docs/adr.md`.

## Estado
- [x] Fase 1: entorno, repo, dataset y EDA (`notebooks/01_data_exploration.ipynb`) (18 nov)
  - 35.887 imágenes; desbalance 16,5 a 1; fuga detectada (531 imágenes de test en train) → ADR-006
- [x] Fase 2: entrenamiento en Colab (`notebooks/02_model_training.ipynb`) (18 nov)
  - Train limpio 24.220 / validación 2.692 / test 7.178
  - Base 58,9 % · Mejorado 64,0 % · v2 65,9 % · **v2 + TTA 66,5 % (top-2 83,6 %)**
  - Modelo final: `models/improved_model_v2.keras` con TTA (`models/selected_model.json`), elegido por validación
- [ ] Fase 3: detección en tiempo real con webcam
- [ ] Fase 4: interfaz con Gradio
- [ ] Fase 5: asistente con LLM, pruebas, README final
- [ ] Fase 6: reporte IEEE y diapositivas
- [ ] Fase 7: video y entrega (24 nov, en la noche)

## Próximos pasos
Fase 3: `notebooks/03_realtime_detection.ipynb` con Haar Cascade + modelo seleccionado (con TTA), suavizado e historial.
