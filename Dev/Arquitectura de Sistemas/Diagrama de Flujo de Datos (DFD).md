---
tags:
  - ArquitecturadeSistemas
---
El **Diagrama de Flujo de Datos (DFD)** es una técnica de análisis estructurado que permite ensamblar una representación gráfica de los procesos de datos a lo largo de una organización. 

Se utiliza una combinación de solo cuatro símbolos para crear una descripción ilustrada y elaborar una documentación sólida del sistema.

### Ventajas Principales:
* No comprometerse demasiado pronto con la implementación técnica.
* Comprender en detalle la interrelación de los sistemas y subsistemas.
* Facilitar la comunicación del sistema actual con los usuarios.
* Analizar el sistema para verificar la correcta definición de datos y procesos.

---

## Elementos del DFD

![[Pasted image 20260803142449.png]]

* **Entidad Externa:** Representa una fuente o destino de datos fuera del sistema 
	(ej. *Estudiante*).
	
* **Flujo de Datos:** Flechas que indican el movimiento de la información 
	(ej. *Información nuevo estudiante*).
	
* **Proceso:** Acción o transformación de datos 
	(ej. *2.1 Crear registro de estudiante*).
	
* **Almacén / Repositorio de Datos:** Lugar donde se guardan los datos 
	(ej. *D3 Archivo maestro de estudiantes*).

---

## Reglas de Construcción

* Debe existir al menos un proceso en el diagrama.
* No debe haber objetos aislados o independientes.
* Un proceso debe recibir al menos un flujo de datos de entrada y producir al menos uno de salida.
* Un almacén de datos debe conectarse siempre con al menos un proceso.
* Las entidades externas **no** se conectan directamente entre sí.

---

##  Errores Comunes

![[Pasted image 20260803142541.png]]

* **Olvidar flujos o invertir flechas:** Todo proceso debe transformar datos recibiendo entradas y produciendo salidas.

* **Conexiones directas prohibidas:** Repositorios de datos y entidades externas nunca se conectan directamente entre sí (deben pasar por un proceso).

* **Etiquetado incorrecto:** 
  * Los **procesos** usan el formato `Verbo + Sustantivo + Adjetivo`.
  * Los **flujos de datos** se describen con un `Sustantivo`.

* **Diagrama sobrecargado:** Si hay demasiados procesos, deben agruparse en subsistemas.

* **Descomposición desbalanceada:** Los diagramas hijos deben mantener exactamente los mismos flujos de entrada y salida que el proceso padre.

### Diagrama Correcto:
![[Pasted image 20260803142607.png]]

---

## DFD Lógico vs. DFD Físico

* **DFD Lógico:** Se enfoca en el negocio y en cómo opera (independiente de la tecnología).
	![[Pasted image 20260803142907.png]]
	
* **DFD Físico:** Muestra la implementación del sistema (hardware, software, archivos y personas involucradas).
	![[Pasted image 20260803142926.png]]
	
	![[Pasted image 20260803142937.png]]
	

> **Progresión ideal:** DFD Lógico Actual ➔ DFD Lógico Nuevo ➔ DFD Físico.
> *Permite mejor comunicación, elimina redundancias y detecta cuellos de botella.*

---

## Metodología Arriba-Abajo (Top-Down)

1. **Listar actividades:** Identificar entidades, flujos, procesos y almacenes.

2. **Diagrama de Contexto:** Nivel más alto; muestra entidades externas y flujos principales sin procesos detallados ni almacenes.
	![[Pasted image 20260803142725.png]]

3. **Diagrama 0 (Alto nivel):** Muestra los procesos generales y almacenes de datos.
	![[Pasted image 20260803142749.png]]

4. **Diagramas Hijos (Detalle):** Descomposición detallada de cada proceso del Diagrama 0.
	![[Pasted image 20260803142815.png]]

5. **Verificación:** Revisar errores y consistencia de etiquetas.

6. **Desarrollar DFD Físico:** Diferenciar procesos manuales/automatizados y agregar controles de error

7. **Particionar:** Agrupar partes para facilitar la programación e implementación.

---
#ArquitecturadeSistemas
