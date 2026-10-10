Un **Module** de NestJS agrupa las piezas que pertenecen a una funcionalidad.

Por ejemplo:

```ts
@Module({
  imports: [],
  controllers: [AuthController],
  providers: [AuthService],
  exports: [AuthService],
})
export class AuthModule {}
```

## Partes principales

### `controllers`

Controllers que pertenecen al módulo.

```text
controllers
↓
reciben solicitudes HTTP
↓
delegan el trabajo
```

### `providers`

Servicios que NestJS debe crear y poder inyectar dentro del módulo.

```ts
providers: [AuthService]
```

Esto permite, por ejemplo:

```ts
constructor(
  private readonly authService: AuthService
) {}
```

### `exports`

Servicios que este módulo permite utilizar desde otros módulos.

```ts
exports: [AuthService]
```

### `imports`

Otros módulos que este módulo necesita utilizar.

```ts
imports: [ConversationModule]
```

---

## AppModule

`AppModule` es el módulo principal de la aplicación.

Los distintos módulos se conectan allí:

```text
AppModule
│
├── HealthModule
├── AuthModule
├── ConversationModule
└── MessageModule
```

Conceptualmente:

```text
FUNCIONALIDAD
↓
Module
├── Controller
├── Service
├── Request
└── Models
```

No todas las funcionalidades necesitan exactamente los mismos archivos.

Lo que normalmente se repite es:

```text
Controller
Service
Module
```

---

