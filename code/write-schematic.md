## Write Our Schematic

```typescript
  import { Rule, SchematicContext, Tree } from '@angular-devkit/schematics';
  import { tsquery } from '@phenomnomnominal/tsquery';
  import * as ts from 'typescript';
  import * as prettier from 'prettier';

  function swap(source: string , x1: number, x2: number, y1: number, y2: number) {
    const first = source.slice(x1, x2 + 1);
    const second = source.slice(y1, y2 + 1);

    return source.slice(0, x1) + second + source.slice(x2 + 1, y1) + first + source.slice(y2 + 1);
  }

  export function fixIt(_options: any): Rule {
    return (tree: Tree, _context: SchematicContext) => {
      const staged = tree.branch();
      staged.getDir('./src').visit(filePath => {
        if (!filePath.endsWith('component.ts')) {
          return;
        }

        const content = tree.read(filePath);
        if (!content) {
          return;
        }

        if (content.indexOf('breakingFunction') > -1) {
          const fileContents = content.toString();
          const ast = tsquery.ast(fileContents);
          const brokenFunctions = tsquery(ast, 'CallExpression:has([name="breakingFunction"])');
          let stagedFile = fileContents; 
          for (let index = 0; index < brokenFunctions.length; index++) {
            const brokenInstance = brokenFunctions[index] as ts.CallExpression;
            const argsToSwap= brokenInstance.arguments;
            stagedFile = swap(stagedFile, argsToSwap[0].pos, argsToSwap[0].end -1, argsToSwap[1].pos, argsToSwap[1].end - 1)
          }
          tree.overwrite(filePath, prettier.format(stagedFile, {parser: 'typescript'}));
        }
      });
      return tree;
    };
  }
```
