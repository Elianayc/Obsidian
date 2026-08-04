---
tags:
  - Programación
  - ProgramaciónII
---
La sobrecarga es cuando una clase tiene **varios métodos con el mismo nombre**, pero con **firmas distintas**.
El tipo de retorno **NO cuenta** para la sobrecarga.

##### Ejemplo:
```java
public String concatPersonInfo(String name, String lastName)
public String concatPersonInfo(String name, String middleName, String lastName)
public String concatPersonInfo(String name, String lastName, int age)
```


**Esto NO sería sobrecarga válida:**
```java
public String concatPersonInfo(String name)
public int concatPersonInfo(String name)
```
Porque solo cambia el tipo de retorno y este no se considera parte de la firma.

---

### Diferencias entre Lenguajes Tipados y No tipados

###### Lenguajes fuertemente tipados
La sobrecarga de métodos funciona de forma **nativa** en lenguajes fuertemente tipados y estáticos como Java, C++ y C#.  
En estos lenguajes, el compilador puede determinar qué método invocar analizando la **firma del método** (tipos, cantidad y orden de parámetros) en tiempo de compilación.
Por eso pueden existir varios métodos con el mismo nombre sin ambigüedad.

###### Lenguajes dinámicos o no tipados
En lenguajes dinámicos o con tipado más flexible la situación cambia.  
Lenguajes como Python o PHP no poseen sobrecarga de métodos tradicional porque **los tipos no forman parte de la firma del método en tiempo de compilación**. 
Normalmente solo puede existir una función con ese nombre y el programador debe manejar los distintos casos manualmente dentro de la función.

###### TypeScript
Aunque TypeScript **transpila** a JavaScript, **sí permite declarar sobrecarga**, pero solo a nivel de tipos (en tiempo de compilación).  
En tiempo de ejecución sigue existiendo **una sola función**, por lo que el desarrollador debe implementar la lógica que diferencie los casos.

```ts
class PersonUtils {  

	// Firmas de sobrecarga (solo definición)  
	concatPersonInfo(name: string, lastName: string): string;  
	concatPersonInfo(name: string, lastName: string, age: number): string;  
	  
	// Implementación real (una sola)  
	concatPersonInfo(name: string, lastName: string, age?: number): string {  //Age va con ? porque es opcional.
		if (age !== undefined) {  
			return `${name} ${lastName} ${age}`;  
		}  
		return `${name} ${lastName}`;  
	}  
}

const utils = new PersonUtils();  
  
utils.concatPersonInfo("Ana", "Gomez");  
utils.concatPersonInfo("Ana", "Gomez", 30);

```

Los parámetros opcionales deben ir al final.


#Programación