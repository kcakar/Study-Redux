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
    &nbsp;
    With immutability you always clone and object and apply changes to the new object using below function:
    &nbsp;
    `Object.Assign({},state,{points:50});`
    -First parameter is the initial object we create.
    -Second parameter is what you want to copy into the initial object.
    -Third parameter is what you want to merge with the object.
    &nbsp;
    Immutability allows you to have State Snapshots, Undo changes and reload from URL in a single page app.
