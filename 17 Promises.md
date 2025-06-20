Promises are a feature in JavaScript that provide a more organized and efficient way to handle asynchronous operations. A promise is an object that represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

Promises have three states:

- Pending: The initial state, neither fulfilled nor rejected.
- Fulfilled: Meaning that the operation completed successfully.
- Rejected: Meaning that the operation failed.

Promises provide a way to register callbacks to be called when the promise is fulfilled or rejected, rather than passing callbacks to functions. This allows for a more structured way of handling asynchronous operations, and makes it easier to chain multiple asynchronous operations together.

Promises have a then method that can be used to register callbacks that are called when the promise is fulfilled, and a catch method that can be used to register callbacks that are called when the promise is rejected.

Promises can be used to handle asynchronous operations such as fetching data from a server, reading from a file, or interacting with a database. They are widely supported in modern JavaScript environments and libraries, and are widely used as an alternative to callbacks to handle asynchronous operations in JavaScript.

The new feature Async/Await is built on top of promises, making it more readable and easy to reason about.


      const API = "https://api.github.com/surajthapliyal";

      const user = fetch(API);

user now stores a promise (resolved when done, rejected when error).
Promise is basically an object.

In pending state (data is undefined, will contain data once promise fullfilled):

![image](https://user-images.githubusercontent.com/72781278/213845049-6a1b9104-7873-4022-968c-c41fa35102e4.png)


      console.log(user);
      
![image](https://user-images.githubusercontent.com/72781278/213845112-44be3ac4-e25a-4893-9b2f-ef92f6f5a63e.png)

pending as the console.log was done when it was pending, but when it was fullflled, the data is stored in the object and is printed as fullfilled.

returned data is immutable and is stored inside the  [[PromiseResult]] data field in the form of ReadableStream.

to access that data:

      user.then((data)=>{
        console.log(data);
      })
      
![image](https://user-images.githubusercontent.com/72781278/213845657-0939bbfd-e3a2-47f2-bac4-7c568cbd6e46.png)

Must write return to return the data to get it on the next chained .then()

![image](https://user-images.githubusercontent.com/72781278/213845708-2a9dd236-b6c3-4f36-8539-a522e9e2db32.png)

