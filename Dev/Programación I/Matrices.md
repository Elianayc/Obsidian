Una matriz es una estructura de datos bidimensional que almacena elementos del mismo tipo organizados en filas y columnas. 

Cada elemento se accede mediante dos índices: el **primero** representa la **fila** y el **segundo** la **columna**.

También existen los **tensores**, que son arreglos multidimensionales.

---

### Declaración
```cpp
int matriz[2][3];
```
Matriz de 2 filas y 3 columnas.

---

### Inicialización
```cpp
int matriz[2][3] = {    
	{1, 2, 3},    //Fila 0
	{4, 5, 6}    //Fila 1.
};
```

---

### Carga de una matriz
```cpp
for (int i = 0; i < 2; i++) {    
	for (int j = 0; j < 3; j++) {       
		 cin >> matriz[i][j];    
	 }
}
```

---

### Mostrar una matriz
```cpp
for (int i = 0; i < 2; i++) {    
	for (int j = 0; j < 3; j++) {        
		cout << matriz[i][j] << " ";    
	}    
	cout << endl;
}
```