---
{"dg-publish":true,"permalink":"/00 - Temporales/Costes algorítmicos/","title":"Costes algorítmicos","noteIcon":""}
---

- **PENDIENTE: Programación2 agregar cosas + organizar mejor**

---

- COSTE PEOR CASO
- COSTE AMORTIZADO
	- Es simplemente el coste medio.
	- Consiste en encontrar la operación más costosa y la menos costosa, y encontrar el punto medio para regularlo.
	- Esto tiene que ver con la práctica 9 de vectores, donde el peor caso para agregar un elemento era de 1, hasta que el array se tenía que duplicar, agregando todos los elementos, y luego agregar el nuevo, siendo un coste de n.
	- BOLETIN
		- es de 2\*(i-2)         el coste acumulado en los peores moomentos, donde se duplica el espaio
		- 3n -4      lineal
		- *si siempre amplias mediante una cosntante, el coste total sale cuadratico, el coste amortizado sale lineal*

- **ESQUEMAS ALGORITMICOS**        (examen practico)
	- busqueda anchura
	- divide y vencerás          (examen hasta aqui)

- algoritmos sobre grafos
	- muchos problemas son adaptar los algoritmos del recorrido sobre grafos
	- GRAFO: conjunto de vértices y aristas
	- Dado un grafo, se quiere hacer cierta tarea, recorrido...

	- Recorrido en anchura      (ejemplo algoritmo)
		- miramos cada nodo y sus vecinos, ponemos en la cola los que no hemos visto y tambien lo ponemos en vistos, luego vamos viendo todos los vecinos etc.
