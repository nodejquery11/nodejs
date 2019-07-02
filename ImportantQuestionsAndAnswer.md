Data type in JS:
1. primitive datatype (string, number, boolean, undefine, null)
2. non-primitive/reference datatype (object, array, regexp)

Object: it's collection of primitive & non-premitied datatype values. It has two kind of 
    - literal object: it is good for small type application or one method execution application
        -Practical pattern:
    - constructor object: for multiple method or application can use it
        -Constructor pattern
        -Prototype pattern

Inheritance in JS: if you define two different class and master class can be access using the second class with prototype keyword. So the second consturctor object can access the master class values.

Hoisting: is basically based on variable scope. Two type of variable scope
    - local/block-level scope
        - never override from global variable
        - limited scope or inside function only
        - JS will give more preference to local variable
        - you can't access the local variable outside but if you not define the local variable with var keyword then JS takes it global variable and accessible.
    - global/non-block-level scope
        - can be override via local variable
        - it has scope in full application
        - if you not define the global variable and try to access it then it throw an error 'is not define', however if you define the gloabl variable but not initilize it then it throw an error 'undefine'

Closure: is an inner function, which has access to the outerfunction variable and arguments - scope chain. three type of scope chain 1. inner variable access, 2. outer variable access and 3. global variable access

Callback: is a higher order function which pass into another function as argument. 
    - http://javascriptissexy.com/understand-javascript-callback-functions-and-use-them/

Call, Apply and Bind



Questions:
1. How much data can Javascript array support?
Ans: 4.29 billion element in ES-262
2. difference b/w null & undefine in JS?
3. difference b/w object and array in JS?
4. Can functions be added to existing data types in JavaScript?
Ans: Yes, we can add fucntions of our own in the data type as well as override the ones that is already there.
Ex, like if you have object which contain the primitive datatype, so it also contain the function in the same object with return data type value.
let a = {
    name: 'string',
    housenumber: 1956,
    gender: 'male',
    add: function(a, b) { /*return integer*/
        return a+b;
    }
}
: override the datatype
let b = 10;
b = function() {
    return 'vikas';
}
5. Why are data types required?
Ans: To able the variable properly, we need to know datatype so only we can perform the dynamic process.
6. What is object in JS?
Ans: it is the collection of unordered primitive datatypes and store into one place.
> Creating the object
    1. literal object
    2. Constructor object
7. Difference b/w primitive datatype & reference datatype
primitive datatype will never override the orignal data. However the refence datatype override it.
// Primitive datatype
let person = "vikas";
let anotherPerson = person;
person = "Siva";

console.log(anotherPerson); //Vikas
console.log(person); //Siva

// Reference datatype
let primitiveDatatype = {name: 'Vikas'};
let anothervar = primitiveDatatype;
primitiveDatatype.name = "Siva";

console.log(primitiveDatatype); //Siva
console.log(anothervar); // Siva
8. Chaining in JavaScript?
9. inheritance in JS?
10.Patterns in object in JS?
    - Practical pattern: This pattern can be used once in your application to store the data. For more application, it will be unuseful as you have to repeat the same thing multiple time. So for small application, it will be useful but in case if you have 100 methods then you have to write the same property 100 times but incase if you need to add or update the property then it will be tedious work.
      var f = {
        color: "Yellow"
      }
    - Constructor pattern: in this pattern, you have to give the defination inside of constrctor and call into multiple time.
      function Fruits(color) {
        this.color = color;
      }
      var f = new Fruits("Yellow");
    - Prototype pattern: Constructor & Prototype pattern both are same only difference to add the property into the constructor before declare object then use prototype keyword.
     function Fruits() { }
      Fruits.prototype.color = "yellow";
      var f = new Fruits();

11.How to inherit in JS?
// Inheritance in JS

function tree(treeName) { /*master class*/
  this.treeName = treeName;
  this.area = 'India';
}

function Fruits(FruitsName, color) { /*child class*/
  this.FruitsName = FruitsName;
  this.color = color;
}

Fruits.prototype.tree = new tree('mango'); /*inherit master class*/
let f = new Fruits('mango', 'yellow');

console.log(f.tree.treeName); /*access the master class values*/

12.variable scope: means, existing the variable. scope meaning that where you can access the variable. Variable has two kind of scope
    - global scope: 
        - call as non-block-level variable scope.
          var fname = "Vikas";
          function a() { .. }
        - It can be use anywhere of application. 
         console.log(fname);
        - But this can we override from the local variable
         if(fname) {
            fname = "Bose";
         }
         console.log(fname);
    - local scope: 
        - call block-level variable scope. It will access inside of function or breses only.
         function a() {
            var b = "Bose";
            return b;
         }
         console.log(b); //is not define
        - But it can't be override from global variable value
        var b = "Vikas";
        function a() {
            var b = "bose";
            return b;
        }
        console.log(b);

13. difference b/w undefine & is not define
Ans: if you define the variable but not initilize with value then it throw an error undefine. However, even if you do not define the variable and try to access the variable, then it throw an error 'is not define'.

Note: if you want to add the new property into Practical or Constructor pattern, then you just do object_variable.property = value. it will add the property into the object but it happen only once you define the object. In case you wanted to add the property before define the object then using prototype keywork, you can add into the object and access the value.

Note: in case if you do not define the var keyword in front of any variable then JavaScript takes it as global variable. Like
    var b = "vikas";
    function a() {
        b = "bose";
        return b;
    }
    console.log(a(), b); //bose, bose
  JavaScript always give priority to the local variable.
  setTimeout() method can be execute the global variable. 
  this.anyVariable; //it will refer the global window object

14. what is closure?
Ans: A closure is a inner function which has access for outer function's variable - scope chain. there are 3 kind of scope chain, 1. access to inner variable, 2. access to the outer function variable, 3. global variable
closure has three rules
- has access the outer function variable even after the outer function return
- store the outer function variable

15. what is callback?
var p_client = new db(arg1, arg2);
p_client.open(function(err, p_client) {
    p_client.dropdatabase(function(err, p_client) {
        p_client.createCollection(function(err, p_client){
            .....
        })
    })
})
to prevent the callback, we can use the modularity.

call: invoke a method of owner object as argument
var paerson = {
    fullName: function(arg1, arg2){
        return arg1+' '+arg2;
    }    
}
person.fullName.call({'vikas', 'bose'}, arg2, arg3);

apply: also do the similar job only the argument pass as an array
person.fullName.apply({'vikas', 'bose'}, [arg1, arg2]);

two type of Datatype
    - primitive and non-primitive or reference datatype
        -primitive datatype - string | integer | boolean | undefine | null
        -reference datatype/non-primitive - object | array | regExp
        - difference: reference datatype can override the variable values but primitive datatype never
        let person = "vikas";
        let anotherPerson = person;
        person = "Hello";
        console.log(anotherPerson, person); //vikas hello
        
        let person = {name: "vikas"};
        let anotherPerson = person;
        person.name = "Hello";
        console.log(anotherPerson, person); //hello hello
        
Object: collection of unordered primitive & non-primitive datatype. Two type of creation 
    - literal object | contructor object
// object literal

/*Initilization object*/
var a = {};

/*Fill with value*/
var a = {
  fname: "Vikas",
  lname: "Bose",
  fullName: function() {
    return this.fname +' '+ this.lname;
  }
};

console.log(a.fullName());

// object constructor

/*Object Initilization*/
var b = new Object();

/*Fill with value*/
b.fname= "Vikas";
b.lname= "Bose";
b.fullname = () => {
  return b.fname+' '+b.lname;
}

console.log(b.fullname());
