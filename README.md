# DeteccionCancerMama
Predicción de cancer de Mama

Detección de Cáncer de mama

Introducción
Detección de cáncer de mama partiendo de un dataset formado con información de imágenes digitalizadas de una masa mamaria que describen las características de los núcleos celulares presentes en las imágenes.

Preparación del Dataset
El dataset está formado inicialmente por 568 filas y 32 columnas. Una columna de Identificador, una columna con el diagnóstico y las restantes las características de las imágenes representadas en números decimales.
Las columnas no tienen cabecera por lo que se agregó etiquetas para cada una basándose en la documentación del dataset.
Se elimina la columna ID ya que no aporta información relevante.
El conjunto de datos no tiene valores nulos.

Modelamiento
Se usó tres tipos de modelamientos con el fin de comparar resultados y evaluar cuál es el que mejor predice los resultados. Los modelos escogidos fueron RandomForestClassifier, SVM (Support Vector Machine) y LogisticRegression.

RandomForestClassifier
Inicialmente se usó este modelo con los parámetros n_estimators=100 y random_state=42, y los demás parámetros por defecto obteniendo asi una precisión de 0.97 y una matriz de confusión con 0 falsos positivos y 3 falsos negativos para test y precisión de 1 para train lo cual quiere decir que en su matriz de confusión no tiene valores de falsos positivos ni falsos negativos. 
Al ser un modelo que tiene como fin identificar si un paciente tiene una enfermedad o no, los falsos negativos tienen mucha importancia por lo que debe ser un valor lo más bajo posible.
Con el objetivo de disminuir el valor de falsos negativos, se hicieron cambios en varios hiperparametros, sin embargo, no se obtuvo resultados exitosos sino lo contrario, la precisión decreció a 0.96, el valor de falsos negativos crecieron e incluso comenzaron a aparecer valores en falsos positivos también.

SVM (Support Vector Machine)
Para este modelo, además de la preparación del dataset previa, se hizo una estandarización de los datos usando StandardScaler(). 
Después de entrenar y predecir el modelo con varios parámetros, la precisión más alta en test fue de 0.96 y en train de 0.98 con los siguientes hiperparametros: kernel='linear', random_state=42.
La matriz de confusión obtenida se presenta con 1 en falsos positivos y 3 en falsos negativos en test lo cual es bueno, pero a pesar de intentar con otros parámetros no se pudo bajar el valor de falsos positivos

LogisticRegression
En este modelo se tuvo que setear un valor inicial en max_iter de 7000 ya que con el valor por defecto de 5000 generó un error ya que el modelo no llegaba a la convergencia.
Este modelo obtuvo valores en precisión tan altos como en los anteriores modelos, se obtuvo 0.92 en test y 0.96 en train.
Las matrices de confusión presentaron valores altos en falsos negativos 7 y 10 en test y train respectivamente, a pesar de hacer cambios en los hiperparametros, los valores no tuvieron un cambio significativo.

Conclusiones 
El modelo que mejor se adaptó a este caso de estudio fue el Rando Forest Classifier, en este modelo, a diferencia de los otros dos aplicados, obtuvo la mayor precisión 0.97. En cuanto a la matriz de confusión los tanto el modelo Rando Forest Classifier como SVM obtuvieron un valor similar en falsos negativos, el cual es un valor de importancia en este ejercicio, el valor fue 3 para ambos modelos. 

