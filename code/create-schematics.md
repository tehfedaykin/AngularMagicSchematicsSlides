## Create Blank Schematic

```bash
schematics blank --name=fix-it
```

Creates a minimal schematic

```typescript
import { Rule, SchematicContext, Tree } from '@angular-devkit/schematics';

export function fixIt(_options: any): Rule {
  return (tree: Tree, _context: SchematicContext) => {
    return tree;
  };
}
```
