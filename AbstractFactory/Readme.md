# Abstract Factory

### Prop�sito
Abstract Factory es un patr�n de dise�o creacional que nos permite producir familias de objetos relacionados sin especificar sus clases concretas.

### Problema

Imagina que est�s creando un simulador de tienda de muebles. Tu c�digo est� compuesto por clases que representan lo siguiente:
Una familia de productos relacionados, digamos: Silla + Sof� + Mesilla.

Algunas variantes de esta familia. Por ejemplo, los productos Silla + Sof� + Mesilla est�n disponibles en estas variantes: Moderna, Victoriana, ArtDec�.

Necesitamos una forma de crear objetos individuales de mobiliario para que combinen con otros objetos de la misma familia. Los clientes se enfadan bastante cuando reciben muebles que no combinan.

Adem�s, no queremos cambiar el c�digo existente al a�adir al programa nuevos productos o familias de productos. Los comerciantes de muebles actualizan sus cat�logos muy a menudo, y debemos evitar tener que cambiar el c�digo principal cada vez que esto ocurra.

### Soluci�n

Lo primero que sugiere el patr�n Abstract Factory es que declaremos de forma expl�cita interfaces para cada producto diferente de la familia de productos (por ejemplo, silla, sof� o mesilla). Despu�s podemos hacer que todas las variantes de los productos sigan esas interfaces. Por ejemplo, todas las variantes de silla pueden implementar la interfaz Silla, as� como todas las variantes de mesilla pueden implementar la interfaz Mesilla, y as� sucesivamente.

El siguiente paso consiste en declarar la F�brica abstracta: una interfaz con una lista de m�todos de creaci�n para todos los productos que son parte de la familia de productos (por ejemplo, crearSilla, crearSof� y crearMesilla). Estos m�todos deben devolver productos abstractos representados por las interfaces que extrajimos previamente: Silla, Sof�, Mesilla, etc.

Ahora bien, �qu� hay de las variantes de los productos? Para cada variante de una familia de productos, creamos una clase de f�brica independiente basada en la interfaz F�bricaAbstracta. Una f�brica es una clase que devuelve productos de un tipo particular. Por ejemplo, la F�bricadeMueblesModernos s�lo puede crear objetos de SillaModerna, Sof�Moderno y MesillaModerna.

El c�digo cliente tiene que funcionar con f�bricas y productos a trav�s de sus respectivas interfaces abstractas. Esto nos permite cambiar el tipo de f�brica que pasamos al c�digo cliente, as� como la variante del producto que recibe el c�digo cliente, sin descomponer el propio c�digo cliente.

Digamos que el cliente quiere una f�brica para producir una silla. El cliente no tiene que conocer la clase de la f�brica y tampoco importa el tipo de silla que obtiene. Ya sea un modelo moderno o una silla de estilo victoriano, el cliente debe tratar a todas las sillas del mismo modo, utilizando la interfaz abstracta Silla. Con este sistema, lo �nico que sabe el cliente sobre la silla es que implementa de alg�n modo el m�todo sentarse. Adem�s, sea cual sea la variante de silla devuelta, siempre combinar� con el tipo de sof� o mesilla producida por el mismo objeto de f�brica.

Queda otro punto por aclarar: si el cliente s�lo est� expuesto a las interfaces abstractas, �c�mo se crean los objetos de f�brica? Normalmente, la aplicaci�n crea un objeto de f�brica concreto en la etapa de inicializaci�n. Justo antes, la aplicaci�n debe seleccionar el tipo de f�brica, dependiendo de la configuraci�n o de los ajustes del entorno.
