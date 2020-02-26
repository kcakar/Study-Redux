# Redux
Redux is a unidirectonal state manager. It makes use of immutable data and a history of states to have better control over states and a have better debugging experience.

## Terms
 * **Reducer**  
    Decides how to handle an action.
 * **Action**  
 * **Pure functions**  
 Below points are the characteristics of pure functions and they are what makes them reliable.
    * Uses only local variables. NO GLOBAL VARIABLES!
    * No side effects. Means they do not change anything in anywhere except variables in themselves.
    * Given the same input, you will always get the same output.
* **Immutability**  
    Without immutability you can apply changes to objects. But once the object has changed you have no idea about what it state was before or how it was changed or why it changed.  
    
* **Container/Presentational components**  
    You shouldn't connect all the components to the store. Instead, create a container component and connect it to the store. This component also has all the logic. Then create presentational components and pass what they need using props. These components do not know about redux, they do not connect to the store.

    With immutability you always clone and object and apply changes to the new object using below function:

    `Object.Assign({},state,{points:50});`  
    -First parameter is the initial object we create.  
    -Second parameter is what you want to copy into the initial object.  
    -Third parameter is what you want to merge with the object.  
    
    Immutability allows you to have State Snapshots, Undo changes, reload from URL in a single page app and time travel.

## What you need
* You need a default state
* You need a reducer. It will update the state. It takes two variables. State and action.
* You need a store. A store is where the state is saved. You pass the reducer to it.
* You need a Provider. Pass the store to the Provider to make it available in every component.
* You need to Connect each component you want to access the store using connect function.

## Packages
* react-redux: 
  * This has the **\<Provider\>** higher order component. It makes the store available in every component.
  * Has the **connect** method to connect components to the store. So that you can reach the store with this.props.
* redux: 
  * This has the **createStore** method used to create a store.
  * Has the **applyMiddleware** function. This function is used to use middleware packages such as logger or thunk.

## Convention
* Your store is stored in stores/configureStore.js file.
* Your presentational components are under /components folder.
* Your container components are under /containers folder.
* Your store needs to be accessed throughout the app.

## Store interactions
You can access the store to get the state or set the state.
1. Create a store with your default state.
2. Create your subscriptions and subscribe them using .subscribe.
3. Dispact actions to change the state.

**Note:**  
When you create a store, all reducers are called once.

**Note:**  
To init the store, you can use this trick: Use store.subscribe() method and use this.setState({}) to force rerender with state values.

**IMPORTANT**   
**NEVER** modify state directly. You have to make immutable updates.  
Always use `Object.assign({},state,{propertyName:propertyValue})` or the object spread operator:  
`{...state , originAmount:action.payload}`
This is to make sure we have access to the history.

# Functions
* **Subscribe** (function)  
Subscribe function is used to changes in the store. You can get the current state using **store.getState()** method. The passed function will be called whenever a change happens in the state. But with react-redux package, you shouldn't need to use this method. The subscribtions are managed with the connect method.

* **Dispatch** ({type:"ACTION_NAME",payload:{})  
You can set the state only through actions. And you do that through dispatch method. Dispact method has an object as a parameter and this object has the type and the payload in it. 

* **Reducer** (state = defaultState, action)
Whenever an action is dispatched, all reducers get called. You basically check the type of action and if it is your type, you change the state. If not you return the state without modifiying it.

* **createStore** (state, applyMiddleware(middlewareName))
    This function is where you create your store with a state and apply middleware to use.  
    Its in configureStore.js
    
* **Provider**  
    Makes the store available in every component. Wrap your main component with this. (react-redux component)  
    Its in App.js
    
* **connect function** (function mapStateToProps(state,props){})(ComponentName)  
    This function makes a component have access to the store. It needs one paramater. It is mapping function. This function gets called whenever the store is updated and we pass it to the props. And since this is a wrapper function, we pass the component for wrapping.  
    Its in every container component.

* **mapStateToProps** (state,props)  
  This function returns an object. The returned object is merged into the props of the component. This is how we expose the necessary parts of the store to the component. This function can also be anonymous but it is what you pass to the connect function.



