Block => {}
block is used to compound multiple statements.
we group multiple statements into one single statement where js expect only one statement.

Let and const are block scoped.

<img width="95" alt="image" src="https://user-images.githubusercontent.com/72781278/206717345-85f96e29-37a5-40df-b151-9383fd8518d4.png">

<img width="129" alt="image" src="https://user-images.githubusercontent.com/72781278/206717388-e66daa0e-126f-4dbe-b9e1-5cfde0eac815.png">

------------------------------------------------------------------

<img width="99" alt="image" src="https://user-images.githubusercontent.com/72781278/206717547-460e61c1-9d9a-4200-8b24-80b678cf0e61.png">

<img width="225" alt="image" src="https://user-images.githubusercontent.com/72781278/206717584-cfa2f580-85e7-40b6-a161-7b1c693fe9ca.png">

Shadowing : When variable of inner block scope, shadows the same variable if it was also declared in outer scope too.

<img width="80" alt="image" src="https://user-images.githubusercontent.com/72781278/206718050-c5da00b5-bd57-4b36-9278-19f1edec7421.png">

Inner a = 10
But for the case of outer a after the block, it prints 10 again, because var are global scoped and function scoped, not block scoped.
In case of let and const, they are block scoped.

<img width="80" alt="image" src="https://user-images.githubusercontent.com/72781278/206718687-f92e8d91-a473-471e-be33-fa6f047691fa.png">

<img width="110" alt="image" src="https://user-images.githubusercontent.com/72781278/206718722-d9c871e9-0ac7-4755-8fcb-244c4a434cdc.png">

Illegal Shadowing: Now, while shadowing a variable, it should not cross the boundary of the scope, i.e. we can shadow var variable by let variable but cannot do the opposite.
Because shadowing variable should not contains similar named varialbe in the scope in which it is in.

      let a = 10;
      {
          var = 10;
      }

Blocked scoped variable are lexical scope also, they also form scope chain.

<img width="88" alt="image" src="https://user-images.githubusercontent.com/72781278/206719904-05cf806d-f17f-4142-9604-323cebdf8f77.png">

prints 200,
In case if it is not present in that inner most block, then it would check for the outer block sequentially.

<img width="96" alt="image" src="https://user-images.githubusercontent.com/72781278/206720013-6b63a4c4-cfd2-43c9-9f08-bb2a59238e44.png">
