
# Fetch

## There are 4 states in fetch. Not 3. 
States: `fetching`, `fetchSuccess`, `fetchFailure` and **`fetchTimeout`**
 - Leaving out `fetchTimeout` might result in unhappy user experiences like spinners showing infinitely.
 - The causes of `fetchTimeout` could be like 
	 - user navigated while loading
	 - server timeout
	 
## Handling the states
**Better way** 
```javascript
const initialState = {  
	updating: false,  
	updated: false,  
	updateError: null
}

// usual way
switch (action.type) {
	case  'updating':
		return { updated: false, updating: true }
	case  'updated':
		return { updating: false, updated: true }
	case  'set-error':
		return { updating: false, updated:false, updateError: action.error }
	default:
		return  state
}

// better way
switch (action.type) {
	case  'updating':
		return { ...initialState, updating: true }
	case  'updated':
		return { ...initialState, updated: true }
	case  'set-error':
		return { ...initialState, updateError: action.error }
	default:
		return  state
}
```
