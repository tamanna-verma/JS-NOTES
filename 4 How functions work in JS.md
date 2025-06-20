![image](https://user-images.githubusercontent.com/72781278/206380303-1cc240af-6e1e-4209-bdf7-186ed193cde0.png)

### Output : 
      10 
      100
      1
      
![image](https://user-images.githubusercontent.com/72781278/206380526-7d964862-9bb8-4894-bacb-d689d1a2963b.png)

Now in code execution phase,
x in GC will store 1 and other EC will be created for function a()

![image](https://user-images.githubusercontent.com/72781278/206380803-8c18a6a7-06bd-4955-955f-7ba04281e981.png)

Each variable in each execution phase store variable limited to that EC and other inside it only.
 
So, 10 will be printed on the console.

![image](https://user-images.githubusercontent.com/72781278/206381443-1e8554da-5d58-46f6-a444-5e5e040c13cc.png)

Now, 100 will be printed on the console after code execution of b() EC is done.

Then both a() and b() EC will get deleted, and we get back to the GEC.

![image](https://user-images.githubusercontent.com/72781278/206381697-888aaa3a-040d-4c4a-a551-1ead9c5f1493.png)

Now, 1 will be printed on the console.
