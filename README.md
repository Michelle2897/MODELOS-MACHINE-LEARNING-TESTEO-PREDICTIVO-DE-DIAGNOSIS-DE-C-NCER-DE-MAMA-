# MODELOS-MACHINE-LEARNING-TESTEO-PREDICTIVO-DE-DIAGNOSIS-DE-C-NCER-DE-MAMA-
Se aplican modelos ML que permitan predecir la asgnación de un diagnostico correcto de existencia de tumores malignos en muestras de pacientes que presentaron posible diagnosos de cáncer de mama.
Aplicación de modelos ML para la identificación de diagnosis de presencia de cáncer de mama

Iniciamos identificando y explorando la base de datos desde el repositorio:
https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic

La base corresponde a una serie de datos tomados de pacientes sometidos a testeo de cáncer de mama, por lo tanto, la base propone algunas características de tumores observados, la base esta compuesta por 32 variables, 31 continuas y 1 categórica misma que describe la diagnosis de la paciente clasificando con la letra B “Benigno” y M “Maligno”.
Para efecto del trabajo de modelos predictivos se usarán tres variables (radius, texture y perimeter). Debido a que según estudios realizados previamente el diagnostico está determinado principalmente por la observación en la muestra de tejido o tumor según lo observado a simple vista. Esto incluye color general, peso, tamaño y consistencia. Por lo tanto, con el fin de que generar convergencia los resultados de los modelos a aplicarse se tomarán las variables que mayormente intervengan en la explicación de la diagnosis, es importante mencionar que las variables asignadas están dadas por la existencia de muestras estudiadas en imágenes encontrando la variación de las intensidades de la escala de grises y tomando en cuenta especialmente los valores extremo, ya que son los más intuitivamente útiles para el problema en cuestión, ya que sólo pueden aparecer unas pocas células malignas en una muestra determinada.

Instalamos todas la librerías y paquetes que se usarán en la ejecución de los modelos predictivos, posterior a ello empezamos cargando los datos con los que trabajaremos en dos dataframes, para X tomaremos 3 variables explicativas cuya eficiencia y uso se justificaron anteriormente ( radius, textura, perimeter), mientras que en el dataframe y se tomara la variable diagnosis misma que se ha dicotomizado con valores de 0 “Malignos” y 1 “Benignos”. 
 
MODELO DE REGRESIÓN LOGISTICA

La técnica de regresión logística de machine learning, se usa típicamente para trazar una línea central dividiendo los datos, en este caso los tumores beningnos de los malignos, se genera la ejecución del modelo de regresión desde la librería Sklearn posterior a esto dividimos el conjunto de datos, aquella fracción muestral que se tomará para el entrenamiento del modelo y la ejecución de la predicción en sí, en este punto se especifica un random_state de 42. Se entrena el modelo empleando el método fit, asignando a los datos de entrada a características de las clases de salida. Usando el método predict se generan las predicciones de testeo.
Para visualizar el comportamiento de predictivo del modelo según los datos y variables usadas se genera la matriz de confusión para la interpretación de los resultados, los ceros representar en la diagonal principales los tumores malignos mientras que el valor en la diagonal derecha inferior en el cuadrante 1 se refiere a los tumores benignos, no obstante el modelo ha presentando un margen de error en la predicción al determinar 14 desaciertos,  asignado 6 tumores como benignos a tumores malignos y ha asignando 8 tumores como malignos  a tumores benignos. Adicionalmente podemos observar un accuracy de 0.94, por lo tanto, la regresión lineal logística explica en un 94% el comportamiento del modelo.
 
 MODELO ÁRBOL DE DECISIÓN
 
Traza una serie de preguntas que si se cumplen darán como resultado un diagnostico ya sea maligno o benigno. Para la ejecución del modelo de árbol de decisión se usa el código DecisionTreeClassifier desde la librería Sklearn. Se definen las mientras divididas para el entrenamiento del modelo asignando un random state de 42 como en el modelo anterior con la finalidad de disminuir mayor cambio en los resultados. Posteriormente se entrena el modelo desde el código fit  y se predicen los valores para los X_test. La aplicación del árbol de decisión da un resultado de 0.92 en accuracy, es decir comparado con el modelo de regresión logística el valor de explicación del modelo es menor.
Respecto a la matriz de confusión, da como resultado en la diagonal principal en el valor izquierdo superior 50 tumores malignos mientras que el valor en la diagonal derecha inferior en el cuadrante se refiere a la predicción de 82 tumores benignos, no obstante el modelo ha presentado un margen de error en la predicción al determinar 11 errores, asignado 4 tumores como benignos a tumores malignos y ha asignado 7 tumores como malignos a tumores benignos.


MODELO RANDOM FOREST

Usa muchos arboles de decisión y en función de los votos que tengan los criterios de los árboles se da el resultado de la diagnosis, para ejecutar el modelo se definen:  
Como en los caso anteriores se definen los conjuntos muestrales para el entrenamiento del modelo y posterior a ellos la predicción para los X_test, dando como resultado una matriz de confusión con un accuracy de 0.92, mismo que comparado con el modero de árbol de decisión simple presenta una coincidencia cercana. La matriz de confusión para el modelo RndomForest muestra en la diagonal principal un valor predictivo de tumores malignos de 44 mientras que en los tumores benignos predictivos acertado un valore de 87, el principal problema para el modelo es la existencia de errores dado que debido a la naturaleza del problema en si, no es aceptable la asignación de 10 predicciones de tumores beningnos que en relidad son malignos. Así también de han determinado una asignación de 2 tumores malignos que en relidad no presentan célular cancerígenas.

  
Decisión

Después de la aplicación de tres modelos de machine learning para la predicción de diagnosis de un tumor maligno en un estudio de cáncer de mama, se determina que el modelo que mejor resultado expresó en la explicación del comportamiento de las variables radio, textura y perímetro del tumor fue la regresión logarítmica en un 94% acertada generalmente en cuanto a la predicción de la diagnosis para un tumor maligno o benigno.
 
La precisión para la clase 0 es del 89%, lo que indica que el modelo identifica correctamente todos los casos de diagnosis de tumores malignos (clase 0) en un 89% de las veces. Para la clase 1, la precisión es del 97%, lo que significa que el modelo identifica correctamente el 97% de los casos benignos (clase 1) de entre todos los casos que clasifica como no malignos.
La sensibilidad o recall, la clase 0, el recall es del 94%, lo que significa que el modelo identifica correctamente el 94% de la diagnosis de tumores malignos (clase 0) de todos los casos maliciosos reales. Para la clase 1, el recall es del 93%, lo que indica que el modelo identifica correctamente el 100% de los tumores benignos(clase 1) de todos los casos no maliciosos reales.
El F1-score para la clase 0 es del 92%, mientras que para la clase 1 es del 95%. El support es el número de ocurrencias reales de cada clase en los datos de prueba. En este caso, hay 54 muestras de la clase 0 y 89 muestras de la clase 1. La precisión global del modelo es del 94%.


