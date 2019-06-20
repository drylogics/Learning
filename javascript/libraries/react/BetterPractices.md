
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
