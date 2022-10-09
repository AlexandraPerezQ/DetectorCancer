# DetectorCancer
ML para detector de cáncer
Se realiza el codigo para detectar cancer de mama con los datos tomados de Wisconsin Diagnostic Breast Cancer (WDBC)
1) número de identificación
2) (M = maligno, B = benigno)
3-32)

Se calculan diez características de valor real para cada núcleo celular:

a) radio (media de las distancias del centro a los puntos del perímetro)
b) textura (desviación estándar de los valores de la escala de grises)
c) perímetro
d) área
e) suavidad (variación local en longitudes de radio)
f) compacidad (perímetro ^ 2 / área - 1.0)
g) concavidad (severidad de las porciones cóncavas del contorno)
h) puntos cóncavos (número de porciones cóncavas del contorno)
i) simetría
j) dimensión fractal ("aproximación a la línea de costa" - 1)

La media, el error estándar y el "peor" o mayor (media de los tres valores más grandes) de estas características se calcularon para cada imagen,
resultando en 30 características. Por ejemplo, el campo 3 es Radio medio, campo 13 es Radius SE, el campo 23 es Worst Radius.

Todos los valores de características se recodifican con cuatro dígitos significativos.

Se cambia M por -1 y B por 1 , para los datos de training y test. 

Se utiliza 5 modelos para la deteccion, los parametros de evaluacion seran la Exactitud y la Sensibilidad pues esta metrica indica la capacidad de poder detectar correctamente la enfermedad entre los enfermos.
Con SGDClassifier se tiene exatitud del 90% y sensibilidad del 91%
Con KNeighborsClassifier se tiene exatitud del 92% y sensibilidad del 95%
Con DecisionTreeClassifier se tiene exatitud del 92% y sensibilidad del 92%
Con RandomForestClassifier se tiene exatitud del 95% y sensibilidad del 95%
Con SVM se tiene exatitud del 92% y sensibilidad del 94%

Basado en los resultados se selecciona el mejor modelo de exactitud y sensibilidad que corresponde al RandomForestClassifier con 95% en ambos parametros considerando que estamos detectando una enfermedad la sensibilidad alcanza un 95% que indica la capacidad de poder detectar correctamente la enfermedad entre los enfermos.

Adicionalmente se realiza tambien validacion cruzada para verificar que la exactitud del modelo no tienda a solo datos del train sino una evaluacion en 10 veces con diferentes datos de la data y se alcanza el 96% con el modelo elegido  RandomForestClassifier. 
