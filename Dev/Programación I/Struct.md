---
tags:
  - Programación
  - ProgramaciónI
---
Son una forma de agrupar varias variables bajo un mismo nombre, pudiendo ser de distintos tipos de datos.  
Se utilizan para crear tipos de datos personalizados.

##### Creación
```cpp
struct Persona{
	char nombre[20];
	int edad;
	float altura;
};
```

##### Creamos una variable del tipo Persona:
```cpp
int main (){
	Persona eli;
}
```

##### Uso de variables de campos:
```cpp
cin >> eli.nombre;
eli.edad = 37;
eli.altura = 1.57;
```