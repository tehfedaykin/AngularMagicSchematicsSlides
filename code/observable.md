### Observable

A lazy Push collection of multiple values over time. 

```typescript
const {Observable} = rxjs;

const observable = Observable.create(function (observer) {
  observer.next(1);
  observer.next(2);
  observer.next(3);
});

observable.subscribe((value)  => {
  console.log('got value ' + value);
    // Logs "got value 1"
    // Logs "got value 2"
    // Logs "got value 3"
});
```