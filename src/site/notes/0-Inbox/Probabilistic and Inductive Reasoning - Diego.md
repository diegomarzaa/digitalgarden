---
{"dg-publish":true,"permalink":"/0-Inbox/Probabilistic and Inductive Reasoning - Diego/","title":"Probabilistic and Inductive Reasoning - Diego","noteIcon":""}
---


# Introducción

1. Incertidumbre en Robótica:
	- Entornos:
		- Controlados: Donde las condiciones son predecibles y hay menos variabilidad.
		- Sociales: Donde la interacción con humanos y otros elementos impredecibles aumenta la incertidumbre.
	- Sensores: Existe una amplia variedad, cada uno con limitaciones y precisiones específicas, afectando la percepción del entorno.
	- Actuadores: La ejecución de acciones puede no ser siempre precisa, introduciendo variabilidad en el resultado esperado.
	- Modelos del Mundo: Se basan en representaciones internas del entorno y acciones posibles, pero son aproximaciones que no capturan totalmente la realidad.

2. Manejo de la Incertidumbre:
	- Ejemplo de la Gripe y Fiebre: No se puede asumir directamente que fiebre equivale a gripe sin considerar otros factores; aquí la lógica tradicional es limitada.
	- Grados de Creencia/Incertidumbre: Se introduce la idea de trabajar con niveles de confianza en lugar de certezas absolutas, buscando un equilibrio. Son aproximaciones necesarias para el razonamiento. A veces no hay plan garantizado para alcanzar un objetivo, pero se tiene que actuar. Se deberían poder comparar los diferentes planes y obtener los diferentes grados de creencia.
	- Teoría de Probabilidad: Se usa para manejar cuantitativamente los grados de creencia, asignando valores entre 0 y 1 para representar la incertidumbre basada en el conocimiento disponible.
	- Teoría de la Utilidad: Representa las preferencias y objetivos deseados, permitiendo evaluar opciones según su valor esperado.
	- Teoría de la Decisión: Combina la Teoría de Probabilidad y la Teoría de la Utilidad, sirviendo para tomar decisiones bajo incertidumbre.
	- Ejemplo: Elegir la mejor ruta al aeropuerto considerando múltiples factores y riesgos.

3. Aplicación Práctica: Máxima Utilidad Esperada (MEU):
	- Concepto: La MEU busca maximizar la utilidad promedio, teniendo en cuenta tanto las probabilidades de diferentes eventos como sus desenlaces deseados o no.
	- Proceso de Decisión: La elección se basa en evaluar las opciones disponibles, sus probabilidades asociadas, y las utilidades de sus posibles resultados para encontrar el mejor equilibrio.

# Reglas básicas de probabilidad

- Posibilidad de que ocurra un evento:
	- Valor entre 0 y 1
- Suma probabilidades de todos los posibles resultados = 1
- **Regla del producto**
	- $P(a \cap b) = P(a|b) \cdot P(b) = P(b|a) \cdot P(a)$
	- $= P(a) \cdot P(b)$ si son independientes
- **Regla de la cadena**
	- $P(a_1, a_2, ..., a_n) = P(a_1|a_2, a_3, ..., a_n) \cdot P(a_2, a_3, ..., a_n)$
		- Se puede volver a aplicar la regla al resto
			- $P(a_2, a_3, ..., a_n) = P(a_2|a_3, ..., a_n)$
	- Se puede escribir como productorio
		- $(\prod_{i=1}^{n} P (a_i | a_{i+1}, ..., a_n))$
- Full joint probability (can be seen as the “knowledge base”)
- Probability of disjunction: 
	- La probabilidad de que ocurra al menos uno de dos eventos es la suma de sus probabilidades menos la probabilidad de su intersección.  (Un ‘or’)
	- Esto se conoce como la regla de la suma de Kolmogorov: P(A∪B)=P(A)+P(B)−P(A∩B)
- Full joint probability: 
	- Es la probabilidad de que ocurran todos los eventos al mismo tiempo. (can be seen as the “knowledge base”)
- Inferencia probabilística: 
	- Es el proceso de determinar la probabilidad de un evento dado el conocimiento de otros eventos. Las proposiciones de consulta son las declaraciones sobre las que queremos inferir la probabilidad.
- ==Query==: 
	- Una consulta probabilística es una pregunta sobre la probabilidad de un evento dado el conocimiento de otros eventos
	1. Probability queries:
		Y = query variables
		E = evidence variables
		P (Y|E = e)
- ==Marginalization==
	- This is the process of determining the probability distribution for a subset of the given variables.  It involves summing or integrating over the unwanted variables to derive the marginal probability. The formula is:
	- $P(Y) = \sum P(Y,Z) = \sum P(Y|Z) \cdot P(Z)$
	- Here, P(Y) is the marginal probability of Y, P(Y,Z) is the joint probability of Y and Z, and P(Y∣Z) is the conditional probability of Y given Z
- Normalization
	- It is a scaling technique applied to data that seeks to bring all values within a particular range. In the context of probabilities, normalization ensures that the sum of all probabilities equals 1. This is often achieved by dividing by the sum of all probabilities or by a constant. The formula in the context of conditional probability could be:
	- $P(\text{{cavity}}|\text{{toothache}}) = \alpha \cdot P(\text{{cavity and toothache}})$
	- Here, α is a normalization constant that ensures the sum of all probabilities equals 1.
- ==Generalization of Inference Procedure==
	- **Query Variable (X)**: This is the variable for which we want to compute the probability distribution. In this case, it's `Cavity`.
	- **Evidence Variables (E)**: These are the variables for which we have observed values. In this case, it's `Toothache`.
	- **Unobserved Variables (Y)**: These are the variables for which we don't have observed values. In this case, it's `Catch`.
	- **Probability of X given E**: This is the probability of the query variable `X` given the evidence `E`. It can be computed using the formula:
		- $P(X|e) = \alpha P(X, e)$
		- Here, $P(X, e)$ is the joint probability of `X` and `e`, and $\alpha$ is a normalization constant to ensure that the sum of all probabilities is 1.
	Problem with using directly the joint distribution: does not scale well with the number of variables and the number of possible values of each variable.

## Exercise:

Given these probabilities
![9649511251b1147b5f41bb12146c5c50_MD5.webp](/img/user/_Archivos/9649511251b1147b5f41bb12146c5c50_MD5.webp)

Compute:
- P(cavity OR toothache) 
- P(cavity OR toothache)=P(cavity)+P(toothache)−P(cavity AND toothache)
- P(cavity), an example of unconditional or marginal probability. We can use marginalization or conditioning
- P(cavity|toothache)
	- An example of conditional probability. 
	- We can use the product rule for normalization
	- ![abba0e100aa339d9dcff6aa24051d1c8_MD5.webp](/img/user/_Archivos/abba0e100aa339d9dcff6aa24051d1c8_MD5.webp)

General inference procedure using query variables X, evidence variables E with values e, and remaining unobserved variables Y.

Problem with using directly the joint distribution: does not scale well with the number of variables and the number of possible values of each variable.

# Conditional Probabilities

- Probability of a hypothesized world state (H) that depends on a condition (given the sensory observations) (E)
- p(H|E)
- **PROSECUTOR'S FALLACY**
	- Conditional probabilities are not conmutative. It consists of not knowing the difference between p(H|E) and p(E|H).
	- Concretamente, confundir la funcion de likelihood con la probabilidad a posteriori.
	- Ejemplos:
	1. p(lluvia | nubes) o p(nubes | lluvia):
		- Mayor: p(nubes | lluvia). La lógica detrás de esto es que siempre que llueve, es un hecho que hay nubes en el cielo (la probabilidad de que haya nubes dado que está lloviendo es muy alta), pero la presencia de nubes no garantiza que vaya a llover (así que la probabilidad de lluvia dado que hay nubes es menor).
	2. p(habla francés | nacido y criado en París) o p(nacido y criado en París | habla francés):
		- Mayor: p(habla francés | nacido y criado en París). Si bien existen personas que hablan francés sin haber nacido ni sido criadas en París, la probabilidad de que alguien hable francés si se sabe que nació y se crió en París es muy alta. Por otro lado, hay muchas personas en todo el mundo que hablan francés pero no nacieron ni se criaron en París.
	3. p(soltero | estudiante universitario) o p(estudiante universitario | soltero):
		- Mayor: p(soltero | estudiante universitario). La mayoría de los estudiantes universitarios, debido a su rango de edad y etapa de vida, tienden a ser solteros. Sin embargo, no todos los solteros son estudiantes universitarios, ya que el estado civil de soltero abarca a una población mucho más grande y variada en cuanto a edad y ocupación.
	4. p(entendiendo la regla de Bayes | leer este libro) o p(leer este libro | entendiendo la regla de Bayes):
		- Mayor: p(entendiendo la regla de Bayes | leer este libro). Es razonable asumir que leer este libro (que explícitamente trata sobre probabilidad y la regla de Bayes) aumentaría significativamente la probabilidad de entender esta regla. Por otro lado, entender la regla de Bayes no necesariamente implica que se haya leído este libro específico, ya que hay múltiples fuentes disponibles para aprender sobre el tema.
- Más ejemplos
	- $P(\text{{cavity}}|\text{{toothache}}) = \frac{P(\text{{cavity and toothache}})}{P(\text{{toothache}})}$
	- [Probabilidad Condicional](https://docs.google.com/document/d/130FB8HWhznnujqkK9Z6oAgsU0RLWShaff1vUXbDQhNw/edit#heading=h.lvj57p4gick1)
- En python: [Probability — Think Bayes](https://allendowney.github.io/ThinkBayes2/chap01.html#conditional-probability)

# *Laws of Probability* + Bayes Rule

PYTHON + LONGER EXPLANATION: [Probability — Think Bayes](https://allendowney.github.io/ThinkBayes2/chap01.html#laws-of-probability)

![Pasted image 20240418213835.webp|578](/img/user/_Archivos/Pasted%20image%2020240418213835.webp)

- Theorem 2: Multiply the Theorem 1 by P(B) both sides.
- Theorem 3: Given that P(A and B) is conmutative, we apply Therem 2 to both options, so moving the parts of the formula we can obtain whatever we need.


![Pasted image 20240405211451.png|455](/img/user/_Archivos/Pasted%20image%2020240405211451.png)

![Pasted image 20240405211700.png|385](/img/user/_Archivos/Pasted%20image%2020240405211700.png)

# Bayes rule + Gaussians for perception (likelihood, prior, posterior...)

- ![Pasted image 20240405220824.png|367](/img/user/_Archivos/Pasted%20image%2020240405220824.png)

- ![94ed8ce59f6e5364f2d79e1073dc3e18_MD5.webp](/img/user/_Archivos/94ed8ce59f6e5364f2d79e1073dc3e18_MD5.webp)
- ![Pasted image 20240419104859.webp|376](/img/user/_Archivos/Pasted%20image%2020240419104859.webp)

- [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#Likelihood (Verosimilitud)\|#Likelihood (Verosimilitud)]]
- [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#Prior (Probabilidad previa)\|#Prior (Probabilidad previa)]]
- [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#Posterior (Probabilidad posterior)\|#Posterior (Probabilidad posterior)]]

- ==MIRAR PRÁCTICA DE PYTHON==

- EXAMPLES
	- El camuflaje permite a un animal pasar inadvertido ante la presencia de un depredador, por ejemplo. Este hecho se puede relacionar con la inferencia Bayesiana en el sentido siguiente. El observador (el depredador) podría estar interesado en la detección de una posible presa en un cierto lugar, y puede tener una cierta probabilidad a priori de que la presa esté presente. Por otro lado, la función de likelihood depende de la calidad de observación. Sin camuflaje, la función de likelihood tendría un valor mayor para la hipótesis de que la posible presa esté presente (detección). Sin embargo, el camuflaje dificultaría esta distinción, y las hipótesis "presente" y "ausente" serían mucho más equiprobables (función de likelihood más parecida a una distribución uniforme) o incluso podría ser mayor la probabilidad de "ausente". Por tanto, para una misma distribución a priori, un likelihood más uniforme no aportaría más información que la propia probabilidad a priori, no reduciría la incertidumbre al depredador, gracias a lo cual el animal camuflado podría pasar más fácilmente desapercibido.
		- ![Pasted image 20240405214608.png|409](/img/user/_Archivos/Pasted%20image%2020240405214608.png)
	- ![Pasted image 20240405205855.webp|409](/img/user/_Archivos/Pasted%20image%2020240405205855.webp)
	- ![Pasted image 20240405213000.png|409](/img/user/_Archivos/Pasted%20image%2020240405213000.png)
	- Ejemplo de *percepción del lenguaje*, dificultad, ya que si 2 palabras suenan igual (likelihood), y tienen la misma probabilidad de cuadrar en el contexto de la frase (prior), tendrán un posterior parecido. O incluso la subjetividad de la persona en base a lo que quiere escuchar afectará al prior.
	- ![Pasted image 20240405220528.png|450](/img/user/_Archivos/Pasted%20image%2020240405220528.png)
	- La inferencia Bayesiana pueden aplicarse tanto de forma continua como discreta.

- EJERCICIO EJEMPLO
	- [[Bayesian_models_of_perception_and_action_v3.pdf#page=50&selection=97,0,99,41|Bayesian_models_of_perception_and_action_v3, page 50]]
	- prior
		- Representa la probabilidad de cada hipótesis antes de considerar la evidencia actual (observación del color, forma, tamaño de la maleta). Cambia con el tiempo a medida que van saliendo más maletas.
		- El conocimiento previo viene dado por la cantidad de personas en el avión, y por la cantidad de maletas iguales que la nuestra. Pero como ya he dicho, no se basa en observaciones actuales.
		- En este ejemplo, siendo H1 "la maleta es nuestra",  p(H1) = 0.01  y  p(H2) = 0.99
		- Aunque *cambia según el numero de maleta*, y para la 86ª maleta: P(H1) = 1/15 ≈ 0.07,    P(H2) = 14/15 ≈ 0.93
	- likelihood
		- Es la probabilidad de que tengamos una observación determinada (la maleta es igual que la nuestra), asumiendo que se cumple una cierta hipotesis
		- Las hipotesis en este caso pueden ser "es nuestra" o "no es nuestra".
		- No cambia entre la 1ª y 86ª maleta. Es *constante*
		- P(observation|H1) = 1   si sabemos que es nuestra, obvio
		- P(observation|H2) = 0.05
	- Posterior
		- Es la probabilidad que tiene una hipotesis de ser cierta teniendo en cuenta la observación y el conocimiento previo de la hipotesis  (prior x likelihood).
		- Se *actualiza tras incorporar la evidencia* que ha modificado al prior
	- hypothesis
		- h1 la maleta es mia
		- h2 la maleta no es mia
	- observation   /   evidence
		- El color, tamaño, forma de la maleta siendo
		- ==No sé bien la diferencia entre las 2 palabras, es lo mismo, no?==
	- En el ejemplo, lo que cambia es la probabilidad a priori (prior probability) de que la maleta sea tuya. Este cambio en el prior afecta directamente a nuestra confianza final (probabilidad a posteriori) en que la maleta sea la nuestra, a pesar de que la observación (forma, tamaño y color de la maleta) y la verosimilitud (likelihood) sean exactamente las mismas para la maleta 1 y la 86
	- Para la primera maleta, el prior de que sea tuya es muy bajo (0.01), porque hay 100 maletas en total y es poco probable que la tuya salga la primera. Por tanto, aunque la observación coincida con las características de tu maleta (likelihood alta), la confianza final (posterior) sigue siendo baja (0.168).
	- Sin embargo, para la maleta 86, el prior ha cambiado significativamente. Ahora quedan sólo 15 maletas, así que la probabilidad a priori de que la siguiente sea la tuya es mucho mayor (1/15 ≈ 0.07). Por tanto, al combinar este prior más alto con la misma observación y likelihood, obtenemos una confianza final (posterior) mucho mayor (0.588).
	- Este cambio en el prior refleja cómo nuestra expectativa o creencia previa se va actualizando a medida que adquirimos nueva información (en este caso, el número de maletas que han salido). Aunque la evidencia directa (la apariencia de la maleta) no cambie, nuestro contexto y expectativas sí lo hacen, y esto influye en nuestra percepción y toma de decisiones.
	- Este es un principio clave de la inferencia Bayesiana: nuestra creencia final (posterior) no sólo depende de la evidencia actual, sino también de nuestras creencias y expectativas previas (prior). A medida que adquirimos nueva información, vamos actualizando nuestras creencias de forma dinámica.

## Likelihood (Verosimilitud)

- **p(observation | world state hypotesis)**
- "Cuán probable es observar los datos experimentales específicos dados ciertos parámetros o un estado del mundo"
- La likelihood del estado del mundo (dadas las medidas)"  L(estado_del_mundo ; datos).
- The *flatter* the likelihood function, the less we learn from our senses. If the likelihood function is perfectly flat, then the observer has learned nothing from the observation (Example camouflage).    So it changes as we get more information through senses over time.
- **No Es Una Probabilidad Propiamente Dicha**: Un aspecto crítico de la likelihood es que, aunque su fórmula pueda parecerse a una probabilidad, no está necesariamente normalizada para sumar uno como las probabilidades. En cambio, la likelihood puede tomar cualquier valor positivo y se usa para comparar relatos distintos de los parámetros en base a los datos observados.

- No se debe decir "la likelihood de las observaciones", ya que las observaciones son fijas y la incerteza/suposiciones se modelan sobre el estado del mundo o los parámetros, no sobre los datos observados.
- Also depends on *background knowledge* like the prior. The observer needs to have an (implicit) understanding of the process by which different world states generate sensory data.
- Ejemplos:
	- Probability that your friend would give rise to the visual image, compared to the probability that another person would give rise to the same visual image.
	- Sonido Pájaros: La observación en este caso sería acústica, sería una función continua
	- Acercar las manos a las orejas y mirar cuidadosamente los labios del hablante son estrategias que modifican las probabilidades de likelihood y que mejoran la calidad de nuestras inferencias bajo condiciones de ruido.

- ![Pasted image 20240419102915.webp|319](/img/user/_Archivos/Pasted%20image%2020240419102915.webp)

## Prior (Probabilidad previa)

- *P(H)*: Representa lo que sabes o esperas sobre las diferentes hipótesis (expectation grounded in previous experience) antes de observar los datos actuales (new evidence).

- Ejemplos
	- *Variable prior*?? If the observer sees a caution sign that indicates a slippery surface, their prior may change to favor the wet hypothesis. So we sometimes write the prior as p(world state | B), where B again signifies information obtained through previous experience.
	- En el ejemplo de *encontrar al amigo*, puede variar segun si está en nuestro pueblo o está fuera del país, cosa que no ocurre con el likelihood.
	- *Sonido pájaros*: La imagen sería el prior, ya que es la base, pero no ofrece nada más, simplemente de donde hay posibilidad de que venga el sonido. Y combinandolo con la observación acústica, sabríamos, combinando el continuo con la posicion del pajaro más proximo, cual ha sido.
	- *También podría ser* completamente flat el prior, sin ninguna informacion, y que la observación fuera la imagen y el posterior las posibles posiciones de los pajaros, y luego calcular otra vez en base a esto pero con el sonido, de forma recursiva

- ![Pasted image 20240419102802.webp](/img/user/_Archivos/Pasted%20image%2020240419102802.webp)

## Posterior (Probabilidad posterior)

- *P(H|D)* combina la información del likelihood y del prior para dar una nueva probabilidad a la hipótesis después de haber visto los datos.
- Esencialmente, actualiza nuestras creencias sobre el estado del mundo dada la nueva evidencia.

- Calculated using *Bayes’ theorem*.
- They sum to 1 if they are *normalized*. Without normalizing, it is called *"protoposterior"*.

- Union de las 2 gaussianas anteriores
- ![Pasted image 20240419104813.webp|269](/img/user/_Archivos/Pasted%20image%2020240419104813.webp)

**a) Define a range of possible values (s values):** Think of 's' as possible values a variable (like the position a thrown ball will land) could take. We discretely hypothesize where we think this variable will lie within a range—from 0 to 40 in this case—and check every 0.2 units (like checking every few steps between 0 and 40).

**d) Normalization:** Since multiplication may not result in a properly scaled probability distribution, normalize the resulting distribution by ensuring its total sum equals 1. This makes it a valid probability distribution.


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/0-inbox/probabilistic-and-inductive-reasoning-diego/#tqi5" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



- **MEDIA DEL POSTERIOR** 

</div></div>


# Generative model and inference

![](https://lh7-eu.googleusercontent.com/5b6CfrPd9m52Axldas5hivb9IfMojcQsc_CdM817x4bM3jVkjL6CXZkLdx2s63LKcsMqQE1zf0uxMP9wsVmClaOxlC_RpojjB75KbkaMJmWGrevQAdQ4Yt1EHTkxUgKCJOfewBUcyDyka7mMkStLOg)

![Pasted image 20240406122746.png|434](/img/user/_Archivos/Pasted%20image%2020240406122746.png)

![4f8510545534e868f45203881f2fca80_MD5.webp](/img/user/_Archivos/4f8510545534e868f45203881f2fca80_MD5.webp)

## Generative model

- Establece las bases sobre las cuales se realizará la inferencia posterior.
- Encapsula nuestro entendimiento o supuestos sobre la naturaleza del proceso que estamos analizando. Como se comportan las cosas de forma natural.

## Inferencia

- Es el proceso en el que el agente hace deducciones sobre el estado del mundo usando el modelo generativo.
- Se actualizan las creencias sobre el estado actual del mundo.
- Formado por el prior, likelihood y posterior.

- Percept: Input to the inference process
- Observation: Output of the inference process.
- Decision: Can incorporate external rewards and costs.
	- For example, it can be much more costly to mistake a wet floor for dry than the other way round. As a consequence, even with a posterior probability of 81.8% that the floor is dry, it might still be a good decision to walk more carefully

# MAP and ML

ML and MAP both aim to estimate parameters but differ in their consideration of prior knowledge.

 El valor que hace maximo la probabilidad es, al tratarse de una gaussiana, su media.

- **ML (Maximum Likelihood)**
	- Su objetivo es buscar el parametro que máximiza la función de likelihood.   La clase (y) que maximiza la probabilidad de los datos observados (x) dada esa clase.
	- $\hat{y} = \arg \max_y P(X | y)$
	- ![d16033475ef0faa8c27232813a3f3d76_MD5.png](/img/user/_Archivos/d16033475ef0faa8c27232813a3f3d76_MD5.png)
	- the ML estimate typically aligns with the condition that directly reflects the observed value under the assumption of data veracity and model correctness
	- Suppose a robot’s sensor measures a distance (x_{obs}). If the measurement error model follows a *Gaussian distribution, the ML estimate of the distance would be exactly (x_{obs})*, assuming no further information about the likelihood distribution other than it peaks at the observed value.
	- ML is best suited for large data scenarios where the sheer volume of data can "speak for itself".

- **Maximum a posteriori (MAP) criterion**
	- Busca el parámetro que maximiza la distribución del posterior, que incorpora el prior y likelihood, a diferencia de el ML que solo usa el likelihood.
	- $\hat{y} = \arg \max_y P(y | X)$
		- max: función máxima
		- argmax: valor de la variable que hace que la funcion sea maxima
	- Dará resultado a la hipótesis con más probabilidad.
	- No necesitamos normalizar la distribución posterior, ya que los máximos seguirán siendo máximos
	- Shines in contexts where data may be sparse or noisy yet substantial prior knowledge is available, making it particularly valuable in fields like robotics, where operational parameters often have well-understood distributions based on design specifications or historical performance
	- DE LA PRÁCTICA:
		- En la parte BT, cuando se pregunta MAP, hay un par de respuestas bastante comunes que parecen mejorables. Por un lado, algunos señalan que dicha estimación sería "aproximadamente X". Intuyo que dicen lo de "aproximadamente" por inspección visual de las gráficas. Pero, ¿y si se quiere una cuantificación? Por otro lado, muchos lo cuantifican usando np.max(·) o np.argmax(·), que no está mal, pero hay una forma mejor sabiendo que la distribución es una gaussiana de la que conocemos sus parámetros.


- **MEDIA DEL POSTERIOR**
{ #tqi5-}

	- Precisión de likelihood y prior:
		- $J_l = \frac{1}{\sigma_x^2}$
		- $J_p = \frac{1}{\sigma_d^2}$
	- Pesos:
		- Reflejan la contribución relativa de la información del likelihood y del prior al conocimiento combinado en el posterior. Un 'w' grande indica que la medida del sensor influye más en la estimación posterior debido a una mayor precisión en comparación con el prior.
		- $w = \frac{J_l}{J_l + J_p}$
		- $1 - w = \frac{J_p}{J_l + J_p}$
	- También tenemos
		- $x_{obs}$
		- $\mu_{prior}$
	- Aplicar los pesos
		- La media del posterior, ( $\mu_{post}$ ), se calcula como: $\mu_{post} = w \cdot x_{obs} + (1 - w) \cdot \mu_{prior}$
		- La fórmula de la media del posterior trata efectivamente la estimación final como un compromiso entre dos creencias: lo que nos dice la observación actual y lo que anticipábamos basados en el conocimiento previo. Aquí, la precisión actúa como un regulador que determina cuánto peso debe darse a la nueva información en comparación con las creencias existentes.

- EJEMPLO EXAMEN
	- la hipotesis de interes es la distancia a la pared, d_hyp
	- ![Pasted image 20240420134012.webp](/img/user/_Archivos/Pasted%20image%2020240420134012.webp)
	- ![Pasted image 20240420133855.webp](/img/user/_Archivos/Pasted%20image%2020240420133855.webp)
	- ![Pasted image 20240420133828.webp](/img/user/_Archivos/Pasted%20image%2020240420133828.webp)

# Bayesian Networks

- RECURSOS
	- MIRAR MONTY HALL PROBLEM PRÁCTICA
	- [[Artificial Intelligence A Modern Approach.pdf#page=780&selection=0,0,0,10|Artificial Intelligence A Modern Approach 4th Edition (Stuart Russell, Peter Novig) (Z-Library), page 780]]

[Bayesian networks](http://en.wikipedia.org/wiki/Bayesian_network) are a powerful inference tool, in which nodes represent some **random variable** we care about, edges **represent dependencies** and a lack of an edge between two nodes represents a **conditional independence**.

Representan relaciones causales mediante un grafo acíclico dirigido (DAG).
Las redes Bayesianas son especialmente útiles para modelar procesos de toma de decisiones y realizar inferencia bajo incertidumbre.

- Variables pueden ser binarias o no serlo.

- **CPT (Cond. Prob Tables)**
	- Shows dependencies
	- each node in a Bayesian network will have a CPT that describes the influence of its parents on that node
	- table where each column represents the parent (or self) values except for the last column which represents the probability of the variable taking on that value given its parent values
- CPT EXAMPLE
	- Suppose ( X ) can take values ( x_1, x_2 ) and has two parents ( Y ) and ( Z ), each of which can take the values ( y_1, y_2 ) and ( z_1, z_2 ) respectively. A simple CPT for ( X ) might look something like this:
	- Each row shows the probability distribution of ( X ) for a given combination of ( Y ) and ( Z ).

| Y   | Z   | ( P(X=x_1 \| Y, Z) ) | ( P(X=x_2 \| Y, Z) ) |
| --- | --- | -------------------- | -------------------- |
| y1  | z1  | 0.1                  | 0.9                  |
| y1  | z2  | 0.4                  | 0.6                  |
| y2  | z1  | 0.7                  | 0.3                  |
| y2  | z2  | 0.2                  | 0.8                  |

- Independence of nodes
	- Dado F y H (es decir, sabemos si el paciente sufre de gripe y/o hayfever), S (Season) no proporciona información adicional sobre C (Congestion). Esto se describe con la independencia condicional: P(C | F, H, S) = P( C | H, F)
	- Esto significa que una vez que conoces el estado de la gripe y la fiebre del heno del paciente, conocer la estación no proporciona información adicional sobre la probabilidad de que el paciente tenga congestión. Por lo que:  C S  |  F, H

- INFERENCE
	- the process of calculating the probabilities of certain unknown variables given some known variables
	- **Initialization**: Start with a Bayesian network where each node (representing a variable) knows its relationship (conditional probabilities) with its connected nodes.
	- **Observation**: Input the values of the observed variables into the network.
	- **Propagation**: Use an inference algorithm to update the beliefs (probabilities) about the hidden variables based on the observed data.

- Compute Joint Distribution
	- ![Pasted image 20240425191210.webp|264](/img/user/_Archivos/Pasted%20image%2020240425191210.webp)
	- The probability of this entire configuration is calculated as $P(i1, d0, g2, s1, l0) = P(i1) \cdot P(d0) \cdot P(g2 | i1, d0) \cdot P(s1 | i1) \cdot P(l0 | g2)$
	- General formula: $P(I, D, G, S, L) = P(I) \cdot P(D) \cdot P(G | I, D) \cdot P(S | I) \cdot P(L | G)$

- Zero prob
	- En la red bayesiana de la parte UI creo que muchos habéis puesto directamente probabilidad 0 (o 1) en algunas entradas de algunas tablas de probabilidad. Como comentamos en clase, dada la naturaleza estocástica y la incertidumbre asociada a muchos procesos reales, no parece buena práctica usar probabilidades extremas (a menos que los correspondientes eventos sean realmente *imposibles* o *seguros*). Ver [1] o [2] sobre alguna discusión al respecto

	[1] [https://stats.stackexchange.com/questions/507349/bayesian-probability-of-zero](https://stats.stackexchange.com/questions/507349/bayesian-probability-of-zero)

	[2] [https://stats.stackexchange.com/questions/588424/problems-with-zero-probability-events-in-bayesian-networks](https://stats.stackexchange.com/questions/588424/problems-with-zero-probability-events-in-bayesian-networks)

## Full joint vs bayesian network

- FULL JOINT DISTRIBUTION
	- Dadas n variables binarias, hay 2^n - 1 combinaciones posibles (la última se puede sacar sabiendo que el total será 1)
	- No se asume ninguna independencia entre las variables y se modela la distribución completa conjunta, simplemente consideraríamos todas las posibles combinaciones de valores entre las variables**
	- Crecimiento exponencial
	- Computacionalmente, es muy grande para almacenar, y costoso para manipular
    - Cognitivamente, es imposible obtener tantos número de expertos humanos
    - Estadísticamente, necesitaríamos grandes cantidades de datos para aprender de distribuciones de datos.

	- ![Pasted image 20240420174345.webp|196](/img/user/_Archivos/Pasted%20image%2020240420174345.webp)
	- ![Pasted image 20240420165036.webp|230](/img/user/_Archivos/Pasted%20image%2020240420165036.webp)
	- 4x2x2x2x2  -  1 = **63 combinaciones (con redundantes)**

- BAYESIAN NETWORK
	- **PGM** (Probabilistic graphical models)
	- **Factorización y parametrización compacta**
		- Cálculo de probabilidades ideal para situaciones en las que múltiples factores contribuyen a un resultado o estado observado.
		- Se ayuda de la estructura de los grafos dirigidos en base a los padres de cada uno
		- ![Pasted image 20240420172236.webp](/img/user/_Archivos/Pasted%20image%2020240420172236.webp) = P(Season=spring) · P(Flu=false | Season=spring) · P(Hayfever=true | Season=spring) · P(Congestion=true | Flue=false, Hayfever=true) · P(MusclePain=true | Flu=false)
	- Se **reducen los parámetros** necesarios
	- $\text{Total parameters} = \sum_{i=1}^{n} (s_i - 1) \times m^{k_i}$
		- where ( n ) is the total number of nodes, ( s_i ) is the number of states for node ( X_i ), and ( m^{k_i} ) is the number of parameter combinations for the parents of ( X_i ).
	- Interpretación más Fácil: Las independencias condicionales claras y explícitas facilitan entender cómo las variables se influencian entre sí.
	- Inferencia Más Rápida: Al factorizar la distribución conjunta y solo enfocarse en las dependencias necesarias, los cálculos para la inferencia se simplifican enormemente.
	- Construcción Flexible: Pueden ser diseñados por expertos humanos que entienden las dependencias del dominio o aprendidos automáticamente a partir de datos, utilizando técnicas como el aprendizaje estructural.

	- Para el ejemplo dado:
		- ![Pasted image 20240420174345.webp|196](/img/user/_Archivos/Pasted%20image%2020240420174345.webp)
		- P(S): Season.
			- Se necesitan (4 - 1) x 1 = 3
			- No tiene padre por lo que no afecta el 1
		- P(F | S)
			- (2 - 1) x 4
			- Padre con 4 combinaciones
		- P(H | S):
			- (2 - 1) x 4 = 4
			- Padre con 4 combinaciones
		- P(C | F, H)
			- (2 - 1) x 4 = 4
			- Tiene 2 padres con 2 combinaciones cada uno
		- P(M | F):
			- (2 - 1) x 2  =  2
			- Padre con 2 posibles combinaciones
		- Suma de todo:
			- 3 + 4 + 4 + 4 + 2 = **17 combinaciones no redundantes de la red bayesiana reparametrizada**

## ==Conditional probability with continuous variables==

Podemos tener nodos cuyos padres son variables continuas, discretas, o una mezcla de ambas. Cuando esto ocurre, en lugar de una tabla de probabilidad, usamos una función de distribución (por ejemplo, una distribución Gaussiana).

### Ejemplo 1: Distribución Normal Condicional

Consideremos la probabilidad condicional $P(C | \text{Subsidy} = \text{true}, \text{harvest}$):
$P(C | \text{Subsidy} = \text{true}, \text{harvest}) = N(c; a \cdot \text{harvest} + b, \sigma^2) ]$

- Vemos que la media depende de una de las variables, harvest que es continua.
- Es una distribucion normal (gaussiana) con media `a·harvest + b` y varianza `sigma^2`
- Queremos asociar las probabilidades de la variable C con los padres.
- En la grafica, la distribución normal sería c el eje x, y la probabilidad en el eje y. La media es `a·harvest + b`, y la varianza `sigma^2`
- a y b son los parametros de la distribucion que encontrariamos.

Si subsidy fuera false, la media seria menor, si no hay subsidio, el coste sería mayor


- El desglose para la probabilidad, la formula de toda la vida: 1/(sqrt(2*pi*sigma^2)) * e^(-(x - a*harvest + b)^2 / 2*sigma^2)   (no sé si está bien)

- Si dibujamos la gráfica en 3D... (mirar Documento)

- Cuantos parametros para representar la bayesiana? 3 (a, b, sigma) * 2 (según subsidy) = 6


- Esta distribución se llama linear Gaussian.

### Ejemplo 2

- Buys en funcion del coste P(Buys|Cost)   (grafica 2 en documento)
- Uso de la función de densidad de probabilidad acumulada.
- Usaremos Sigmoid(x) = integral de -infinito a infinito de N(s, 0.1) ds
- P(Buys|Cost) = 1 - Sigmoid((c - mu) / sigma)
- Vemos que con esto, cuando el coste es alto, la probabilidad de compra es baja, y cuando el coste es bajo, la probabilidad de compra es alta.

### Ejemplo car insurance complejo

- Redes Bayesianas pueden ser muy complicadas, con muchos nodos y conexiones.  (EJEMPLO EN el AI A Modern Approach)
- Hay inputs y outputs.
- También hay variables ocultas, cuyos variables no se pueden observar directamente, pero que influyen en otras variables.

## Práctica 4 (+ Student Network)

- CONCEPTOS IMPORTANTES DE LA PRÁCTICA:
	- probabilidad, probabilidad conjunta y probabilidad condicional, y sus propiedades, incluyendo el teorema de Bayes
	- Dado dataframe en pandas, cálculo de probabilidades, incluyendo la conjunta y la condicional, con sentencias de python sencillas
	- Función gaussiana de una variable, codificación en numpy, evaluación sobre varios valores de esta o varias medias o varianzas en forma de vector.
	- Prior, likelihood, posterior.  Cálculo con código para la gaussiana.  Poder mostrar sus funciones
	- Maximum likelihood y maximum a posteriori  (ML, MAP), calcularlas matematicamente y numericamente con python.

	- Definir red bayesiana con pomegranate, dadas variables y tablas probabilidad (condicional).
	- Saber Caclular diferentes probabilidades de una red bayesiana(conjunta, marginal, condicional)
	- Dada una red bayesiana, traducir una pregunta planteada en lenguaje natural a una consulta probabilística
	- Dada la descripción de un problema de complejidad moderada que implica variables aleatorias y probabilidades, tengo confianza en formalizar esta descripción humana en una red Bayesiana.


![](https://uol.de/f/2/_processed_/a/a/csm_Koller_Fig_3.3_Bayesian-student-network_01_2013b4f2ff.png)

```md
"... now consider a slightly more complex scenario. The student’s grade, in this case, depends not only on his intelligence but also on the difficulty of the course, represented by a random variable _D_ whose domain is _Val(D) = {easy, hard}_. Our student asks his professor for a recommendation letter. The professor is absentminded and never remembers the names of her students. She can only look at his grade, and she writes her letter for him based on that information alone. The quality of her letter is a random variable _L_, whose domain is _Val(L) = {strong, weak}_. The actual quality of the letter depends stochastically on the grade. (It can vary depending on how stressed the professor is and the quality of the coffee she had that morning.)  
We therefore have five random variables in this domain: the student’s intelligence (_I_), the course difficulty (_D_), the grade (_G_), the student’s SAT score (_S_), and the quality of the recommendation letter (_L_). All of the variables except _G_ are binary-valued, and _G_ is ternary-valued. Hence, the joint distribution has 48 entries.  
As we saw in our simple illustrations ..., a Bayesian network is represented using a directed graph whose nodes represent the random variables and whose edges represent direct influence of one variable on another. We can view the graph as encoding a generative sampling process executed by nature, where the value for each variable is selected by nature using a  
distribution that depends only on its parents. In other words, each variable is a stochastic function of its parents.  
Based on this intuition, perhaps the most natural network structure for the distribution in this example is the one presented in the figure (left). The edges encode our intuition about the way the world works. The course difficulty and the student’s intelligence are determined independently, and before any of the variables in the model. The student’s grade depends on both of these factors. The student’s SAT score depends only on his intelligence. The quality of the professor’s recommendation letter depends (by assumption) only on the student’s grade in the class. Intuitively, each variable in the model depends directly only on its parents in the network. We formalize this intuition later." (Koller & Friedman, Probabilistic Graphical Models, 2009, p.52f)
```


2x2x3x2x2 = 48 entries

Each entry in this distribution represents the probability of a specific combination of values across these five variables

  Val(D) = <d0, d1> = <easy, hard>

  Val(I) = <i0, i1> = <non smart, smart>

  Val(G) = <g0, g1> = <A, B+C> = <excellent, good+average>

  Val(S) = <s0, s1> = <low score, high score>

  Val(L) = <l0, l1> = <strong_letter, weak_letter>

## Knowledge Engineering

El proceso de Knowledge Engineering implica tomar decisiones críticas sobre qué variables incluir y cómo modelar sus interacciones. No todas las variables tienen un impacto significativo, y algunas pueden tener una relevancia limitada dependiendo del contexto. La decisión sobre si modelar una variable como continua o discreta es crucial y puede variar según la especificidad del problema.

Cuando quieres modelar una red bayesiana a partir de un problema, que hacer??

Es simplemente una idea en la que no profundizamos, es saberlo

Picking variables
- Clarity test
- Hidden variables
- Not every relevant variable is included
- Reasonable domain of values
- (Qué rango de valores en una variable continua es razonable? Quizás renta discretizarla)


Picking structure

Picking probabilities
- Zero probability
	- Un aspecto clave discutido es el tratamiento de eventos improbables. Es vital no asignar una probabilidad de cero a un evento raro, ya que esto puede afectar significativamente las predicciones del modelo.
- Orders of magnitude
- Relative values
- Sensitivity analysis

Naive Bayes, PathFinder, Performance, Adoption... Medical diagnosis: case study  (libro)

## Dynamic Bayesian Networks (DBNs)

Caso concreto. Pueden cambiar con el tiempo.

Ejemplo tratamiento diabetico // Ejemplo seguir la posicion de un robot  // Comprender una secuencia de palabras

En resumen, lo que pasa ahora depende de lo que ha pasado antes.

## Concepts

Perception: Observar el mundo
..Modelo de sensor: Como se relaciona el mundo con las observaciones
Belief state: Tengo una confianza de un estado
..Modelo de transición: Como cambia el estado de un tiempo a otro
Predicción de la evolución: Que pasará en el futuro

## States and observations

State X_t (unobservable)
- de esto va el tema, predecir cosas no observables  (tiempo discreto)

Evidence E_t (observable)
- lo que llega por los sensores, lo que se puede medir, el sensor puede ser muy bueno, pero no perfecto, esto afectará a la varianza de la gaussiana.


Ejemplo diabetes:
E_t = {MeasuredBloodSugar_t, PulseRate_t, ...}
X_t = {BloodSugar_t, StomachContents_t, ...}

## Transition model

P(X_t | X_{0:t-1})



Ejemplo:

X € {a, b, c}
X_0 = a
X_1 = b
X_2 = a
X_3 = b

a -> b -> a -> b

P(X_4 | X_{0:3}=a,b,a,b) = P(X_4 | X_3=b)




Suposicion de Markov:

- Solo depende del estado anterior, no de todos los anteriores. Esto simplifica el modelo, hace los problemas más manejables.
- P(X_t | X_{0:t-1}) = P(X_t | X_{t-1})

## Sensor (observation) model

P(E_t | X_{0:t}, E_{0:t}) = P(E_t | X_t)

## Complete joint distribution

- Viendo la estructura, ver las dependencias condicionales

P(X_0:t, E_1:t) = P(X_0) * productorio de k=1 a T  .....

## Markov assumption

- Se puede aumentar el orden de la cadena de Markov, que dependa de los 2 anteriores, o de los 3 anteriores, etc.

Ejemplo localizacion robot

X_t = {X_t, Y_t, v_xt, v_yt}

*Bateria*, puede afectar a la velocidad, puede depender de velocidades previas.   Parece que la suposicion de Markov no se cumple.

Para arreglarlo, actualizamos el estado

X_t = {X_t, Y_t, v_xt, v_yt, B_t}  (agregando el nivel de bateria)

Lo malo es que se aumenta la complejidad del modelo, pero habrá una mejor predicción.

## Affordances

- Affordances: Lo que un objeto permite hacer con él.
- Relación segun pares de entradas, se puede predecir la otra (Acciones, objetos, efectos)
- Si empujo y veo el efecto de que se desplaza rapido, vemos que es un objeto ligero

## SLAM

Simultaneous Localization and Mapping

## En python ==IMPORTANTE==
{ #v7iel}


`marginal_prob(X)` computes the marginal probability for a set of variables X given as a Python dictionary of the name of variables (the keys, as strings) and their values.

Write a python function `probBA()` that computes the probability P(B|A=a_1)


Ejemplo:

$P(A=a_0, B=b_1) = P(A=a_0 | B=b_1) \cdot P(B=b_1) = 0.7 \cdot 0.8$

Respuesta:

$P(B| A=a_1) = \frac{P(B, A=a_1)}{P(A=a_1)}$

```python
prob_marginal({'A': 'a_0', 'B': 'b_1'})
```

```python
def probBA():
	num_b0 = marginal_prob({'A': 'a_1', 'B': 'b_0'})
	num_b1 = marginal_prob({'A': 'a_1', 'B': 'b_1'})

	den = marginal_prob({'A': 'a_1'})

	return (num_b0 / den,  num_b1 / den)
```

## Exercise 3 coins

- Mirar hoja ProbabilisticReasoningExercises

There are three coins in a bag. The first one is biased towards heads, with 75% probability of heads occurring if the coin is flipped. The second one is fair, so a 50% chance of heads occurring. The third coin is biased towards tails, and has a 25% probability of coming up heads. Assume we cannot identify which coin is which simply by looking at or touching them.


(a) We pull out a coin from the bag, we flip it and it comes up heads. Let the random variable C{1,2,3} represent the identity of the coin, with probability of heads being <0.75, 0.50, 0.25>, respectively. Obtain the likelihood.

| C | `Likelihood(C, H) = P(X=H \| C)` | P(C) | P(C \| X=H) |
|----|----|--|--|
| 1 | 3/4 | 1/3 | 3/4*1/3 / E |
| 2 | 2/4 |	1/3 |	1/2*1/3 / E |
| 3 | 1/4 |	1/3 |	1/4*1/3 / E |

C(con sombrerito)_MLE = argmax P(X=H \| C=c) = argmax {3/4, 2/4, 1/4}

# Inductive knowledge and reasoning: Machine Learning

Machine Learning:

- Algoritmos que mejoran de la experiencia E, con respecto a una tarea T y una medida de rendimiento P.
- Tareas *inductivas* ya que se *generaliza a partir de ejemplos*.

Tipos de machine learning y tipos de tareas/problemas que queremos resolver con el ML

- **Supervised Learning**:
{ #ec2qi}

	- Modelo entrenado con un training set formado por pares de datos con etiquetas (Xi, Yi).
	- Tenemos unas *características* (features, entrada al modelo) que decimos que son x y una etiqueta (class label, salida del modelo) que será la y.
{ #bfzn-}

	- El modelo aprende a mapear inputs con outputs. Lo importante es la [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#^84yxy\|generalización]]

	- **Classification**:
		- Categorización de datos a clases predefinidas, características discretas. Por ejemplo Spam/No Spam. Puede ser binario o multiclase. Se usan matrices de confusión para medir el performance

	- **Regression**:
		- En este caso se predice un valor continuo en lugar de clases predefinidas. Por ejemplo, predecir el valor de un plátano solo viéndolo. El label es un valor continuo.
		- Un problema de regresión se puede convertir en uno de clasificación discretizándolo.

- **Unsupervised Learning**:
	- El algoritmo intenta encontrar patrones en datos sin etiquetas, sin saber de antemano la respuesta correcta o los grupos a los que pertenecen los datos.

	- **Clustering**:
		- Técnica cuyo objetivo es dividir un conjunto de datos en grupos (clusters) de tal manera que los elementos dentro de cada grupo sean más similares entre sí y más diferentes a los elementos de otros grupos.
		- Sabemos las características (x), pero no el cluster label, que es lo que se generará (y), el cluster label es el identificador que se dará a cada uno de los grupos, y forma parte de la salida, no del entrenamiento.

- Semi-Supervised Learning:
	- A form of unsupervised learning where the data itself provides the supervision. The model is trained to predict any part of its input from any other part.
	- Imagen manzana, dividida en 4 partes, las desordenamos, ahora hay que predecir como ordenarlas.    Este ejemplo no era supervisado en el sentido que te dan el dato y no la etiqueta, pero si que era supervisado cuando se genera la etiqueta a partir de los propios datos

- Reinforcement Learning:
	- Models learn to make decisions by receiving *rewards or penalties* for the actions they take.
	- It's up to the agent to decide which actions were more responsible for it.

- **Ejemplo examen:**
	- Is this True??? Estimating the age of a person, in years y ∈ R+, from images of their face, can be solved with *supervised* machine learning; in particular, it can be stated as a *classification* task.   ->   False
	- La primera parte de la frase es cierta porque, efectivamente, se puede usar aprendizaje supervisado para asociar una imagen de la cara de una persona (directamente la imagen o las características que de ella se puedan extraer) con la edad correspondiente. Con múltiples imágenes y su correspondiente etiqueta tendríamos pues los pares de entrenamiento (xi, yi), donde xi sería una imagen (o las características) y yi la etiqueta (la edad correspondiente).
	- Lo que es falso en la frase es que se podría formular como una tarea de clasificación, puesto que *la clasificación asume que los posibles valores de las etiquetas yi son discretos (categorías)*, mientras que aquí se indica que las etiquetas son las edades como números reales (podríamos tener que una persona tenga 13.7 años, otra 76.08, etc.). En estos casos, el problema se plantea como una tarea de *regresión*. Si en lugar de etiquetas reales tuviéramos *categorías discretas* de edad (e.g. “bebé”, “niño”, “adolescente”, “joven”, “adulto”, “anciano”), entonces sí tendría sentido plantearlo como un problema de clasificación.


Conceptos de ML

- *Generalization*
{ #84yxy}

	- Es la capacidad del modelo para aplicarse efectivamente a ejemplos externos al conjunto de datos sobre el que fue entrenado.
- *Overfitting*
	- Sucede cuando el modelo se ajusta demasiado a los datos de entrenamiento, por lo que no generaliza bien en nuevos ejemplos
	- Cuantos más grados de libertad tenga el modelo, más fácil es que ocurra.
- Underfitting
	- Modelo es demasiado simple para capturar la estructura de los datos. No ha sido suficientemente entrenado.

- Bias-Variance Dilemma
	- El *sesgo* es un error de predicción sistemático debido a suposiciones simplificadas del modelo
	- La varianza se refiere a la cantidad que la predicción de un modelo cambiaría si se usaran *diferentes conjuntos de datos de entrenamiento*. Un modelo con alta varianza es muy sensible a variaciones específicas en el conjunto de entrenamiento, lo que puede llevar a *overfitting*.  Ejemplo:   Baja varianza y mayor bias   vs   pequeña varianza y menor bias.
	    - ![Pasted image 20240501180513.webp|184](/img/user/_Archivos/Pasted%20image%2020240501180513.webp)
	- $Err(x) = (E[f(x)] - f_{grandtruth}(x))^2 + E[(f(x) - E[f(x)])^2] + \sigma^2$
    - $Err(x) = Bias^2 + Variance + Irreducible Error$

- El **Efecto Clever Hans**
	- Cuando un modelo aprende a hacer predicciones correctas por las razones incorrectas, generalmente debido a sesgos o patrones inadvertidos en los datos de entrenamiento.
	- puede llevar a modelos que funcionan bien durante la evaluación pero fallan en situaciones reales debido a que no han aprendido realmente la tarea deseada.
	- Este efecto obtiene su nombre de un caballo en el siglo 20 que supuestamente podía resolver problemas matemáticos, pero en realidad respondía a las señales inconscientes de su dueño.


- ==Modelos de aprendizaje, ejemplo con imágenes. Creación de modelos==
	1. **Introducción de Datos**:
	    - Comenzamos con datos de entrada, como una imagen de una banana.
	    - Este dato inicial puede ser de cualquier tipo (no solo imágenes), como textos, valores numéricos, audio, etc.
	2. **Extracción de Características**:
	    - Del dato inicial (ejemplo, la banana), se extraen características relevantes. En el caso de la imagen, estas podrían ser características como formas, colores, tamaño, textura, etc., que se transforman en valores numéricos (características).
	    - Esta etapa es crucial porque las características extraídas alimentarán el modelo de aprendizaje automático.
	3. **Entrada en un Modelo de ML**:
	    - Los numeritos (características extraídas) se introducen en un modelo de aprendizaje automático.
	    - Este modelo procesa las características según las reglas o patrones que ha aprendido durante su entrenamiento.
	4. **Salida - Predicción**:
	    - El resultado del proceso es una predicción. Por ejemplo, el modelo podría predecir si la imagen de banana es madura, inmadura o podrida basándose en las características proporcionadas.

	Creación de modelos
		1. **Datos de Entrenamiento**:
		    - Para crear un modelo, comenzamos con un conjunto grande de datos de entrenamiento. Estos datos deben ser variados y representativos del problema real. En tu ejemplo, serían muchas imágenes de bananas en diferentes estados y condiciones.
		2. **Algoritmo de Aprendizaje**:
		    - Se selecciona un algoritmo de aprendizaje adecuado para entrenar un modelo. Este algoritmo ajustará sus parámetros internos para adaptarse lo mejor posible a los datos de entrenamiento.
		    - Ejemplos de algoritmos incluyen K-NN (K-nearest neighbors), SVM (Support Vector Machines), árboles de decisión, regresión lineal, entre otros.
		3. **Modelo**:
		    - El output del proceso de entrenamiento con un algoritmo de aprendizaje es un modelo. Este modelo encapsula lo que el algoritmo ha aprendido sobre las relaciones en los datos de entrenamiento.
		4. **Predicción**:
		    - Una vez que el modelo está entrenado, puede ser utilizado para hacer predicciones sobre nuevos datos. Por ejemplo, podría predecir la categoría de nuevas imágenes de bananas que nunca ha visto.

- ==MODELOS==
	- **Modelos Geométricos y Lógicos**: Como los árboles de decisión, que toman decisiones lógicas basadas en las características de los datos.
	- **Modelos Probabilísticos**: Como Naive Bayes, que calcula la probabilidad de que un dato pertenezca a una clase basándose en las características observadas.
	- **Otros Modelos Comunes**: Incluyen K-vecinos más cercanos (K-NN), K-means para clustering, máquinas de vectores de soporte (SVM), y regresión lineal para tendencias.

==(mira foto 25 abril)==

División conjunto de datos / cross validation
- Uno para entrenar, otro para evaluar. De forma que la evaluación no esté condicionada por el entrenamiento.

**CONFUSION MATRIX**

- performance of a predictive model on a set of test data for which the true values are known
- helping to understand not just the overall accuracy but also to see the model’s strengths and weaknesses in terms of its predictive capabilities
- dealing with imbalanced datasets. In such cases, even if a model has a high accuracy rate, the confusion matrix can reveal if that accuracy is biased towards the majority class.

|                     | Predicted Positive  | Predicted Negative  |
| ------------------- | ------------------- | ------------------- |
| **Actual Positive** | True Positive (TP)  | False Negative (FN) |
| **Actual Negative** | False Positive (FP) | True Negative (TN)  |

- **Accuracy**: $\frac{TP + TN}{TP + TN + FP + FN}$ - measures overall correctness.
- **Error rate**: 1 - Accuracy
- TPR (True Positive Rate, sensitivity) -> De todos los positivos, cuales hemos predicho que son positivos
- TNR (True Negative Rate, specificity)
- FNR (False Negative Rate)
- FPR (False Positive Rate)
- **Precision**: TP / (TP + FP). measures accuracy among predicted positive detections.
- **Recall (Sensitivity or True Positive Rate)**: $TP / (TP + FN)$. measures the ability of a model to find all the relevant cases (all actual positives).
- **F1-Score**: Es el promedio armónico de la precisión y la recuperación (recall), que equilibra ambas métricas. Se calcula como ( $2 \times \frac{precision \times recall}{precision + recall}$ ).

## Naive Bayes

Naive Bayes es un clasificador probabilístico basado en el teorema de Bayes. Es "naive" porque asume que todas las características (X_1, X_2, ..., X_n) son independientes entre sí, dada la clase.

Es por esto que la probabilidad conjunta P(X_1, X_2, ..., X_n | C) puede expresarse como el producto de las probabilidades individuales: P(x_1, x_2, ..., x_n | C) = P(x_1 | C) · P(x_2 | C) · P(x_n | C)

Usa diferentes distribuciones de probabilidad para diferentes tipos de datos:
- Distribución Bernoulli: Para características binarias.
- Distribución Multinomial: Para características categóricas (por ejemplo, conteo de palabras en un documento).
- Distribución Gaussiana: Para características continuas.

Decision criterion:
- [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#MAP and ML\|Probabilistic and Inductive Reasoning - Diego#MAP and ML]]

Ratios of likelihood, prior and posterior

- **Odds a Posteriori (Posterior Odds)**: $\frac{P(y=1 | X)}{P(y=0 | X)}$ Representa la razón de las probabilidades posteriores de las dos clases.
- **Razón de Verosimilitud (Likelihood Ratio)**: $\frac{P(X | y=1)}{P(X | y=0)}$ Es la razón entre las verosimilitudes de las dos clases.
- **Odds Previos (Prior Odds)**: $\frac{P(y=1)}{P(y=0)}$ Esta es la proporción de las probabilidades previas de las clases.

Clasificación

- Usando un criterio MAP, vemos si los odds a posteriori da mayor o menor que 1, según este número, será de una clase o de otra la predicción.

Conceptos

- Se asume que lo que *contribuye* cada feature (pixel) a la hora de clasificar una class (número) es *independiente* de lo que contribuye otro feature (píxel).
	- ![Pasted image 20240501175120.webp|249](/img/user/_Archivos/Pasted%20image%2020240501175120.webp)
- En el caso de números, podemos decir que el color de cada píxel se considera independiente del color de otro píxel en la misma imagen.
- Esto ayuda a *reducir la cantidad de computación*, pero también puede provocar que se pierdan de vista ciertos patrones importantes.
- Se asume que se sigue una *distribución Gaussiana*, con mean, standard deviation y funciones de probabilidad de densidad. $p(x_i \mid c) = \frac{1}{\sqrt{2\pi\sigma^2_{i,c}}} \exp\left(-\frac{(x_i-\mu_{i,c})^2}{2\sigma^2_{i,c}}\right)$.   La media y la desviación estándar se calculan en el entrenamiento.
- Para testear, se calculan las likelihoods y así obtener la clase más probable.

- **Respuesta Examen**:
	- El modelo Naive Bayes sirve como clasificador, pero nada impide que pueda usarse para cualquier número de clases. El modelo simplemente hace la suposición de que un conjunto de variables Xi son independientes entre sí dada otra variable Y.
	- En el caso de la clasificación, las variables Xi se corresponden con características que representan datos concretos del problema en cuestión, y Y corresponde con la etiqueta de clase.
	- Como Y puede tener múltiples valores, no solo dos, no hay nada que limite el uso del modelo para problemas de clasificación multi-clase.
	- Aunque hemos estudiado como ejemplo la aplicación de Naive Bayes para la clasificación (binaria) de correo-e como spam vs ham, podríamos aplicarlo a cualquier otro problema de clasificación. Por ejemplo, sin salir del ejemplo de correo-e, podríamos aplicarlo a clasificar los mensajes en estas cuatro categorías: “trabajo”, “ocio”, “formación” y “familia” (o sea, serían cuatro clases), en función de su contenido.

- more:
	- Aplicar el modelo gaussiano a cada "feature" de cada clase consiste en calcular la media y la varianza de las features (ya sean pixeles individuales, por columnas, etc)...
	- Luego, para un nuevo dataset, se calculará la probabilidad de cada valor de un pixel para una determinada clase (likelihood p(x|c)).
	- Será una forma de juzgar nuevas entradas basándose en como de bien (probabilidad) encajan en los patrones definidos por el set de entrenamiento.

	- This method estimates the parameters of the Gaussian distribution for each feature of each class.
	- It is based on the provided training data (Xa and Xb). Which are 2 classes for 2 different digits.
	- Xa and Xb are arrays of size n_instances (different images) x n_features (different pixels or columns...).
	- Each feature gets its own mean and standard deviation across all instances of images for each class.
	- We will get then arrays that represent the mean and standard deviation of each feature.

	- From this, we will be able to compare if a new image is more likely to belong to class A or B.

To understand the calculation for Bayesian prediction using Naïve Bayes, especially when comparing different decision rules like Maximum Likelihood (ML) and Maximum A Posteriori (MAP), and the application of Bernoulli and multinomial models, let's break down each part of the question.

- Part 1: Bernoulli Model for Spam (-) vs. Ham (+)

	Given:

	- **Vocabulary**: $\{a, b, c\}$
	- **Model parameters** (probabilities of word presence for each class):
	  - For spam (+): $\theta+ = (0.5, 0.67, 0.33)$
	  - For ham (-): $\theta- = (0.67, 0.33, 0.33)$

	### Task:
	Classify an email containing words $\{a, b\}$ but not $\{c\}$. Represented as $x = (1, 1, 0)$.

	**Likelihood Calculation - Bernoulli**:

	Considering the Bernoulli model, the likelihood is calculated by:
	$$P(x|y) = \prod \theta_i^{x_i} \cdot (1 - \theta_i)^{1-x_i}$$

	For class (+) spam:
	$$P(x|+) = (0.5)^1 \cdot (1-0.5)^{1-1} \cdot (0.67)^1 \cdot (1-0.67)^{1-1} \cdot (0.33)^0 \cdot (1-0.33)^{1-0} = 0.5 \cdot 1 \cdot 0.67 \cdot 1 \cdot 1 \cdot 0.67 = 0.224$$

	For class (-) ham:
	$$P(x|-) = (0.67)^1 \cdot (1-0.67)^{1-1} \cdot (0.33)^1 \cdot (1-0.33)^{1-1} \cdot (0.33)^0 \cdot (1-0.33)^{1-0} = 0.67 \cdot 1 \cdot 0.33 \cdot 1 \cdot 1 \cdot 0.67 = 0.148$$

	By the **ML decision rule**, we choose the class with the highest likelihood:
	$$y = \arg \max_y P(x|y) = + = \text{spam}$$

- Part 2: Applying the MAP Decision Rule

	To use the MAP decision rule, we need to know the prior probabilities of each class, $P(+)$ and $P(-)$. The decision rule becomes:
	$$y = \arg \max_y P(x|y) \cdot P(y)$$
	And the posterior odds are given by:
	$$\frac{P(+|x)}{P(-|x)} = \frac{P(x|+)}{P(x|-)} \cdot \frac{P(+)}{P(-)}$$

	To classify as spam (+) using MAP, the prior odds threshold for getting a spam classification (i.e., $\frac{P(+)}{P(-)}$) must be high enough to make $\frac{P(+|x)}{P(-|x)}$ exceed 1 when multiplied by the likelihood ratio.

- Part 3: Multinomial Model

	In a multinomial model, we use frequency counts, and the likelihood is computed based on counting occurrences of each word:

	Given:
	- For spam (+) using multinomial distribution: $\theta+ = (0.3, 0.5, 0.2)$
	- For ham (-) using multinomial distribution: $\theta- = (0.6, 0.2, 0.2)$
	- Occurrences: $x = (3$ occurrences of 'a', $1$ of 'b', $0$ of 'c'$)$

	**Likelihood Calculation - Multinomial**:

	$$P(x|+) = \binom{4}{3,1,0} (0.3)^3 (0.5)^1 (0.2)^0$$
	$$P(x|-) = \binom{4}{3,1,0} (0.6)^3 (0.2)^1 (0.2)^0$$

	Here, both $P(x|+)$ and $P(x|-)$ calculate out to be equal (0.054), showing this rare case when both classes have equal likelihoods when using frequency counts of features, leading to an ML classification as ham by default, unlike the Bernoulli model where specific presence/absence mattered more.

	**Note**: This can show differences due to how each model accounts for feature prevalence: Bernoulli model accounts for the presence/absence, and multinomial accounts for the frequency making different assumptions about the importance of frequency vs. occurrence.


- ==Training a Naïve Bayes Model for Spam Classification==

	A Naïve Bayes classifier is a probabilistic machine learning model that's particularly well-suited for binary classification tasks. Applied to a spam classification problem, it involves learning the probabilities of observing certain conditions in the data — in this case, the presence of specific words — associated with each class (spam or ham).

	Let's break down your example to see how this model can be trained using both the Bernoulli and Multinomial distributions.

- Bernoulli Naïve Bayes

	The Bernoulli model is appropriate for data where each feature is binary, indicating the presence or absence of a word. This type of model considers "success" to be the presence of a word in a document.

	- **Laplace Smoothing**:
    	- Often used to handle zero probabilities, involves adding a pseudo-count (commonly 1) to the counts of each word in each class, and a corresponding adjustment to the normalization factor (adding the size of the vocabulary, often times each weight factor, here 2 for binary).
    	- Es otra forma de introducir otro prior, que no solo dependa de los datos.
    	- Bernoulli: O = d+1 / n+2  (el 2 es pq puede estar o no estar una palabra)
    	- Categorical: O = d+1 / n+k   (k es el número de categorías posibles)
	- Esto generaliza a la m-estimate: O = (d+p_i\*m) / (n+m)




	**Parameter Calculation with Smoothing**:
	- **Spam Class (θ+) Calculation Example**:
	  - **Word a**: Present in 2 actual spam messages. With smoothing, θ+a = (2 messages with 'a' + 1 pseudo-document containing 'a') / (4 actual messages + 2 pseudo-documents) = (2 + 1) / (4 + 2) = 0.5
	  - **Word b**: Similar calculation results in θ+b = 0.67
	  - **Word c**: θ+c = 0.33

	- **Ham Class (θ-) Calculation**:
	  - Without explicit details, but with the provided final results similar smoothing applies:
	  - \[ θ- = \left(\frac{4+1}{6+2}, \frac{2+1}{6+2}, \frac{2+1}{6+2}\right) = (0.625, 0.375, 0.375) \]







- Multinomial Naïve Bayes

	The Multinomial model is a better fit for count data. Instead of just noting whether a word occurred, it counts how many times it occurs.

	- **Smoothing in the Multinomial Model**:
	  - **Word a**: Observed 5 times in spam out of 17 total words. With smoothing, θ+a = (5 count of 'a' + 1 for smoothing) / (17 total words + 3 for smoothing) = 6 / 20 = 0.3
	  - **Word b**: θ+b = 0.5
	  - **Word c**: θ+c = 0.2

	- **For Ham Class (θ-)**:
	  - Given the provided results without the raw count in the question, we apply smoothing similarly:
	  - $θ- = \left((12+1)/(20+3), (4+1)/(20+3),(4+1)/(20+3)\right) = (0.541, 0.208, 0.208)$



- Summary on Models:
	**Post-training usage:** After calculating these parameters, the model can classify new emails by calculating the probability of the email being in each class based on the presence (in Bernoulli) or count (in Multinomial) of each word, and classify the email into the class with the highest probability.

	**Choosing the Model:** Deciding between Bernoulli and Multinomial depends on whether the mere presence of a word or the frequency of words is more predictive in your specific application scenario.

	These models allow handling different kinds of data and assumptions about how word occurrence or count affects the likelihood of a message being spam or not spam. The extensions with smoothing help ensure that the classifier works well even with previously unseen features during training.


- For real valued data:   (práctica de números)
    - Gaussian distribution.
        - Univariate: Parameters to estimate: mean and standard deviation for each feature and class.
        - Multivariate: Parameters to estimate: mean vector and covariance matrix for each feature and class.
            - La media sigue siendo igual, pero la covarianza es una matriz que relaciona las variables entre sí.
            - La matriz de covarianza es simétrica, la diagonal es cada número
                - Caso 2D: $\begin{bmatrix} \sigma_{x}^2 & \sigma_{xy} \\ \sigma_{yx} & \sigma_{y}^2 \end{bmatrix}$
                    - Positive covariance with numbers: $\begin{bmatrix} 4 & 3 \\ 3 & 4 \end{bmatrix}$
                    - Negative covariance with numbers: $\begin{bmatrix} 4 & -3 \\ -3 & 4 \end{bmatrix}$
                    - Zero covariance with numbers: $\begin{bmatrix} 4 & 0 \\ 0 & 4 \end{bmatrix}$ (sale un círculo perfecto)
                    - Covariance with high values: $\begin{bmatrix} 100 & 90 \\ 90 & 100 \end{bmatrix}$
                    - Covariance with low values: $\begin{bmatrix} 0.1 & 0.09 \\ 0.09 & 0.1 \end{bmatrix}$   (sale parecido, no importa la escala de los datos)

- Is Naive Bayes Bayesian?
	- Usage of Bayes' theorem: Not really, in theory, pero en la práctica no (assumptions -> poor likelihood estimates -> recalibrated likelihoods calculating the weights)
	- Does it compute a full posterior probability?  -> No, Bayesian sería trabajar con todas las posibilidades, en este caso se trabajan con valores puntuales, no con distribuciones. ML parameter estimation -> single value, not a distribution.

## Árboles de decisión

![Pasted image 20240501182307.webp|459](/img/user/_Archivos/Pasted%20image%2020240501182307.webp)

- Motivación:
   - Distinguir entre clases. Muchos ifs xd

- 3 tipos de nodos:
	- **Root Node**: Inicia el árbol, representa la característica que mejor divide los datos.
	- **Internal Node**: Divide los datos en subconjuntos más pequeños. Criterios que vamos aplicando.
	- **Leaf Node**: Representa una clase o una decisión. No se dividen más. La decisión

- Relación con la lógica:
	- Output <=> Path1 OR Path2 OR ... Path
	- Each path: Cond1 AND Cond2 AND ... CondN  (Disyuntive normal form)


- Representation of a function that maps a vector of attribute values to an output value (= the decision)

- The decision is taken by performing a sequence of tests:
	- Starting at the root
	- Following the appropriate branch
	- Until reaching a leaf

- Internal node = test of the value of one attribute
- Leaf nodes = specify which is the output value of the function
- Feature tree (Flach) = compact way of representing a number of conjunctive concepts in the hypothesis space. The learning problem is then to decide which of the possible concepts will be best to solve the given task.


BUILDING A DECISION TREE

- recursively *partitioning* the data into subsets that are as *homogeneous* as possible

- Componentes clave
	- Homogeneidad(D)
	  - Returns True or False
		- checks if the instances in a dataset `D` are *homogeneous enough* to be labeled with a *single label*. In practice, a subset of the data is considered homogeneous if all (or most) of its examples belong to a single class or can be labeled with the same value.
	- Label(D):
		- For *classification* tasks, this function usually returns the *majority class* within the dataset `D`. This label is used to classify new data points that fall into the associated leaf in the decision tree
	- BestSplit(D, F)
		- Cual nos interesa para hacer la partición? Para una característica concreta.
		- This function determines the most informative feature from set `F` based on its ability to split data `D` effectively. The goal is to maximize the homogeneity of the resulting subgroups. For binary classification, this involves dividing `D` into subsets where ideally one group contains only positives and the other only negatives

- Medidas de cuantificación de impureza:
	- Minority Class (error rate):
		- Given by $(\min(p, 1-p))$, where $p$ is the empirical probability of the positive class. This measure bases the impurity on the proportion of misclassified examples if the subset is classified as the majority class.
	- Gini Index (Expected error):
		- Defined as $(2p(1-p))$. It represents the expected error if examples are labeled randomly according to the distributions of $p$ and $1-p$. The Gini index is particularly favored because of its sensitivity to changes in the node probabilities.
		- Si se clasificara de forma aleatoria, ese sería el error esperado. El error promedio.
		- error = $P(+|-) \cdot P(-) + P(-|+) \cdot P(+) = p(1-p) + (1-p)p = 2p(1-p)$
	- Entropy:
		- Defined as $(-p \cdot \log_2(p) - (1-p) \cdot \log_2(1-p))$. Entropy measures the expected information (in bits) needed to classify an example. It achieves its maximum when the classes are perfectly balanced ($p=0.5$), and its minimum (0) when all examples belong to a single class ($p=0$ or $p=1$).
		- Expected information (bits):  Que información nos proporciona un mensaje.  La cantidad de información que nos proporciona un evento es inversamente proporcional a su probabilidad. Si algo es muy probable, no nos aporta mucha información.
		- La formula proviene de $\sum p_i \cdot log(1/p_i) = - \sum p_i \cdot log(p_i)$

	- Generalización para más de dos clases

  - Impurity of a set of leaves
    - Calculamos el inpurity de cada uno, y la media ponderada de todos ellos es la impureza del conjunto de conjuntos.
    - ![Pasted image 20240525113732.webp|589](/img/user/_Archivos/Pasted%20image%2020240525113732.webp)


- EJEMPLO: COMPUTE THE BEST SPLIT

	Exercise: (a) Consider these examples of “cycles” (+, P...) vs non-cycles (-, N...) vehicles:

	P1: Wheels = 2, WheelsSameSize=Yes, Motor=No, MaxSpeed=Low                  (bicicleta)
	P2: Wheels = 2, WheelsSameSize=Yes, Motor=Yes, MaxSpeed=Med                (bicicleta eléctrica)
	P3: Wheels = 4, WheelsSameSize=No, Motor=No,  MaxSpeed=Low                (con ruedecitas) 
	P4: Wheels=3, WheelsSameSize=No, Motor=No, MaxSpeed=Low                   (triciclo) 
	
	N1: Wheels = 4, WheelsSameSize=Yes, Motor=Yes, MaxSpeed=High                 (coche) 
	N2: Wheels = 2, WheelsSameSize=Yes, Motor=Yes, MaxSpeed=High                (moto) 
	N3: Wheels=3, WheelsSameSize=No, Motor=Yes, MaxSpeed=High                  (sidecar) 
	N4: Wheels=2, WheelsSameSize=Yes, Motor=Yes, MaxSpeed=Med                 (patinete eléctrico) 
	
	- a) Compute the impurity (using the entropy) for the data {P1,P2,P3,P4,N1,N2,N3,N4}. 
	
		Possible splits:
		
		Tenemos las diferentes características con las diferentes posibilidades, y vemos para cada posibilidad cuantas se corresponden con ciclos (+) y cuántas con no-ciclos (-).
		
		`Wheels[2,3,4]: con 2 [2+, 2-], con 3 [1+, 1-], con 4[1+, 1-]`
		`WheelsSameSize[Yes, No]: con Yes [2+, 3-], con No [2+, 1-]`
		`Motor[Yes, No]: con Yes [1+, 4-], con No [3+, 0-]`
		
		Ahora calculamos las diferentes impurezas según cada característica:
		
		**Impurity using wheels**
		`D1 = [2+, 2-] -> |D1| = 4 ->  Imp(D1) = -2/4 * log2(2/4) - 2/4 * log2(2/4) = 1`
		`D2 = [1+, 1-] -> |D2| = 2 -> ... = 1`
		`D3 = [1+, 1-] -> |D3| = 2 -> ... = 1`
		`|D| = 4 + 2 + 2 = 8  -> ... -> Imp({D1, D2, D3}) = 4/8 * 1 + 2/8 * 1 + 2/8 * 1 = 1`
		Vemos que usando Wheels da la impuridad máxima, ya que en este caso está 50%-50%
		
		Impurity using WheelsSameSize = 0.9512
		Impurity using Motor = 0.45
		**Impurity using MaxSpeed** = 0.25
	
	- b) What’s the best and the worst feature to split the dataset on? Can you make any sense of this?
	
		La mejor característica para dividir el dataset sería MaxSpeed, ya que habiéndo calculado la impureza para cada característica, es el que menos tiene.
		La peor sería usando Wheels, ya que tiene una impureza de 1


Divide-and-conquer algorithm
- Dado un problema grande, se divide en subproblemas más pequeños
- Greedy aproach: Se elige la mejor opción en cada momento, aunque quizás en pasos siguientes no sea la mejor opción. Sin corrección de errores.

Dealing with overfitting   (falta seguir de aquí)
- *Capacity*:
	- Más adaptación a los datos de entrenamiento. Niveles
- *Pruning*:
	- A posterior, analizar los nodos y ver si se pueden eliminar si no aportan nada.
- *Early stopping*:
- *Limit depth when building the tree*:

SKLEARN
- Libreria de python, clasificador basado en árboles de decisión
- `from sklearn.datasets import load_iris`  -> Problemas clasicos
- `from sklearn import tree`
```python
iris = load_iris()
x, y = iris.data, iris.target
clf = tree.DecisionTreeClassifier()   # Instanciar árbol
clf = clf.fit(x, y)   # Entrenar, ajustar modelo a datos
# Vemos que es supervisado ya que se le pasan las etiquetas
y_test = clf.predict(x_test)   # Predecir con otro set que no se ha usado en el entrenamiento

# Visualización
tree.plot_tree(clf)   
```


Explicabilidad
- Redes neuronales -> Caja negra
- Arboles de decisión si que son más explicables, ya que son muchos ifs, en redes neuronales no se aprecia esto ya que se devuelve directamente.


REPASO DE ÁRBOLES DE DECISIÓN
- **Decision Trees**:
	- **Components**:
		- **Homogeneity(D)**: Checks if instances in a dataset are homogeneous enough to be labeled with a single label.
		- **Label(D)**: Returns the majority class in the dataset.
		- **BestSplit(D, F)**: Determines the most informative feature from a set based on its ability to split data effectively.  Evaluar todas las características y ver cual tiene una impurity menor.
	- **Impurity Measures**:
		- Más puro cuando domina una clase sobre otras.
		- **Minority Class**: Measures the error rate based on the minority class.
		- **Gini Index**: Represents the expected error if examples are labeled randomly.
		- **Entropy**: Forma de cuantificarlo. Measures the expected information needed to classify an example.
	- **Generalization**: Impurity of a set of leaves is calculated as the weighted average of the impurities of individual leaves.
	- **Example**: Compute the best split for a dataset of cycles and vehicles based on features like wheels, motor, and max speed.

  - También usable en regresión. Habría que cambiar las hojas y el criterio de homogeneity, ya que la etiqueta no sería una clase, sino un valor numérico.

## Práctica Image

Variable compuesta de varios números.

Covarianza

Se da hecho, entender el código dado lo máximo

Carácteristicas. Columnas o filas o las dos.   Probar que es mejor que generar características random.

Naive bayes o multivariante

---

**we should not evaluate a learning model with instances used during training that model!**

FEATURES

Using raw pixels as features retains most information about the image but might be sensitive to changes in image scale, rotation, etc. Projections reduce dimensionality and might lose some information but can sometimes give robust features that emphasize general patterns in the data


p(c | x) using the bayes theorem

Prior p(c): 0 or 1, would be 50% each, if there are the same images of both in the dataset.
Likelihood p(x|c): Given a number (c), how probable is that the pixel values of x correspond to that number



$\hat{c} = \arg\max_c p(c|x)$  ->  The predicted class (number c) is the one for wich the posterior is the highest. We look at each and pick the highest.

Here instead of calculating the posterior for each class and comparing them, we compute a decision variable. A single calculation.  (*MAXIMUM A POSTERIORI*)
$$d = \ln \frac{p(x|c=c1)}{p(x|c=c2)} + \ln \frac{p(c=c1)}{p(c=c2)}$$

Let's break down what this formula represents:

$\ln \frac{p(x|c=c1)}{p(x|c=c2)}$  This is the natural logarithm of the ratio of the likelihoods of the features ( x ) under the assumption that they belong to class ( c1 ) versus ( c2 ). Essentially, it compares how much more likely the features are to appear in ( c1 ) than in ( c2 ).

$\ln \frac{p(c=c1)}{p(c=c2)}$ This is the natural logarithm of the ratio of the prior probabilities of classes ( c1 ) and ( c2 ). It reflects any initial preference or bias toward class ( c1 ) over ( c2 ) before seeing the features.



Performance:  correct / total


2 MODELS: NAÏVE BAYES and GAUSSIAN MULTIVARIATE

- [[0-Inbox/Probabilistic and Inductive Reasoning - Diego#Naive Bayes\|#Naive Bayes]]

- **MULTIVARIATE GAUSSIAN CLASSIFIER**
	- No asume independencia de features, captura las relaciones entre estas.
	- powerful in scenarios where feature relations strongly influence classification tasks
	- Ahora, la *media*, ya no tiene un número para cada feature, sino que es un *vector por clase*, que representa todas las tendencias a la vez
	- *==Covarianza==*: Matriz nxn donde cada elemento: $\Sigma_{i,j,c} = \frac{1}{m-1} \sum_{k=1}^m (x^{(k)}_i - \mu_{i,c})(x^{(k)}_j - \mu_{j,c})$
	    - Here, ( $x^{(k)}_i$ ) is the value of the ( i )-th feature in the ( k )-th data point.
	    - Measures how each pair of features covary (or relate) in the data for each class. Diagonal elements represent variances (like in Naïve Bayes), but off-diagonal elements capture the interdependencies between different features.

- **ALL TOGETHER**
	- Our classifiers make the assumption that the classification problem is binary (two classes), not always.
	- Resusable code.


# Reinforcement Learning

Aplicaciones
- Tareas tipo control: robotica, videojuegos, cooling systems, stock trading...

Toma de decisiones complejas y secuenciales

Secuential decision problems
- Diferencia entre el mundo simulado y el mundo real. En el mundo real las acciones que quieres hacer no siempre son las que haces realmente. Te puedes resbalar.

Transition model
p(s'|s,a) = Probabilidad de pasar de un estado a otro dado un estado y una acción.   Futuro depende del presente y de la acción que se tome.   Con la misma acción puede haber diferentes resultados.

(Markovian Assumption)

Rewards and utility
- R(s, a, s') = Reward function. Basado en el estado actual (s), la acción (a) y el siguiente estado (s').
- Los rewards se asocian a la transición de un estado a otro. No a un estado en sí.
- Return (G): Suma de los rewards futuros.  Gt = Rt+1 + Rt+2 + Rt+3 + ... + Rt+n.
	- *Goal*: Maximise sum of rewards of an environment history.
	- Setting: Stochastic generalization of search problems.


Markov decision process (MDP)
- S: Set of states
- A(s): Set of actions in state s
- P(s'|s,a): Transition model
- R(s, a, s'): Reward function

- How to solve it? By goal decomposition
  - Dynamic programming

Policy
- π(s): Convenient action to take in state s.  a $\in$ A(s)
  - Podemos tener que en π(s_1) = a_3   (determinista)  o una distribución de probabilidad (estocástica)
- π(a|s): Probability of taking action a in state s


Cart Pole example
- Estado: {x, v_x, θ, w_θ}
- Acciones: {push left, push right}   (la inacción en este caso no es posible)
- Recompensas: +1 por cada paso que no se caiga. 0 si se cae.  Se podría crear una función de recompensa más compleja, por ejemplo en base al ángulo.


Tetris example
- Estado: Pantalla del juego
- Acciones: 
  - A: {4 orientaciones x {<-, ->, nothing}, hard drop}  -> 13 acciones posibles
  - B: final column and piece orientation
- Recompensas: 
	- fitness = -0.51 x height + 0.76 x lines - 0.35 x holes - 0.18 x bumpiness
	- reward = change in fitness


Quality of a policy
- Expected utility over histories

Optimal policy
- π*
- Ejemplo del grid: What's the optimal policy for r=-0.04?
	- Al ser estocastico, a veces compensa el camino más largo para evitar el -1.

Variety of policies
- r < -1.6497: Al agente le renta suicidarse, no le compensa moverse.
- r > 0: Viva la vida, al agente le renta moverse, sin coger el -1 ni el 1.
- Different rewards lead to different optimal policies.







Utility of a state (under given policy)
- Uπ(s) = E[∑γ^t x R(s_t) | π, s_0 = s]      (????????)
- Promedio de la suma de recompensas con un factor de descuento γ
- $Uπ(s) = E[\sum_{t=0}^∞ \gamma^t \cdot R(s_t, π(s_t), s_{t+1})]$
- Best policies from state s: $π^*(s) = argmax_π Uπ(s)$


Ejemplo:
Compute U(s) at s = [1, 1] using Bellman equation.
U(s) será el maximo de de las 4 posibles acciones.

Q(s, a) en función de él mismo
- Q(s, a) = sumatorio desde s' P(s'|s,a) x [ R(s, a, s') + γ U(s') ]
- U(s) = max_a Q(s, a)



Action-utility function
- Q(s, a):  Expected utility of taking action a in state s
- Write U(s) in terms of Q(s, a):   $U(s) = max_a Q(s, a)$
- Q está definida para todas las acciones posibles
- Write the *optimal* action from s using Q(s, a):  $π^*(s) = argmax_a Q(s, a)$
- What about Q(s, a) in terms of U(s)?	$Q(s, a) = \sum_{s'} P(s'|s, a) [R(s, a, s') + γ U(s')]$ 		(recompensa inmediata + recompensa futura)

- Bellman equation, hay diferentes variantes, relaciona la utilidad entre un estado y los vecinos. Luego se puede ver si las acciones están determinadas o no, etc.
- Importante entender esta ecuación, ya que es la base de muchos algoritmos de RL.



REPASANDO

Markov Decision Process (MDP)
- S: Set of states
- A(s): Set of actions in state s
- P(s'|s,a): Transition model
- R(s, a, s'): Reward function
- **Gamma: Discount factor (0 < γ < 1)**

REPRESENTING MDPs

Guardar lo siguiente:
P(s'|s, a) 
R(s, a, s')

Cantidad de memoria necesaria:

- P(s'|s, a): |S| x |A| x |S|  (número de estados x número de acciones x número de estados) = O(|S|^2 x |A|)

## Algoritmos de MDPs

Value iteration

- n states -> n Bellman equations
- U(s1), U(s2), ..., U(sn)
- $\pi$ -> PE -> $U^{\pi}$ 

- No podemos usar algebra lineal, ya que se usa el max.
- En la iteración i+1 usaremos la U de la iteración i

- Ejemplo: Frozen Lake con libreria de gym
- Hay un umbral de convergencia, si la diferencia entre dos iteraciones es menor que ese umbral, se para, se considera que ya no se ofrece más información.



Policy iteration

- Partimos de una politica $\pi_0$ -> Policy evaluation -> $U^{\pi}$ -> Policy improvement -> $\pi_1$ -> Policy evaluation -> U^{\pi_1} -> Policy improvement -> $\pi_2$ -> ...
- Simpler than value iteration because Bellman equation is not used.
- Simpler than value iteration?   a = $\pi(s)$
- Standard Bellman equation is not used.

```python
policy = init_policy()
...
```


Policy improvement.

- Dada una utilidad, mejorar una política.
- Para todas las posibles acciones.




Reinforcement Learning

- Que pasa si no sabes las probabilildades de transicion? Tienes que actuar en el entorno para aprenderlas.
- En el aprendizaje por refuerzo tiene que actuar para ver las consecuencias de sus acciones.


Can we use supervised learning?

- Chess example
- x: Board state
- y: Best move
- Por refuerzo implicaría recolectar datos según expertos las mejores posiciones.

Learning from rewards, we still need rewards
- Trabajar con recompensas implica que es más fácil de definir. No haría tanta información experta.
- Rewards are easier because they are concise and require less expertise.
- Sparse rewards...
- RL is not just solving and MDPI. It must act to learn.
- Agente toma acción -> Environment -> Recompensa -> Agente toma acción -> Environment -> Recompensa -> ...



Model based vs model-free 

Passive vs active RL

Passive RL

- Fixed pi
- Similar to policy evaluation task
- Unknown P and R
- Assumed known pi
- Goal: Estimate U^pi(s)
- Trials in the environment using pi
- Annotate transitions: a taken, r received
- U^pi(s) = E[sum of rewards con el descuento x R(st, pi(st), st+1)]
- Direct utility estimation

- Adaptive Dynamic programming
- Temporal difference learning
- Mientras voy actuando voy aprendiendo cosas.  Este quiere aprovechar lo que va aprendiendo para no ir tan a lo loco

- Direct utility estimation
- Haciendo acciones y viendo las recompensas, para x accion en x estado, se puede estimar la utilidad.  Irán convergiendo a la utilidad real.
- No necesitamos la P.
- A lo largo de varios trials se puede pasar por el mismo estado, por lo que tendré varias estimaciones. Habrá que realizar el promedio.
- Después de varias iteraciones, ya habrá que cuestionarse que hacer.
- Bellman equation for a fixed policy.
- ADP: Adaptive Dynamic Programming.   Ahora podemos usar el algebra lineal.   Sigue estando el problema de números de estados elevados.   
  - Como estimar P(s'|s, a), vas viendo las visitas que haces y construyes tu estimación de la P

- TDL: Temporal Difference Learning
- 2 fuentes de información, lo esperado según sabemos como se comporta, y lo observado. Se combinan.
- Esto ayuda a ver si tenemos que ajustar mejor la estimación, queriendo decir que igual estamos subestimando o sobreestimando. 
- Current estimate: U^pi(s) = U^pi(s) + alpha x [R + gamma x U^pi(s') - U^pi(s)]
  - R + gamma x U^pi(s') -> Expected
  - - U^pi(s) -> Current estimate
  - alpha -> Learning rate


- Comparación ADP vs TDL
- Más variabilidad y sencillez el TDL.
- ADP hace todas las sumas, TDL solo compara la utilidad estimada con la real.
- Siguiente estado observado: TDL, sin hacer la transición no se sabe.
- Uses all successors: ADP


Active RL
- An active agent decides its actions. Greedy agent.
- Exploration and exploitation.   Explotar lo que ya sabemos, explorar para aprender más.  Probar acciones que no son optimas pero que quizás nos den más información.  Hay que buscar un equilibrio.
- Example n-armed bandit problem.  
- **Epsilon=1 estaríamos haciendo siempre...**


Temporal difference learning   Q-learning
- Bellman equation for Q(s, a) = Q(s, a) + alpha x [R(s, a, s') + gamma x max_a Q(s', a) - Q(s, a)]





