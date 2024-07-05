---
{"dg-publish":true,"permalink":"/3-Resources/PERSONAL/Deep Learning - Curso by Pepe Marqués/","title":"Deep Learning - Curso by Pepe Marqués","noteIcon":""}
---


Recursos:
- ==[[0-Inbox/Neural Networks, Deep Learning, (Recursos para aprender)\|Neural Networks, Deep Learning, (Recursos para aprender)]]==
- [[0-Inbox/Probabilistic and Inductive Reasoning - Diego\|Probabilistic and Inductive Reasoning - Diego]]

![[DeepLearningI.pdf]][^1]

La teoria en general del deep learning se queda hasta 2018, hasta transformers. Más reciente es más difícil.
Las redes convolucionales están siendo superadas o complementadas por nuevos enfoques y modelos más avanzados y complejos. Modelos máscomplejos como las [[Deep Neural Networks\|Deep Neural Networks]], y [[Recursive Neural Networks\|Recursive Neural Networks]]. También los [[Transformers\|Transformers]] y mecanismos de atención. Las [[GANs\|GANs]] y modelos de difusión, que van más allá de las típicas tareas de clasificación.

Asignatura de ML el año que viene, a Pepe le gustó mucho.

# Deep learning, por qué se usa y aplicaciones

Tiene más escalabilidad que el [[Machine Leaning\|Machine Leaning]] normal, ya que a mayores datos se tiene más performance, cosa que no pasa con el otro, ya que se queda estancado en cierto punto y solo es útil en datasets pequeños.

![Pasted image 20240705154216.webp](/img/user/_Archivos/Pasted%20image%2020240705154216.webp)

Aplicaciones del Deep Learning:
- Conducción autónoma (absolutamente todo, motion planing)
- Detección de objetos (encontrar las metricas necesarias para buen rendimiento, importante entender)
- Segmentación de imagenes (dividir las imágenes en partes, en clases)
- Reconstrucción de escenas (a partir de imagenes con varias posiciones estimar profundidades)
- Interacción robot-humano (reconocimiento de audio, voz...)

# Introducción

[[0-Inbox/Redes Neuronales\|Redes Neuronales]]
[[0-Inbox/Activation functions\|Activation functions]]

- **EJEMPLO CON BINARY CLASSIFICATION**[^2]
	- Dada una imagen, ver si hay gato o no.
	- Entradas (N_x):
		- Píxeles de la imagen
		- En este caso (64x64x3) -> 12288 valores de entrada
	- Salidas (y):
		- 0 o 1

- Para realizar el entrenamiento hay que vectorizar, convertir los datos en números.

- Teniendo en cuenta la [[0-Inbox/Redes Neuronales#Notación\|notación]], tenemos el siguiente **dataset de entrenamiento**
	- $X = [x^{(1)}, x^{(2)}, \ldots, x^{(m)}]$
		- x^(i) es un vector con todas las características de cada imagen (Dimensión N_x, en este caso 12288)
		- m es la cantidad de imagenes
		- Por tanto, dimensión: N_x·m
			- X.shape = (12288, m)
	- $Y = [y^{(1)}, y^{(2)}, \ldots, y^{(m)}]$
		- y^(i) es el resultado, 0 o 1, da la ground truth
		- m es la cantidad de imagenes.
		- Por tanto, dimensión 1·m
			- Y.shape = (1, m)

- Predicción?   Logistic regression
	- Queremos ver P(y=1|x), dado una imagen, probabilidad de que sea un gato.
	- Tenemos en cuenta los [[0-Inbox/Redes Neuronales#Parámetros de una red Neuronal\|Parámetros de una red Neuronal]]
	- Si suponemos una red neuronal de 4 entradas, 1 neurona, 1 salida...
	- $W = [w1, w2, w3, w4]$
	- b será 1x1

- Para cada pixel un peso. (*1 en la libreta espaitec*)
	- Lo que llega a la 1a neurona es W^T * X + b = Z

- En este caso usaremos la [[0-Inbox/Sigmoid activation function\|Sigmoid activation function]]

- Objetivo del proceso:
	- Ir encontrando los mejores parámetros w y b para la mejor predicción posible.

- **Forward propagation**:
	- Forma parte del entrenamiento del modelo.
	- Es todo el proceso en el que se mapea un input a un output. Se tienen diversos hiperparámetros y hay que tunearlos.
	- Evitamos bucles for con esto, usamos numpy
	- ==¿?==...

	- **Loss function**
{ #d28fx}

		- Calcula la diferencia entre el ground truth y la predicción hecha con los parámetros w y b en cada momento.
		- Según la aplicación se suele diseñar esta función.
		- $L(\hat{y}, y) = \frac{1}{2} * (\hat{y} - y)^2$
			- Cuanto más cercano a 0, mejor la predicción respecto al ground truth
		- $L(\hat{y}, y) = - (y \log(\hat{y}) + (1 - y) \log(1 - \hat{y}))$
			- Se llega con la anterior ecuación.

	- **Cost function**
		- Consiste en la media de todas las media de todas las loss functions. Es la que se busca minimizar.
		- $J(w, b) = \frac{1}{m} \sum_{i=1}^{m} L(\hat{y}^{(i)}, y^{(i)})$

	- Pasos para una red neuronal de L capas
		- $a[0] = x$
		- For each layer $l$ (from 1 to $L$):
			- Compute $z[l] = W[l] \cdot a[l-1] + b[l]$
			- Apply *activation function*: $a[l] = \sigma[l](z[l])$
				- La función no lineal


		- Input layer:
			- Input: $x$
			- Weights (hidden layer): $W_1$
			- Biases (hidden layer): $b_1$
			- Compute $z_1 = W_1 \cdot x + b_1$
			- Apply activation function: $a_1 = \sigma(z_1)$
		- 2nd to 3rd layer:
			- Weights (output layer): $W_2$
			- Biases (output layer): $b_2$
			- Compute $z_2 = W_2 \cdot a_1 + b_2$
			- Apply activation function: $a_2 = \phi(z_2)$


- **Gradient descent**
	- Es el algoritmo cuyo objetivo es ir reduciendo constantemente la cost function.
	- Lo hace actualizando constantemente los valores de los pesos y el bias. ($:=$ es el simbolo para 'actualizar')
	- $w:= w - \alpha \frac{\partial J(w, b)}{\partial w}$
	- $b:= b - \alpha \frac{\partial J(w, b)}{\partial b}$
	- Es importante el hiperparámetro del *tamaño de los pasos*, ya que si es muy grande, se pasará siempre, y si es pequeño, será muy lento el entrenamiento.

# INBOX [[2024-07-03\|2024-07-03]] - Falta organizar

**BACKWARD PROPAGATION**


- Es volver atrás, aprender

- Derivatives
	- dJ/dv = 3   ->  J increase 3 times v  (1 step backpropagation)
	- dJ/da = dJ/dv * dv/da -> Chain rule (2 steps backpropagation)

- Ejemplo
	- Entradas -> Z = X1W1 + X2W2 + b  -> y_hat = σ(Z) la predicción -> f(y_hat, y) loss function   (forward propagation)
	- dz = df/dz = df(y_hat, y) / dz = df / dy_hat * dy_hat / dz
	- Luego habría otro paso para llegar a los pesos y bias (W1, W2, b), con dW y db
	- Esto el framework lo hace solo, no es tan esencial, lo que programamos nosotros es el forward propagation, con el loss incluido, y el framework se encarga del backward propagation.

- J(A, B, C) = 3(A + BC)
	- Funcion de coste, esto es un ejemplo
	- u = BC
	- v = A + BC
	- J = 3v



**PSEUDOCODIGO**:

```python
z = np.dot(w.T, X) + b
A = G(z)
dw = 1/m * X * dz.T
db = 1/m * np.sum(dz)

W = W - learning_rate * dw
```


- El siguiente está hecho sin vectorizar, usando bucles for, para entenderlo mejor. Será más lento.
- Velocidad de entrenamiento del modelo.
	- 1 millon de parámetros con bucles for, sin vectorizar -> 450ms
	- Con vectorización, 1-3ms.
	- Con vectorización y GPU estaría más chetado aún.

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




**REDES NEURONALES CHIDAS**

- Single NeuronNN  (p11)
- Varias hidden layers, varias outputs, etc.
- ![alt text](/img/user/3-Resources/PERSONAL/image.png)
- Input de 4, hidden layer 1 de 2, hidden layer 2 de 2, output de 1
- La [[0-Inbox/Sigmoid activation function\|Sigmoid activation function]] se aplica en las 4 de las hidden layeres y el output
- PESOS Y BIASES:
	- W[1]: 2x4 (2 neuronas de la hidden layer 1, 4 de la input)
	- W[2]: 2x2 (2 neuronas de la hidden layer 2, 2 de la hidden layer 1)
	- W[3]: 1x2 (1 neurona de la output, 2 de la hidden layer 2)
	- b[1]: 2x1 (2 bias de la hidden layer 1, 1 por neurona)
	- b[2]: 2x1 (2 bias de la hidden layer 2, 1 por neurona)
	- b[3]: 1x1 (1 bias de la output)

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

# Footnotes

[^1]: PDF descargado del grupo de whatsapp del Asti
[^2]: Primer ejemplo red neuronal de 1 entrada y una salida.
