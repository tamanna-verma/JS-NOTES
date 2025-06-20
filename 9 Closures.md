###  A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).

<img width="88" alt="image" src="https://user-images.githubusercontent.com/72781278/206722511-60dfee5d-5370-486e-884b-449f37bac7f0.png">

<img width="142" alt="image" src="https://user-images.githubusercontent.com/72781278/206722549-c1dd907d-dacd-4fbc-8260-8f099f1a37a7.png">

<img width="90" alt="image" src="https://user-images.githubusercontent.com/72781278/206723439-d165b74c-a14f-474a-9e60-a93c41a85eef.png">

returning function from function will also return closure of that function.

prints: 
        
        whole function
        7

<img width="87" alt="image" src="https://user-images.githubusercontent.com/72781278/206724275-180a5628-de31-4f5f-b049-994791b65f62.png">

Now closure of y contains a=100.
Because closure contains varialbe referrences not the static values.

<img width="103" alt="image" src="https://user-images.githubusercontent.com/72781278/206725417-1bbe42b4-5f83-41da-933d-f307974e136d.png">

<img width="240" alt="image" src="https://user-images.githubusercontent.com/72781278/206725453-32a0d14c-806f-4b65-b824-9edc73c82d6d.png">


1. An inner function can be directly called using two parenthesis ()().
2. Even parameters can be passed this way (Remember that the function needs to be returned to do this)
3. Closures can also be used for data hiding and encapsulation. So other code cannot access this value.
4. Unused variables are automatically deleted in High Level Programming language by garbage collector. Closures allocate a lot of memory which cannot be deleted so this acts as a disadvantage.
5. Some browsers now have smart garbage collectors that automatically deletes variables that are not used outside closures.
