---
{"dg-publish":true,"permalink":"/01 - Recursos/Curso Drone Espaitec/","noteIcon":""}
---


- ejemplos drones: dji dron, dron fpv

- Obtener titulo operador: 
	- [Registro de operador de drones/UAS | AESA-Agencia Estatal de Seguridad Aérea - Ministerio de Fomento](https://www.seguridadaerea.gob.es/es/ambitos/drones/registro-de-operador-de-drones-uas)
	- [HTTP Status 400 – Bad Request](https://sede.seguridadaerea.gob.es/fire-signature/public/chooseCertificateOriginService)

- Construcción nuestro dron: [(10) Zd850 build - YouTube](https://www.youtube.com/playlist?list=PLq8CK9yN-s_dqlWjc8TeKk-9_cbGYpRhB)

- PARTES:
	- Batería: 
		- Generalmente conectada en paralelo a todos los sistemas y al BEC (Battery Elimination Circuit).
	- Placa de distribución: 
		- Distribuye la energía de la batería a los motores y contiene el BEC, que filtra el voltaje y proporciona 5V para la electrónica y 12V para otros componentes.
	- Variador (speed controller): 
		- Puede tener 2 o 3 cables. Los de 2 cables no incluyen BEC.
	- Motor: 
		- Componente final que convierte la energía eléctrica en movimiento.


- Baterías más comunes en drones: LIPO (polímero de litio)
	- Ofrecen mayor capacidad de entrega de energía y flexibilidad en su forma. En forma de celdas o paquetes, se pueden ver en tablets, etc.
	- Las baterías de ion-litio se usan menos debido a su peso, aunque tienen la ventaja de mantener la carga por más tiempo. Vsitas usualmente en forma de pila

- Cálculos importantes para el diseño y operación de drones:
	- MTOW (Maximum Take Off Weight): Determina el peso máximo al despegue. Por ejemplo, un dron de 249g tendrá un MTOW superior.
	- Autonomía: Varía según la aplicación. Para rescate en playas se requieren al menos 10 minutos, mientras que para supervisión policial se necesitan entre 30-50 minutos.


- Baterías de Litio para Drones: Manejo y Características

	- Tensión Nominal y Niveles de Carga:
		- 4,2V: Representa el 100% de carga. Es importante notar que mantener la batería a este nivel por períodos prolongados puede acelerar su degradación.
	    - 3,7V: Indica aproximadamente el 50% de carga. Este es el voltaje nominal de una celda de litio.
	    - 3,2V: Nivel crítico, por debajo del cual la batería sufre daños significativos. Se considera el 0% efectivo de carga.

	- Ciclo de Uso Recomendado, y almacenamiento
		- a) Carga completa (100%) antes del vuelo. La carga al 100% solo es perjudicial cuando no se va a usar enseguida.
		- b) Uso del dron hasta que la batería alcance aproximadamente el 30% de carga. No bajar del 30% de carga de forma habitual para preservar la salud de la batería.
		- c) Recarga al 60% para almacenamiento si no se va a utilizar pronto. Si se usará dentro de un día, se puede dejar al 30% y cargarla al día siguiente hasta el 100%.
	    - Rango óptimo de carga: Mantener la batería entre el 40% y el 60% de su capacidad.
	
	- Configuraciones de Voltaje para Drones:
	    - Conexión en serie: Se utilizan múltiples celdas para aumentar el voltaje. Por ejemplo, 3,7V + 3,7V = 7,4V (configuración 2S).
	    - Ejemplo de batería de dron: 22,2V, compuesta por 6 celdas de 3,7V (configuración 6S).
	    - El voltaje de la batería influye directamente en la velocidad de giro de los motores.
	
	- Tipos de Baterías según Tamaño del Dron:
	    - Drones pequeños: Suelen utilizar configuraciones 1S (una celda, 3,7V) o 2S (dos celdas, 7,4V).
	    - Drones más grandes: Utilizan configuraciones con más celdas, como la mencionada 6S de 22,2V.
	
	- Conexión en paralelo (P): Mantiene el voltaje, aumenta la capacidad.
		- Al conectar paquetes en paralelo se dupica la capacidad total
		- Por ejemplo, si cada paquete tiene una capacidad de 10.000 mAh, dos en paralelo te darán una capacidad total de 20.000 mAh
		- La cosa es que también duplicas el peso de la batería, por lo que duplicar la capacidad no termina de duplicar la autonomía, ya que el dron tiene que cargar con el peso adicional
		- Por ejemplo, si inicialmente podías volar 10 minutos con un solo paquete de 10.000 mAh, con dos paquetes (20.000 mAh), podrías volar menos de 20 minutos debido al mayor peso.

	- Configuraciones mixtas:
        - 3S2P: 3 celdas en serie, 2 en paralelo. 11,1V con doble capacidad.
        - 6S: 6 celdas en serie (como 22,2V mencionado anteriormente).
        - 6S2P: 6 en serie, 2 en paralelo. Mismo voltaje que 6S pero doble capacidad.

	- Carga y Balanceo:
	    - Carga rápida: Puede desbalancear las celdas.
	    - Carga balanceada (recomendada): Cargar hasta 80% y luego balancear individualmente cada celda
	    - Los cargadores y baterías inteligentes, usadas en drones industriales, contienen su propia electrónica para gestionar la carga y el balanceo, además de proporcionar información sobre el estado de la batería.

	- Capacidad y Tasa de Descarga (C-rating):
	    - Capacidad: Medida en mAh (ejemplo: 10.000mAh).
	    - C-rating: Indica la tasa máxima de descarga segura. Ejemplo: 30C en una batería de 10.000mAh puede suministrar hasta 300A (10A * 30).
	    - Importancia: Cuanto más alto el C-rating, mejor rendimiento, pero más costosa la batería.
	- Cálculo de Requerimientos:
	    - Ejemplo: Si los motores consumen 40A cada uno, y hay 6 motores: 40A * 6 = 240A requeridos
	    - La batería debe tener un C-rating suficiente para soportar esta demanda.
	3. Ejemplo Práctico: Batería mencionada: 10.000mAh, 6S (22,2V), 30C
	    - Puede suministrar hasta 300A (10A * 30C)
	    - Adecuada para la configuración de 6 motores que requieren 240A en total.


- Motores:
    - Sin escobillas para mayor velocidad.
    - Velocidad regulada mediante activación de bobinas.
    - Notación: Por ejemplo, 2204 significa 22mm de diámetro y 4mm de altura.
    - Capacidad de empuje: Aproximadamente 1kg por motor.
    - Configuración de giro: En drones cuadricópteros, 2 giran en un sentido y 2 en otro. En hexacópteros (como el mencionado), 3 en cada sentido.
    - Control de dirección: Se logra desacelerando los motores de un mismo sentido de giro.
	- Rendimiento y Autonomía:
	    - Ejemplo: Un dron con MTOW (Peso Máximo al Despegue) de 6kg tendría aproximadamente 15 minutos de autonomía.


- Títulos de Operación:
    - Operador: Para drones hasta 250g sin cámara.
    - Piloto: Para drones más grandes o complejos.
	- Categorías de Operación:
	    - A1: Para drones pequeños.
	    - A2: Para drones más grandes que A1 pero menores que A3.
	    - A3: Para drones de hasta 25kg.
	    - STS: Para drones aún más grandes.

- Nueva Legislación:
    - Drones de 250g ahora pueden volar en ciudad sin necesidad de cortar calles.
    - Requisito: Notificar a la policía antes de la operación.


# Concepto Normativo
[seguridadaerea.gob.es/sites/default/files/Curso.Formacion.A1.A3.Completo.v6.pdf](https://www.seguridadaerea.gob.es/sites/default/files/Curso.Formacion.A1.A3.Completo.v6.pdf)
