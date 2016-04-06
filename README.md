# [redux-elm](http://salsita.github.io/redux-elm)

> [The Elm Arhicture](https://github.com/evancz/elm-architecture-tutorial) in JavaScript for building really scalable applications.

`redux-elm` is framework specifically tailored for solving difficult problems that people have to face in modern front-end application development, it is heavily based on [Composition](http://salsita.github.io/redux-elm/composition/).

Goal of this project is to solve hard problems **by defining patterns, not implementation**. Library is very lightweight and you should be able to fully understand the codebase. Main building block is **[redux](http://github.com/reactjs/redux)** which serves as predictable state container and because `redux-elm` is built on top of that, you will be able to benefit from all of its tooling:


* [DevTools](https://github.com/zalmoxisus/redux-devtools-extension)
* Time Travel
* Immutable application snapshots
* Easy unit testing

Because `redux-elm` is about Patterns, we have really [thorough documentation](http://salsita.github.io/redux-elm) which guides you to utilize all the ideas that `redux-elm` provides.

## How does it look?

`redux-elm` is about Components and every Component must define two pieces `Updater` and `View` where `Updater` is very similar to Redux [`reducer`](http://redux.js.org/docs/basics/Reducers.html) and `View` is simple [`React`](https://facebook.github.io/react/) Component, of course you can use your own View library.

### Counter Updater

```javascript
import { Updater, Matchers } from 'redux-elm';

const initialModel = 0;

export default new Updater(initialModel, Matchers.exactMatcher)
  .case('Increment', function*(model) {
    return model + 1;
  })
  .case('Decrement', function*(model) {
    return model - 1;
  })
  .toReducer();
```

### Counter View

```javascript
import React from 'react';

export default ({ model, dispatch }) => (
  <div>
    <button onClick={() => dispatch({ type: 'Decrement' })}>-</button>
    <div>{model}</div>
    <button onClick={() => dispatch({ type: 'Increment' })}>+</button>
  </div>
);

```

## Documentation

Goal of documentation is explaining basic principle of `redux-elm` and this is Composition, it's divided into few chapters to gradually increase amount of complexity. 

1. [Getting Started Tutorial](http://salsita.github.io/redux-elm/getting-started/)
2. [GifViewer Tutorial](http://salsita.github.io/redux-elm/gif-viewer/)
3. [Composition](http://salsita.github.io/redux-elm/composition/)

First two chapters describes basic principles, while Composition part is the most important part explaining how `redux-elm` helps you building really scalable application.

## Examples

You will find original Elm Architecture examples written in JavaScript using `redux-elm`:

1. [Counter](./examples/counter)
2. [Counters Pair](./examples/pair-of-counters)
2. [Dynamic List of Counters](./examples/dynamic-list-of-counters)
2. [Random GIF Viewer](./examples/random-gif-viewer)
2. [Random GIF Viewers Pair](./examples/gif-viewer-pair)
2. [Dynamic List of Random GIF Viewers](./examples/gif-viewers-dynamic-list)

## Discussion
Join the [discussion on gitter](https://gitter.im/salsita/redux-elm)