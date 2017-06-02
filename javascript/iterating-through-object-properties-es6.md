Iterating through object properties with ES6
===

When I have to iterate through _plain_ JavaScript objects, I usually do something like:

```js
for (var key in obj) {
  console.log(key + " -> " + obj[key]);
}
```

And, if the object has a _non-default_ prototype:

```js
for (var key in obj) {
  if (obj.hasOwnobjroperty(key)) {
    console.log(key + " -> " + obj[key]);
  }
}
```

However, in an environment with _decent_ ES6 support, you can write something like this:

```js
for (let [key, value] of Object.entries(obj)) {
  console.log(key)
  console.log(value)
}
```

Which I think is way more elegant and useful. Basically, here we are using those ES6 features:

- [Object.entries](https://developer.mozilla.org/it/docs/Web/JavaScript/Reference/Global_Objects/Object/entries) 
- [Destructuring assignment](https://developer.mozilla.org/it/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [for...of statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)
