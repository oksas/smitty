# smitty

[![npm version](https://badge.fury.io/js/smitty.svg)](https://badge.fury.io/js/smitty)

Tiny flux implementation built on [mitt](https://git.io/mitt)

### Demos
[Basic Example - CodePen](http://codepen.io/tkh44/pen/zNNPPq)


### Basics
```javascript
import { createStore } from 'smitty'

const store = createStore({ count: 0 })

// lets add one reducer
store.addReducer({
  'count/ADD': (state, e) => {
    // just log out the action and return original state
    console.log('count/ADD\n', JSON.stringify(e, null, 2))
    return state
  }
})

// lets add another
store.addReducer({
  'count/ADD': (state, e) => {
    // increment foos by ammount and return NEW state
    return Object.assign({}, state, { count: state.count + e.ammount })
  }
})

store.emit('foo/ADD', { ammount: 5 })
console.log(store.state)
```
