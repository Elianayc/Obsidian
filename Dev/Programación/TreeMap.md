---
tags:
  - Programación
  - ProgramaciónII
---
Es una implementación de Map que **ordena automáticamente las claves**.
El orden puede ser natural (alfabético o numérico) o definido por un criterio.

### Ejemplo

```java
import java.util.TreeMap;
import java.util.Map;
public class Main {    
	public static void main(String[] args) {        
		Map<String, Integer> map = new TreeMap<>();        
		
		map.put("Luis", 30);        
		map.put("Ana", 25);        
		map.put("Pedro", 40);        
		
		System.out.println(map);    
	}
}
```

##### Resultado
{Ana=25, Luis=30, Pedro=40}