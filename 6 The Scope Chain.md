![image](https://user-images.githubusercontent.com/72781278/206394413-1f37f516-4e54-42bd-b342-8394868861eb.png)

Output : 10

If the variable which we are accessing is not found in the local memory of that EC
then it is being checked at the outer EC, if not in there then outer of the EC
up till GEC if not found anywhere.
If found, value is updated in all those ECs.
Other wise referrence error is thrown


![image](https://user-images.githubusercontent.com/72781278/206394879-41602e5e-29a4-4b9f-8a4d-f749434eea56.png)

But in this case, error will be thrown as scope checking always moves outside current EC.
It never checks nested ECs.

![image](https://user-images.githubusercontent.com/72781278/206396076-c0b261f2-9328-4fdb-8988-9d933ff16f78.png)

When a variable is used in JavaScript, the JavaScript engine will try to find the variable's value in 
the current scope. If it could not find the variable, it will look into the outer scope and will 
continue to do so until it finds the variable or reaches global scope.
