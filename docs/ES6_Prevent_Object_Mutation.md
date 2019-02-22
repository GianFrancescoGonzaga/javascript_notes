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

# ES6: Write Higher Order Arrow Functions
It's time we see how powerful arrow functions are when processing data.

Arrow functions work really well with higher order functions, such as  `map()`,  `filter()`, and  `reduce()`, that take other functions as arguments for processing collections of data.

Read the following code:

> FBPosts.filter(function(post) {  
> return post.thumbnail !== null && post.shares > 100 && post.likes > 500;  
> })

We have written this with  `filter()`to at least make it somewhat readable. Now compare it to the following code which uses arrow function syntax instead:

> FBPosts.filter((post) => post.thumbnail !== null && post.shares > 100 && post.likes > 500)

This code is more succinct and accomplishes the same task with fewer lines of code.

----------

Use arrow function syntax to compute the square of only the positive integers (decimal numbers are not integers) in the array  `realNumberArray`and store the new array in the variable  `squaredIntegers`.
```javascript
const realNumberArray = [4, 5.6, -9.8, 3.14, 42, 6, 8.34, -2];

const decimal = (num) => {
	return num % 1 != 0;
}

const squareList = (arr) => {
	
	"use strict";

	// change code below this line

	// remove decimal numbers
	arr = arr.filter((el) => {
	if(!decimal(el)) {
		return el
	}
	});
	
	// remove negative integers
	arr = arr.filter((el) => {
		if(el > 0) {
			return el
		}
	});
	
const squaredIntegers = arr.map((el) => {
	return el * el
});

// change code above this line
return squaredIntegers;
};

// test your code

const squaredIntegers = squareList(realNumberArray);

console.log(squaredIntegers);
```

# ES6: Use the Rest Operator with Function Parameters

In order to help us create more flexible functions, ES6 introduces the  rest operator  for function parameters. With the rest operator, you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function.

Check out this code:

> function howMany(...args) {  
> return "You have passed " + args.length + " arguments.";  
> }  
> console.log(howMany(0, 1, 2)); // You have passed 3 arguments  
> console.log(howMany("string", null, [1, 2, 3], { })); // You have passed 4 arguments.

The rest operator eliminates the need to check the  `args`array and allows us to apply  `map()`,  `filter()`and  `reduce()`on the parameters array.

----------

Modify the function  `sum`so that it uses the rest operator and it works in the same way with any number of parameters.

```javascript
const sum = (function() {
	
	"use strict";

	return  function sum(...args) {
		const arr = [...args];
		return arr.reduce((a, b) => a + b, 0);
	};

})();

console.log(sum(1,2,3,4)); // 10
```
# ES6: Use the Spread Operator to Evaluate Arrays In-Place

ES6 introduces the  spread operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

The ES5 code below uses  `apply()`to compute the maximum value in an array:

> var arr = [6, 89, 3, 45];  
> var maximus = Math.max.apply(null, arr); // returns 89

We had to use  `Math.max.apply(null, arr)`because  `Math.max(arr)`returns  `NaN`.  `Math.max()`expects comma-separated arguments, but not an array.

The spread operator makes this syntax much better to read and maintain.

> const arr = [6, 89, 3, 45];  
> const maximus = Math.max(...arr); // returns 89

`...arr`returns an unpacked array. In other words, it  _spreads_  the array.

However, the spread operator only works in-place, like in an argument to a function or in an array literal. The following code will not work:

> const spreaded = ...arr; // will throw a syntax error

----------

Copy all contents of  `arr1`into another array  `arr2`using the spread operator.

```javascript
const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];

let arr2;

(function() {
	"use strict";
	arr2 = [...arr1]; // change this line
})();

console.log(arr2);
```
# ES6: Use Destructuring Assignment to Assign Variables from Objects

We saw earlier how spread operator can effectively spread, or unpack, the contents of the array.

We can do something similar with objects as well.  Destructuring assignment  is special syntax for neatly assigning values taken directly from an object to variables.

Consider the following ES5 code:

> var voxel = {x: 3.6, y: 7.4, z: 6.54 };  
> var x = voxel.x; // x = 3.6  
> var y = voxel.y; // y = 7.4  
> var z = voxel.z; // z = 6.54

Here's the same assignment statement with ES6 destructuring syntax:

> const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54

If instead you want to store the values of  `voxel.x`into  `a`,  `voxel.y`into  `b`, and  `voxel.z`into  `c`, you have that freedom as well.

> const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54

You may read it as "get the field  `x`and copy the value into  `a`," and so on.

----------

Use destructuring to obtain the average temperature for tomorrow from the input object  `AVG_TEMPERATURES`, and assign value with key  `tomorrow`to  `tempOfTomorrow`in line.

```javascript
const AVG_TEMPERATURES = {
	today: 77.5,
	tomorrow: 79
};

function getTempOfTmrw(avgTemperatures) {
	"use strict";
	// change code below this line
	const {tomorrow : tempOfTomorrow} = avgTemperatures; // change this line
	// change code above this line
	return tempOfTomorrow;
}

console.log(getTempOfTmrw(AVG_TEMPERATURES)); // should be 79
```

# ES6: Use Destructuring Assignment to Assign Variables from Nested Objects

We can similarly destructure  _nested_  objects into variables.

Consider the following code:

> const a = {  
> start: { x: 5, y: 6},  
> end: { x: 6, y: -9 }  
> };  
> const { start : { x: startX, y: startY }} = a;  
> console.log(startX, startY); // 5, 6

In the example above, the variable  `start`is assigned the value of  `a.start`, which is also an object.

----------

Use destructuring assignment to obtain  `max`of  `forecast.tomorrow`and assign it to  `maxOfTomorrow`.

```javascript
const LOCAL_FORECAST = {
	today: { min: 72, max: 83 },
	tomorrow: { min: 73.3, max: 84.6 }
};

function getMaxOfTmrw(forecast) {
	"use strict";
	// change code below this line
	const { tomorrow : { max : maxOfTomorrow } } = forecast; // change this line
	// change code above this line
	return maxOfTomorrow;
}

console.log(getMaxOfTmrw(LOCAL_FORECAST)); // should be 84.6
```

# ES6: Use Destructuring Assignment to Assign Variables from Arrays

ES6 makes destructuring arrays as easy as destructuring objects.

One key difference between the spread operator and array destructuring is that the spread operator unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables.

Destructuring an array lets us do exactly that:

> const [a, b] = [1, 2, 3, 4, 5, 6];  
> console.log(a, b); // 1, 2

The variable  `a`is assigned the first value of the array, and  `b`is assigned the second value of the array.

We can also access the value at any index in an array with destructuring by using commas to reach the desired index:

> const [a, b,,, c] = [1, 2, 3, 4, 5, 6];  
> console.log(a, b, c); // 1, 2, 5

----------

Use destructuring assignment to swap the values of  `a`and  `b`so that  `a`receives the value stored in  `b`, and  `b`receives the value stored in  `a`.

```javascript
let a = 8, b = 6;

(() => {
	"use strict";
	// change code below this line
	[b, a] = [a, b];
	// change code above this line
})();

console.log(a); // should be 6
console.log(b); // should be 8
```

# ES6: Use Destructuring Assignment with the Rest Operator to Reassign Array Elements

In some situations involving array destructuring, we might want to collect the rest of the elements into a separate array.

The result is similar to  `Array.prototype.slice()`, as shown below:

> const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];  
> console.log(a, b); // 1, 2  
> console.log(arr); // [3, 4, 5, 7]

Variables  `a`and  `b`take the first and second values from the array. After that, because of rest operator's presence,  `arr`gets rest of the values in the form of an array.

The rest element only works correctly as the last variable in the list. As in, you cannot use the rest operator to catch a subarray that leaves out last element of the original array.

----------

Use destructuring assignment with the rest operator to perform an effective  `Array.prototype.slice()`so that  `arr`is a sub-array of the original array  `source`with the first two elements omitted.

```javascript
const source = [1,2,3,4,5,6,7,8,9,10];

function removeFirstTwo(list) {
	"use strict";
	// change code below this line
	const [a, b, ...arr] = list; // change this
	// change code above this line
	return arr;
}

const arr = removeFirstTwo(source);
console.log(arr); // should be [3,4,5,6,7,8,9,10]
console.log(source); // should be [1,2,3,4,5,6,7,8,9,10];
```
