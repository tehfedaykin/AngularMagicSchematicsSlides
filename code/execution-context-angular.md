## Real World Execution Context in Angular

```typescript
constructor(httpClient: HttpClient) {
    const apiCall = httpClient.get('https://acnhapi.com/v1/villagers/1');

    apiCall.subscribe(val => {
        // get request made
        console.log('doing something with', val);
    });

    apiCall.subscribe(val => {
        // get request made AGAIN
        console.log('doing something else with', val);
    });
}
```