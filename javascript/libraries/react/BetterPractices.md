
# Better Practices

## Keep Components Logic free as possible
Condsider a `ContactItem` component as follows
```javascript
ContactItem.propTypes = {
  name: PropTypes.string.isRequired,
  pictureUrl: PropTypes.string.isRequired,
};
```
If there is a case that the person wants to use a default picture instead of the profile picture
```javascript
// Bad way
ContactItem.propTypes = {
  name: PropTypes.string.isRequired,
  pictureUrl: PropTypes.string.isRequired,
  defaultPictureUrl: PropTypes.string.isRequired,
  preferDefault: PropTypes.boolean.isRequired
};
```
Either we could have the logic in its parent but then it is the same problem we handle again, `logic in the wrong place`
But we could have a **`container`** which will do all sort of logic works and just pass the data to the natural component.
```
/ContactItem
  -ContactItem.js ------ the "natural" component
  -index.js ----------- the "container"
```
[source](https://medium.com/@ricokahler/how-the-golden-rule-of-react-components-can-help-you-write-better-code-127046b478eb)

## Use ES6 defaults against React defaultProps
-   React def. values lets us have a unified way of setting default values.
-   React def. values will be slower the more default values you set.
-   ES6 def. values may reduce your bundle size if deploying to browsers that already have destructuring assignment enabled.
-   When using ES6 def. values you have to remember the pitfalls and create non primitive values upfront so they won’t cause a render on child elements.
-   The React team decided on ES6 def. values as a way to set default values for functional components. A warning was already [added](https://github.com/facebook/react/pull/16210) as a part of the process to deprecate `defaultProps` in functional components.
```javascript
const defaultUser = {firstName = 'John', lastName = 'Doe'}
const ContactItem = ({user = defaultUser }) => {
	return(<span>{`${user.firstName} ${user.lastName}`}</span>)
};
```
[source](https://medium.com/@matanbobi/react-defaultprops-is-dying-whos-the-contender-443c19d9e7f1)
