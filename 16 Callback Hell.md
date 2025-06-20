To make dependency in asynchronous callbacks, like proceedToPayment() callback function will be executed after createOrder() function gets executed asynchronously and then showOrderSummary() to execute once the proceedToPayment() is done executing : 
          
          api.createOrder(cart , function(){
            api.proceedToPayment(function(){
              api.showOrderSummary();
            });
          })

now it is the responsibility of createOrder() implementation to execute the proceedToPayment() function, once the work of createOrder() is done.

In JavaScript, you can use promises to chain callbacks together in a specific order. Here's an example of how you might use promises to make sure that the proceedToPayment() callback is called after the createOrder() callback, and the showOrderSummary() callback is called after the proceedToPayment() callback:

        function createOrder() {
            // Code to create an order
            return new Promise((resolve, reject) => {
                // If the order is successfully created
                resolve();
            });
        }

        function proceedToPayment() {
            // Code to proceed to payment
        }

        function showOrderSummary() {
            // Code to show the order summary
        }

        createOrder()
            .then(() => {
                proceedToPayment();
            })
            .then(() => {
                showOrderSummary();
            });

In this example, the createOrder() function returns a promise, which is resolved when the order is successfully created. The then() method is used to call the proceedToPayment() callback after the promise is resolved. Then, then() is used again to call the showOrderSummary() callback after the proceedToPayment() callback is called.


If the proceedToPayment() function also needs to perform an asynchronous operation, such as sending a request to a server to make a payment, then it should also return a promise so that the next callback in the chain (in this case, showOrderSummary()) is not called until the payment has been successfully processed.

However, if proceedToPayment() is only performing synchronous operations, such as updating the state of your application or displaying a message to the user, then it does not need to return a promise.

But if you need to update the state of your application or call some api then you can return promise from proceedToPayment() as well.

        function proceedToPayment() {
            // Code to proceed to payment
            return new Promise((resolve, reject) => {
                // If the payment is successful
                resolve();
            });
        }
        
        
Callback hell is a term used to describe a situation where a program becomes difficult to read, understand, and maintain due to a large number of nested callbacks. This often happens when using callbacks to handle asynchronous operations in JavaScript. As the number of asynchronous operations increases, the code can become increasingly nested and hard to read, making it difficult to reason about the program's behavior.

Here's an example of callback hell, and the deep nesting of callbacks function is called Pyramid of Doom:

          function getData(callback) {
              // Code to fetch data
              callback(data);
          }

          function processData(data, callback) {
              // Code to process data
              callback(processedData);
          }

          function displayData(processedData, callback) {
              // Code to display data
              callback();
          }

          getData(function(data) {
              processData(data, function(processedData) {
                  displayData(processedData, function() {
                      // More code
                      getData(function(data) {
                          processData(data, function(processedData) {
                              displayData(processedData, function() {
                                  // Even more code
                              });
                          });
                      });
                  });
              });
          });

In this example, the code is nested several levels deep, making it difficult to understand the overall flow of the program.

To avoid callback hell, you can use other techniques such as Promises, async/await, generators, and more. These techniques can make the code more readable, easier to understand and maintain.


In case of callback chaining, the control of calling the next callback is given to a callback after whose execution we want to call that other callbck function. Its now the responsibility of that callback to call it and do the required things, but we can't trust it that way, as we dont know whether its calling perfectly or even calling it or not. This is called inversion of control. This can be resolved using Promises.
