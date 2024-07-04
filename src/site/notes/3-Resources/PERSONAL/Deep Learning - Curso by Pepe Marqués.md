---
{"dg-publish":true,"permalink":"/3-Resources/PERSONAL/Deep Learning - Curso by Pepe Marqués/","title":"Deep Learning - Curso by Pepe Marqués","noteIcon":""}
---


Ver también: [[0-Inbox/Probabilistic and Inductive Reasoning - Diego\|Probabilistic and Inductive Reasoning - Diego]][^1]

![[DeepLearningI.pdf]][^2]

---

Hay cursos hechos a partir de papers científicos, de hace 10 años o más.
También hay enlaces en las diapos a los papers en ese momento.
La teoria en general del deep learning se queda hasta 2018, hasta transformers. Más reciente es más difícil.
Las redes convolucionales están siendo superadas o complementadas por nuevos enfoques y modelos más avanzados y complejos. Modelos máscomplejos como las [[Deep Neural Networks\|Deep Neural Networks]], y [[Recursive Neural Networks\|Recursive Neural Networks]]. También los [[Transformers\|Transformers]] y mecanismos de atención. Las [[GANs\|GANs]] y modelos de difusión, que van más allá de las típicas tareas de clasificación.

Asignatura de ML el año que viene, a Pepe le gustó mucho.

**Books to Read**
1. [Getting started with deep learning by Andrew Ng (Coursera)](https://www.coursera.org/learn/neural-networks-deep-learning)
2. [Neural Networks and Deep Learning by Michael Nielsen](http://neuralnetworksanddeeplearning.com/)
3. [Deep Learning by Ian Goodfellow, Yoshua Bengio, and Aaron Courville](https://www.deeplearningbook.org/)
4. [Machine Learning Yearning by Andrew Ng (text)](http://www.mlyearning.org/)
5. [Artificial Intelligence: A Modern Approach by Stuart Russell and Peter Norvig](http://aima.cs.berkeley.edu/)
6. [Bayesian Reasoning and Machine Learning by David Barber](http://web4.cs.ucl.ac.uk/staff/D.Barber/textbook/031210.pdf)](https://www.springer.com/gp/book/9783030622283)

---

# Deep learning, por qué se usa y aplicaciones

Viene del [[0-Inbox/Machine Learning\|Machine Learning]], el cual solo es útil en pequeños datasets, pero no es escalable conforme añadimos más datos.

Con las Deep Neural Networks si que hay escalabilidad, más performance a mayores datos.

Aplicaciones del Deep Learning:
- Conducción autónoma (absolutamente todo, motion planing)
- Detección de objetos (encontrar las metricas necesarias para buen rendimiento, importante entender)
- Segmentación de imagenes (dividir las imágenes en partes, en clases)
- Reconstrucción de escenas (a partir de imagenes con varias posiciones estimar profundidades)
- Interacción robot-humano (reconocimiento de audio, voz...)

# Qué es una red neuronal

Como sabemos, en el [[Machine Leaning\|Machine Leaning]] hay [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#^ec2qi\|supervised y unsupervised learning]].

El objetivo es crear *funciones* que se ajusten a los datos.
ue la *predicción* dado el size de la casa, el precio sea el más ajustado posible.
Es obligatorio tener *datos* de entrenamiento, si ellos no se puede hacer nada.

Tenemos entradas, neuronas intermedias y salidas de un modelo.
(Puede haber infinitas de lo que sea, no ha límite)

Las entradas pueden ser cualquier característica, como el tamaño de la casa, el número de habitaciones, etc.

En el caso de una neurona, todas esas entradas van a esa neurona.

---

**Binary classification**[^3]

- tenemos  imagen, queremos ver si hay gato o no.
- Imagen -> Valor de entrada:  Cogemos valores de pixeles (64x64x3) -> 12288 valores de entrada
- Salida: 0 o 1, si hay gato o no.
- Notación:
	- m: número de ejemplos de entrenamiento, número imagenes
	- N_x: número de entradas
	- labeled data: (x, y)
	- x pertenece a R^N_x
	- y pertenece a {0, 1}
- Entrenamiento:
	- Vectorizar: Poner los datos en vectores para acelerar

- Mi ejemplo 1, la primera imagen, será X^(1)

- X = [x^(1), x^(2),..., x^(m)]
	- Dimensión: N_x x m
	- Cada x^(i) es un vector de 12288 valores
	- X.shape = (12288, m)

- Y = [y^(1), y^(2),..., y^(m)]
	- Dimensión: 1 x m
	- Y.shape = (1, m)

- Esto anterior será el dataset de entrenamiento, esquema principal

- 


Logistic regression

- Seguimos con el ejemplo
- Dada la imagen, queremos saber la probabilidad de que haya un gato: P(y=1|x)
- Parámetros de la red (asumimos 4 entradas, 1 neurona, 1 predicción)
	- w: vector de pesos, 4x1 en este caso  (weights). Su tamaño es Nx, número de entrada.
	- b: bias, 1x1, pertenece a R

- Para cada pixel un peso. (*1 en la libreta espaitec*)
	- W = [w1, w2, w3, w4]
	- Lo que llega a la 1a neurona es W^T * X + b = Z

- Sigmoid function, cuando son 2 clases se usa, en este ejemplo se usa en la neurona del medio y la de salida. Más adelante se usa solo en la de salida.
	- A = σ(Z) = 1 / (1 + e^(-Z))
l objetivo es saber los mejores parámetros w y b para que la predicción sea lo más acertada posible, por lo que se irán probando diferentes valores.

- Forward propagation

	- Loss function: calcula la diferencia entre el ground trh y la predicción. Fórmula
		- Hay muchos tipos (un cojón), según la aplicación. Se van diseñando nuevas constantemente.
		- L(y_hat, y) = 1/2 * (y_hat - y)^2
			- Esto dice lo buena que es la prediccion respecto al ground truth
			- A partir de esto se llega a L(y_hat, y) = - (y * log(y_hat) + (1 - y) * log(1 - y_hat))

	- Cost function: media de todas las loss functions, coste global
		- J(w, b) = 1/m * Σ(L(y_hat, y))
			- el sumatorio es de i=1 hasta m
		- Se busca minimizar esta función

- Backward propagation

- Gradient descent: algoritmo para minimizar la función de coste. Se updatean los valores de los pesos y bias.
	- w:= w - learning_rate * dJ(w, b / dw
	- b:= b - learning_rate * dJ(w, b) / db

	- learning_rate también como alpha
	- Según el tamaño de los pasos, quizás no se puede llegar al mínimo global. Si da saltos muy grandes, se pasará siempre de largo. Si son muy pequeños, el entrenamiento será muy lento.   Es un hiperparámetro que se puede ajustar (es fundamental para el tiempo de entrenamiento).
	- El objetivo es ir disminuyendo el coste global, la loss function.


---
DESCANSO
- Es fundamental entender lo anterior, es la base, que aunque pueda ser pesado. Es la base para saber si se puede mejorar algo.
---


Computation graph

Forward propagation -> predicción

- J(A, B, C) = 3(A + BC)
	- Funcion de coste, esto es un ejemplo
	- u = BC
	- v = A + BC
	- J = 3v


Como volvemos atras, como aprendemos

- Derivatives
	- dJ/dv = 3   ->  J increase 3 times v  (1 step backpropagation)
	- dJ/da = dJ/dv * dv/da -> Chain rule (2 steps backpropagation)

- Ejemplo
	- Entradas -> Z = X1W1 + X2W2 + b  -> y_hat = σ(Z) la predicción -> f(y_hat, y) loss function   (forward propagation)
	- dz = df/dz = df(y_hat, y) / dz = df / dy_hat * dy_hat / dz
	- Luego habría otro paso para llegar a los pesos y bias (W1, W2, b), con dW y db
	- Esto el framework lo hace solo, no es tan esencial, lo que programamos nosotros es el forward propagation, con el loss incluido, y el framework se encarga del backward propagation.


Volvemos al forward propagation

- Quizás tenemos 20 hiperparámetros, hay que tunearlos
- El modelo lo haces tú (jeje)
- Evitamos bucles for, usamos numpy, te lo hace en un momento.


---

**Todo en pseudocódigo**

- AVISO: Está hecho sin vectorizar, usando bucles for, para entenderlo mejor.

```python
J = 0
dw1 = 0
dw2 = 0

for i in range(m):
    # Forward propagation
    Z(i) = Wt * X(i) + b
    a(i) = σ(Z(i))
    J += y(i) * log(a(i)) + (1 - y(i)) * log(1 - a(i))
    dz(i) = a(i) - y(i)
    dw1 += X1(i) * dz(i)
    dw2 += X2(i) * dz(i)
    db += dz(i)

J /= m
dw1 /= m
dw2 /= m
db /= m
```

Ahora cambiamos un par de cosas
El objetivo es quitar los bucles for usando vectorización. Dan una velocidad de entrenamiento mucho mayor.

Si tengo 1 millon de parámetros, con bucles for etc, sin vectorizar una iteración tardaria unos 450ms. Con vectorización, 1-3ms. Encima con la GPU, más chetado aún.

Final code -> 1 iteración. Esto lo hace todo de una.


```python
z = np.dot(w.T, X) + b
A = G(z)
dw = 1/m * X * dz.T
db = 1/m * np.sum(dz)

W = W - learning_rate * dw
```

# Ahora se viene lo chido (redes neuronales)

==PASAR A MARIO EXPLICADO FACILITO (ingeniero aeroespacial FALLIDO TREMENDAMENTE)==

- Single NeuronNN  (p11)
- Varias hidden layers, varias outputs, etc.
- ![alt text](/img/user/3-Resources/PERSONAL/image.png)
- Input de 4, hidden layer 1 de 2, hidden layer 2 de 2, output de 1
- La función sigmoide se aplica en las 4 de las hidden layeres y el output
- PESOS:
	- W[1]: 2x4 (2 neuronas de la hidden layer 1, 4 de la input)
	- W[2]: 2x2 (2 neuronas de la hidden layer 2, 2 de la hidden layer 1)
	- W[3]: 1x2 (1 neurona de la output, 2 de la hidden layer 2)
	- b[1]: 2x1 (2 bias de la hidden layer 1, 1 por neurona)
	- b[2]: 2x1 (2 bias de la hidden layer 2, 1 por neurona)
	- b[3]: 1x1 (1 bias de la output)


Forward propagation
Primer layer
- $Z[1] = W[1] * X + b[1]$
	- cuando no tenemos Z1 o Z2... es que lo metemos todo en una matriz
	- X son las entradas
- $A[1] = G(Z[1])$

Segundo layer
- $Z[2] = W[2] * A[1] + b[2]$
	- $A[1]$ es la salida de la primera hidden layer

Funcones de activación
- Hy muchas, la SigmoidFunction solo se usará cuando queremos hacer prediccones binarias, con 2 clases. Fue de las primeras, pero ya casi no se usa.
- Ls que se usan actualmente son:
	- ReLU: max(0, x)
	- tanh: se usa siempre antes que la sigmoid: (e^z - e^-z) / (e^z + e^-z):
	- Leaky ReLU: 0.01x si x < 0, x si x >= 0

- Las funciones de activación son siempre no lineales, si no, no tiene 'salsa'.

# Pytorch: FCNN from scratch

- Es un framework. Solo funciona en Python.
- Otros populares son:
	- TensorFlow, funciona con C++ y tiene más cosas
	- TensorRT, de Nvidia
- Es importante saber varios, al menos 2.

- pagina 14 presentación, implementación de una red neuronal desde 0 en Pytorch
- ![alt text](/img/user/3-Resources/PERSONAL/image-1.png)
- Clase DENSEBlock, es un layer concreto de la red, independiente del resto
  - init
  	- linear: input units, output units
		- dropout, para cada iteración la probabilidad de borrar una neurona, esto ayuda a que no haya overfitting, que no dependa el modelo de la información de una sola neurona, obligamos a que todas las neuronas sean importantes. Se suele empezar sin dropout, y si hay overfitting, se añade.
		- Relu, función de activación, se la aplicamos
	- forward
		- ...
- Net  (producto global)
	- init
		- metemos los diferentes denseblocks
		- flatten, pasamos el input a un vector,  es lo mismo que el reshape que sale en forward

# Digits recognition

[Digits_Recognition.ipynb - Google Drive](https://drive.google.com/file/d/1P-Cjgbl_9UiRxCVePXo4qLBOYq7CCgi1/view?usp=sharing)
Dudas entre si hace falta hacer el flatten para pasar de imagen a lineal,
Este ejemplo hacerlo sin convoluciones.
Intentos de superar un 97% de accuracy.

[^1]: Esto se debe a que muchos de los conceptos de este curso están relacionados con la asignatura de fundamentos de IA, durante el documento, cuando es interesante, se han enlazado partes de esta asignatura o de otras que puedan ayudar a entender mejor todo.
[^2]: PDF descargado del grupo de whatsapp del Asti
[^3]: Primer ejemplo red neuronal de 1 entrada y una salida.
