### Let and const declarations are hoisted but different from var.
These decalrations are in the **TEMPORAL DEAD ZONE** for the time being.

Accessing Let and Const declarations before creating, will give referrence error (cant access before initialization).

      console.log(a); -> referrence error (cant access before initialization)
      console.log(b); -> undefined.
      let a = 10;
      var b = 100;

In the memory allocation phase : 

<img width="126" alt="image" src="https://user-images.githubusercontent.com/72781278/206710456-de58e060-1545-40dd-816d-4959966e4095.png">

The memory is allocated,
but var decalarations and functions get into global space and let and const declarations will get into script space.
So they are not in the attached with window object.

Temporal dead zone = since when the let and const variable are hoisted and were initiated.

- When we access any variable which is not created : 
Referrence error, varaible is not defined.

- When we access any var variable before its declaration : 
undefined

- When we access any let and const variable before declaration :
Referrence error, cannot access before initialization.

- Creating any variable (let-var/ let-const/ let-let/ const-const) twice in same scope(be it): 
(var-var is fine) 
Syntax error. 

- Const variable should be initialized while declaration.
if done, we get Syntax Error.
If we initialise const again, we get TypeError.
