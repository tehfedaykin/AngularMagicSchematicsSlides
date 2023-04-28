## Breaking Change in 3rd Party Library

Old Function
```typescript
export function breakingFunction(param1: string, param2: number) {
    const numberToString = param2.toString();
    return `${param1} is a string and ${numberToString} was a number`;
}
```

New Function
```typescript
export function breakingFunction(param1: number, param2: string) {
    const numberToString = param1.toString();
    return `${param2} is a string and ${numberToString} was a number`;
}
```