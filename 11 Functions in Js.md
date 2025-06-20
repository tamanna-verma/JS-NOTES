### Function Statement: 

      function(){
        console.log("a");
      }

### Function Expression:

      var b = function(){
          console.log("a");
      }
      
Difference between function statement and function expression is hoisting.

### Function Declaration:

      function(){
        console.log("a");
      }
similar to function statement.

### Anonymous Functions: 

A function without a name, does not have thier own identity.

      function () {

      }
      
but cant be created like this,
An anonymous function is not accessible after its initial creation, it can only be accessed by a variable it is stored in as a function as a value. An anonymous function can also have multiple arguments, but only one expression.

      var a = function(){

      }

We may also declare anonymous function using arrow function technique which is shown below:

      (()=>{
        //function body
      })();
      
in react,

      useState(()=>{},[])

### Named Function Expression: 

expression function with a name associated with.

      var b = function xyz(){
            // function body
      }

but, calling function xyz() is error, because it is not created in the global scope, instead it is created and assigned to the variable b which is in globla scope, so b() is correct.

       var b = function xyz(){
             console.log(xyz);
             //recur
             xyz();
       }

it is correct.

### Parameter amd Argument:

      function x(parameters...)

      x(arguments....)

### First Class Functions:

First-class functions is functions treated like any other variables. So the functions can be assigned to any other variable or passed as an argument or can be returned by another function.

      var b = function (f){
            f();
            return ()=>{
                  //function code
            }
      }
      
      function xyz(){
            // function code
      }
      
      b(xyz);
      
      b(()=>{
            // function code
      })

here the function assigned to var b, function passed as an argument to function assigned in var b are becuase function in JS are first class functions.
