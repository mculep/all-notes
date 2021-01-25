#### What does the React Dev Server do?

---

- load browser
- watch for changes
- reload your changes



#### Getting started

----

* npx create-react-app *name of app*

* Delete everything in the default README.md file. 

* npm start

* Go to src > app.js

* Get everything inside of header

* Next to memory in inspect find the components tool

* create a HelloReact.js

* 1. import React

     - import React from 'react';

  2. write your component

     - export default HelloReact (function name); 

  3. 

  4. ```javascript
     function HelloReact () {
     		return (
     		<div className="message">
     		  	Hello Custom Component!!!!
     		</div>
     	);
     }
     export default HelloReact;
     ```


​     

* #### propname {value of prop inside bere } | props - Are arguements, 

* #### state

  ### 

### Basic React Hooks

---

* useState
* useEffect
* useContext
* useReducer
* useCallback
* useMemo
* useRef
* useImperativeHandle
* useLayoutEffect
* useDebugValue



### useState Hook

-----

> Value:  Will be your initial state (You can call it whatever you want)
>
> setValue: Will be your function to set a new state

```jsx
const [value, setValue] = useState(Whatever you put in here is your starter value)

```

![useState](https://github.com/mculep/all-notes/blob/main/assets/useState.png)


### Conditional Rendering: 

* Example if someone is not logged in, do not show their name. If they are logged in,  welcome them with   their name. 

* Use a ternary if you have a real alternative



```jsx
function PhotoCard(props) {
  console.log(props);
  
  return (
  	<div className="card-frame">
    	{props.title && <h3>{props.title}</h3>}  //ternary
      <img src={props.url} alt={props.description} />
      <p>{props.description}</p>
    </div>
  )
}
```

