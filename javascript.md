Links: [[PROGRAMMING]]
Rel: 
Ref: https://www.w3schools.com/js/default.asp
- [string](https://www.w3schools.com/jsref/jsref_obj_string.asp); [string - mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
Tags: #public 

typescript - is type checking 

--- 
libraries:
jQuery https://www.w3schools.com/jquery/default.asp

frameworks:
Angular
Node
React
Vue
...

--- 
save an .html file, click in file explorer -> view in browser
runs in browser, errors show up in ("Inspect Element" console)

--- 
comments: 
```javascript
// like in Java, this is single-line a comment
```
```javascript
/*
This is the syntax for a
multi-line comment !!!
*/
```

variables:
- no spaces, can't start with a number, letters and numbers only, 

EOL:
- ```;``` unnecessary unless performing multiple operations on the same line

--- 

#### console, document, .getElementById

```html
<!-- console, document -->
<!-- call the document.getElementById *method* on a *parameter* -->
<!-- .innerHTML to reference what's inside the tags -->
<!-- use .value to get/put from <input> element -->

<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title></title>
</head>
<body>

	<h1 id="header0"> Hello World </h1>
	<input type="text" id="inp0"/>
	
	<script type="text/javascript">
	
		document.write('<h1>Hello Again!</h1>')
		console.log('hello world');
		console.warn('close to an error here!');
		console.error('error raised!');
		
		// ...
		document.getElementById("header0").innerHTML = "Hi Earth";
		document.write(document.getElementById("header").innerHTML);
		
		document.getElementById("inp0").value = "hello";
		console.log(document.getElementById("inp0").value);
		
		
	</script>

</body>
</html>
```

--- 
#### primitives, fundamentals of

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title></title>
</head>
<body>
	<h1> Hello World </h1>
	
	<script type="text/javascript">

		<!-- Datatypes -->
		// Primitive (datatypes in js):
		// string		" " ''
		// number 		5.0 -72 
		// boolean		true false
		// undefined	(cant set, comes undefined)
		// null			null

		// Variables:
		var x = 6;
		x = 9;
		console.log(x);
		
		
		<!-- Operators -->
		var x = 10;
		var y = 2;

		// ...
		var z = x + y;
		var z = x - y;
		var z = x * y;
		var z = x / y;
		var z = x % y;
		
		// ...
		var x+= 5;
		var x-= 5;
		var x*= 5;
		var x/= 5;
		var x%= 5;

		y++;
		y--;

		console.log(z)
		
		
		<!-- String concatination -->
		
		var str1 = "Hello ";
		var str2 = "World";
		console.log(str1 + str2)
		
		str1+=" World"

		var str3 = "hello" - 3;
		var str3 = "hello" / 3;
		// -> NaN
		// no error thrown
		// program still runs,
		
		
		<!-- Order of Operations -->
		
		var result = 4 * 5 / 3 + 9 - 2;
		var result = 4 * 5 / (3 + 9 - 2);
		var result = 4 * (5 / 3 + 9 - 2);
		console.log(result)
		
		
		<!-- Conditions and Boolean -->
		<!-- = assignment operator -->
		<!-- == equivelancy operator (value) -->
		<!-- === equivelancy operator (value & type) -->
		<!-- != non- ... (value) -->
		<!-- !== non- ... (value & type) -->
		
		var x = 8;
		var y = 9;

		var z = x < y;
		var z = x <= y;

		var z = x > y;
		var z = x >= y;

		var z = x == y;
		var z = x === y;
		// -> bool

		var a = '10';
		var b = 10;
		// a == b -> true
		// a === b -> false

		var x != y;
		var x !== y;
				
			
		<!-- Chaining Conditionals -->
		
		<!-- &&  logical and -->
		<!-- ||  logical or -->
		<!-- !  not -->
		var name = "curtis";
		var name2 = "Curtis";
		var x = 10;
		var y = 9;
		var z = '8';

		console.log(name == name2);
		console.log(name == name2 && y < x);
		console.log(name == name2 || y < x);
		console.log(name == name2 || y < x && z == 8);

		console.log(!false);
		console.log(!(x < y));
		
		
		
	</script>

</body>
</html>
```

--- 
#### functions

```html
<!-- Functions (fundamentals) -->
<!-- "One thing and one thing well" -->
<!-- w/ and w/out parameters -->

<html>
<head>
	<meta charset="utf-8">
	<title></title>
</head>
<body>

	<h1 id="header"> Hello World </h1>
	<button onclick="red()">Red</button>
	<button onclick="green()">Green</button>
	
	<h2 id="header2"> Hello World !</h2>
	<input type="text" id="inp" />
	<button onclick="pressed()">Click</button>
	
	<h3 id="header3"> Hello World !!</h3>
	<input type="text" id="inp2" />
	<button onclick="pressed2()">Click</button>
	
	<h4 id="header4"> Hello World !!!</h4>
	<input type="text" id="inp3" />
	<button onclick="checkAge()">Check Age</button>
	<p id="output"></p>
	
	<input type="text" id="inp4" />
	<button onclick="yellThis()">CLICK</button>
	<p id="output2"></p>
	

	<script>
		function add(){
			console.log("add");
		}

		add();
		add();
		
		function add(a, b){
			return a + b;
		}

		var x = add(5,5);
		var y = add(10,10);
		console.log(add(x,y));
		
		
		// as registered
		// onclick events
		function red(){
			console.log("red");
			document.getElementById("header").style.color = "red";
		}
		function green(){
			console.log("green");
			document.getElementById("header").style.color = "green";
		}
		
		// ...
		// conditionally
		function pressed() {
			var text = document.getElementById("inp").value;
			if (text == "red") {
				document.getElementById("header2").style.color = "red";
			} else if (text == "green") {
				document.getElementById("header2").style.color = "green";
			} else if (text == "blue") {
				document.getElementById("header2").style.color = "blue";
			} else {
				document.getElementById("header2").style.color = "black";
			}
		}
		
		// ... same as ^^, but using a
		// switch statement
		function pressed2() {
			var text = document.getElementById("inp2").value;
			switch (text) {
				case "red": 
					document.getElementById("header3").style.color = "red";
					break;
				case "green":
					document.getElementById("header3").style.color = "green";
					break;
				case "blue":
					document.getElementById("header3").style.color = "blue";
					break;
				default:
					document.getElementById("header3").style.color = "black";
			}
		}
		
		
		function checkAge() {
			// using parseInt()
			// as from input type="text", input alaways string
			var text = parseInt(document.getElementById("inp3").value);
			var output = document.getElementById("output");

			if (text > 18){
				output.innerHTML = "You've been an adult.";
			} else if (text == 18){
				output.innerHTML = "You are now an adult!";
			} else {
				output.innerHTML = "You are a child.";
			}

		}
		
		function yellThis() {
			var text = document.getElementById("inp4").value;
			// var output = document.getElementById("output2");
			// reference id directly
			output2.innerHTML = text.toUpperCase();
		}

	</script>

</body>
</html>

```

--- 
#### Array

```html
<html>
<body>

	<script>
		var myArr = ["hello",  42, 2.4, "world"]
		var myArr2 = new Array()

		console.log(myArr[0])
		// ...
		console.log(myArr[8])
		// -> undefined
		// doesn't throw error

		myArr[2] = "updated element"
		console.log(myArr)
		console.log(myArr.pop())
		// ^^ returns last element
		// ... -> is removed from arr
		console.log(myArr)

		myArr[9] = 11.0
		// ... -> generates *empty* indicies up to


	</script>

</body>
</html>
```


--- 
#### while loop, do while loop

```html
<html>

	<body>

		<script>

			var i = 0

			// while (i < 10){
			// 	console.log(i);
			// 	i++;
			// }

			while(true){
				console.log(i);
				i++;
				if (i == 9){
					break
				}
			}
			console.log('Broke out of "infinite loop"')


			// ... w/ arrays
			var i = 0
			var arr = ["hello", "world", "!"]
			while (i < arr.length){
				console.log(arr[i])
			}


			// .push() ~= python's .append()
			var i = 0
			var arr = new Array()
			while (i <= 100){
				arr.push(i);
				i++;
			}
			console.log(arr)
			
			
			// do while loop
			var b = false

			while (b){
				console.log("not gonna happen.")
			}

			do {
				// ... once (even if cond is false) 
				console.log("Alright I get to disturb this guy.")
			} while (b) {
				// and then while condition if condition) 
				console.log("...")
				console.log("not gonna happen.")
			}

		</script>

	</body>
</html>
```

--- 

##### for loop

```html
<html>

	<body>

		<script>

			for(var i = 0; i < 10; i++){
				console.log(i)

				if (i == 7){
					break
				}
			}



			function findInArray(arr, value){
				for (var i = 0; i < arr.length; i++){
					if (arr[i] == value){
						return true
					}
				}
				return false
			}


			var arr = [1,2,3,4,5,6,7,8,9,10]
			console.log(findInArray(arr, 11))


			function nsquared(n){
				for (var i = 0; i < n; i++){ // n 
					for (var j = 0; j < n; j++){ // n 
						console.log("running n x n")
					}
				}
			}
			nsquared(5) // 25
			
			
			
			// for each / for of :
			
			var arr = ["x", "y", "z"]

			console.log(arr);
			for (let element of arr){
				console.log(element)
				element = 5
				// ^^ doesn't update
				// the element of arr
				console.log(element)
			}
			console.log(arr)

			// ^^ same array -> 
			for (var i = 0; i < arr.length; i++){
				console.log(arr[i])
				arr[i] = 5
				console.log(arr[i])
				// does update
				// the element of the array
			}
			console.log(arr)

			// string indexing!
			var x = "hello world"
			for (var i = 0; i < x.length; i++){
				console.log(x[i])
			}

		</script>

	</body>
</html>
```

--- 

#### Set

```html
<!-- sets -->
<!-- "unordered collection of unique elements" -->
<!-- Sets maintain O(1) (constant time) for look-ups -->


<!-- methods: -->
<!-- .add() -->
<!-- .delete(e) -->
<!-- .forEach(func) - for each element, perform func on it -->

<html>

	<body>

		<script>

			var mySet = new Set()

			mySet.add(3).add(5).add(7).add(3).add(3).add(9)

			console.log(mySet) // Set(3) [ 3, 5, 7 ]
			console.log(mySet.has(5)) // -> boolean 

			// var arr = [3,5,7,9]
			// ^^ in an array, you'd have to 
			// loop through it to look up
			// time expensive with large arrays

			console.log(mySet.delete(5)) // -> true
			console.log(mySet.delete(5)) // -> false, but doesn't break

			console.log(mySet.values()) // -> SetIterator
			// gives order in which inserted 
			// "unordered" -> it's technically ordered by insertion

			for (var entry of mySet.values()){
				console.log(entry)
			}

			// ...
			var mySet = new Set([3,5,7,3,3,9])
			var mySet2 = new Set("Hello World")
			console.log(mySet2)
			// -> Set(8) [ "H", "e", "l", "o", " ", "W", "r", "d" ]


			function test(x){
				console.log(x)
				if (x == "l"){
					console.log("l")
				}
			}

			mySet2.forEach(test)


		</script>

	</body>
</html>
```


--- 

#### Map

```html
<!-- Maps -->
<!-- properties -->
<!-- .size - length keys -->

<!-- methods -->
<!-- .set() -->
<!-- .delete() -->
<!-- .get() -->
<!-- .has() -->
<!-- .clear() -->

<html>

	<body>

		<script>

			// arr = [1,2,3,4] // O(n) look-up time
			// but advantage of use of indexing

			// set -> O(1)
			// ...

			// map -> "instant time"
			// key, value pair

			var mp = new Map(
				[
				["hello", 6],
				["world", 7]
				])

			// update pair
			mp.set("hello", 8)

			// new pair
			mp.set("!", 6)
			// delete it
			mp.delete("!")

			console.log(mp.size)
			console.log(mp)
			// mp.clear()

			for (var entry of mp){
				// getting the [k,v] pairs
				// Array [ "hello", 8 ]
				console.log(entry)
			}
			for (var entry of mp){
				// -> index to access
				console.log(entry[0])
				console.log(entry[1])
			}

			// empty the map
			mp.clear()
			console.log(mp)


			// ...
			var mp = new Map()
			myStr = "this is my new string content"

			for (var letter of myStr){
				if (mp.has(letter)){
					// add to the count
					mp.set(letter, mp.get(letter)+1)
				} else {
					// initialize found letter
					// to the map
					mp.set(letter, 1)
				}
			}

			console.log(mp)
			// Map(14) { t → 4, h → 1, i → 3, s → 3, " " → 5, m → 1, y → 1, n → 4, e → 2, w → 1, … }

		</script>

	</body>
</html>
```

--- 

#### mutability

```html
<!-- Mutability -->
<!-- changable or unchangable -->

<html>

	<body>

		<script>

			// primitive datatypes: 
			var w = 5 // number, string, boolean, undefined, null
			var x = w
			var x = 2 // w is uneffected (still 5)
			// ... 

			var y = [] // an object
			var z = y // another name that *references* variable y
			// ^^ changes to z effect y, changes to y effect z, 
			// v.s. python, where ```z = x``` sets z to the value of x
			// in javascript is an *alias*
			// z has the same pointer in memory now as y
			// e.g. "id=1"
			// v.s. python, where a copy and entirely new var is generated

			// ...
			function add5(num){
				num += 5
				console.log(num)
			}

			var x = 5
			add5(x) // performing function against primitive datatype
			console.log(x) // still 5 (uneffected)


			// reference (aka object) datatypes 

			function append5(arr){
				arr.push(5)
				console.log(arr)
			}

			var myArr = [1,2,3,4,5]

			console.log(myArr)
			append5(myArr)

			console.log(myArr) // effected (still append5()-ed (inplace))


			function prepend100(arr){
				var arr2 = arr
				arr2[0] = 100
				// even though setting and changing arr2,
				// we're changing arr's reference value!
				console.log(arr2)
				console.log(arr)
			}

			var myArr = [1,2,3,4,5]

			console.log(myArr)
			prepend100(myArr)
			console.log(myArr)


			// make a copy with .slice()
			var myArr = [1,2,3,4,5]
			var myArr2 = myArr.slice()
			var myArr3 = myArr.slice(0,3) // from index 0->3

			// another way to copy:
			var myArr4 = [...myArr]

			prepend100(myArr2)
			console.log(myArr)
			console.log(myArr2)

		</script>

	</body>
</html>
```

--- 