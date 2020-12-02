### Reducer

```typescript
function reducer(state, action) {
  switch (action.type) {
    case 'LOAD_VILLAGERS':
      return {
        ...state,
        villagers: action.payload,
      };
    case 'SELECT_SORT':
      return {
        ...state,
        selectedSortOption: action.payload,
      };
    default:
      return state;
  }
}
```