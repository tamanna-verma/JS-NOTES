SetTimeout's callback function gets entered into the callback queue after the timer gets exhausted (similar to any callback function gets inserted into the callback queue once the required task for which its waiting is finished executing).

Issue: 
If whole code itself takes 10 sec. to execute, and the setTimeout registered callback after 5 sec. then in that case, the callback function will execute only after the GEC gets deleted, so in total the callback function will take 10 sec. to execute not 5.

Ex:

![image](https://user-images.githubusercontent.com/72781278/213460618-ad3b8e78-72e6-4472-83e9-23b7708d3b15.png)

So setTimeout waits atleast the given timer, not exact.
