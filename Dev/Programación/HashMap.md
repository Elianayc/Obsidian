---
tags:
  - Programación
  - ProgramaciónII
---
Es la implementación más común de **Map**.
No garantiza **ningún orden** en los elementos.
Es muy eficiente para inserción, búsqueda y eliminación.

> [!example]
> 
> ```java
> import java.util.HashMap;
> import java.util.Map;
> 
> public class Main {    
> 	public static void main(String[] args) {        
> 		Map<String, Integer> map = new HashMap<>(); 
> 		
> 		map.put("Ana", 25); 
> 		map.put("Luis", 30);        
> 		map.put("Ana", 40);        
> 		
> 		System.out.println(map);    
> 	}
> }
> ```
> 
> ##### Resultado (ejemplo posible)
> {Luis=30, Ana=40}