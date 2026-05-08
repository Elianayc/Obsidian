1. Errores sintácticos y semánticos
	De diseño. Fáciles de detectar por el IDE.

2. Errores de lógica
	Cumplen con lo primero. De ejecución. Bugs.

3. Eventos externos

Excepción
El flujo normal es alterado por un evento no contemplado (punto 2 o 3) resultando en la terminación inmediata del programa sin el adecuado tratamiento.

Control de Excepciones
La mayoría de los lenguajes de alto nivel implementan el bloque de control conocido como **try/catch**.
Este tiene por objetivo ejecutar un camino alternativo en caso de un suceso poco habitual.

Estructura de un bloque try/catch

Try
Debe encerrar el algoritmo que se espera ejecutar en condiciones normales. 
Código que podría tener un error.

Catch
Dee contener el camino alternativo en caso de una excepción. 
Manejo del error.

Finally
Subbloque opcional que se ejecuta siempre. Normalmente de limpieza o liberación de recursos.
Es opcional.


Si un bloque try/catch intercepta una excepción en el código que sobrevenga al bloque catch no se ejecutará.