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