# Spread and Rest Operator!

### Spread vs Rest Operator
Spread Operator vs Rest Operator
```javascript
// Our list of numbers:

const set1 = [1, 2, 3, 4, 5];
const set2 = [6, 7, 8, 9, 10];

const combined = [...set1, ...set2]; // spread operator

function sum(...numbers) { // rest operator
  return numbers.reduce((a, b) => a + b)
}

sum(...combined) // spread operator
```

### Downsides
- way too slower than `.apply` (spread is slower while rest is the slowest)
```javascript
// implementing using .apply
const set1 = [1, 2, 3, 4, 5];

// The good old way:
function sum() {
  return Array.apply(null, arguments).reduce((a, b) => a + b)
}

sum.apply(null, set1)
```
Lesson - ***consider for arrays with large number of elements*** (Note: Future updates of node, browsers, transpilers might continuously improve on this. So, not a big deal.)
