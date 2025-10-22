# 🤖 Proyecto Interactivo de CNN para MNIST en Colab

Este proyecto implementa una **Red Neuronal Convolucional (CNN)** en TensorFlow/Keras para clasificar dígitos escritos a mano del dataset MNIST.

El notebook está diseñado para ejecutarse en **Google Colab** y sigue las fases de la metodología **CRISP-DM**. Su característica principal es la **persistencia y el aprendizaje interactivo**: el modelo se guarda en tu Google Drive y puede ser re-entrenado con correcciones proporcionadas por el usuario.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/[TU_USUARIO]/[TU_REPOSITORIO]/blob/main/[NOMBRE_DEL_NOTEBOOK].ipynb)
*(¡Recuerda reemplazar el enlace de arriba con el de tu propio repositorio!)*

---

## 🚀 Características

* **Modelo CNN:** Una arquitectura de CNN simple pero efectiva construida 100% con `tf.keras`.
* **Persistencia en Google Drive:** El modelo entrenado se guarda (`.keras`) y se carga desde tu Google Drive. ¡No es necesario re-entrenar cada vez que abres el notebook!
* **Aprendizaje Interactivo (Feedback Loop):**
    * Prueba el modelo con ejemplos aleatorios del set de prueba.
    * Si el modelo se equivoca, puedes **corregirlo** ingresando la etiqueta correcta.
    * El modelo se re-entrena (fine-tuning) inmediatamente con esa corrección.
* **Base de Datos de Correcciones:** Todas las correcciones se guardan en un archivo (`.npz`) en tu Drive, permitiendo un re-entrenamiento masivo futuro.
* **Prueba con Imágenes Propias:** Incluye una función para que **subas tu propia imagen** de un dígito, la procese y la prediga.

---

## 🛠️ Cómo Empezar

Solo necesitas una cuenta de Google para usar Colab y Drive.

1.  **Abrir en Colab:** Haz clic en el botón "Open In Colab" de arriba.
2.  **Conectar Google Drive:** Ejecuta la primera celda de código. Te pedirá permisos para montar tu Google Drive. Esto es necesario para guardar el modelo.
3.  **Ejecutar el Notebook:** Puedes ejecutar todas las celdas (`Runtime > Run all`).

---

## 📋 Uso del Notebook

El script se ejecuta en varias fases automáticas:

1.  **Configuración:** Importa librerías y define las rutas en tu Google Drive (creará la carpeta `mnist_cnn_proyecto`).
2.  **Carga de Datos:** Descarga y pre-procesa el dataset MNIST (normalización y redimensión).
3.  **Carga o Entrenamiento del Modelo:**
    * **Si es la primera vez:** Creará, entrenará (aprox. 2-3 min) y guardará el modelo (`mnist_cnn_model.keras`) en tu Drive.
    * **Si ya existe:** Cargará el modelo guardado en menos de un segundo.
4.  **Carga de Feedback:** Revisa si existen correcciones previas (`feedback_data.npz`) y las carga.
5.  **Métricas:** Muestra la precisión actual del modelo.

### Flujo Interactivo

Al final del script, el programa te guiará por dos pruebas:

#### 1. Prueba Interactiva (Feedback Loop) 🧠

* Se te mostrará una imagen del dataset de prueba y la predicción del modelo.
* Te preguntará: `¿Es esta predicción correcta? (s/n):`
* Si respondes **'s' (sí)**: El programa continúa.
* Si respondes **'n' (no)**:
    * Te preguntará: `¿Cuál era el dígito correcto? (0-9):`
    * Al ingresar el dígito correcto, el modelo se **re-entrenará** con esa imagen, guardará la corrección y guardará el modelo mejorado en Google Drive.

#### 2. Prueba con Imagen Propia ✍️

* Se te pedirá que **subas tu propia imagen** (idealmente un `.png` con un dígito oscuro sobre fondo claro, o viceversa).
* El script procesará la imagen (la convertirá a $28 \times 28$, escala de grises, e invertirá los colores si es necesario) y te dará la predicción.

---

## 📁 Estructura de Archivos en Google Drive

El script creará la siguiente estructura en tu Google Drive:
