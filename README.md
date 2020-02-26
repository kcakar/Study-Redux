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

## Store interactions
You can access the store to get the state or set the state.
1. Create a store with your default state.
2. Create your subscriptions and subscribe them using .subscribe.
3. Dispact actions to change the state.

**Note:**
When you create a store, all reducers are called once.

**IMPORTANT**   
**NEVER** modify state directly. You have to make immutable updates.  
Always use Object.assign({},state,{propertyName:propertyValue}) or the object spread operator:  
{...state , originAmount:action.payload}
This is to make sure we have access to the history.

* **Subscribe** (function)  
Subscribe function is used to changes in the store. You can get the current state using **store.getState()** method. The passed function will be called whenever a change happens in the state.

* **Dispatch** ({type:"ACTION_NAME",payload:{})  
You can set the state only through actions. And you do that through dispatch method. Dispact method has an object as a parameter and this object has the type and the payload in it. 

* **Reducer** (state = defaultState, action)
Whenever an action is dispatched, all reducers get called. You basically check the type of action and if it is your type, you change the state. If not you return the state without modifiying it.
    
    


