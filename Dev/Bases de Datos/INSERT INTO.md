El comando **INSERT INTO** permite **agregar registros** a una tabla.

### Sintaxis básica
```SQL
INSERT INTO tabla (campo1, campo2, ..., campoN)
VALUES (valor1, valor2, ..., valorN);
```

### Ejemplo
```SQL
INSERT INTO usuarios (name, surname, age)
VALUES ('Juan', 'Perez', 20);
```

---

## Consideraciones importantes
- Los campos **autonumerados (SERIAL)** normalmente **no se especifican**  
    → La secuencia asigna el valor automáticamente.

- Si un campo tiene **valor por defecto (DEFAULT)**:
    - Si se especifica → se usa el valor indicado
    - Si no se especifica → se usa el valor por defecto

---

## INSERT usando SELECT
Permite insertar datos obtenidos desde otra tabla o consulta.

### Sintaxis
```SQL
INSERT INTO tabla_destino (campo1, campo2, ..., campoN)
SELECT campoA, campoB, ..., campoNFROM tabla_origen;
```