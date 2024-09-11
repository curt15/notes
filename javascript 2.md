Tags: #public 

https://www.javascript.com/learn/

```js
"this is a string";
"'this is fine.'";
'"this is fine"';
'\'this is fine\'';

.length
.toLowerCase()
.toUpperCase()
```

```js
12345;

>> 55/55;
<- 1



```

var obj {
    ‘x’: 1,
    ‘y’: 2,
    ‘z’: 3
}

obj.x 
obj[‘x’] 


const - used if the value or type should not be changed 
must be assigned a value when they are declared 
`const PI = 3.14159265359;`
```js
// You can create a constant array:
const cars = ["Saab", "Volvo", "BMW"];

// You can change an element:
cars[0] = "Toyota";

// You can add an element:
cars.push("Audi");
```
- A new Array
- A new Object
- A new Function
- A new RegExp
```js
// You can create a const object:
const car = {type:"Fiat", model:"500", color:"white"};

// You can change a property:
car.color = "red";

// You can add a property:
car.owner = "Johnson"; 
```

let - used if you can't use const; don't use var unless you *have* to support old browsers

```js
let x = 5;
let z = x ** 2;
let z = Math.pow(x,2);
```

let identifier; 

```js
 <p id="demo"></p>

<script>
let carName = "Volvo";
document.getElementById("demo").innerHTML = carName;
</script> 
```

(tick) - template string literal 
^^ are like f’ 

```js
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Hoisting</h2>
<p>With <b>let</b>, you cannot use a variable before it is declared.</p>
<p id="demo"></p>

<script>
try {
  carName = "Saab";
  let carName = "Volvo";
}
catch(err) {
  document.getElementById("demo").innerHTML = err;
}
</script>

</body>
</html>
```


JavaScript has 8 Datatypes

1. String
2. Number
3. Bigint
4. Boolean
5. Undefined
6. Null
7. Symbol
8. Object
The Object Datatype

The object data type can contain:

1. An object
2. An array
3. A date

JavaScript has dynamic types. This means that the same variable can be used to hold different data types:
```js
let x;       // Now x is undefined
x = 5;       // Now x is a Number
x = "John";  // Now x is a String
```

scientific (exponential) notation: 
```js
let y = 123e5;    // 12300000
let z = 123e-5;   // 0.00123 
```

```js
let x = 5;
let y = 5;
let z = 6;
(x == y)       // Returns true
(x == z)       // Returns false 
```

```js
typeof ""             // Returns "string"
typeof "John"         // Returns "string"
typeof "John Doe"     // Returns "string" 
typeof 0              // Returns "number"
typeof 314            // Returns "number"
typeof 3.14           // Returns "number"
typeof (3)            // Returns "number"
typeof (3 + 4)        // Returns "number" 
let car;    // Value is undefined, type is undefined
car = undefined;    // Value is undefined, type is undefined 
```

```js
// Function to compute the product of p1 and p2
function myFunction(p1, p2) {
  return p1 * p2;
}
```

```js
const person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```

```js
x = new String();        // Declares x as a String object
y = new Number();        // Declares y as a Number object
z = new Boolean();       // Declares z as a Boolean object 
```

```js
<button onclick="document.getElementById('demo').innerHTML = Date()">The time is?</button>

<button onclick="this.innerHTML = Date()">The time is?</button>
```
```js
<!DOCTYPE html>
<html>
<body>
<h1>JavaScript HTML Events</h1>
<h2>The onclick Attribute</h2>

<p>Click the button to display the date.</p>
<button onclick="displayDate()">The time is?</button>

<script>
function displayDate() {
  document.getElementById("demo").innerHTML = Date();
}
</script>

<p id="demo"></p>

</body>
</html> 
```

```js
// template strings (not usable for IE)
let text = `He's often called "Johnny"`;
// allows multi-line strings
let text =
`The quick
brown fox
jumps over
the lazy dog`;
```

A safe way to break up a statement is after an operator:
```js
 document.getElementById("demo").innerHTML =
"Hello Dolly!"; 
```

Comparing two JavaScript objects **always** returns **false**.

https://www.w3schools.com/js/js_string_methods.asp

```js
let text = "HELLO WORLD";
let char = text[0]; 
// unpredictable
// It makes strings look like arrays (but they are not)
// If no character is found, [ ] returns undefined, while charAt() returns an empty string.
// It is read only. str[0] = "A" gives no error (but does not work!)

let letter = name.at(2);
```

```js
let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace("Microsoft", "W3Schools");

// To replace case insensitive, use a **regular expression** with an `/i` flag (insensitive):
let text = "Please visit Microsoft!";
let newText = text.replace(/MICROSOFT/i, "W3Schools");

// To replace all matches, use a **regular expression** with a `/g` flag (global match):
let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace(/Microsoft/g, "W3Schools");
```
```js
text = text.replaceAll("Cats","Dogs");
```
```js
// string to array
text.split(",")    // Split on commas
text.split(" ")    // Split on spaces
text.split() // return an array with full string at index 0
```

https://www.w3schools.com/js/js_string_search.asp

```js
let firstName = "John";
let lastName = "Doe";

let text = `Welcome ${firstName}, ${lastName}!`;


// Expression Substitution
let price = 10;
let VAT = 0.25;

let total = `Total: ${(price * (1 + VAT)).toFixed(2)}`;


// HTML Templates
let header = "Template Strings";
let tags = ["template strings", "javascript", "es6"];

let html = `<h2>${header}</h2><ul>`;
for (const x of tags) {
  html += `<li>${x}</li>`;
}

html += `</ul>`;
```

**Integer Precision**
Integers (numbers without a period or exponent notation) are accurate up to 15 digits.
```js
let x = 999999999999999;   // x will be 999999999999999
let y = 9999999999999999;  // y will be 10000000000000000
```

The maximum number of decimals is 17.

**Floating Precision**
Floating point arithmetic is not always 100% accurate:
```js
let x = 0.2 + 0.1; // 0.30000000000000004
```
To solve the problem above, it helps to multiply and divide:
```js
let x = (0.2 * 10 + 0.1 * 10) / 10; // 0.3
```

```js
typeof NaN;
typeof Infinity;
```

BigInt
```js
let x = 1234567890123456789012345n;
let y = BigInt(1234567890123456789012345)
```
Arithmetic between a `BigInt` and a `Number` is not allowed (type conversion lose information).
A `BigInt` can not have decimals.

```js
let x = Number.MAX_SAFE_INTEGER;
let x = Number.MIN_SAFE_INTEGER;

Number.isInteger()
Number.isSafeInteger()
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.toString();
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let length = fruits.length;

let fruit = fruits[0];
let fruit1 = fruits[fruits.length - 1];
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let fLen = fruits.length;

let text = "<ul>";
for (let i = 0; i < fLen; i++) {
  text += "<li>" + fruits[i] + "</li>";
}
text += "</ul>";
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];

let text = "<ul>";
fruits.forEach(myFunction);
text += "</ul>";

function myFunction(value) {
  text += "<li>" + value + "</li>";
} 
```

```js
const fruits = ["Banana", "Orange", "Apple"];
fruits.push("Lemon");  // Adds a new element (Lemon) to fruits

const fruits = ["Banana", "Orange", "Apple"];
fruits[fruits.length] = "Lemon";  // Adds "Lemon" to fruits 
```

```js
// Create an array with one element:
const points = [40];

// Create an array with 40 undefined elements:
const points = new Array(40);  
```

https://www.w3schools.com/js/js_array_methods.asp

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let fruit = fruits.pop();
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon");
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.join(" , ");
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
delete fruits[0];
/*
Warning !

Using delete() leaves undefined holes in the array.

Use pop() or shift() instead.
*/
```

```js
const myGirls = ["Cecilie", "Lone"];
const myBoys = ["Emil", "Tobias", "Linus"];

const myChildren = myGirls.concat(myBoys);

/*
The concat() method does not change the existing arrays. It always returns a new array.

The concat() method can take any number of array arguments. 
*/
```

```js
const arr1 = ["Emil", "Tobias", "Linus"];
const myChildren = arr1.concat("Peter"); 
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 0, "Lemon", "Kiwi");

/*
The first parameter (2) defines the position where new elements should be added (spliced in).

The second parameter (0) defines how many elements should be removed. (removed AFTER the spliced in index)

The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be added.
*/
```

```js
<!DOCTYPE html>
<html>
<body>
<h1>JavaScript Arrays</h1>
<h2>The splice() Method</h2>

<p>The splice() methods can be used to remove array elements:</p>

<p id="demo1"></p>
<p id="demo2"></p>

<script>
const fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo1").innerHTML = fruits;
fruits.splice(0, 1);
document.getElementById("demo2").innerHTML = fruits;
</script>

</body>
</html>
```
^^
JavaScript Arrays
The splice() Method

The splice() methods can be used to remove array elements:

Banana,Orange,Apple,Mango

Orange,Apple,Mango

```js
const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus = fruits.slice(1);
// citrus
// Orange,Lemon,Apple,Mango

/*
The slice() method creates a new array.

The slice() method does not remove any elements from the source array.
*/
```

https://www.w3schools.com/js/js_array_search.asp

```js
const fruits = ["Apple", "Orange", "Apple", "Mango"];
let position = fruits.indexOf("Apple") + 1;

const fruits = ["Apple", "Orange", "Apple", "Mango"];
let position = fruits.lastIndexOf("Apple") + 1;

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.includes("Mango"); // is true 


const numbers = [4, 9, 16, 25, 29];
let first = numbers.find(myFunction);

function myFunction(value, index, array) {
  return value > 18;
} 
// First number over 18 is 25

const numbers = [4, 9, 16, 25, 29];
let first = numbers.findIndex(myFunction);

function myFunction(value, index, array) {
  return value > 18;
} 


const temp = [27, 28, 30, 40, 42, 35, 30];
let high = temp.findLast(x => x > 40);
// The last temperature over 40 was 42
```

https://www.w3schools.com/js/js_array_sort.asp

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
// Apple,Banana,Mango,Orange

// The `sort()` method sorts an array alphabetically

fruits.reverse();
const sorted = months.toSorted();
const reversed = months.toReversed();

// ascending 
const points = [40, 100, 1, 5, 25, 10];  
points.sort(function(a, b){return a - b});

// decending
const points = [40, 100, 1, 5, 25, 10];  
points.sort(function(a, b){return b - a});

// randomly 
const points = [40, 100, 1, 5, 25, 10];  
points.sort(function(){return 0.5 - Math.random()});
```

