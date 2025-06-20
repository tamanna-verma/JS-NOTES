Functions passed as an argument to another function is Callback function.

      function greet(name, callback) {
          console.log('Hi' + ' ' + name);
          callback();
      }

      // callback function
      function callMe() {
          console.log('I am callback function');
      }

      // passing function as an argument
      greet('Peter', callMe);
      
In setTimeout, the call back  functions gets placed in the call stack after certains amount of time, so thats why it is called callback functions.

Some code which might take time to execute, like fetching data from any API, might block the main thread, as javascript is single threaded synchronous lang.
so we should never block the main thread, because it make program slow and execution of other code delay too.
For such kind of operations we should do asynchronous programming, use callbacks.

      function addEventListener() {
          let count = 0;
          document.getElementById("button").addEventListener("click",function(){
            // gets into callstack when click event occurs.
            console.log("button clicked = ", ++count, "times"); 
          })
      }
      
      addEventListener();

This is the best way to add event listener, through this way we dont have any global variables, 
the function also maintains the local closure state.

Event listener are heavy for memory, because, they continiously listen for the event to get occur.
So, we should remove them.
