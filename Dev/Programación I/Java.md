Java es un lenguaje orientado a objetos, compilado e interpretado mediante la JVM (Java Virtual Machine).  
Su lema es _“Write once, run anywhere”_, porque el mismo programa puede ejecutarse en distintos sistemas operativos.

Se usa mucho en backend, aplicaciones empresariales y Android.

### **Sintaxis básica**

##### Programa mínimo:

```Java
public class Main {    
	public static void main(String[] args) {        
		System.out.println("Hola mundo");    
	}
}
```

##### Variables:

```Java
int edad = 20;
double altura = 1.70;
String nombre = "Ana";
```

##### Condicional:

```Java
if (edad >= 18) {    
	System.out.println("Mayor de edad");
}
```

##### Clase básica:

```Java
class Persona {    
	String nombre;    
	int edad;    
	
	void saludar() {        
		System.out.println("Hola soy " + nombre);    
	}
}
```