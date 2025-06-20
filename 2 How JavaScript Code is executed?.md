### When we run a JS program , an execution context is created.
### Created using Two phases : 
#### 1 - Memory Creation Phase:
Stores Undefined in case of var variable and whole function code for functions.
#### 2 - Code execution Phase:
All Variables get their values, in case of functions execution an all together a 
execution context is created recursively in these two phases.
After Completion of code execution(for functions: return statement), then its execution phase is deleted. 

This whole process is Similar to the Call Stack.
In the bottom of the stack, there is a global ex. context.
Other function invocation places their ex. context on the stack and gets pop when completed.

![image](https://user-images.githubusercontent.com/72781278/206373409-0e2f8d1c-5423-48d2-80c5-9140b2043884.png)

![image](https://user-images.githubusercontent.com/72781278/206374425-997c9d29-f198-4951-b2f4-2dd039654ab9.png)

![image](https://user-images.githubusercontent.com/72781278/206374915-2b395ee0-9733-4dbd-9348-224e821bda6d.png)
