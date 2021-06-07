## Imperative Code

Component: 

```TypeScript
ngOnInit(): void {
  this.apiService.getVillagers().subscribe((villagers: Villager[]) => {
    this.displayedVillagers = this.villagers = villagers;
  });
}

filterList() { // function called when user clicks
  this.displayedVillagers = this.villagers.filter((villager: Villager) => {
    const villagerVals = Object.values(villager);
    return villagerVals.some(r=> this.filters.includes(r));
  })
}
```

Template: 

```html
<mat-card *ngFor="let villager of displayedVillagers">
    {{villager.name}}
</mat-card>
```