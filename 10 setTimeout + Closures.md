setTimeout is an asynchronous function which calls the callback function after the certain ms.  

![image](https://user-images.githubusercontent.com/72781278/206741340-5be05b1f-1bde-44cd-9336-ed6a2dd197ee.png)

Output: 
Namaste Javascript
1(after 3 seconds)

even after 3 seconds, the callback function maintains its closure.
because its obvious that after 3sec, the EC of the x() will be removed out from GEC.

after 3 second, this callback function of setTimeout will again gets inside the callstack along with its closure and does its work.

![image](https://user-images.githubusercontent.com/72781278/206742376-8e1cb5d6-ac23-4623-b1c5-0ba8387cf1d0.png)

output: 

        6
        6
        6
        6
        6
        
because, closures store the referrence of the required varialbes not the static value of the required variable and var declared variables are not block scoped.
so, when after 1 second, the loop would have exhausted, because value variable i would have been 6.
and the var variable are also not block scoped so thats why wherever in the function x the i's last value will be, the closure will refer to that value.
so after each required time, the function along with the closure containing i's referrence again comes to the call stack and does its work.
so thats why we see 6 6 6 6 6 in the output.

To fix this use block scoped variables, 

![image](https://user-images.githubusercontent.com/72781278/206743332-2e195db9-8e46-45f8-8ea5-5b90b166a2fb.png)

output: 

        1
        2
        3
        4
        5

Now, as the variables are block scoped, each function have their own block, so the closure of eack function will now maintain new variable all together of i, that will always points to the value which was at time the function was invoked.

or we can solve this problem like this also, 

![image](https://user-images.githubusercontent.com/72781278/231343936-d06e8288-4db0-468b-93d2-4b88a13084a2.png)


As var declarations are either global scoped or function scoped, so eack call to the callback function will have variable i in the closure whose scope is only limited to the close() function, so in case of it updating next time in the loop it wont change, as it is updating for the loop not for the close() function.
the i variable passed to the close() parameters, is the one to which the closure is referring to, which is totally a new variable.

whenever we want not to have closure related problems, use block scoped variables let and const, but if in case it is prohibited, wrap the code inside function to prevent issue because of the function scoped nature of var declarations.
