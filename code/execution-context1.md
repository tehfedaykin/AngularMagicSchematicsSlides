## Execution Context

For every new subscription, a new execution. 

```typescript
const ourObservable = new Observable(observer => {
    console.log('execution context going');
    observer.next(1);
    observer.next(2);
    observer.next(3);
});

ourObservable.subscribe(value => {
    // Logs 'execution context going'
    console.log('got value ' + value);
    // Logs 1, 2, 3
});

ourObservable.subscribe(value => {
    // Logs 'execution context going'
    console.log('got value ' + value);
    // Logs 1, 2, 3
});
```