In JavaScript, a higher-order function is a function that takes one or more functions as arguments, and/or returns a function as its result. 

Ex: 

      function repeat(operation, num) {
          for (let i = 0; i < num; i++) {
              operation();
          }
      }
      
Another example of Higher order function is map and filter:

      const numbers = [1, 2, 3, 4, 5];
      const double = x => x * 2;
      const doubledNumbers = numbers.map(double);
      console.log(doubledNumbers); // [2, 4, 6, 8, 10]

      const evenNumbers = numbers.filter(x => x % 2 === 0);
      console.log(evenNumbers); // [2, 4]

In the example I provided, the function passed to the map() method, double, is an arrow function, which is a shorthand syntax for defining a function. In this case, when we pass double to map, it is equivalent to passing double(). If we had written double() instead of double, it would have called the function immediately and passed its return value to map, rather than passing the function itself.

In JavaScript, when you pass a function without parentheses as an argument to another function, it is called a function reference. This means that the function is being passed by reference, and the receiving function can call the function later.

On the other hand, if you pass a function with parentheses as an argument, it is called a function invocation. This means that the function is being called immediately and its return value is passed as an argument to the receiving function.

So in short, the reason why we didn't wrote parenthesis in the double function on map function is because we want to pass the function itself as a reference, not the result of calling the function.


Follow DRY Principle : 

![image](https://user-images.githubusercontent.com/72781278/213467459-7c8a6ae3-fd18-4ecc-b41b-3ff7db8668fc.png)

Can be also done using Higher Order Function, this code follows DRY Principle: 

![image](https://user-images.githubusercontent.com/72781278/213467785-ab3c7bd5-170e-439f-a61b-f932f41714d3.png)


Can also be done using map:

      console.log(radius.map(area));
      console.log(radius.map(circumference));
      console.log(radius.map(diameter));
      
To use calculate function like the map function (available for all arrays) : 
Attach it with Arrays.prototype

      Attach.prototype.calculate = function (logic) => {
        const output = []
        // this points to the array for which it is called upon.
        for(let i=0;i<this.length;i++){
          output.push(logic(this[i]));
        }
        return output;
      }

      console.log(radius.calculate(area));
