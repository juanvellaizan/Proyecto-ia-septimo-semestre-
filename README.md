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

## 👨‍💻 Integrantes

### Juan Manuel Vellaizan

Estudiante de Economía  
Universidad Externado de Colombia

### María Paula Orozco

Estudiante de Economía  
Universidad Externado de Colombia

### Valery Nayuni Ccaulla

Estudiante de Economía  
Universidad Externado de Colombia

**Universidad Externado de Colombia**  
**Facultad de Economía**  
**Curso: Inteligencia Artificial 1**  
**Fecha: 18 de agosto de 2026**
