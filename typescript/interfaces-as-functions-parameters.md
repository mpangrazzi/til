Using interfaces as function parameters with TypeScript
===

In **JavaScript** when you have to manage multiple arguments in a funcion with some default values and/or mandatoriness, you usually tend to use an object (e.g. `params`) as the only argument:

```js
  const assert = require('assert')

  function example(params) {
    params = params || {}

    assert.equal(typeof params.url, 'string', 'url should be type string')
    assert.equal(typeof params.data, 'object', 'data should be type object')

    let id = params.id || 'defaultValue'

    // ...
  }

  example({
    url: 'http://www.example.com',
    data: { a: 'b' }
  })
```

Which is perfectly fine and works great.

In **TypeScript** you can do the same thing in the same way if you want, but you can also use an [Interface](https://www.typescriptlang.org/docs/handbook/interfaces.html) as the only argument, taking advantage of some language features:

```ts
  interface IExampleParams {
    url: string     // `url` IS mandatory
    data?: object   // `data` is not mandatory
    id?: ID         // `ID` is a custom type
  }

  function example(params: IExampleParams) {
    params.url                            // `url` is mandatory a string
    let data = params.data || { a: 'b' }  // `data` could be undefined

    // ...
  }

  function example(params?: IExampleParams) { // Also, `params` interface could be not mandatory...
    params = params || {}                     // ... and if it's missing, you'll have to assign a default value
    params.url                                // `url` is mandatory and is a string
    let data = params.data || { a: 'b' }      // check if `data` present because it's not mandatory

    // ...
  }

  example({
    url: 'http://www.example.com',
  })
```
