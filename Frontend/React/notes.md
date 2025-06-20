    import React, { Component } from 'react';

    class ExampleComponent extends Component {
      constructor(props) {
        super(props);
        this.state = {
          count: 0,
        };
        console.log('constructor');
      }

      static getDerivedStateFromProps(props, state) {
        console.log('getDerivedStateFromProps', props, state);
        return null;
      }

      componentDidMount() {
        console.log('componentDidMount');
      }

      shouldComponentUpdate(nextProps, nextState) {
        console.log('shouldComponentUpdate', nextProps, nextState);
        return true;
      }

      getSnapshotBeforeUpdate(prevProps, prevState) {
        console.log('getSnapshotBeforeUpdate', prevProps, prevState);
        return null;
      }

      componentDidUpdate(prevProps, prevState, snapshot) {
        console.log('componentDidUpdate', prevProps, prevState, snapshot);
      }

      componentWillUnmount() {
        console.log('componentWillUnmount');
      }

      handleClick = () => {
        this.setState((prevState) => ({ count: prevState.count + 1 }));
      };

      render() {
        console.log('render');
        return (
          <div>
            <p>Count: {this.state.count}</p>
            <button onClick={this.handleClick}>Increment</button>
          </div>
        );
      }
    }

    export default ExampleComponent;


### OUTPUT:

    constructor
    getDerivedStateFromProps {}
    render
    componentDidMount
    shouldComponentUpdate {} {count: 0}
    getSnapshotBeforeUpdate {} {count: 0}
    componentDidUpdate {} {count: 0} null
    shouldComponentUpdate {} {count: 1}
    getSnapshotBeforeUpdate {count: 0} {count: 1}
    componentDidUpdate {count: 0} {count: 1} null

This output shows that the component is initially constructed and then mounted to the DOM. When the button is clicked, the state is updated and the component is re-rendered. During this re-render, the shouldComponentUpdate() method is called to determine if the component needs to update. Since the method returns true, the component is updated and the getSnapshotBeforeUpdate() and componentDidUpdate() methods are called.

It's important to note that the console output may vary depending on the specific actions taken in the component, but understanding the lifecycle methods and their order of execution will help you make an educated prediction of how the component will respond.


### why getDerivedStateFromProps method is static in the above code ?

Sure! In simpler terms, the getDerivedStateFromProps method is a special function that React calls automatically when a component receives new props or state. Its job is to take in the current props and state and return a new state object if necessary.

In the above code, getDerivedStateFromProps is declared as a static method because it doesn't need to access any instance variables or methods of the component. It only relies on its inputs (props and state) to do its job.

By making getDerivedStateFromProps a static method, it can be called without having to create an instance of the component. This makes it a more efficient way to update the component's state based on changes in props or state.

Overall, getDerivedStateFromProps is a useful method for handling certain kinds of updates to a component's state, but it's important to use it judiciously and not rely on it too heavily, since it can make the component's state more complex and harder to reason about.

### but we never instantiate the class in react inorder to render the component ?

You are correct that we don't explicitly create instances of React components ourselves, but rather let React handle the instantiation and rendering of components for us.

When I said that getDerivedStateFromProps can be called without having to create an instance of the component, I meant that it can be called on the component class itself, without having to first create an instance of the component. This is because getDerivedStateFromProps is a static method, which means it belongs to the class itself, rather than to individual instances of the class.

So, when a component is rendered, React creates an instance of the component class and calls its lifecycle methods, including getDerivedStateFromProps. But we as developers don't need to create these instances ourselves, since React does it for us under the hood.

### so in case of functional components, how react handles the instantiation to render the component ?

In functional components, React handles instantiation and rendering of the component automatically under the hood. When you define a functional component, you are essentially defining a function that returns some JSX elements.

When React needs to render the component, it simply calls this function and uses the returned JSX elements to create the component's rendered output. So, there's no need to manually instantiate the functional component like you would with a class component.


      import React, { useState, useEffect } from 'react';

      function MyComponent() {
        const [count, setCount] = useState(0);
        const [isDarkMode, setIsDarkMode] = useState(false);

        useEffect(() => {
          console.log('useEffect called');

          const intervalId = setInterval(() => {
            setCount((prevCount) => prevCount + 1);
          }, 1000);

          return () => {
            console.log('useEffect cleanup called');
            clearInterval(intervalId);
          };
        }, [isDarkMode]);

        const handleToggle = () => {
          setIsDarkMode((prevIsDarkMode) => !prevIsDarkMode);
        };

        return (
          <div>
            <button onClick={handleToggle}>Toggle dark mode</button>
            <p>Count: {count}</p>
          </div>
        );
      }

### OUTPUT: 

Answer: When the user clicks the button, the handleToggle function is called, which toggles the isDarkMode state. This causes the component to re-render.

When the component re-renders, the useEffect hook is called again, since isDarkMode is included as a dependency. This means that the interval is cleared and restarted, and the count state starts counting from 0 again. The console will log "useEffect cleanup called" and "useEffect called" when this happens.

Therefore, when the user clicks the button, the count will start from 0 again and start incrementing by 1 every second. The console will log "useEffect cleanup called" and "useEffect called" every time the button is clicked.

f the user clicks the button multiple times, the console will log "useEffect cleanup called" and "useEffect called" multiple times, as the useEffect hook is being called every time the isDarkMode state changes.

The output of the console will look something like this:

      useEffect called
      useEffect cleanup called
      useEffect called
      useEffect cleanup called
      useEffect called
      ...
      
      
### what is clearInterval() function ?

clearInterval() is a built-in JavaScript function that is used to stop the interval timer created using the setInterval() function.

When you create an interval using setInterval(), it returns a numeric ID that identifies the interval, which you can use to stop the interval using clearInterval().

For example, let's say you create an interval using setInterval() like this:

      const intervalId = setInterval(() => {
        console.log('Hello world!');
      }, 1000);

The interval will run every second and log "Hello world!" to the console. You can stop the interval using clearInterval() like this:

      clearInterval(intervalId);

This will stop the interval from running and prevent any further "Hello world!" messages from being logged to the console.

### what does setInterval do  exactly ? and what it returns ?

setInterval() is a built-in JavaScript function that is used to repeatedly execute a function at a specified time interval.

The setInterval() function takes two arguments: a function to be executed and a time interval in milliseconds at which the function should be executed.

For example, let's say you want to execute a function called updateTime() every second. You can use setInterval() like this:

    setInterval(updateTime, 1000);

This will call the updateTime() function every 1000 milliseconds (1 second).

setInterval() returns a numeric ID that identifies the interval, which you can use to stop the interval using the clearInterval() function. For example, you can store the interval ID in a variable like this:

    const intervalId = setInterval(updateTime, 1000);

To stop the interval, you can use clearInterval() like this:

    clearInterval(intervalId);

This will stop the interval with the specified ID from running.

### useState only gets called once in the whole component lifecycle ?

Yes, the useState hook is called once during the whole component lifecycle.

When a functional component is first mounted, React calls the function body and executes all of the statements inside it, including the useState hook. The useState hook initializes the state value to the provided initial value and returns an array with two elements: the current state value and a function to update it.

When the component re-renders due to changes in state or props, the function body is called again, but this time React uses the previous state value and state update function returned by the useState hook. This allows the component to maintain its state between renders and update the state value as needed.

### When component re-render because of change in ref-data ?

If an 

update to the ref does not affect the component's state or props, then React will not re-render the component. If an update to the ref affects the component's state or props, then React will re-render the component.

### In normal functions , this keyword is associated to which context ? and in arrow function ?

In normal functions defined in the global scope or in the scope of an object method, the this keyword refers to the global window object or the object that the method is called on, respectively. In normal functions defined inside another function, the this keyword can have a different context depending on how the function is called.

In arrow functions, the this keyword is lexically bound to the context of the surrounding scope, which means it retains the value of this from the enclosing function or global scope.


### Write react code for two state passing down in a class component using context

Here's an example of how you can use React Context to pass down two states from a parent component to its child components:

            import {createContext} from "react"
            export const MyContext = createContext();
            const App = ()=>{
                const [darkTheme,setDarkTheme] = useState(false)
                const [count, setCount] = useState(0)

                const handleClick = ()=>{
                    setDarkTheme(prev=>!prev)
                    setCount(prev=>prev+1)
                }

                return <MyContext.Provider value={{darkTheme,count}} > 
                        <button onClick={handleClick}>Change Theme</button>
                        <ClassComponent/>
                        <FunctionalComponent/>
                    </MyContext.Provider>
            }
            export default App
            
// Class Component

            class ClassComponent extends Component {
                constructor(){
                    super();
                    this.styles = this.styles.bind(this)
                }
                styles(dark){
                    return {
                        backgroundColor: dark ?"gray":"whitesmoke",
                        margin:"10px",
                        padding:"40px",
                    }
                }
                render(){
                    return <MyContext.Consumer>
                           {
                                data=>{
                                    return <div style={()=>this.styles(data.darkTheme)}>Class Component, count: {data.count}</div>
                                }
                           }
                    </MyContext.Consumer>
                }
            }


// Functional Component: 

            import {useContext} from "react"

            const FunctionalComponent = ()=> {
                const data = useContext(MyContext)

                const styles = {
                    backgroundColor : data.darkTheme ? "gray" : "whitesmoke",
                    margin:"20px",
                    padding:"40px",
                }

                return <div style={styles}> Functional Component, Count: {data.count} </div>   
            }
            export default FunctionalComponent;
            
### To restrict some child to access some passed state from the context: 
            
            import { createContext, useState } from "react";
            import ClassComponent from "./classComponent";
            import FunctionalComponent from "./functionalComponent";
            export const ThemeContext = createContext();
            export const ThemeAndCountContext = createContext();
            const App = () => {
              const [darkTheme, setDarkTheme] = useState(true);
              const [count, setCount] = useState(0);
              const handleClick = () => {
                setDarkTheme((prev) => !prev);
                setCount((prev) => prev + 1);
              };
              return (
                <div>
                  <button onClick={handleClick}>Theme change</button>
                  <ThemeContext.Provider value={darkTheme}>
                    <ClassComponent />
                  </ThemeContext.Provider>
                  <ThemeAndCountContext.Provider value={{ darkTheme, count }}>
                    <FunctionalComponent />
                  </ThemeAndCountContext.Provider>
                </div>
              );
            };

            export default App;
