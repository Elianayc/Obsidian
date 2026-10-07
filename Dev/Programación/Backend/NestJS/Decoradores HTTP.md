NestJS utiliza decoradores para indicar qué método HTTP atiende cada operación:

```ts
@Get()
@Post()
@Patch()
@Put()
@Delete()
```

Equivalen a:

```ts
@Get()    → consultar
@Post()   → crear/enviar
@Patch()  → modificar parcialmente
@Put()    → reemplazar
@Delete() → eliminar
```

Ejemplo:

```ts
@Controller('encounters')
export class EncountersController {

  @Get()
  getEncounters() {
  }

}
```

Representa el endpoint:

```ts
GET /encounters
```

---
