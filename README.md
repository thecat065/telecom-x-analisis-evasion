<h1 align="center">Telecom X - Análisis de Evasión de Clientes (Churn)</h1>

<p align="center">
  <img src="https://img.shields.io/badge/STATUS-COMPLETADO-brightgreen" alt="Estado del Proyecto: Completado">
  <img src="https://img.shields.io/badge/Python-3.9%2B-blue" alt="Python Version">
  <img src="https://img.shields.io/badge/Pandas-1.3%2B-orange" alt="Pandas Version">
  <img src="https://img.shields.io/badge/Matplotlib-3.4%2B-purple" alt="Matplotlib Version">
  <img src="https://img.shields.io/badge/Seaborn-0.11%2B-red" alt="Seaborn Version">
</p>

## 📖 Índice
* [Descripción del Proyecto](#descripción-del-proyecto)
* [Estado del Proyecto](#estado-del-proyecto)
* [Proceso Realizado (ETL y EDA)](#proceso-realizado-etl-y-eda)
* [Acceso al Proyecto y Ejecución](#acceso-al-proyecto-y-ejecución)
* [Tecnologías Utilizadas](#tecnologías-utilizadas)
* [Principales Hallazgos e Insights](#principales-hallazgos-e-insights)
* [Recomendaciones Estratégicas](#recomendaciones-estratégicas)
* [Persona Desarrolladora del Proyecto](#persona-desarrolladora-del-proyecto)
* [Agradecimientos](#agradecimientos)

## <a name="descripción-del-proyecto"></a> 📝 Descripción del Proyecto
Este proyecto fue desarrollado como parte del desafío "Churn de Clientes" de Telecom X. El objetivo principal es analizar un conjunto de datos de clientes para identificar los factores clave que contribuyen a la evasión (churn). A través de un proceso de Extracción, Transformación y Carga (ETL) y un Análisis Exploratorio de Datos (EDA), se busca extraer información valiosa que permita al equipo de Data Science de Telecom X avanzar en la creación de modelos predictivos y desarrollar estrategias para reducir la tasa de cancelaciones.

## <a name="estado-del-proyecto"></a> 📈 Estado del Proyecto
:white_check_mark: **Proyecto Completado** :white_check_mark:

Todas las etapas del desafío, desde la extracción de datos hasta la generación del informe final y análisis de correlación, han sido concluidas.

## <a name="proceso-realizado-etl-y-eda"></a> ⚙️ Proceso Realizado (ETL y EDA)

El proyecto se estructuró en los siguientes pasos principales:

1.  **Paso 1: Extracción (E)**
    *   Carga de datos directamente desde la API proporcionada (formato JSON).
    *   Conversión de los datos a un DataFrame de Pandas.

2.  **Paso 2: Transformación (T)**
    *   **2.1. Conocimiento del Conjunto de Datos:** Exploración inicial de columnas y tipos de datos. Identificación de estructuras anidadas.
    *   **2.2. Comprobación de Incoherencias:** Verificación de valores ausentes (strings vacíos en 'Churn'), duplicados (`customerID`), y formatos incorrectos (`total_charges` como string).
    *   **2.3. Manejo de Inconsistencias:**
        *   Eliminación de filas con `Churn` vacío.
        *   Aplanamiento de columnas con datos JSON anidados (`customer`, `phone`, `internet`, `account`) en columnas individuales.
        *   Conversión de `total_charges` a numérico, imputando valores para `tenure = 0`.
        *   Conversión de `Churn` a formato binario (0/1).
    *   **2.4. Creación de Columna de Cuentas Diarias:** Cálculo de `daily_charges` a partir de `monthly_charges`.
    *   **2.5. Estandarización y Transformación (Opcional):**
        *   Renombrado de columnas para mayor claridad.
        *   Conversión de columnas categóricas binarias ('Yes'/'No') a formato numérico (1/0).
        *   Estandarización de valores como "No internet service" a "No" y posterior conversión a 1/0.

3.  **Paso 3: Carga y Análisis (L - Load & Analysis)**
    *   **3.1. Análisis Descriptivo:** Cálculo de métricas estadísticas (media, mediana, std, etc.) para variables numéricas y categóricas.
    *   **3.2. Distribución de Evasión:** Visualización de la proporción de clientes que evadieron vs. los que no.
    *   **3.3. Recuento de Evasión por Variables Categóricas:** Análisis de la tasa de churn para diferentes categorías de variables como tipo de contrato, servicio de internet, método de pago, etc., utilizando gráficos y tablas de contingencia.
    *   **3.4. Conteo de Evasión por Variables Numéricas:** Análisis de la distribución de variables como antigüedad, cargos mensuales y totales para clientes que evadieron vs. los que no, utilizando histogramas y boxplots.
    *   **3.5. Informe Final:** Elaboración de un resumen estructurado del trabajo realizado, incluyendo hallazgos y recomendaciones (este mismo README y el informe en el notebook).

4.  **Paso 4: ¡EXTRA! Análisis de Correlación**
    *   Creación de una nueva característica: `num_total_services`.
    *   Cálculo y visualización de una matriz de correlación para identificar relaciones lineales entre las variables numéricas/binarias, con especial atención a su correlación con `Churn`.

## <a name="acceso-al-proyecto-y-ejecución"></a> 📁 Acceso al Proyecto y Ejecución
El proyecto se desarrolló íntegramente en un notebook de **Google Colaboratory** (`.ipynb`).

**Para ejecutar el proyecto:**
1.  Abre el archivo `.ipynb` en Google Colaboratory.
2.  Asegúrate de tener conexión a internet para la extracción de datos desde la API en el Paso 1.
3.  Ejecuta las celdas de código en orden secuencial. Las bibliotecas necesarias (`requests`, `pandas`, `numpy`, `matplotlib`, `seaborn`) son comúnmente preinstaladas en Google Colab. Si alguna faltara, se puede instalar usando `!pip install nombre_biblioteca` en una celda de código.

## <a name="tecnologías-utilizadas"></a> 💻 Tecnologías Utilizadas
*   **Python 3:** Lenguaje de programación principal.
*   **Pandas:** Para la manipulación y análisis de datos tabulares.
*   **NumPy:** Para operaciones numéricas eficientes.
*   **Matplotlib:** Para la creación de visualizaciones estáticas.
*   **Seaborn:** Para la creación de visualizaciones estadísticas más elaboradas.
*   **Requests:** Para realizar solicitudes HTTP y extraer datos de la API.
*   **Google Colaboratory:** Entorno de notebook basado en la nube para la ejecución del código.
*   **Markdown:** Para la documentación y el informe.

## <a name="principales-hallazgos-e-insights"></a> 💡 Principales Hallazgos e Insights
El análisis reveló varios factores clave asociados con la evasión de clientes:
*   **Contratos Mes a Mes:** Presentan la tasa de churn más alta.
*   **Servicio de Fibra Óptica:** Clientes con este servicio tienden a evadir más, sugiriendo posibles problemas de precio o expectativas.
*   **Método de Pago "Electronic Check":** Asociado con una tasa de churn significativamente elevada.
*   **Baja Antigüedad (Tenure):** Clientes más nuevos son más propensos a cancelar.
*   **Cargos Mensuales Más Altos:** Se correlacionan con una mayor tasa de evasión.
*   **Ausencia de Servicios Adicionales:** No tener servicios como Seguridad Online, Soporte Técnico, etc., incrementa la probabilidad de churn.
*   **Demografía:** Adultos mayores, y clientes sin pareja o dependientes, muestran mayores tasas de evasión.

*El informe detallado con estos insights se encuentra en la celda "3.5. Informe final" del notebook.*

## <a name="recomendaciones-estratégicas"></a> 🚀 Recomendaciones Estratégicas
1.  **Fomentar Contratos a Largo Plazo:** Ofrecer incentivos para migrar de planes mes a mes.
2.  **Optimizar Oferta de Fibra Óptica:** Investigar y abordar las causas de alta evasión en este segmento.
3.  **Promover Métodos de Pago Seguros:** Incentivar el cambio desde "Electronic check".
4.  **Programas de Retención Temprana:** Enfocarse en clientes nuevos.
5.  **Impulsar Servicios de Valor Agregado:** Destacar sus beneficios y crear paquetes atractivos.
6.  **Revisar Estrategia de Precios:** Especialmente para segmentos con cargos altos y alta evasión.
7.  **Atención a Segmentos Vulnerables:** Diseñar ofertas para adultos mayores y clientes sin pareja/dependientes.

*Las recomendaciones detalladas se encuentran en la celda "3.5. Informe final" del notebook.*

## <a name="persona-desarrolladora-del-proyecto"></a> 👨‍💻 Persona Desarrolladora del Proyecto

| <a href="https://github.com/thecat065" target="_blank"><img src="https://avatars.githubusercontent.com/u/84462727?s=400&u=e1e54489ec1ad20af8034beff9354a122b9e9a79&v=4" width="115" height="115" style="border-radius:50%; object-fit: cover;" alt="Foto de Carlos Victorio"><br><sub>Carlos Victorio 💻</sub></a> |
| :---: |

## <a name="agradecimientos"></a> 🙏 Agradecimientos
*   A Alura y al programa ONE por la oportunidad de participar en este desafío.
*   Al instructor Wilfredo Rojas por la presentación del desafío.
*   A Ingrid Cristh por proporcionar el dataset y la API para este proyecto.

---
*Este README fue generado para cumplir con los requisitos del desafío de Data Science de Telecom X.*
