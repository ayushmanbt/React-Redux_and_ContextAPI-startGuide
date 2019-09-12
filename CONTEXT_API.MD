# Working With Context API in React

**Context API** is the Built in way of react to handle global state mannagement and it is easier than **Redux**

## Important things

***provider*** => This is a react component with a state and a return JSX

***context*** => it is created using a function called createContext()

## Structure of Context.js

```JS
    import React, {useState, createContext} from 'react' 

    export const xyzContext = createContext();

    export const xyzProvider = (props) => {

        const [state, setState] = useState([1,2,3]);

        return(
            <xyzContext.Povider value = {[state, setState]}>{props.childern}</xyzContext.Povider>
        )
    }
```

Now just import the Provider and wrap the App with that component



Now in individual component import Context and useContext

const value = useContext(xyzContext);