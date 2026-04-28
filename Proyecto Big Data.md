![][image1]

**Materia:** 

Introducción de Big Data y Data Analytics

**Actividad:** 

Proyecto: Turismo digital y precios de alojamiento

**Profesor:** 

Alan Victor Raul Morante

**Integrantes:**

| Dayra Barboza | Ingeniera de datos |
| :---- | :---- |
| Fabiana Gomez | Analista de datos |
| Dayanara Rodriguez | Documentadora |
| Andrea Nicole Vera Tacilla | Analista de negocio |
| Ian Yucra | Líder de proyecto |

1. **Descripción del problema de negocio**

   URBVI es una empresa de gestión y análisis de propiedades de corta estancia que administra un portafolio de activos inmobiliarios en New York City, enfocados en maximizar la rentabilidad mediante estrategias de pricing, ocupación y selección de ubicaciones.

   La empresa enfrenta dificultades para optimizar el desempeño de sus propiedades debido a una comprensión limitada del impacto que tienen los puntos de interés urbanos en la variabilidad del precio y la demanda, lo que deriva en decisiones subóptimas de pricing y asignación de capital.

   Resolver este problema es altamente relevante porque permite a la empresa mejorar la precisión en sus estrategias de pricing y maximizar indicadores clave como ingresos por propiedad y tasa de ocupación. Asimismo, facilita una asignación más eficiente del capital al identificar zonas con mayor potencial de rentabilidad dentro de la ciudad, reduciendo el riesgo asociado a la adquisición o gestión de nuevos activos. La integración de variables geoespaciales en el análisis del desempeño permite transformar datos del entorno urbano en insights accionables, disminuyendo la incertidumbre en la toma de decisiones y generando una ventaja competitiva frente a operadores que no incorporan este tipo de análisis.

2. **Descripción de los datos**

   1. **Fuentes principales**

Dataset: NYC Airbnb Open Data

Fuente: Kaggle

La fuente principal utilizada es el dataset NYC Airbnb Open Data, que contiene información sobre propiedades publicadas en Airbnb dentro de la ciudad de Nueva York. Este dataset permite analizar factores relacionados con precios, ubicación, disponibilidad y comportamiento de los anfitriones, este cuenta con aproximadamente 48,895 registros (filas) y 16 variables principales (columnas), entre las más relevantes:

* **price:** precio por noche del alojamiento

* **neighbourhood\_group:** distrito principal (Manhattan, Brooklyn, Queens, etc.)

* **room\_type:** tipo de habitación (entire home, private room, shared room)

* **latitude:** latitud de la propiedad

* **longitude:** longitud de la propiedad

* **neighbourhood:** barrio específico

* **number\_of\_reviews:** número total de reseñas

* **reviews\_per\_month:** promedio mensual de reseñas

* **availability\_365:** cantidad de días disponibles al año

* **calculated\_host\_listings\_count:** número de propiedades del mismo anfitrión

Estas variables permiten identificar patrones asociados a precios premium y posibles                 niveles de ocupación.

Dataset: Inside Airbnb \- [(https://insideairbnb.com/get-the-data/)](https://insideairbnb.com/get-the-data/)

Esta fuente proporciona datos más detallados y actualizados sobre el mercado de Airbnb, incluyendo disponibilidad real, comportamiento de ocupación, métricas de reviews y desempeño de los alojamientos por zona, cuenta con aproximadamente 15,895 registros y más de 80 variables adicionales, lo que permite complementar el análisis del dataset principal con una visión más profunda sobre la dinámica real del mercado y la demanda.

Las variables más importantes utilizadas son:

* **neighbourhood\_cleansed**

* **neighbourhood\_group\_cleansed**

* **latitude**

* **longitude** 

* **number\_of\_reviews** 

* **minimum\_nights** 

* **review\_scores\_rating**

* **review\_scores\_location**   

* **review\_scores\_value** 

Estas variables permiten aproximar mejor la ocupación real del alojamiento y evaluar si   ciertas características del host o de la propiedad influyen en precios premium y mayor demanda.

2. **Fuente de enriquecimiento:** 

Dataset: Overpass Turbo (OpenStreetMap) \- [(https://overpass-turbo.eu/\#)](https://overpass-turbo.eu/#)

Además, se utilizó Overpass Turbo, basado en datos de OpenStreetMap, esta herramienta permite extraer información geográfica sobre puntos de interés cercanos a las propiedades, como: estaciones de metro, paraderos,restaurantes,zonas turísticas, parques, centros comerciales, atractivos urbanos,etc.

Se trabajó con etiquetas de OpenStreetMap como:

* amenity=restaurant

* amenity=cafe

* shop=supermarket

* leisure=park

* tourism=attraction

* railway=station

Las principales variables incorporadas fueron:

* cantidad de restaurantes cercanos

* cantidad de estaciones de metro cercanas

* cantidad de parques cercanos

* cantidad de supermercados cercanos

* cantidad de cafeterías cercanas

* cantidad de atracciones turísticas cercanas

* densidad comercial de la zona

* proximidad a zonas turísticas importantes

Estas variables ayudan a medir el valor estratégico de la ubicación y su impacto en el precio y ocupación.

3. **Limitaciones identificadas**

Se identificaron algunas limitaciones iniciales en los datos:

* No existe una variable directa de ocupación real

* Algunos precios presentan valores extremadamente altos que podrían distorsionar el análisis

* Existen valores nulos en variables como ***reviews\_per\_month***

* La disponibilidad no siempre representa demanda real, ya que puede depender de decisiones del anfitrión

Por ello, será necesario realizar un proceso de limpieza de datos, tratamiento de valores nulos, detección de outliers y validación de consistencia antes de desarrollar el EDA y validar las hipótesis de negocio.

3. **EDA Inicial**

   1. **Distribución de precios por ubicación**

   El análisis de la distribución de precios por distrito evidencia diferencias significativas entre las distintas zonas de la ciudad. En particular, se observa que Manhattan presenta una mediana de precios más elevada, así como una mayor dispersión y presencia de valores atípicos asociados a propiedades de alto costo. Brooklyn muestra un comportamiento similar, aunque en menor magnitud, mientras que distritos como el Bronx y Staten Island concentran opciones relativamente más económicas.

   Estos resultados sugieren la existencia de una segmentación geográfica del mercado inmobiliario de corta estancia, donde la ubicación podría estar asociada a distintos niveles de disposición a pagar por parte de los usuarios.

   2. **Análisis de demanda acumulada**

   El volumen total de reseñas, utilizado como aproximación al nivel de actividad o demanda, muestra una clara concentración en los distritos de Brooklyn y Manhattan. Este patrón indicaría una mayor rotación de huéspedes en estas zonas, lo que podría estar vinculado a factores como accesibilidad, conectividad o cercanía a áreas de interés.

   No obstante, al tratarse de un análisis exploratorio, estos resultados deben interpretarse con cautela, ya que el número de reseñas puede estar influenciado por múltiples factores adicionales.

   3. **Distribución geográfica de precios**

   El análisis espacial de los precios revela una mayor concentración de valores elevados en determinadas áreas de la ciudad, particularmente en zonas de Manhattan y sectores de Brooklyn cercanos al East River. Estas áreas coinciden con regiones de alta densidad urbana y potencialmente mayor actividad económica y turística.

   Este patrón sugiere que la ubicación geográfica podría desempeñar un rol relevante en la determinación del precio de los alojamientos, aunque se requiere un análisis más profundo para identificar los factores específicos que explican estas diferencias.

   4. **Relación entre variables de calidad, precio y disponibilidad**

   La matriz de correlación muestra una relación positiva moderada entre la puntuación de ubicación y la calificación general del alojamiento, lo que indicaría que la percepción de la ubicación podría influir en la valoración global por parte de los usuarios. Por otro lado, la correlación entre el precio y el número de reseñas resulta baja, lo que sugiere que la demanda no estaría determinada únicamente por el nivel de precios.

   Estos resultados evidencian que el desempeño de los alojamientos podría depender de múltiples dimensiones, más allá de variables puramente económicas.

   5. **Disponibilidad y demanda según tipo de alojamiento**

   El análisis de la relación entre disponibilidad anual y número de reseñas sugiere la existencia de un patrón no lineal. En particular, los alojamientos con niveles intermedios de disponibilidad tienden a concentrar una mayor cantidad de reseñas, lo que podría estar asociado a una mayor rotación de huéspedes.

   Asimismo, se observa que los alojamientos completos (“entire home/apt”) presentan una mayor dispersión en términos de demanda, lo que indicaría una mayor heterogeneidad en su desempeño.

   6. **Influencia de la ubicación en la percepción de valor**

   El análisis de la puntuación promedio de ubicación por distrito evidencia diferencias en la percepción de valor asociada a la localización de las propiedades. En particular, se observa que distritos como Manhattan presentan las puntuaciones más altas en términos de ubicación, lo que indicaría una valoración positiva por parte de los usuarios respecto a su entorno.

   Este patrón sugiere que la ubicación podría ser un factor relevante en la experiencia percibida del alojamiento. Sin embargo, al tratarse de un análisis exploratorio, no es posible atribuir esta valoración exclusivamente a la densidad de puntos de interés, ya que podrían intervenir otros factores asociados al contexto urbano.

   7. **Relación entre puntuación de ubicación y calificación general**

   El análisis de dispersión entre la puntuación de ubicación y la calificación general muestra una tendencia positiva entre ambas variables. Se observa una mayor concentración de observaciones en niveles altos de ambas métricas, lo que indicaría que propiedades con mejor valoración de su ubicación tienden a recibir calificaciones generales más altas.

   Este comportamiento sugiere que la percepción de la ubicación podría estar asociada a la satisfacción global de los usuarios. No obstante, esta relación no implica necesariamente causalidad, por lo que sería necesario un análisis más profundo para determinar el peso relativo de la ubicación frente a otros factores en la evaluación de los alojamientos.

   

4. **Hipótesis de negocio**

A partir de los hallazgos del análisis exploratorio, se plantean las siguientes hipótesis de negocio, orientadas a evaluar el impacto de la ubicación y el entorno urbano en el desempeño de las propiedades.

1. ¿El distrito en el que se encuentra una propiedad Airbnb tiene mayor impacto en su precio que sus características internas como el tipo de habitación o el número mínimo de noches requeridas? 

   2. ¿Las propiedades rodeadas de una mayor oferta de servicios y atracciones urbanas en un radio de 500 metros presentan un mayor número de reseñas y menor disponibilidad anual, indicando una demanda más alta y sostenida? 

   3. ¿Los anfitriones que gestionan múltiples propiedades tienden a ubicarlas en zonas de alta densidad de puntos de interés, obteniendo precios superiores al promedio del mercado? 

   4. ¿Existe un perfil óptimo de propiedad en NYC — definido por su tipo, distrito y entorno urbano — que permita a un gestor de alojamientos maximizar simultáneamente sus ingresos por noche y su tasa de ocupación? 

5. **Plan de trabajo para la Etapa 2**

| Semana | Ian (Líder de proyecto) | Dayra (Ingeniera Datos) | Fabiana (Analista de Datos) | Andrea (Analista de Negocio) | Dayanara (Documentadora) |
| :---- | :---- | :---- | :---- | :---- | :---- |
| 7 | Supervisión general \+ validación hipótesis | Integración final de datasets  | Análisis bivariado y correlaciones | Interpretación de resultados de hipótesis | Documentación del análisis |
| 8 | Definición de enfoque de segmentación | Preparación de datos para clustering | Aplicación de clustering  | Identificación de perfiles de negocio | Redacción de insights iniciales |
| 9 | Validación de resultados del modelo | Optimización del dataset | Análisis de clusters y patrones | Traducción a insights de negocio | Documentación técnica del modelo |
| 10 | Definir estructura del dashboard | Preparación de dataset para visualización | Creación de gráficos clave | Definir preguntas de negocio del dashboard | Redacción de descripciones |
| 11 | Revisión del dashboard | Soporte técnico | Ajustes de visualizaciones | Validación de insights | Documentación final del dashboard |
| 12 | Definir recomendaciones estratégicas | Soporte en datos para escenarios | Análisis de impacto | Desarrollo de recomendaciones | Redacción del informe final |
| 13 | Ensayo presentación \+ feedback | Ajustes finales de datos | Validación final de análisis | Preparación de storytelling | Redacción final \+ reflexión |
| 14 | Presentación final | Soporte técnico en entrega | Soporte en preguntas | Exposición insights | Entrega documentación |

6. **Apéndice de uso de IA**

* Limpieza de Datos: 

  * Prompt:Te he proporcionado un archivo CSV que forma parte de un proyecto de Big Data. Mi problema de investigación es el siguiente: ¿Cómo influyen los puntos de interés urbanos en la variabilidad del precio y la demanda de alojamientos Airbnb en NYC, y cómo puede una empresa utilizar esta información para maximizar ingresos? Necesito que realices un proceso completo de análisis y limpieza de datos, alineando cada decisión con este objetivo. 

    ETAPA 1: Análisis exploratorio (SIN modificar los datos) Genera código en Python (pandas) que analice el dataset tal como está: head(), shape, info(), describe() Conteo de valores nulos por columna Detección de duplicados Identificación de problemas de calidad: Tipos de datos incorrectos Valores inconsistentes Variables mal formateadas (fechas, precios, texto, etc.).  Luego del código, incluye un breve análisis escrito donde expliques: Qué problemas encontraste Qué columnas parecen relevantes o irrelevantes respecto al problema de investigación. No realices ninguna limpieza todavía.

    ETAPA 2: Selección de variables (Feature Selection) Antes de limpiar, analiza las columnas y: Identifica cuáles son relevantes para el problema (precio, disponibilidad, ubicación, demanda, etc.) Identifica cuáles son irrelevantes o redundantes Elimina las columnas irrelevantes mediante código. Explica brevemente: Por qué cada columna eliminada no aporta al análisis Cómo las columnas seleccionadas ayudan a responder la pregunta de investigación

    ETAPA 3: Limpieza de datos (Data Cleaning) Ahora sí, genera código que limpie el dataset: Manejo de valores nulos (eliminación o imputación con justificación) Eliminación de duplicados Conversión de tipos de datos Estandarización de formatos: Fechas Precios (eliminar símbolos, convertir a numérico) Texto (minúsculas, espacios, etc.). Justifica brevemente cada decisión de limpieza en función del análisis..

    ETAPA 4: Resultado final Muestra el dataset limpio (head()) Resume los cambios realizados Explica si el dataset ahora está listo para analizar: Variación de precios Relación con puntos de interés Comportamiento de la demanda FORMATO DE RESPUESTA Usa bloques de código separados por etapa Incluye comentarios en el código Explicaciones claras, cortas y enfocadas en el problema No inventes datos, usa solo el CSV proporcionado Actúa como un analista de datos profesional trabajando en un proyecto real.

* Validación de calidad de hipótesis:

  * Prompt: Estoy desarrollando el entregable PC1 para el curso AD3005 — Introducción a Data Analytics y Big Data de UTEC. He formulado 4 hipótesis de negocio para el Caso 3: Turismo digital y precios de alojamiento. Necesito que evalúes cada hipótesis considerando los siguientes criterios de la rúbrica oficial: (1) si están redactadas como preguntas de negocio y no como afirmaciones técnicas, (2) si son verificables con los datos disponibles en el dataset NYC Airbnb Open Data y las fuentes de enriquecimiento seleccionadas, (3) si están conectadas directamente al problema de investigación planteado, y (4) si superan el mínimo de 3 hipótesis requeridas. Para cada hipótesis indica su nivel estimado según la escala Excelente/Satisfactorio/En desarrollo/Insuficiente y justifica tu evaluación.

    

  * Validación: Comparamos la evaluación generada por Claude con los criterios oficiales de la rúbrica del curso, verificando manualmente que cada hipótesis estuviera redactada en lenguaje de negocio, fuera medible con las variables disponibles en el dataset y respondiera directamente al problema de investigación planteado. Las hipótesis que no cumplían algún criterio fueron reformuladas por nosotros hasta alcanzar el nivel Excelente.

* Selección de fuentes de enriquecimiento

  * Prompt: Me encuentro desarrollando el Caso 3 del Proyecto Final del curso AD3005 de UTEC, cuyo problema de investigación es: '¿Cómo influyen los puntos de interés urbanos en la variabilidad del precio y la demanda de alojamientos Airbnb en NYC, y cómo puede una empresa utilizar esta información para maximizar ingresos?' Las fuentes de enriquecimiento sugeridas por el curso son: datos de puntos de interés (Foursquare/Google Places API), temporadas turísticas, reseñas de TripAdvisor e índice de criminalidad por zona. Para cada fuente necesito que indiques: (1) si está disponible de forma gratuita, (2) cómo se obtiene y en qué formato, (3) qué tan fácil es integrarla con el dataset base de Kaggle, y (4) qué variables aportaría al análisis. Finalmente recomienda cuáles dos fuentes son más convenientes considerando tiempo, facilidad de acceso y relevancia para el problema.

  * Validación: Ingresamos directamente a cada fuente recomendada por Claude para verificar su disponibilidad real, formato de descarga y compatibilidad con el dataset base. Descartamos las fuentes que requerían APIs de pago o registro complejo, y confirmamos que Overpass Turbo e Inside Airbnb eran accesibles de forma gratuita y directa antes de seleccionarlas como fuentes definitivas. 

* Convertir datos en puntos de interés

  * Prompt: Te adjunto un archivo en formato GeoJSON exportado desde Overpass Turbo, basado en datos de OpenStreetMap, que contiene información geográfica sobre puntos de interés urbanos en la ciudad de Nueva York (específicamente: estaciones de metro / museos / parques / restaurantes). Necesito que desarrolles un script en Python que realice las siguientes tareas: (1) lea y parsee correctamente la estructura del archivo GeoJSON, (2) extraiga los campos relevantes: nombre del lugar, latitud, longitud y tipo de punto de interés, (3) construya un DataFrame de pandas con esas columnas, (4) limpie valores nulos o registros sin coordenadas, y (5) exporte el resultado como archivo CSV limpio con el nombre coordenadas\_\[tipo\]\_nyc.csv, listo para ser cruzado con el dataset base de Airbnb mediante cálculo de distancias geoespaciales. 

  * Validación: Abrimos y revisamos manualmente los archivos CSV generados para verificar que las coordenadas correspondieran a ubicaciones reales dentro de NYC. Tomamos una muestra de puntos al azar y comprobamos su ubicación en Google Maps, confirmando que las estaciones de metro, museos, parques y restaurantes extraídos correspondían a lugares existentes en la ciudad. Adicionalmente verificamos que no hubiera valores nulos en las columnas de latitud y longitud. 

[image1]: <data:image/png;base64,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>