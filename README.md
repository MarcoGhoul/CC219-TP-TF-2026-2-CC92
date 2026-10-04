# Sistema de recomendación de películas con MovieLens

**Trabajo parcial — Hito 1** del curso **CC219 – Aplicaciones de Data Science**, Universidad Peruana de Ciencias Aplicadas (UPC), ciclo **2026-02**.

## Descripción y objetivo

En este primer hito definiremos el caso de uso de un sistema de recomendación de películas con **MovieLens**. Cargaremos y prepararemos sus datos, analizaremos las etiquetas de texto libre, los géneros y las valoraciones, y redactaremos la propuesta de modelización.

El objetivo del parcial es comprender los datos y establecer cómo se utilizarán técnicas de procesamiento de lenguaje natural (NLP) para recomendar películas acordes con los intereses del usuario. **Este hito no incluye entrenar modelos ni implementar el recomendador.**

## Datos

Utilizaremos **MovieLens Latest Small**, publicado por GroupLens, de la Universidad de Minnesota. La ficha corresponde a la edición generada el 26 de septiembre de 2018.

| Campo | Valor |
| --- | --- |
| Fuente | GroupLens — Universidad de Minnesota. |
| Dataset | MovieLens Latest Small (`ml-latest-small`). |
| Archivos originales | `movies.csv`, `ratings.csv`, `tags.csv` y `links.csv`. |
| Tamaño | 100 836 valoraciones, 9 742 películas, 610 usuarios y 3 683 asignaciones de etiquetas. |
| Período de las interacciones | Del 29 de marzo de 1996 al 24 de septiembre de 2018. |
| Formato | Archivos CSV codificados en UTF-8. |
| Información de películas | Identificador, título y géneros. |
| Información de usuarios | Identificadores anónimos y sus interacciones con películas. |
| Valoraciones | Calificaciones de 0,5 a 5 estrellas, con incrementos de 0,5. |
| Contenido textual | Etiquetas libres de usuarios: palabras o frases breves que describen películas. |
| Relación entre archivos | `movieId` identifica películas; `userId` relaciona valoraciones y etiquetas por usuario. |
| Descarga | [MovieLens Latest Datasets](https://grouplens.org/datasets/movielens/latest/). |

El componente no estructurado del proyecto será el texto de `tags.csv`. MovieLens Latest Small no contiene sinopsis. Durante el EDA identificaremos qué películas tienen etiquetas y delimitaremos el catálogo del recomendador textual a las que dispongan de texto utilizable; reportaremos su cobertura respecto del catálogo completo.

## Herramientas del parcial y técnicas de la propuesta

| Herramienta o técnica | Qué haremos |
| --- | --- |
| Python | Programar la carga, limpieza y análisis exploratorio de los datos. |
| pandas y NumPy | Cargar, relacionar y preparar los archivos de MovieLens. |
| Matplotlib y seaborn | Graficar géneros, valoraciones, actividad de usuarios y disponibilidad de etiquetas. |
| TF-IDF con scikit-learn | Proponer la representación numérica de las etiquetas agrupadas por película. |
| Similitud coseno | Describir cómo se calculará la afinidad entre películas y perfiles de preferencias. |
| Regresión logística multietiqueta | Proponer la clasificación de géneros a partir de etiquetas textuales. |
| Jupyter Notebook | Documentar la carga, la preparación y el EDA. |
| Git y GitHub | Organizar el código y registrar los aportes del equipo. |

## Contenido del informe del trabajo parcial

| Punto obligatorio | Qué desarrollaremos |
| --- | --- |
| **1. Descripción del caso de uso** | Explicaremos el problema de descubrir películas acordes con los gustos del usuario, fundamentaremos su relevancia con fuentes y plantearemos las preguntas de clasificación y predicción. |
| **2. Descripción del dataset** | Documentaremos el origen de MovieLens, sus archivos, variables, tamaño, relaciones, condiciones de uso y contenido textual. |
| **3. Análisis exploratorio de datos (EDA)** | Cargaremos los archivos, inspeccionaremos faltantes y duplicados, relacionaremos películas con interacciones, normalizaremos las etiquetas y elaboraremos gráficos con su interpretación. |
| **4. Propuesta de modelización** | Describiremos el uso de TF-IDF, perfiles de preferencias y similitud coseno para recomendar películas, y de regresión logística para clasificar géneros. Incluiremos el diseño de la separación de datos y las métricas previstas, sin ejecutar el entrenamiento. |

### Preguntas del proyecto

1. **Clasificación:** ¿Qué géneros podemos identificar en una película a partir de las etiquetas textuales asignadas por los usuarios? Para esta tarea, los géneros serán las etiquetas objetivo, no las variables de entrada.
2. **Predicción de relevancia:** ¿Qué películas tendrán mayor afinidad con un usuario a partir de sus valoraciones anteriores y del contenido textual de las películas que prefiere?

La propuesta explicará cómo construir perfiles a partir de valoraciones favorables y ordenar películas no vistas según su afinidad. Definiremos el criterio de valoración favorable y cómo evitar el uso de información futura. También describiremos F1 para clasificación y Precision@K y Recall@K para recomendaciones, sin presentar resultados de modelos en este hito.

## Integrantes y distribución del trabajo

| Sección del informe | Responsable principal | Entregables |
| --- | --- | --- |
| **1. Descripción del caso de uso** | **Piero Marcos Contreras Albornoz** | Planteamiento del problema, justificación de su relevancia con fuentes citadas, y redacción de las 2 preguntas de clasificación/predicción. |
| **2. Descripción del dataset** | **Piero Marcos Contreras Albornoz** | Ficha y diccionario de datos de MovieLens (origen, archivos, variables, tamaño, período, relaciones entre tablas y condiciones de uso). |
| **3. Análisis Exploratorio de Datos (EDA) y Preparación de Datos** | **Enzo Daniel Medina Oropeza - Frank Alexander Flores Peralta** | Carga e inspección de `movies.csv`, `ratings.csv` y `tags.csv`; tratamiento de faltantes/duplicados; normalización de las etiquetas de texto; gráficos (géneros, valoraciones, cobertura de etiquetas) con su interpretación. |
| **4. Propuesta de Modelización** | **Piero Marcos Contreras Albornoz** (coordina), con aportes de Frank y Enzo | Descripción de TF-IDF + similitud coseno para recomendar películas y de regresión logística multietiqueta para clasificar géneros; diseño de la separación de datos y métricas previstas (F1, Precision@K, Recall@K), sin entrenar modelos todavía. |

Los tres integrantes revisaremos los resultados del EDA, las preguntas y la propuesta metodológica. Cada integrante documentará su aporte y participará en la revisión del informe y la exposición.

## Cómo clonar el repositorio

Para trabajar en el proyecto, cada integrante debe **clonar** el repositorio (no crear uno nuevo con `git init`) para compartir el mismo historial de cambios:

```bash
git clone https://github.com/TU-USUARIO/CC219-TP-TF-2026-2-CC92.git
cd CC219-TP-TF-2026-2-CC92
```

Luego instala las dependencias del proyecto:

```bash
pip install -r requirements.txt
```

Antes de empezar a trabajar cada día, trae los últimos cambios del equipo:

```bash
git pull origin main
```

Y al terminar tus cambios, súbelos con:

```bash
git add .
git commit -m "Describe brevemente tu cambio"
git push origin main
```

## Estructura del proyecto

```text
├── data/
│   ├── raw/                         # Dataset original y condiciones de uso
│   └── processed/                   # Dataset limpio y preparado
├── code/
│   ├── 01_carga_inspeccion.ipynb    # Carga de movies.csv, ratings.csv y tags.csv; inspección inicial
│   ├── 02_eda_visualizacion.ipynb   # Entendimiento de los datos: distribución de géneros, valoraciones, cobertura de etiquetas 
│   └── 03_preprocesamiento.ipynb    #Preparación de los datos: limpieza, normalización de etiquetas
├── requirements.txt                 # Dependencias utilizadas
├── .gitignore                       # Exclusiones de Git
└── README.md                        # Descripción del parcial
```

La estructura corresponde únicamente al **Hito 1** y conserva las carpetas obligatorias `data` y `code`. La propuesta de modelización y el diccionario de datos se documentarán en el informe. El nombre del repositorio se mantiene según el enunciado, aunque esta entrega sea solo el parcial.

## Licencia y referencias

La licencia del código será acordada por el equipo. MovieLens conserva las condiciones de uso y atribución indicadas por GroupLens en su documentación original.

- UPC. *CC219-TP-TF-Enunciado-2026-02.docx*, ciclo 2026-02.
- GroupLens. [MovieLens Latest Small: descripción y condiciones de uso](https://files.grouplens.org/datasets/movielens/ml-latest-small-README.html).
- Harper, F. M., y Konstan, J. A. (2015). *The MovieLens Datasets: History and Context*. ACM Transactions on Interactive Intelligent Systems, 5(4), artículo 19. https://doi.org/10.1145/2827872
