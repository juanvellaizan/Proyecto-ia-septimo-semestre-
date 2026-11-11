# **📊Brechas de desempeño en las pruebas Saber 11 (2020-2) entre zonas rurales y urbanas de Colombia: identificación de factores explicativos mediante aprendizaje automático**

**Universidad Externado de Colombia**  
Facultad de Economía · Inteligencia Artificial con Aplicaciones en Economía I  
Docente: Lina María Castro

## **Autores**

- Juan Manuel Vellaizan
- María Paula Orozco
- Valery Nayuni Ccaulla
- Nicolás Orduña

---

## 🌍 **Descripción del proyecto y relevancia económica**

En Colombia, las diferencias entre los resultados de los estudiantes de colegios rurales y urbanos siguen siendo un reto para la política educativa. En las pruebas Saber 11 del período 2020-2, los estudiantes de zonas rurales obtuvieron, en promedio, 28,3 puntos menos que los estudiantes de zonas urbanas en el puntaje global. Sin embargo, observar esa diferencia no es suficiente para entender el problema. También es necesario revisar qué condiciones del hogar, del colegio y del territorio están relacionadas con ella. Esta pregunta fue especialmente importante para el período estudiado, porque la aplicación se realizó después de varios meses de educación remota durante la pandemia.

Para estudiar esta situación utilizamos microdatos del Icfes y los integramos con información de pobreza multidimensional del DANE. Aplicamos modelos de regresión y clasificación para analizar y predecir el desempeño, además de herramientas de interpretación como Oaxaca-Blinder y Shapley. También utilizamos K-means para identificar distintos perfiles de sedes rurales oficiales. Los resultados muestran que la brecha está relacionada principalmente con diferencias en las condiciones de los estudiantes y sus instituciones, más que con la ruralidad por sí sola. Entre los factores que aparecen con mayor importancia están el contexto territorial, el nivel socioeconómico del colegio y las condiciones de conectividad. Estos hallazgos permiten discutir cómo orientar mejor los recursos y las intervenciones educativas.

**Hallazgo principal.** Al comparar estudiantes con características observadas similares, el modelo estima una diferencia favorable a los estudiantes rurales de 3,9 puntos. La descomposición indica que las diferencias de composición explican el 114 % de la brecha bruta. Este resultado no significa que la ruralidad no importe; muestra que la diferencia promedio está vinculada con las condiciones que se concentran de manera desigual entre ambos grupos. Por eso, el análisis debe leerse como evidencia de asociaciones y no como una demostración de causalidad.

---

## 📂 **Estructura del repositorio**

El repositorio está organizado para separar los datos originales, los archivos de análisis y los resultados que se generan durante el proyecto. De esta manera, es más sencillo seguir el proceso y encontrar cada producto.

```text
├── data/
│   ├── raw/          # Bases originales descargadas del Icfes y del DANE
│   ├── interim/      # Archivos intermedios que se generan durante la limpieza
│   └── processed/    # Base analítica limpia utilizada para estimar los modelos
│
├── notebooks/
│   ├── 01_Datos_y_Analisis_Exploratorio.ipynb
│   │                 # Carga, limpieza, integración de las bases y análisis exploratorio
│   └── 02_Modelos_e_Interpretacion.ipynb
│                     # Modelos, evaluación, interpretación y análisis de perfiles
│
├── docs/
│   └── Documento_Final_Brecha_Rural_Urbana_Saber11.docx
│                     # Documento final del proyecto
│
├── results/
│   ├── figuras/      # Gráficas generadas durante el análisis
│   └── tablas/       # Tablas de limpieza, resultados y evaluación de modelos
│
├── README.md         # Guía general del proyecto y de su ejecución
└── requirements.txt  # Librerías y versiones necesarias
```

Los notebooks se entregan ejecutados, por lo que es posible consultar sus tablas y gráficas sin volver a correr todo el proceso.

---

## ⚙️ **Instrucciones para reproducir el proyecto**

A continuación se explica cómo preparar el entorno y ejecutar el análisis desde otro computador. Para seguir estos pasos se necesita Python 3.13 y aproximadamente 3 GB de espacio libre. La primera lectura de los archivos puede tardar algunos minutos, especialmente por el tamaño de la base del Icfes.

### 1. Clonar el repositorio

Primero, descarga una copia del repositorio. Reemplaza el enlace y el nombre de la carpeta por los datos reales del repositorio en GitHub:

```bash
git clone [URL_DEL_REPOSITORIO]
cd [NOMBRE_DEL_REPOSITORIO]
```

### 2. Crear y activar un entorno virtual

Esto permite instalar las librerías del proyecto sin modificar las de otros trabajos de Python.

```bash
python -m venv .venv
```

En Windows:

```bash
.venv\Scripts\activate
```

En Mac o Linux:

```bash
source .venv/bin/activate
```

### 3. Instalar las dependencias

Con el entorno virtual activado, instala las librerías incluidas en `requirements.txt`:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### 4. Descargar y ubicar los datos

Descarga las bases desde las fuentes oficiales indicadas en la sección Datos y fuentes. Después, guárdalas en `data/raw/` con los siguientes nombres:

```text
data/raw/Saber_11°_2020-2_20260928.xlsx
data/raw/anex-PMultidimensional-Departamental-2025.xlsx
```

Es importante conservar los nombres de los archivos y no modificar las bases originales, porque los notebooks esperan encontrarlas en esas rutas.

### 5. Ejecutar los notebooks en orden

Abre el repositorio en Visual Studio Code o Jupyter, selecciona como kernel el entorno `.venv` y ejecuta cada notebook completo (*Run All*). El orden es importante, ya que el segundo notebook utiliza la base que genera el primero.

| Orden | Notebook | Proceso | Tiempo aproximado |
|---|---|---|---|
| 1 | `notebooks/01_Datos_y_Analisis_Exploratorio.ipynb` | Carga y limpia los datos, integra la información del DANE, construye las variables y genera la base analítica y las primeras gráficas. | 10–20 minutos la primera vez; después, cerca de 1 minuto. |
| 2 | `notebooks/02_Modelos_e_Interpretacion.ipynb` | Entrena y evalúa los modelos, analiza la brecha, interpreta los factores y construye los perfiles de sedes rurales. | 30–45 minutos. |

El segundo notebook necesita que el primero haya terminado correctamente. Para facilitar la reproducción, el proyecto utiliza una semilla fija (`SEMILLA = 42`) y una partición determinística entre entrenamiento y prueba.

---

## 📊**Datos y fuentes**

El análisis combina información individual de los estudiantes que presentaron Saber 11 en el período 2020-2 con indicadores territoriales de pobreza multidimensional. La unidad principal de observación es el estudiante.

| Base | Fuente | Dimensiones reportadas | Unidad de observación | Archivo |
|---|---|---:|---|---|
| Resultados Saber 11, período 2020-2 | Icfes, [DataIcfes](https://www.icfes.gov.co/data-icfes) | 504.872 filas × 81 columnas | Estudiante que presentó la prueba | `Saber_11°_2020-2_20260928.xlsx` |
| Pobreza multidimensional departamental 2018–2025 | DANE, [Pobreza multidimensional](https://www.dane.gov.co/index.php/estadisticas-por-tema/pobreza-y-condiciones-de-vida/pobreza-multidimensional) | 33 departamentos × 2 zonas | Departamento y zona | `anex-PMultidimensional-Departamental-2025.xlsx` |
| Base analítica generada en el proyecto | Elaboración propia | 458.907 filas × 66 columnas | Estudiante después del proceso de limpieza e integración | `data/processed/base_analitica.csv.gz` |

**Integración de las fuentes.** A cada estudiante se le asignó el indicador de pobreza multidimensional correspondiente al año 2020, al departamento y a la zona de ubicación de su colegio. La unión se realizó mediante el código DIVIPOLA. Para San Andrés, donde no se encuentra publicado un valor rural del IPM, se utilizó el valor total del departamento.

**Depuración de los registros.** Durante la limpieza se retiraron los resultados no publicados, los registros de estudiantes privados de la libertad, los puntajes globales iguales a cero y las jornadas sabatina y nocturna, debido a que estas últimas corresponden principalmente a educación de adultos. La base analítica resultante contiene 458.907 registros. Para la estimación de los modelos se trabajó con 449.695 estudiantes que respondieron el cuestionario socioeconómico.

**Variables utilizadas.** La variable objetivo principal es el puntaje global de Saber 11, en una escala de 0 a 500. Para clasificación se definió bajo desempeño como un puntaje inferior al percentil 25 calculado en la muestra de entrenamiento (216 puntos). Los predictores reúnen características del colegio, el hogar, el estudiante y el territorio. Se incluyen, entre otras, la zona rural, la naturaleza y jornada del establecimiento, el nivel socioeconómico del colegio, la educación y ocupación de los padres, los bienes del hogar, la conectividad, la alimentación, la edad, las horas de trabajo y el IPM territorial.

Se excluyeron los puntajes, percentiles y niveles de las áreas evaluadas porque forman parte del cálculo del puntaje global y utilizarlos como predictores produciría fuga de información. También se dejaron por fuera variables que resumen características ya incluidas en el modelo, para evitar duplicar información.

📁 **Carpeta de datos**

Los archivos utilizados en el proyecto pueden consultarse y descargarse desde la siguiente carpeta:

👉 [Acceder a la carpeta de datos en Google Drive](https://drive.google.com/drive/u/0/folders/1tfxHj5XB1XwfKu-13S0sf4KXE44_-jhd)

---

## **🧪 Metodología**

El proyecto combina herramientas predictivas y métodos de interpretación. La idea no es quedarse únicamente con el modelo que obtiene la mejor métrica, sino revisar qué información utiliza y qué puede aportar para comprender las diferencias entre estudiantes rurales y urbanos.

- **Análisis exploratorio:** comparación de los resultados entre zonas y revisión de la distribución de las variables.
- **Regresión:** regresión lineal, Ridge, Lasso, Random Forest y Gradient Boosting para estimar el puntaje global.
- **Clasificación:** regresión logística y Gradient Boosting para identificar estudiantes con bajo desempeño.
- **Segmentación:** K-means para construir perfiles de sedes rurales oficiales.
- **Interpretación:** descomposición Oaxaca-Blinder, Shapley por grupos de factores, importancia por permutación y dependencia parcial.

Para evaluar la capacidad de generalización, la partición de entrenamiento y prueba se hizo por sede educativa (80/20). También se utilizó validación cruzada agrupada, de manera que el desempeño se evaluara en sedes que los modelos no habían visto durante el entrenamiento. En regresión se reportan R² y RMSE; en clasificación se consideran ROC-AUC, PR-AUC, precisión, *recall* y F1, entre otras métricas.

**Alcance de la interpretación.** Los resultados muestran asociaciones condicionadas por las variables incluidas en el análisis. No deben interpretarse automáticamente como efectos causales. Por ejemplo, el escenario de ampliar la conectividad permite estimar cómo cambiarían las predicciones bajo determinadas condiciones del modelo, pero no reemplaza una evaluación causal de una política pública.

---

## **🏆 Resultados clave**

Los modelos se evaluaron en sedes educativas que no participaron en el entrenamiento. Esto permite tener una idea más exigente de su capacidad para predecir resultados en instituciones diferentes a las utilizadas para ajustarlos.

| Modelo (prueba, sedes no vistas) | Métrica principal |
|---|---|
| Solo zona (línea base) | R² = 0,046 |
| Regresión lineal / Ridge / Lasso | R² = 0,393 · RMSE = 37,9 |
| Random Forest | R² = 0,387 · RMSE = 38,1 |
| **Gradient Boosting (regresión)** | **R² = 0,434 · RMSE = 36,6** |
| Regresión logística | ROC-AUC = 0,803 · PR-AUC = 0,584 · F1 = 0,571 |
| **Gradient Boosting (clasificación)** | **ROC-AUC = 0,819 · PR-AUC = 0,616 · F1 = 0,590** |
| K-means (sedes rurales oficiales) | 5 perfiles · silueta = 0,16 |

A partir de los resultados, destacamos los siguientes puntos:

1. **La brecha promedio está relacionada con diferencias de composición.** En la comparación ajustada por las características observadas, los estudiantes rurales obtienen 3,9 puntos más que los urbanos (IC del 95 %: 2,4 a 5,4). La descomposición de Oaxaca-Blinder estima que las diferencias de composición explican el 114 % de la brecha bruta.
2. **El contexto territorial y las condiciones del colegio tienen un peso importante.** En la descomposición, el territorio representa el 36 % y el nivel socioeconómico del colegio el 25 % del aporte explicado. La conectividad representa el 17 %, mientras que la alimentación y la situación económica del hogar aportan el 8 %.
3. **Las variables adicionales mejoran la predicción.** Al incorporarlas, el R² del modelo Gradient Boosting pasa de 0,397 a 0,434. En clasificación, el PR-AUC aumenta de 0,590 a 0,616. Entre las variables que más aportan aparecen la lectura por gusto, la situación económica del hogar, la alimentación, el uso de internet y la ocupación de los padres.
4. **La conectividad aparece como una oportunidad de intervención.** Los escenarios analizados estiman que ampliar el acceso a internet y computador entre los estudiantes rurales podría cerrar entre el 16 % y el 23 % de la brecha, dependiendo del modelo utilizado. Esta cifra corresponde a un escenario predictivo y no a un efecto causal comprobado.
5. **Las sedes rurales no son todas iguales.** El análisis K-means identificó cinco perfiles de sedes rurales oficiales, con diferencias de hasta 54 puntos entre el perfil de mayor y el de menor desempeño. Esto muestra la importancia de diseñar estrategias que tengan en cuenta las condiciones particulares de cada institución.
6. **La focalización puede dejar por fuera a poblaciones con necesidades importantes.** En el perfil de sedes con mayores dificultades, solo el 29 % de los estudiantes aparece focalizado por Sisbén y el 88 % pertenece a un grupo étnico. Este resultado invita a revisar si los criterios actuales identifican adecuadamente a todos los estudiantes que requieren apoyo.
7. **Existen territorios donde el bajo desempeño rural merece especial atención.** Entre los departamentos con mayores tasas de bajo desempeño rural aparecen Vaupés, Guainía, Chocó, Amazonas y La Guajira. En el análisis municipal, Uribia, Manaure y Maicao presentan los mayores riesgos predichos.

En conjunto, los resultados sugieren que las políticas educativas no deberían concentrarse únicamente en la condición rural o urbana. También necesitan considerar las diferencias económicas, territoriales, institucionales y de acceso a recursos que enfrentan los estudiantes. La conectividad es una de las líneas de acción que merece atención, junto con la alimentación escolar y una focalización que no dependa exclusivamente de un indicador socioeconómico.


---

## **🔁 Cambios frente al planteamiento inicial**

Durante el desarrollo del proyecto fue necesario ajustar algunos aspectos de la propuesta inicial a las características de los datos disponibles y a los resultados del procesamiento.

| Planteamiento inicial | Decisión en la versión final | Motivo |
|---|---|---|
| Analizar el período 2024 | Trabajar con 2020-2 | Es el período de la base de microdatos utilizada y permite estudiar el contexto particular de la pandemia. |
| Usar los puntajes por área como predictores | Excluirlos | Los puntajes por área componen el puntaje global y generarían fuga de información. |
| Incluir el nivel del Sisbén | Usar el indicador de focalización disponible | El puntaje del Sisbén no está en los microdatos; se utiliza la información disponible sobre focalización. |
| Incluir el municipio como predictor | Incorporar el IPM del DANE por departamento y zona | El municipio genera muchas categorías; el IPM ofrece una medida territorial más manejable e interpretable. |
| Utilizar XGBoost | Utilizar HistGradientBoosting de scikit-learn | XGBoost no se pudo instalar en el entorno de ejecución. |
| Limitar el análisis a regresión y clasificación | Añadir Ridge, Lasso, Gradient Boosting, Oaxaca-Blinder, Shapley y K-means | Estas herramientas permiten comparar modelos, interpretar los factores y reconocer perfiles distintos de sedes rurales. |

---

## **📌 Consideraciones finales**
En conclusión, este proyecto nos permitió llegar a una idea que al principio no era tan evidente. No necesariamente son los colegios rurales los que tienen un menor desempeño, sino que sus estudiantes muchas veces deben enfrentarse a condiciones más difíciles. De hecho, cuando se comparan estudiantes con características similares, los resultados muestran una diferencia a favor de los rurales de 3,9 puntos. Esto cambia la forma de entender la brecha y nos lleva a pensar que el esfuerzo no debería centrarse únicamente en mejorar los resultados académicos, sino en revisar las condiciones que hay detrás de ellos. Consideramos que ahí está el verdadero reto de la política educativa, lograr que el lugar donde nace o estudia un estudiante no termine determinando las oportunidades que puede alcanzar.
