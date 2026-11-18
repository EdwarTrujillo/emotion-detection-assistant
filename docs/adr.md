# Registro de decisiones de arquitectura (ADR)

Formato corto: contexto, decisión y consecuencias.

## ADR-001: Dataset FER-2013 (18 nov 2026)
- **Contexto:** se necesita un dataset público y etiquetado de expresiones faciales.
- **Decisión:** FER-2013 (35.887 imágenes de 48x48 en escala de grises, 7 clases), descargado de Kaggle.
- **Consecuencias:** es el estándar de referencia y permite comparar resultados; tiene desbalance de clases
  ("disgust" tiene muy pocas imágenes) y etiquetas ruidosas (la precisión humana ronda el 65 %).

## ADR-002: Python 3.11 + TensorFlow 2.21.0 en un entorno conda (18 nov 2026)
- **Contexto:** el sistema tiene Python 3.15, que TensorFlow no soporta. TF 2.21 soporta Python 3.10 a 3.13.
- **Decisión:** entorno conda `emotion-ai` con Python 3.11; librerías instaladas con pip; registrado como kernel de Jupyter.
- **Consecuencias:** entorno aislado y reproducible con `requirements.txt`. En Windows nativo TF no usa GPU,
  por eso el entrenamiento se hace en Colab.

## ADR-003: Entrenamiento en Google Colab (18 nov 2026)
- **Contexto:** el PC tiene GPU AMD integrada, sin CUDA; entrenar en CPU tardaría horas.
- **Decisión:** entrenar en Colab con GPU gratuita; inferencia (predicción) en local con CPU.
- **Consecuencias:** hay que subir el dataset a Colab y descargar el modelo `.keras` resultante.

## ADR-004: Detección de rostros con Haar Cascade (18 nov 2026)
- **Contexto:** se necesita detectar rostros rápido en CPU.
- **Decisión:** Haar Cascade de OpenCV (Viola-Jones); alternativa: detector DNN de OpenCV.
- **Consecuencias:** muy rápido y viene incluido en OpenCV; menos preciso con rostros girados o poca luz.

## ADR-005: Interfaz con Gradio y asistente con Google Gemini (18 nov 2026)
- **Contexto:** la interfaz se lanza desde Jupyter y debe tener video, panel de emociones y chat.
- **Decisión:** Gradio en lugar de Flask; chatbot con la API de Gemini (plan gratuito) que solo recibe etiquetas y porcentajes.
- **Consecuencias:** menos código y se ve dentro de Jupyter; depende de conexión a internet para el chat.

## ADR-006: Limpieza de duplicados para evitar fuga de datos (18 nov 2026)
- **Contexto:** el EDA encontró 531 imágenes de test idénticas a imágenes de train (hash MD5),
  1.236 duplicados dentro de train y 57 imágenes idénticas con etiquetas distintas.
- **Decisión:** limpiar solo train (quitar las imágenes que están en test, los duplicados exactos y las de
  etiquetas contradictorias). El conjunto de test no se modifica.
- **Consecuencias:** la accuracy en test es honesta (sin fuga) y sigue siendo comparable con otros trabajos
  que usan el test original. Train pierde menos del 5 % de sus imágenes.
