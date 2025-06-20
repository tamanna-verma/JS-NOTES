
slice creation, 
It is a way to define a portion of the Redux state and the associated reducers and actions that operate on that state.

            // counterSlice.js

            import { createSlice } from '@reduxjs/toolkit';

            const counterSlice = createSlice({
              name: 'counter',
              initialState: {
                value: 0,
              },
              reducers: {
                increment: (state) => {
                  state.value += 1;
                },
                decrement: (state) => {
                  state.value -= 1;
                },
              },
            });

            export const { increment, decrement } = counterSlice.actions;
            export default counterSlice.reducer;
            
            

Store configuration:
each slice's reducer will be configured in the reducer:{...} of configureStore.

          // store.js

          import { configureStore } from '@reduxjs/toolkit';
          import counterReducer from './counterSlice';

          const store = configureStore({
            reducer: {
              counter: counterReducer,
            },
            

Add Store to the app:
            
        // App.js

        import React from 'react';
        import { Provider } from 'react-redux';
        import store from './store';

        function App() {
          return (
            <Provider store={store}>
              <Counter />
            </Provider>
          );
        }

        export default App;

          });

          export default store;



usage:

            // Counter.js

            import React from 'react';
            import { useSelector, useDispatch } from 'react-redux';
            import { increment, decrement } from './counterSlice';

            function Counter() {
              const counter = useSelector((state) => state.counter.value);
              const dispatch = useDispatch();

              const handleIncrement = () => {
                dispatch(increment());
              };

              const handleDecrement = () => {
                dispatch(decrement());
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



If we have two slices: 

          // store.js

          import { createStore, combineReducers } from 'redux';
          import counterReducer from './counterSlice';
          import userReducer from './userSlice';

          const rootReducer = combineReducers({
            counter: counterReducer,
            user: userReducer,
          });

          const store = createStore(rootReducer);

          export default store;


store will look something like this:


        {
          counter: { /* counter state */ },
          user: { /* user state */ }
        }

