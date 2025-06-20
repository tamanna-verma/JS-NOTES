![image](https://user-images.githubusercontent.com/72781278/206865818-5315800f-577b-4695-a3f7-e9fa213def66.png)

Web APIs are provided by browser, they are not a part of Js, but can be used in javscript

When any asynchronous code is executed, the call back it is having, gets registered.
When the callback is done waiting, then it gets entered in the callback queue.
The event loop acts as a gatekeeper which continuously checks wheter there is anything in the callback queue that needs to be entered in the callstack.
If there's any , event loop enter it to the callstack.

![image](https://user-images.githubusercontent.com/72781278/206866213-8f2c2c74-3ffe-42fa-9df5-98fe6f6e278d.png)

--------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/72781278/206866335-553f2e04-d40f-42ec-a227-385a51d01ca9.png)

When click event happens : 

![image](https://user-images.githubusercontent.com/72781278/206866359-4168e65c-407b-43a7-887a-7686c87d30e7.png)

Callback queue's functions will only be put in the callstack when the callstack is empty.
After execution : 

![image](https://user-images.githubusercontent.com/72781278/206866380-76cb97aa-ce67-40a8-a920-8c52fdae1c72.png)


### Microtask Queue:
Similar to callback queue, but it has higher priority. 
functions inside microtask queue executed first than the callback queue's functions. 

![image](https://user-images.githubusercontent.com/72781278/206866567-2804acd8-dfaf-423f-98d8-10aa715c3dda.png)

![image](https://user-images.githubusercontent.com/72781278/206866578-7d73e3cc-9665-45b6-931f-88dbc7d0110b.png)

![image](https://user-images.githubusercontent.com/72781278/206866594-48a6498e-9143-4753-8be9-c5003792de52.png)

All callback functions created through promises, comes inside the microtask queue.
Mutation observer's functions are also put inside the microtask queue
The MutationObserver interface provides the ability to watch for changes being made to the DOM tree. 

        // Create an observer instance linked to the callback function
        const observer = new MutationObserver(callback);

        // Start observing the target node for configured mutations
        observer.observe(targetNode, config);

        // Later, you can stop observing
        observer.disconnect();


### Starvation:
When microtask queue's functions are so much, or any function inside the microtask queue creted another function that too for the microtask queue recursively, then the functions of callback will not get chance to execute for a long or indefinte period of time, this phenomena is called startvation of callback functions.
