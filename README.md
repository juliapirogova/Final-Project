# Final-Project
Proyecto final thePower
## Bienestar Subjetivo en Europa
Análisis Exploratorio de Datos (EDA) y Dashboard Interactivo
European Social Survey – Round 11 (2023–2024)

📌 Descripción del Proyecto
Este proyecto analiza el bienestar subjetivo en Europa utilizando datos del European Social Survey (ESS) Round 11 (2023–2024).
El objetivo principal es estudiar:
Las diferencias generacionales en bienestar.
Las diferencias entre España y el resto de Europa.
Los factores que más influyen en la felicidad y la satisfacción vital.
Se realiza un EDA completo, análisis estadístico y la construcción de un dashboard interactivo que permite explorar los resultados de forma dinámica.

🎯 Objetivos del Análisis
Analizar la felicidad y satisfacción vital en Europa.
Comparar España con el resto de Europa.
Estudiar diferencias entre generaciones:
Baby Boomers
Generación X
Millennials
Generación Z
Silent Generation
Evaluar el impacto de diferentes factores sobre el bienestar:
Ingresos
Educación
Reuniones sociales
Deporte
Confianza política
Interés político
Uso de internet
Problemas de sueño
Horas de trabajo
Entre otros


📂 Estructura del Repositorio
📁 bienestar-europa-ess
│
├── 📁 data
│   ├── testeuropa.csv
│   ├── datoseuropa.csv
│   └── datos_unidos.csv
    ├── datos_limpios.csv
│   ├── datos_finales.csv
│   └── datos_paraexcel.csv
│
├── 📁 notebooks
│   └── 01.Prep.ipynb
    └── 02.Preliminar.ipynb
│   └── 03.Limpieza.ipynb
│   └── 04.Nulos.ipynb
    └── 05.Analisis.ipynb
│   └── 06.Comparacion.ipynb

├── 📁 dashboard
│   └── dashboard.xlsx
│
├── 📁 report
│   └── resultados.pdf
│
└── README.md

# El contenido de los notebooks:
01.Prep
En el primer notebook hacemos un analisis muy preliminar de los datos crudos que tenemos. Es un dataset  real de  European Social Survey (ESS) sobre el bienestar y las costumbres europeas. El set inicial tiene 50.116 observaciones y 691 columnas originales. Busca estudiar el bienestar subjetivo, los factores sociales y económicos, la confianza política, la demografía y las posibles diferencias entre países y generaciones.
Diagnóstico inicial:
Dataset muy grande (264 MB)
691 variables
Más de 12 millones de valores nulos
Muchas variables con códigos especiales (77, 88, 99, 6666…)
Se procede a la reducción de variables para poder trabajar con el conjunto y quedarse solo con variables útiles para análisis social (de  691 columnas a 18 columnas clave)
Se realiza un reemplazo de valores especiales y se convierten en nulos y el sexo se convierte en variable categórica. 
Se renombran las  columnas para aumentar la claridad. 
Luego se procede a trabajar con la  segunda base de datos que contiene las variables relacionadas con la entrevista. Se hace el merge por ID y pais. 
02.Preliminar
En este notebook hacemos un análisis preliminar de nuestro dataset para detectar que tipo de limpieza y gestión de nulos habrá que hacer posteriormente. 
Se procede a realizar las graficas y claramente se ve un desafio importante: valores imposibles. 
Se realiza un matriz de correlación pero con los datos inexactos todavia no aporta la totalidad de información. 
En cuanto a los nulos, la columna que más nulos tiene es de ingresos (unos 20%), lo cual parece lógico, puesto que a la gente le suele ser incómodo todas estos temas. 
03.Limpieza
Este notebook tiene como objetivo realizar la limpieza, transformación y análisis exploratorio de datos. El propósito principal es preparar el dataset para posteriores análisis estadísticos y estudiar los factores asociados al bienestar y las diferencias generacionales y entre los paises. 
Se realiza una limpieza sistemática que incluye el reemplazo de códigos especiales por valores nulos (NaN) en varios variables. 
Se eliminan códigos inválidos y se sustituyen valores numéricos por categorías descriptivas.
Posteriormente, se procede a la creación de nueva variable: generación
Se crea una nueva variable categórica generacion basada en el año de nacimiento:
	Silent Generation (1928–1945)
	Baby Boomers (1946–1964)
	Generación X (1965–1980)
	Millennials (1981–1996)
	Generación Z (1997–2012)
Esto permite facilitar análisis comparativos intergeneracionales.
Se invierten las escalas de interes_politica e importancia_tradiciones: para que valores más altos representen mayor intensidad o mayor importancia, mejorando la coherencia interpretativa del análisis.
Para finalizar, se realiza el  análisis exploratorio de datos (EDA) que incluye:
	Histogramas de todas las variables numéricas
	Boxplots para detectar valores extremos
	Gráficos de frecuencia para variables categóricas
	Matriz de correlación entre variables numéricas
Eso permite identificar:
	Fuerte correlación entre satisfacción con la vida y felicidad.
	Relación positiva entre ingresos y bienestar.
	Relación negativa entre problemas de sueño y felicidad.
	Asociación entre uso de internet e ingresos.
	Relación inversa entre interés político y confianza en políticos.
En cuanto a los valores nullos, la variable con mayor proporción de nulos es decil_ingresos (~21%), probablemente debido a la sensibilidad del tema.
El resto de variables presentan porcentajes bajos de datos faltantes (<2%).
Se deja preparado el dataset para un tratamiento posterior de los valores nulos.
04.Nulos
Este notebook realiza el tratamiento de valores nulos del dataset previamente limpiado, aplicando diferentes estrategias según el tipo de cada variable.
Para empezar, se hace un análisis previo de nulos:
Estado civil → hay muchos nulos
Ingresos → variable sensible, con muchos nulos (un 20%), posiblemente porque a la gente no le gusta indicar su nivel de ingresos
Horas trabajo nulos tras limpiar  valores irreales
Estrategias aplicadas:
Hemos aplicado distintas estrategias según el tipo de variable. 
	Eliminación de filas:
Edad es clave para crear generacion, que es el objetivo del analisis, además, representa menos del 1% y no afecta significativamente al tamaño de la muestra
	Variable categórica estado_marital:
se añade una categoria nueva ¨desconocido¨. Eso permite usar la variable sin perder datos
	Variables numéricas → Mediana por generación
	Categóricas con pocos nulos → Moda, ya que no afectan distribución
05. Analisis
El objetivo de este notebook es analizar las diferencias generacionales en diferentes factores mencionados anteriormente. 
El enfoque principal es estudiar si existen diferencias importantes entre generaciones en los niveles de bienestar.
Se procede a hacer las gráficas agrupadas por generación para cada factor, sacando la media para cada grupo.
Se han hecho las correlaciones y se ha detectado que el bienestar está más relacionado con factores sociales y económicos (nivel de satisfacción, reuniones sociales, salarios).
Posteriormente, se ha realizado un ANOVA para ver las diferencias en felicidad de cada generación. (F = 103.36, p < .001) Se comprueba que  existen diferencias estadísticamente significativas entre generaciones.
Después, se añade un test Post-hoc (Tukey). Podemos observar que todas las generaciones difieren entre sí (p < .05) y la mayor diferencia se observa entre Gen Z y Silent Generation (0.60 puntos), lo cual representa una brecha generacional importante.
Para resumir este notebook, llegamos a la conclusión que existen diferencias generacionales claras en bienestar. Las generaciones jóvenes reportan mayor felicidad. El bienestar se asocia positivamente con vida sociañ y nivel de ingresos y negativamente con problemas de sueño. 
06.Comparacion
Este notebook tiene el propósito de analizar las diferencias en bienestar entre España y el resto de Europa.
Para ello, empezamos creando la variable region (España vs Resto Europa) y también añadimos la segmentación adicional por generación.
Paso siguiente, se procede a la comparación descriptiva por región y generación: se realizan los cálculos de medias para todas las variables numéricas y visualización mediante gráficos de barras por variable.
A continuación, se desarrolla un análisis de correlaciones con el cálculo de matrices de correlación separadas y visualización con mapas de calor. Esto permite explorar qué variables están asociadas al bienestar.
Se comparan las medias agregadas mediante el cálculo de medias globales para variables clave. Se hace la construcción de tabla comparativa España vs Mundo y el cálculo de diferencias absolutas.
Asimismo, se estiman tamaños de efecto para evaluar la magnitud real de las diferencias entre España y el resto del mundo.

Resultados más relevantes que hemos encontrado son:
	Educación (efecto moderado)
	Reuniones sociales (efecto moderado)
	Confianza política (efecto moderado negativo)
	Felicidad (efecto pequeño-moderado)
	Ingresos (efecto prácticamente nulo)

En cuanto al  análisis generacional, se puede identificar patrones globales (por ejemplo, jóvenes más felices). Y se evalua si la ventaja española se mantiene en todas los grupos.
	Los  hallazgos que hemos obtenido en este punto son:
	España presenta mayores niveles de felicidad y satisfacción vital.
	La diferencia no se explica por ingresos.
	España destaca por mayor educación y mayor capital social.
	La confianza política es menor en España.
	El bienestar parece estar más vinculado a factores sociales que económicos.
	El patrón generacional de mayor felicidad en jóvenes es global.
Para concluir, se estima que el diferencial positivo de bienestar en España podría estar asociado más a factores sociales y educativos que a variables económicas o institucionales. 

# Análisis Descriptivo
Edad media: 51.6 años.
Felicidad media: 7.32 / 10.
Satisfacción vital media: 7.00 / 10.
Distribución generacional:
Generación	N
Baby Boomers	15.283
Gen X	13.566
Millennials	11.047
Gen Z	5.978
Silent Generation	3.849
Hallazgos descriptivos principales:
España presenta mayor felicidad que la media europea (+0.55).
España presenta mayor satisfacción vital (+0.51).
España tiene más reuniones sociales.
España tiene menor confianza en políticos.
# Análisis Estadístico
Diferencias de medias (España vs Europa)
Variable	Diferencia
Felicidad	+0.55
Satisfacción	+0.51
Reuniones sociales	+0.51
Educación	+1.23 años
Confianza política	-0.74
Correlaciones principales con felicidad
Variable	Correlación
Satisfacción vital	0.67
Reuniones sociales	0.23
Ingresos	0.22
Uso de internet	0.20
Interés político	-0.22
Problemas de sueño	-0.22

# Dashboard

El dashboard fue desarrollado en Excel.
Incluye:
Comparación España vs Europa.
Filtros por generación.
Filtros por sexo y país.
Visualización de:
Felicidad
Satisfacción
Ingresos
Educación
Reuniones sociales
Confianza política
Gráficos de correlación.
Relación ingresos–felicidad.
Relación interés político–felicidad.

El dashboard permite análisis dinámico y exploración interactiva.

🛠 Herramientas Utilizadas
EDA y Análisis
Python
Pandas
NumPy
Matplotlib / Seaborn
Scipy
Statsmodels
Visual Studio Code
Visualización y Dashboard
Microsoft Excel

🧠 Conclusiones Generales
Los resultados sugieren que:
España presenta mayor bienestar subjetivo que la media europea.
Este diferencial no se explica por ingresos ni por confianza institucional.
Las relaciones sociales parecen ser el factor diferencial clave.
El bienestar español parece estar más vinculado al capital social informal que al capital institucional.
Existen diferencias generacionales claras en bienestar.
La Silent Generation presenta los niveles más bajos de felicidad.

⚠️ Limitaciones
Análisis principalmente bivariado.
Posible efecto edad vs efecto cohorte.

🚀 Cómo reproducir el proyecto
Clonar el repositorio.
Instalar dependencias:
pip install pandas numpy matplotlib seaborn scipy statsmodels
Ejecutar los notebooks

Abrir el dashboard en Excel.

📌 Valor del Proyecto
El proyecto proyecto demuestra:
Limpieza y transformación avanzada de datos.
Uso eficiente de Python y Pandas.
Análisis estadístico aplicado.
Capacidad de interpretación sociológica.
Creación de un dashboard operativo.
Organización de repositorio.