# elx [![NPM version](https://img.shields.io/npm/v/elx.svg?style=flat-square)](https://npmjs.com/package/elx) [![NPM downloads](https://img.shields.io/npm/dm/elx.svg?style=flat-square)](https://npmjs.com/package/elx) [![Build Status](https://img.shields.io/circleci/project/egoist/elx/master.svg?style=flat-square)](https://circleci.com/gh/egoist/elx)

## Install

```bash
$ npm install --save elx
```

## Usage

```js
import {elx} from 'elx'

// a counter in 4 lines
elx('button', 0)
  .on('click', 1)
  .reduce((state, received) => state + received)
  .subscribe((el, state) => el.textContent = state)
```

## Concepts

### Initial State

Every element has its initial state.

```js
// for the counter example
const initialState = 0
const source = elx('button', initialState)
```

### Handler for events

Notify your element with some data, of course it does not know how to handle the data for now.

```js
source.on('click', 1)
```

### Reducer

Tell your element how to get the new state after received data from event hander.

```js
// since it's just a count
// we simply add the currentState 
// and the received data in event handler
const reducer = (currentState, received) => currentState + received
source.reduce(reducer)
```

### Subscribe

Trigger when element's state got changed.

```js
source.subscribe((el, newState) => {
  el.textContent = newState
})
```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

[MIT](https://egoist.mit-license.org/) © [EGOIST](https://github.com/egoist)
