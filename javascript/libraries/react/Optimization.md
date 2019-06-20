# Optimization

> “The real problem is that programmers have spent far too much time worrying about efficiency in the wrong places and at the wrong times; **premature optimization is the root of all evil** (or at least most of it) in programming.”     - Donald Knuth (The Art of Computer Programming)

## Use Objects instead of Arrays for storing lists
**Why not to use Arrays**
 - Always have to iterate for Read, Update or Delete action in Arrays.
 - When merging api results (like infinite scroll), you have to check for duplicates.

**When to use Arrays**
 - You want the list to be in a specific order
 - You dont have an unique identifier between list items

## Avoiding Unnecessary Rerenders
**Careful with props** 
```javascript
// below will rerender each time
const DontCreateObjectProps = () => <PureComponent style={{ color: 'red'}} />
const DontCreateAnonymousFnProps = () => <PureComponent onPress={() => {}} />
const DontCreateChildrenProps = () => <PureComponent><span>Hello</span></PureComponent>
```
