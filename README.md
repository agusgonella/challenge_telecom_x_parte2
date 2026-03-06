# 📊Challenge Telecom X: Análisis de evasión de clientes - Parte 2

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-150458.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Data_Visualization-orange.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)

## Este proyecto forma parte del programa de formación Oracle Next Education (ONE) en colaboración con Alura Latam.

## 📌 Propósito del Proyecto
El objetivo principal de este análisis es predecir el **Churn (cancelación de servicio)** de los clientes de la empresa de telecomunicaciones Telecom X. A través de la exploración de datos históricos y la implementación de algoritmos de Machine Learning, este proyecto busca identificar los factores de riesgo tempranos y los perfiles de clientes más propensos a abandonar la compañía, permitiendo así diseñar estrategias de retención proactivas.

---

## 📂 Estructura del Proyecto
El repositorio está organizado de la siguiente manera para facilitar su reproducibilidad:

* `TelecomX_Parte_2.ipynb`: Cuaderno principal (Jupyter Notebook) que contiene todo el código fuente, desde la limpieza de datos hasta la evaluación final de los modelos predictivos.
* `TelecomX_Data.json`: Dataset original, el que se usó en la Parte 1 del Challenge.
* `datos_tratados.csv`: Dataset final limpio y preprocesado resultante de la Parte 1, listo para ser consumido por los algoritmos.
* `README.md`: Este archivo, con la documentación central del proyecto.

---

## ⚙️ Proceso de Preparación de los Datos
Para garantizar que los algoritmos de Machine Learning pudieran interpretar correctamente la información, se implementó un pipeline de preprocesamiento robusto:

1. **Limpieza Inicial:** Se eliminaron columnas irrelevantes para la predicción que actuaban como ruido (ej. `customerID` y `Unnamed: 0`).
2. **Clasificación de Variables:** El dataset se dividió lógicamente en columnas numéricas (ej. `tenure`, `Charges.Monthly`, `Charges.Total`) y columnas categóricas (ej. `Contract`, `InternetService`).
3. **Transformación y Codificación:**
   * **Codificación (Encoding):** Se aplicó `OneHotEncoder` a las variables categóricas para transformar textos en formato binario (0 y 1) sin asumir un orden jerárquico.
   * **Normalización (Scaling):** Se utilizó `StandardScaler` para las variables numéricas, comprimiendo sus valores a una escala estándar para evitar que atributos con magnitudes altas (como el Gasto Total) sesgaran a los modelos basados en distancia.
4. **Separación de Datos:** Se dividió el set utilizando `train_test_split` (70% para entrenamiento, 30% para prueba). 

---

## 📊 Exploratorio de Datos (EDA) e Insights Clave
El análisis visual previo al modelado reveló patrones de comportamiento críticos en la base de clientes:

* **La Zona de Peligro (Tenure):** Los diagramas de caja (Boxplots) mostraron que el 50% central de las cancelaciones ocurre entre los meses 10 y 30. Existe un alto riesgo de abandono en la fase temprana del ciclo de vida del cliente.
  
  <img width="517" height="423" alt="image" src="https://github.com/user-attachments/assets/eaa5f9c0-55a6-4fae-87ce-aa3d9afcfd4a" />

* **El Perfil del Desertor:** Los clientes con tecnología de **Fibra Óptica** y aquellos que poseen **contratos mes a mes** concentran la mayor tasa de fuga, ya que carecen de barreras de salida o penalidades.
  
  <img width="447" height="274" alt="image" src="https://github.com/user-attachments/assets/874feae8-1d03-47e7-9f45-a303464a30b7" />

---

## 🧠 Modelización Predictiva: Decisiones y Justificaciones
Se evaluaron múltiples algoritmos, tomando decisiones arquitectónicas basadas en la naturaleza matemática de cada uno:

* **KNN:** Se incluyó la etapa de normalización para que el modelo pudiera funcionar correctamente. Sin esto, variables como los cargos totales habrían dominado otras variables.
  
* **Árbol de Decisión:** Se entrenó sin necesidad de normalizar los datos numéricos, ya que los métodos basados en reglas o particiones de nodos son inmunes a las diferencias de magnitud.

**Modelo Ganador:** El **Árbol de Decisión** demostró el mejor desempeño general. Superó los graves problemas de sobreajuste (overfitting) que presentó el algoritmo KNN y logró la métrica de **Recall** más alta (~59%), convirtiéndolo en la herramienta más eficaz para detectar proactivamente a los clientes a punto de cancelar.

---

## 🚀 Instrucciones de Ejecución

Para reproducir este análisis en tu entorno local:

1. Clona este repositorio a través de Git:
   `git clone <url-del-repositorio>`

2. Abre el proyecto en tu editor de preferencia (recomendado: Visual Studio Code con la extensión de Jupyter instalada).

3. Asegúrate de tener instalado Python y las bibliotecas requeridas para el análisis de datos. Puedes instalarlas ejecutando:
    `pip install pandas scikit-learn matplotlib seaborn`
4. Abre el archivo TelecomX_Parte_2.ipynb, verifica que la ruta de carga de datos_tratados.csv sea correcta relativa a tu directorio, y ejecuta las celdas de forma secuencial.

## Autora
- 👩‍💻 Desarrollado por Agustina Gonella.
