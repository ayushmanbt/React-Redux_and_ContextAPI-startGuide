# Working With React and Redux

Working with Redux in react is not a thing which we, the small developers generally don't need. But it is a skill required by the industry. So this Markdown File is to guide me and others to set up Redux in React

## Packages needed

- react
- redux => for createStore, combineReducer
- react-redux => contains the methodes like **useDipatch**(used to dispatch an action) and **useSelector**(used to select things from global state) **Provider** is also a part of react-redux.

## Components of redux
***reducer*** => these are actually functions with state and actions passed in .. they work with **action.type** in swich cases and return the updated state it optionally needs to accept **payload** to work properly..
Sometimes you will need to merge seperate reducers before creating a store
(generally in *reducer folder* for each reducer)

***store*** => store is the hub of all data. It is also passed to the provider
(generally created in *index.js*, but the combining of reduceers happen in a *index.js* in reducer folder)

***provider*** => a react based component which takes store as an arguement
(generally created in *index.js*)

***actions*** => functions providing / returning payload and action type to the dispacher which will call the required reducer.
(generally created in *seperate file called actions.js*)


## Folder Structure 

- src/ 
    - actions
        -index.js [this file stores all the actions which we need to call using dipatcher] example =>
        ```JS
            export const action_a = (data) => {
                return {
                    type: "ACTION_NAME", //generally action names are written in all caps
                    payload: data
                }
            }
        ```
    - reducers
        -reducer1.js example =>
        ```JS
            const initialState = 0
            export const reducer1 = (state = initialstate, action) => {
                switch(action){
                    case 'ACTION_NAME':
                        return state + payload; // always return the complete updated set, using spread operator will be helpful
                    default: 
                        return state;
                }
            }
        ```
        -reducer2.js
        -index.js [for exporting the **combineReducer()** product] example =>
        ```js
            import { combineReduce } from 'Redux';
            import { reducer1 } from './reducer1';
            import { reducer2 } from './reducer2';

            export default allReducer = combineReducer({
                reducer1,
                reducer2
            })
        ```
    - App.js (React App component)
    - index.js (Main injecting component) => 
        ```JS
            import React from 'react'
            import ReactDOM from 'react-dom';
            import App from './App'
            import { Provider } from 'react-redux'
            import { createStore } from 'redux'
            import allReducer from './reducers'
            

            const store = createStore(allReducer ,//this is for devtools-redux
            window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
            );

            ReactDOM.render(
            <Provider store = {store}>
                <App />
            </Provider>
            ,
            document.getElementById('root'));

        ``` 
        
To understand Closely follow the repo [REACT-REDUX-BASIC](https://www.google.com)