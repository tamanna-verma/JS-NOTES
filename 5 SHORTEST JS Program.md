Shorted JS program is an empty file.

Window is a global object which is created along with the global execution context.
This is an object created along with each EC.

At the global level, this === window.

Each global variable gets attached to the window object as they are in global space. 

![image](https://user-images.githubusercontent.com/72781278/206383629-04ecc3e6-bae4-4c27-856e-964287a5095d.png)

output will be : 

        10 
        10 
        referrence error : x is not defined.
        
console.log(this.a) = 10
