# Proyecto-ia-septimo-semestre
# 📊 Primer Avance Proyecto

## Brechas de Desempeño en las Pruebas Saber 11 año 2024 entre Zonas Rurales y Urbanas de Colombia: Identificación de Factores Explicativos mediante Aprendizaje Automático

## 🎯 1. Objetivo

El Objetivo general se basa en desarrollar un modelo de aprendizaje automático que permita identificar y cuantificar las variables que explican las diferencias de rendimiento académico entre estudiantes de zonas rurales y urbanas que presentaron las pruebas Saber 11 en el año 2024, con el propósito de generar una evidencia relevante para la contribución del diseño de políticas educativas orientadas en reducir la brecha entre la zonas rural-urbana.

## 🔎 2. Descripción

El Icfes evalúa anualmente a los estudiantes de educación media colombianos a través de las pruebas Saber 11, que reportan resultados en Lectura Crítica, Matemáticas, Ciencias Naturales, Sociales y Ciudadanas e Inglés, además de un puntaje global. El informe nacional obtenga resultados del año 2024 desagrega esta información por zona (rural/urbana), lo que permite analizar de manera competitiva el desempeño en ambos contextos.

Las diferencias de desempeño entre zonas rurales y urbanas suelen atribuirse de forma general a la ruralidad, sin determinar con exactitud la relación con factores naturales del establecimiento (oficial/no oficial), jornada, nivel educativo de los padres, estrato socioeconómico o acceso a conectividad explican en mayor precisión dicha brecha. Este proyecto busca ir más allá de la comparación descriptiva de promedios, se construirá un modelo de aprendizaje automático que, a partir de las variables de contexto disponibles en las bases de microdatos del Icfes, haga posible identificar y pronosticar el desempeño de los estudiantes, y cuantificar la importancia relativa de cada variable en la brecha observada entre zonas.

De esta manera, el proyecto no solo documentará cuál grupo presenta un mejor desempeño, sino que aportará evidencia sobre los mecanismos que permiten entenderla, un elemento clave para priorizar recursos y estrategias de intervención en las instituciones educativas rurales con mayor rezago.

## ⚠️ 3. Desafíos

- **Heterogeneidad territorial:** las condiciones de la ruralidad varían sustancialmente entre departamentos (conectividad, oferta docente, infraestructura), lo que puede limitar la capacidad de generalización de un único modelo nacional.
- **Variables de contexto incompletas o con no respuesta:** los formularios socioeconómicos que acompañan la prueba presentan datos faltantes, particularmente en hogares rurales.
- **Correlación entre variables predictoras:** estrato, ruralidad y naturaleza del colegio están correlacionados entre sí, lo que exige un análisis cuidadoso de multicolinealidad e importancia de variables para no confundir causalidad con asociación.
- **Volumen de datos:** las bases de microdatos de Saber 11 superan el medio millón de registros por período, lo que exige un procesamiento eficiente.

## 💡 4. Entrega de Valor

El proyecto busca ofrecer al Ministerio de Educación Nacional, al Icfes y a las secretarías de educación departamentales un modelo que permita identificar qué factores están más relacionados con las diferencias de desempeño entre las zonas rurales y urbanas, más allá de la ubicación geográfica. Esta información podría ayudar a orientar mejor programas como el acceso a conectividad, la formación docente o la implementación de la jornada única hacia las instituciones rurales que presenten mayores dificultades. Además, los resultados podrían servir como punto de referencia para hacer seguimiento a la evolución de esta brecha en futuras aplicaciones de las pruebas.

## 👥 5. Stakeholders

**Decisores:** Ministerio de Educación Nacional, Icfes, secretarías de educación departamentales y municipales.

**Afectados / beneficiarios:** estudiantes y familias de zonas rurales, rectores y docentes de instituciones educativas rurales, e investigadores en política educativa.

## 🤖 6. Técnicas que se Utilizarán

El proyecto se desarrollará inicialmente como un problema de aprendizaje supervisado. Primero se realizará un análisis exploratorio de los datos (EDA) y se compararán los resultados entre las zonas rurales y urbanas en las cinco áreas evaluadas y en el puntaje global. Luego, se utilizarán modelos de regresión, como (Regresión Lineal y Random Forest Regressor), para estimar el puntaje global a partir de diferentes características del contexto educativo. También se aplicarán modelos de clasificación, como Regresión Logística y XGBoost Classifier, para identificar la probabilidad de obtener un bajo desempeño. Finalmente, se evaluarán los modelos mediante validación cruzada y métricas como R² y RMSE para regresión, y precisión, recall y F1-score para clasificación. Además, se analizará la importancia de las variables para identificar cuáles factores están más relacionados con las diferencias de desempeño entre estudiantes de zonas rurales y urbanas.

## 📚 7. Fuentes de Datos

- **Icfes — Informe Nacional de Resultados Saber 11 (2024):** resultados agregados por zona, entidad territorial y dependencia del colegio.
- **Icfes — Bases de microdatos de resultados Saber 11 (portal de datos abiertos del Icfes):** registros individuales con puntajes por área y variables de contexto socioeconómico y familiar.
- **DANE — Datos Abiertos:** indicadores municipales de pobreza y cobertura de servicios, para caracterizar el contexto territorial de cada institución educativa.

## 📊 8. Variables

### Variable objetivo (target)

**Puntaje global Saber 11** (para el modelo de regresión) y **categoría de desempeño bajo/no bajo según percentil** (para el modelo de clasificación).

### Variables predictoras (features)

- Puntajes en Lectura Crítica, Matemáticas, Ciencias Naturales, Sociales y Ciudadanas e Inglés.
- Zona del colegio (rural/urbana).
- Naturaleza del establecimiento (oficial/no oficial) y jornada.
- Nivel educativo del padre y de la madre.
- Estrato socioeconómico y nivel del Sisbén del hogar.
- Acceso a internet y computador en el hogar.
- Número de personas en el hogar.
- Departamento y municipio de ubicación del colegio.

## 🔄 9. Ajustes al Planteamiento Original

Durante el desarrollo del proyecto se realizaron ajustes al planteamiento inicial debido a la disponibilidad de los microdatos y a las características de las fuentes de información utilizadas.

| Primera entrega | Ajuste | Justificación |
|---|---|---|
| Período 2024 | *2020-2* (calendario A) | Es la base de microdatos disponible para realizar el análisis. El objetivo general y el enfoque del proyecto se mantienen. |
| Nivel del Sisbén | *Se elimina* | Esta variable no se encuentra disponible en los microdatos utilizados. |
| Municipio como variable | *Se sustituye por el IPM del DANE* | El municipio presenta un número elevado de categorías. El IPM permite incorporar información sobre las condiciones de pobreza multidimensional del territorio de una manera más agregada. |
| Informe Nacional 2024 | *Cifras oficiales de 2020 (MEN)* | Se utilizan cifras correspondientes al período efectivamente analizado, permitiendo mantener consistencia entre los microdatos y la información oficial. |
| — | *Exclusión de jornadas sabatina y nocturna* | Estas jornadas presentan características diferentes a las jornadas regulares y corresponden principalmente a población de educación de adultos. Por esta razón, se excluyen del análisis principal y se revisan durante el análisis exploratorio. |

## 📂 10. Datos

Debido al tamaño de las bases originales, los archivos de datos no se versionan directamente en GitHub. Las bases de datos utilizadas se encuentran disponibles en la carpeta de Google Drive asociada al proyecto.

| Archivo | Fuente |
|---|---|
| Saber_11°_2020-2_20260928.xlsx | Icfes — DataIcfes, microdatos Saber 11 2020-2 |
| anex-PMultidimensional-Departamental-2025.xlsx | DANE — Pobreza multidimensional departamental |

### 📁 Carpeta de datos

Los archivos utilizados en el proyecto pueden consultarse y descargarse desde la siguiente carpeta:

👉 [Acceder a la carpeta de datos en Google Drive](https://drive.google.com/drive/u/0/folders/1tfxHj5XB1XwfKu-13S0sf4KXE44_-jhd)

## 🛠️ 11. Procesamiento de los Datos

El procesamiento del proyecto se organiza inicialmente en dos etapas principales:

### 11.1. Carga, Limpieza e Integración

En esta etapa se realiza la preparación de las bases de datos necesarias para el análisis. Las principales actividades incluyen:

- Carga de los microdatos de Saber 11 2020-2.
- Limpieza y organización de las variables.
- Selección de la población de interés.
- Tratamiento de valores faltantes.
- Homologación de variables necesarias para el análisis.
- Integración de la información de Saber 11 con los datos de pobreza multidimensional del DANE.
- Construcción de la base final utilizada en el análisis exploratorio.

### 11.2. Análisis Exploratorio de Datos (EDA)

En esta etapa se realiza un análisis descriptivo de la información para caracterizar las diferencias entre estudiantes de zonas rurales y urbanas.

El análisis incluye:

- Descripción general de la base de datos.
- Distribución de las principales variables.
- Comparación del desempeño entre zonas rurales y urbanas.
- Análisis de los resultados de las áreas evaluadas en Saber 11.
- Comparación del puntaje global entre zonas.
- Análisis de variables socioeconómicas y educativas.
- Exploración de la relación entre las características del establecimiento, el contexto socioeconómico y la zona.
- Identificación de valores faltantes y posibles inconsistencias.
- Análisis de la distribución territorial de las observaciones.
- Incorporación del Índice de Pobreza Multidimensional (IPM) como medida de contexto territorial.

## 👥 12. Población de Análisis

La población de análisis está conformada por estudiantes que presentaron las pruebas Saber 11 durante el período *2020-2, calendario A*, y que cuentan con resultados publicados.

Para el análisis principal se consideran las *jornadas regulares*, excluyendo las jornadas sabatina y nocturna debido a sus características particulares. Estas jornadas son revisadas de manera independiente durante el análisis exploratorio.

## 🧹 13. Tratamiento de Valores Faltantes

Los valores faltantes de las variables categóricas se conservan como una categoría explícita *«No reporta»*, evitando reemplazarlos automáticamente por la categoría más frecuente.

La categoría *«Sin estrato»* se mantiene como una categoría independiente cuando aparece en la información socioeconómica.

Para las variables numéricas se realiza el tratamiento correspondiente de los valores faltantes de acuerdo con las características de cada variable, procurando conservar la mayor cantidad posible de información disponible para el análisis exploratorio.

## 👨‍💻 Integrantes

### Juan Manuel Vellaizan

Estudiante de Economía  
Universidad Externado de Colombia

### María Paula Orozco

Estudiante de Economía  
Universidad Externado de Colombia

### Nicolas Orduña

Estudiante de Economía  
Universidad Externado de Colombia

### Valery Nayuni Ccaulla

Estudiante de Economía  
Universidad Externado de Colombia

**Universidad Externado de Colombia**  
**Facultad de Economía**  
**Curso: Inteligencia Artificial 1**  
**Fecha: 18 de agosto de 2026**
