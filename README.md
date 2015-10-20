# rxdart

[![Build Status](https://travis-ci.org/frankpepermans/rxdart.svg)](https://travis-ci.org/frankpepermans/rxdart)

This library uses the new Dart-Js interop available as of SDK 1.13.0

The RxJs library is wrapped and exposed via the Observable Dart class:

**Example:**

```dart
new Rx.Observable<int>.range(0, 100)
    .flatMapLatest((int x) => new Rx.Observable.from([x * 3]))
    .partition((int x) => x % 2 == 0)
      ..first
        .bufferWithCount(2)
        .subscribe((List<int> i) => print('even: $i'))
      ..last
        .bufferWithCount(3)
        .subscribe((List<int> i) => print('odd: $i'));
```