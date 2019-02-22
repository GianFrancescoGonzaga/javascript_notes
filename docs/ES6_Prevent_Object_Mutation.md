# Mutate Array Declared with Const

The  `const` declaration has many use cases in modern JavaScript.

Some developers prefer to assign all their variables using  `const` by default, unless they know they will need to reassign the value. Only in that case, they use  `let`.

However, it is important to understand that objects (including arrays and functions) assigned to a variable using  `const` are still mutable. Using the  `const` declaration only prevents reassignment of the variable identifier.

> "use strict";  
> const s = [5, 6, 7];  
> s = [1, 2, 3]; // throws error, trying to assign a const  
> s[2] = 45; // works just as it would with an array declared with var or let  
> console.log(s); // returns [5, 6, 45]

As you can see, you can mutate the object  `[5, 6, 7]` itself and the variable  `s` will still point to the altered array  `[5, 6, 45]`. Like all arrays, the array elements in  `s` are mutable, but because  `const` was used, you cannot use the variable identifier  `s` to point to a different array using the assignment operator.

----------

An array is declared as  `const s = [5, 7, 2]`. Change the array to  `[2, 5, 7]` using various element assignment.

#### Solution

```javascript
const s = [5, 7, 2];

function editInPlace() {

"use strict";

// change code below this line

  

// s = [2, 5, 7]; <- this is invalid

s[0] = 2;

s[1] = 5;

s[2] = 7;

// change code above this line

}

editInPlace();
```

# ES6: Prevent Object Mutation

As seen in the previous challenge,  `const` declaration alone doesn't really protect your data from mutation. To ensure your data doesn't change, JavaScript provides a function  `Object.freeze` to prevent data mutation.

Once the object is frozen, you can no longer add, update, or delete properties from it. Any attempt at changing the object will be rejected without an error.

> let obj = {  
> name:"FreeCodeCamp",  
> review:"Awesome"  
> };  
> Object.freeze(obj);  
> obj.review = "bad"; //will be ignored. Mutation not allowed  
> obj.newProp = "Test"; // will be ignored. Mutation not allowed  
> console.log(obj);  
> // { name: "FreeCodeCamp", review:"Awesome"}

----------

In this challenge you are going to use  `Object.freeze` to prevent mathematical constants from changing. You need to freeze the  `MATH_CONSTANTS` object so that no one is able alter the value of  `PI`, add, or delete properties .

```javascript
function freezeObj() {

"use strict";

const MATH_CONSTANTS = {

PI: 3.14

};

// change code below this line

Object.freeze(MATH_CONSTANTS);

// change code above this line

try {

MATH_CONSTANTS.PI = 99;

} catch( ex ) {

console.log(ex);

}

return MATH_CONSTANTS.PI;

}

const PI = freezeObj();
```

# ES6: Use Arrow Functions to Write Concise Anonymous Functions

In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead, we create inline functions. We don't need to name these functions because we do not reuse them anywhere else.

To achieve this, we often use the following syntax:

> const myFunc = function() {  
> const myVar = "value";  
> return myVar;  
> }

ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use  **arrow function syntax**:

> const myFunc = () => {  
> const myVar = "value";  
> return myVar;  
> }

When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword  `return`as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:

> const myFunc = () => "value"

This code will still return  `value`by default.

----------

Rewrite the function assigned to the variable  `magic`which returns a new  `Date()`to use arrow function syntax. Also make sure nothing is defined using the keyword  `var`.

```javascript
const magic = () => {

"use strict";

return  new Date();

};
```

# ES6: Write Arrow Functions with Parameters

Just like a normal function, you can pass arguments into arrow functions.

> // doubles input value and returns it  
> const doubler = (item) => item * 2;

You can pass more than one argument into arrow functions as well.

----------

Rewrite the  `myConcat`function which appends contents of  `arr2`to  `arr1`so that the function uses arrow function syntax.

```javascript
const myConcat = (arr1, arr2) => {

"use strict";

return arr1.concat(arr2);

};

// test your code

console.log(myConcat([1, 2], [3, 4, 5]));
```
