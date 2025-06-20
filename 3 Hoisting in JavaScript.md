Hoisting in JavaScript is a behavior in which a function or a variable can be used before declaration.
Because, the memory is allocated to each and every variable and function in the memory allocation phase.

![image](https://user-images.githubusercontent.com/72781278/206376632-b0ea928e-cc14-4168-b33b-e05218aa2940.png)

Even before executing the first line of the code, the memory allocation phase have completed, and code execution phase have started.

##### So, Output will be : 

Namastre Javascript 
undefined
f getName(){
  console.log("Namaste Javascript");
}

Undefined means, there is no value for the variable.
Not defined means, it is a referrence error when we access variable which is not created.

![image](https://user-images.githubusercontent.com/72781278/206377387-af5dff95-a46f-44c7-bfc6-a24f0383b899.png)

When we access arrow function, or function which is stored in variable before their creation then we get typeError, 
saying that variable is not a function.
Because at first all variables get undefined.
In the code execution phase, those variables which contains then they store the function and work like functions.

![image](https://user-images.githubusercontent.com/72781278/206379293-077d3fe7-ccf0-41aa-8a31-7f9d215ccb4c.png)
