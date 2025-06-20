Call method is used for function borrowing.
We can use function of object to be used with another object.
Every function in js has call() method.
Object passed in the call() method, will be used as a reference to which "this" keyword inside the call() function will refer to.

          let name: {
            firstName:"Suraj",
            lastName:"Thapliyal"
            print:function(){
              console.log(this.firstName + " " + this.lastName);
            }
          }
          name.print();

          OUTPUT: 
          Suraj Thapliyal


          let name2: {
            firstName:"Mohit",
            lastName:"Negi"
          }
          name.print.call(name2);

          OUTPUT:
          Mohit Negi

-----

        let name:{
          firstName:"Suraj",
          lastName:"Thapliyal"
        }
        function print(){
          console.log(this.firstName + " " + this.lastName); 
        }
        print.call(name);

        OUTPUT:
        Suraj Thapliyal
        
-----
If the function is itself accepting some arguments already, then in the callmethod the first argument will always be the "this" referrence and later on the remaining agrs will follow.


        let name:{
          firstName:"Suraj",
          lastName:"Thapliyal"
        }
        function print(hometown){
          console.log(this.firstName + " " + this.lastName + " is from " + hometown); 
        }
        print.call(name,"Dehradun");

        OUTPUT:
        Suraj Thapliyal is from Dehradun
        
-----
#### Apply Method:

Same as call method, but the extra args will be passed as an array.
Then that array gets spread out in the required parameters in that function.


        let name:{
          firstName:"Suraj",
          lastName:"Thapliyal"
        }
        function print(hometown, state){
          console.log(this.firstName + " " + this.lastName + " is from " + hometown + ", " + state); 
        }
        print.call(name,["Dehradun","Uttarakhand"]);

        OUTPUT:
        Suraj Thapliyal is from Dehradun, Uttarakhand
        
-----

#### Bind Method:

The bind() method in JavaScript is used to create a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding.

        let name:{
          firstName:"Suraj",
          lastName:"Thapliyal"
        }
        function print(hometown, state){
          console.log(this.firstName + " " + this.lastName + " is from " + hometown + ", " + state); 
        }
        let newPrint = print.bind(name,"Dehradun", "Uttarakhand");
        newPrint();

        OUTPUT:
        Suraj Thapliyal is from Dehradun, Uttarakhand
