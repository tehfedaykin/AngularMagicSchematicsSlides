### Rule Interface

```typescript
export type Rule = (tree: Tree, context: SchematicContext) => Tree | Observable<Tree> | Rule | Promise<void | Rule> | void;
```