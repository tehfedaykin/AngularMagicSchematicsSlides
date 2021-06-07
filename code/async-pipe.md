## Our Hero: The Async Pipe

```typescript
// summarized from Angular source code
@Pipe({name: 'async', pure: false})
export class AsyncPipe implements OnDestroy, PipeTransform {
  ngOnDestroy(): void {
    if (this._subscription) {
      this._dispose();
    }
  }
  transform<T>(obj: Observable<T>|Subscribable<T>|Promise<T>|null|undefined): T|null {
    if (!this._obj) {
      if (obj) { this._subscribe(obj); }
      return this._latestValue;
    }
    return this._latestValue;
  }

  private _subscribe(obj: Subscribable<any>|Promise<any>|EventEmitter<any>): void {
    this._obj = obj;
    this._strategy = this._selectStrategy(obj);
    this._subscription = this._strategy.createSubscription(
        obj, (value: Object) => this._updateLatestValue(obj, value));
  }
  private _updateLatestValue(async: any, value: Object): void {
    if (async === this._obj) {
      this._latestValue = value;
      this._ref.markForCheck();
    }
  }
}
```

Creates a subscription to the Observable we pass it AND unsubscribes in the OnDestroy lifecycle hook.