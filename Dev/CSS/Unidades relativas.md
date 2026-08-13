Las **unidades relativas** no están completamente definidas, ya que su valor depende de otro valor de referencia.

Son las más utilizadas en el diseño web debido a la **flexibilidad con la que se adaptan a diferentes medios**.

Las unidades relativas son:

| Unidad | Referencia                                                                                                                                                                                                                                                                                                                                                                                 |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `em`   | Tamaño de letra del elemento.<br>La unidad `em` hace referencia al tamaño en puntos de la letra que se está utilizando.<br>Por ejemplo, si se utiliza una tipografía de **12 puntos**, `1em` equivale a **12 puntos**.<br>Aunque no es una definición exacta, `1em` equivale aproximadamente a la anchura de la letra **M** (_eme mayúscula_) del tipo y tamaño de letra del elemento.<br> |
| `ex`   | Altura de la letra `x` del tipo y tamaño de letra del elemento.<br>La unidad `ex` hace referencia a la altura de la letra **x minúscula** del tipo y tamaño de letra del elemento.<br>Su valor puede aproximarse a:<br>**1ex ≈ 0,5em**                                                                                                                                                     |
| `px`   | Píxel, relacionado con la resolución de la pantalla del dispositivo.<br>`px` representa un **píxel** y su referencia está relacionada con la resolución de la pantalla del dispositivo en el que se visualiza la página HTML.                                                                                                                                                              |

> `em` no debe confundirse con la etiqueta `<em>` de HTML.

---

## Consideraciones generales

- Si el valor es `0`, la unidad de medida es opcional.
- Si el valor es distinto de `0` y no se indica ninguna unidad, la medida se ignora.
- Algunas propiedades permiten indicar medidas negativas, aunque habitualmente sus valores son positivos.
- Si el valor decimal es inferior a `1`, se puede omitir el `0` de la izquierda. Por ejemplo, `0.5em` es equivalente a `.5em`.

---

## Ventaja de las unidades relativas

La principal ventaja de las unidades relativas es que **mantienen las proporciones del diseño de la página**.

Por ejemplo, establecer el margen de un elemento en `1em` equivale a indicar que el margen debe tener el mismo tamaño que su letra y cambiar proporcionalmente.

---

## Porcentajes

El **porcentaje (`%`)** también es una unidad de medida relativa.

CSS lo trata de forma separada de `em`, `ex` y `px` debido a su importancia.

Un porcentaje está formado por un **valor numérico seguido del símbolo `%`** y siempre está referenciado a otra medida.

Cada propiedad CSS que permite utilizar un porcentaje define cuál es la medida de referencia utilizada para calcularlo.

---

