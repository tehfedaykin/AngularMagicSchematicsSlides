## Declarative Code

Component: 

```TypeScript
ngOnInit(): void {
  const villagersApi$ = this.apiService.getVillagers();
  this.displayedVillagers$ = this.villagersApi$;
}
```

Template: 

```html
<mat-card *ngFor="let villager of displayedVillagers$ | async">
    {{villager.name}}
</mat-card>
```