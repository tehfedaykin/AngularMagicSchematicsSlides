## Reactive Code

Component: 

```TypeScript
ngOnInit(): void {
  const villagersApi$ = this.apiService.getVillagers();
  this.displayedVillagers$ = this.filterSubject$.pipe(
      withLatestFrom(this.villagersApi$),
      map(([filters, villagersAPI]) => {
          return villagersAPI.filter((villager: Villager) => {
              const villagerVals = Object.values(villager);
              return villagerVals.some(r=> filters.includes(r));
          })
      });
}

filterList() { // function called when user clicks
  this.filterSubject$.next(this.filters);
}
```