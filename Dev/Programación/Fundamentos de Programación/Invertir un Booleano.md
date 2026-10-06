
También se puede utilizar `!` para invertir directamente el valor de una variable booleana:

```typescript
this.showArchived = !this.showArchived;
```

Equivale a:

```ts
if (this.showArchived) {
  this.showArchived = false;
} else {
  this.showArchived = true;
}
```

Por lo tanto:

```
true  → false
false → true
```

---

