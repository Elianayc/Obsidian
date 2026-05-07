#### Asignación " = "
Le asigna un valor a una variable.
```cpp
numero = 4;
```

#### Aritméticos " + - * / "
Operaciones.
- **+** suma.
- **-** resta
- ***** multiplicación
- **/** división.
- **%** resto de una división entera.


#### Lógicos y relacionales " > < >= <= == != AND OR"
Devuelven un bool.
- **>** mayor.
- **<** menor
- **>=** mayor o igual
- **<=** menor o igual
- **==** igual
- **!=** distinto
- **&&** and
- **||** or


#### Expresiones combinadas
Si usamos varias operaciones y/o expresiones se aplicará un orden de procedencia.

##### De mayor a menor:
1.  ***** multiplicación / **%** resto de una división entera.
2. **+** suma / **-** resta
3. **>** mayor /  **<** menor /  **>=** mayor o igual / **<=** menor o igual
4.  **==** igual / **!=** distinto
5. **&&** and
6. **||** or
7. **=** resultado

Si todos son del mismo nivel se evalúa de izquierda a derecha.
Se puede usar paréntesis.