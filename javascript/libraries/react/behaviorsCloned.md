### Default Props

```javascript
class Foo {
  constructor(props) {
    this.setThings(props)
  }
  setThings(recieved) {
    const allProps = {...(this.constructor.dProps || {}), ...recieved};
    for (const prop in allProps) {
      if (allProps.hasOwnProperty(prop)) {
        this[prop] = allProps[prop];
      }
    }
  }
}

Foo.dProps = {
  a: 1,
  b: 2,
  c: 3
}
f = new Foo({c: 33})

console.log(f.a) // 1
console.log(f.b) // 2
console.log(f.c) // 33
```