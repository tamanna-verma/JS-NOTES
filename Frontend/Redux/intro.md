
Redux Action creator functions, they create the action object for reducers, we can pass data using payload field.
They only return action object.

        // Redux Actions: actions.js

        export const INCREMENT_COUNTER = 'INCREMENT_COUNTER';
        export const DECREMENT_COUNTER = 'DECREMENT_COUNTER';

        export function incrementCounter() {
          return { type: INCREMENT_COUNTER };
        }

        export function decrementCounter() {
          return { type: DECREMENT_COUNTER };
        }



Redux reducers, they are called according to the action type they recieve. They do the real manipulation of state store.
If data is passed then it can be obtained using action.payload.
They are pure functions, only intended to do state manipulation and don't have access to outer environment.
Side effects not suggested to be used here, like API calls.

        // Redux Reducer: reducer.js

        import { INCREMENT_COUNTER, DECREMENT_COUNTER } from './actions';

        const initialState = {
          counter: 0
        };

        function counterReducer(state = initialState, action) {
          switch (action.type) {
            case INCREMENT_COUNTER:
              return { ...state, counter: state.counter + 1 };
            case DECREMENT_COUNTER:
              return { ...state, counter: state.counter - 1 };
            default:
              return state;
          }
        }

        export default counterReducer;


Store creation, whole project will have access to this store, to have access to the state data stores in Redux.
 
        // Redux Store Configuration: store.js

        import { createStore } from 'redux';
        import counterReducer from './reducer';

        const store = createStore(counterReducer);

        export default store;
        

Store inclusion in the project.

        // Main App Component: App.js

        import React from 'react';
        import { Provider } from 'react-redux';
        import Counter from './Counter';
        import store from './store';

        function App() {
          return (
            <Provider store={store}>
              <Counter />
            </Provider>
          );
        }

        export default App;


useDispatch return dispatch function which can call the reducer functions.
useSelector is used to store a field of store in a variable.
When this variable changes, component re-renders.

          // React Component: Counter.js

          import React from 'react';
          import { useSelector, useDispatch } from 'react-redux';
          import { incrementCounter, decrementCounter } from './actions';

          function Counter() {
            const counter = useSelector(state => state.counter);
            const dispatch = useDispatch();

            const handleIncrement = () => {
              dispatch(incrementCounter());
            };

            const handleDecrement = () => {
              dispatch(decrementCounter());
            };

            return (
              <div>
                <h1>Counter: {counter}</h1>
                <button onClick={handleIncrement}>Increment</button>
                <button onClick={handleDecrement}>Decrement</button>
              </div>
            );
          }

          export default Counter;

