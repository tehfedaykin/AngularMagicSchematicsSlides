### Actions

```typescript
interface Action {
    type: string;
    payload: any;
}
fetch(`https://acnhapi.com/v1/villagers`)
    .then(data => data.json())
    .then((res) => {
        store.dispatch({
            type: 'LOAD_VILLAGERS',
            payload: res,
        });
    })
```