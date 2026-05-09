---
tags:
  - Programación
  - ProgramaciónII
---
Es una implementación de Map que **mantiene el orden** de inserción.
Es decir, los elementos se almacenan en el orden en que fueron agregados.


### Ejemplo

```java
import java.util.LinkedHashMap;
import java.util.Map;

public class Main {    
	public static void main(String[] args) {        
		Map<String, Integer> map = new LinkedHashMap<>();        
		
		map.put("Ana", 25);       
		map.put("Luis", 30);        
		map.put("Pedro", 40);        
		
		System.out.println(map);    
	}
}
```

##### Resultado
{Ana=25, Luis=30, Pedro=40}