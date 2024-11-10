### Redux
state manager folosit pentru aplicatii mari. 

# Store  
- Globalized states.

import { createStore } from "redux"
- as argument of createStore we use the reucer

let store = createStore(reducer)

* if we have much than one reudcer we need to use :
<!-- combineReducers -->
import { combineReducers } from "redux";
const allReducers = combineReducers({
    counter  : counterReducer,
    isLogged : isLoggedReducer
})
then:
let store = createStore( allReducers )

* Provider
- connect our store to the entire app
* 
  <Provider store = {myStore}>
    <App />
  </Provider>

# Action 
- Name (type) of the action we wanna do (ex: increment).
- A function that returns an OBJECT
 <!-- action -->
  const increment = () =>{
    return {
      type:'increment'
    }
  }

# Dispatch
- send (dispatch) the Action to the Reducer and the store get updated.
 import { useDispatch } from "react-redux" 
 const dispach = useDispatch()
 <button onClick={() => dispach(increment())}>+</button>
 <button onClick={() => dispach(decrement())}>-</button>

# Reducer
- how the state will be changed in base of the action (name = type).
- as agruments it takes the 'initial value' and 'action'
<!-- reducer -->
  const counter = ( state = 0 , action) => {
    switch(action.type){
      
      case 'increment':
        return state + 1 ;

      case 'decrement':
        return state - 1 ;

      default: return state
    }
  }

* useSelector 
- pentru a avea aceces la datele din state , de ex valoarea lui counter actuala 

import { useSelector } from "react-redux" 
const counter = useSelector(state => state.counter)





















* window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__() 