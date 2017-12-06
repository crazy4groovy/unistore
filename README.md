# unistore

A tiny store + connect implementation for [Preact].

### Usage

```js
import { Provider, createStore, connect } from 'unistore'

let store = createStore({ count: 0 })

// Actions are just functions that call store.setState()
let actions = store => ({
	increment() {
		store.setState({ count: store.getState().count+1 })
	}
})

const App = connect('counter', actions)(
	({ count, increment }) => (
		<div>
			<p>Count: {count}</p>
			<button onClick={increment}>Increment</button>
		</div>
	)
)

export default () => (
	<Provider store={store}>
		<App />
	</Provider>
)
```

### API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### createStore

Creates a new store, which is a tiny evented state container.

**Parameters**

-   `state`   (optional, default `{}`)

**Examples**

```javascript
let store = createStore();
   store.subscribe( state => console.log(state) );
   store.setState({ a: 'b' });   // logs { a: 'b' }
   store.setState({ c: 'd' });   // logs { c: 'd' }
```

#### connect

Wire a component up to the store. Passes state as props, re-renders on change.

**Parameters**

-   `mapStateToProps` **([Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function) \| [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array) \| [String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String))** A function mapping of store state to prop values, or an array/CSV of properties to map.
-   `actions` **([Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function) \| [Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object))?** Action functions (pure state mappings), or a factory returning them.

**Examples**

```javascript
const Foo = connect('foo,bar')( ({ foo, bar }) => <div /> )
```

### License

MIT

[preact]: https://github.com/developit/preact
