### Store

```typescript
const initialState: VillagerState ={
  villagers: [],
  selectedSortOption: undefined,
  filterOptions: [],
  showOnlyFavorites: false
}

function createStore(reducer, initialState) {
  let state = initialState;
  function getState() {
    return state;
  }

  function dispatch(action) {
    state = reducer(state, action);
  }

  return { getState, dispatch };
}
```