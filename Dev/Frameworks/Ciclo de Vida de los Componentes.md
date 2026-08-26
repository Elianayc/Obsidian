Un componente tiene un **ciclo de vida**: se crea, se renderiza, puede actualizarse varias veces y finalmente puede eliminarse.

---

### Etapas principales

- **Montaje:** el componente se crea, se renderiza y aparece en el DOM.
- **Actualización:** cambian sus datos, props o estado y la interfaz se vuelve a renderizar.
- **Desmontaje:** el componente se elimina del árbol y del DOM.

Los frameworks proporcionan **hooks de ciclo de vida**, que permiten ejecutar código automáticamente en cada etapa.

|       Etapa       |                        Uso habitual                        |
| :---------------: | :--------------------------------------------------------: |
|    **Montaje**    |      Obtener datos de una API o inicializar recursos.      |
| **Actualización** |    Recargar datos cuando cambia un filtro o parámetro.     |
|  **Desmontaje**   | Cancelar suscripciones, limpiar timers y liberar recursos. |

---

### Hooks principales

|     **Etapa**     |   **Angular**   |
| :---------------: | :-------------: |
|    **Montaje**    |  `ngOnInit()`   |
| **Actualización** | `ngOnChanges()` |
|  **Desmontaje**   | `ngOnDestroy()` |

|     **Etapa**     |                                           **React**                                           |
| :---------------: | :-------------------------------------------------------------------------------------------: |
|    **Montaje**    |                        `useEffect(() => { cargarProductos(); }, []);`                         |
| **Actualización** |               `useEffect(() => { cargarProducto(productoId); }, [productoId]);`               |
|  **Desmontaje**   | `useEffect(() => { const sub = servicio.subscribe(); return () => sub.unsubscribe(); }, []);` |

|     **Etapa**     |                                   **Vue**                                   |
| :---------------: | :-------------------------------------------------------------------------: |
|    **Montaje**    |                 `onMounted(() => { cargarProductos(); });`                  |
| **Actualización** | `watch(() => props.productoId, (nuevoId) => { cargarProducto(nuevoId); });` |
|  **Desmontaje**   |            `onUnmounted(() => { subscription.unsubscribe(); });`            |

Los hooks permiten ejecutar cada operación en el momento adecuado del ciclo de vida del componente.

---

