# JavaScript

**Operators**

```javascript
`This string
can habe newlines`

'Hello' + 5     // "hello5"

console.log(3 > 2) // -> true
console.log(true ? 1 : 2); 	// -> 1
```

**Program Structure**

```javascript
/----------------Bindings:--------------------

var x = 5;
let y = 6;
y = 7; // -> 7
const z = 8;
z = 9; // -> error
let message = 'Hello';

/------------Conditional Execution:-------------

const isItTrue = 4 < 5;
if(isItTrue){
  console.log("Yes!");
}else {
  console.log("No.")
}  // -> Yes!

let number = 0;
while(number <= 12){
  console.log(number);
  number += 2;
}  // 0, 2, ... , 14

for(let i = 0; i < 10; i++){
  console.log(i);
}  //0, 1, ... , 9

/-----------Functions:---------------------------

function square(x){
  return x * x;
}

let sq = function(x){
  return x * x;
}

sq = (x) => x * x; // (x) => x * x
sq(5); 	// -> 25

sq = x => x * x; 	// x => x * x

sq = x => {
  const theAnswer = x * x;
  return theAnswer;
}  // -> return x * x

const factorial = n =>
	n === 0
		? 1
		: n * factorial(n - 1); // return n!

for ( let i = 0; i < 10; i++){
  console.log(factorial(i));
} 	//1 2 6 24 120 720 5040 ...

/-------Data structures: Objects and arrays--------

car = {
  year: 1997,
  make: 'Honda',
  model: 'Accord',
  price: 2800
};
car.year; 	// -> 1997

cars = [car];
cars.push({
  make: "Nissan",
  model: "Leaf",
  year:	2012,
  price: 1800
})

//way1 of list a car price
for(let i = 0; i < cars.length; i++){
  const car = cars[i];
  console.log(car.price);
}

//way2
for(car of cars) {
  console.log(car.price);
} 		//2800 1800

//way3: frequent used -> cars.forEach();
cars.forEach(car => {
  console.log(car.price);
});

//way3.1
const printCarPrice = car => {
  console.log(car.price);
};
car.forEach(printCarPrice);

//get a array of price
cars.map(car => car.price);  //[...]

// what's the cheapest car
const prices = cars.map(car => car.price);
prices.sort(); //[prices from low to high]

cars.filter(car => car.price < 2000);

//format a car like "1997 Honda Accord: $2800"
let formatCar = car => `${car.year} ${car.make} ${car.model}: $${car.price}`;  //too long

// let formatCar be more easy read
let formatCar = car => {
  const year = car.year;
  const make = car.make;
  const model = car.model;
  const price = car.price;
  
  return `${year} ${make} ${model}: $${price}`;
}

// or more clear:
let formatCar = car => {
  const {
    year,
    make,
    model,
    price
  } = car;
  
  return `${year} ${make} ${model}: $${price}`;
} 

//list all cars under $2000 in format
cars
	.filter(car => car.price < 2000)
	.map(formatCar)
	.join('\n');  //join all array element on a new line

JSON.stringify(cars, null, 2);  // toString
JSON.parse(); // to valuable

/-------------------Promises-------------------------
setTimeout(() => console.log("Tick"), 1000); //1000ms
let myPromise = new Promise((resolve, reject) => {
  setTimeout(() => resolve(), 2000);
});


```

# HTML, CSS and SVG

**Cars Report with HTML**

- Header title
- Bulleted list

**Cars Report with HTML and CSS**

- Customize Font
- Highlight an item

**Making Shapes with SVG** : Scalable Vector Graphics

- SVG as Image Format
- SVG in HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <title>HTML Cars Report(html title)</title>
    <!--load css file-->
    <link rel="stylesheet" href="styles.css">
  </head>
  <!--set fond size like below or use css file-->
  <body style="font-size: 2em">
    <h1>(head tag) Cars Report</h1>
    <ul>
      <!--set highlight-->
      <!-- <li></li> is bulleted list-->
      <li class="highlighted">2012 Nissan Leaf: $1800</li>
      <li>2009 Ford F150: $1950</li>
      <li>2009 Chevrolet Trailblazer: $1550</li>
    </ul>
  </body>
</html>

```

Styles.css

```css
body {
  font-size: 2em;
  font-family: monospace;
}

.highlighted{
  color: red;
}
```

注释：

- em： 2em, 24pt, 24px  都是字体大小单位

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Shapes with SVG and CSS</title>
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>
    <svg width="960" height="500">
      <circle cx="100" cy="10" r="400" fill="#83cc2a"></circle>
      <rect x="100" y="25" width="50" height="50" fill="green"></rect>
      <!--use group elements-->
      <!--use transform to move all elem in group down-->
      <!--change color of all elem in group-->
      <g transform="translate(0, 200)" fill="blue">
        <!--use stroke.width to set outline of circle-->
        <circle width="50" height="50" stroke.width="5"></circle>
        <rect width="50" height="50"></rect>
      </g>
      
      <!--use scale(1.5) to zoom it to 1.5 times-->
      <g class="lines" transform="scale(1.5)">
      	<line x1="200" y1="20" x2="300" y2="280" stroke="black" stroke.width="10"></line>
     	  <!--move the line-->
    	  <path fill="none" d="M300 280 L350 200 L400 20"></path>
        <!--M: move to(300,280), dh. starting point of the path  L: line to(350, 200)-->
      </g>
    </svg>
  </body>
</html>
```

Styles.css

```css
body {
  margin: 0px;
  overflow: hidden;
}

.lines {
  stroke: black;
  stroke-width: 10;
}

.lines path{
  stroke: #25656d;
  stroke-linejoin: round;
}

.highlighted {
  color: red; 
}
```

注释：

- cx: centre x of a circle
- x: we can just position a rectangle just use x and y



# D3.js

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Let's make a face with D3.js!</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://unpkg.com/d3@5.6.0/dist/d3.min.js"></script>    
  </head>
  <body>
    <svg width="960" height="500"></svg>
    <script src='bundle.js'>
//      const svg = d3.select('svg');
//      <!--svg.style(key, value)-->
//     svg.style('backgroud-color', 'red');
      
    </script>
  </body>
</html>
```

index.js

```javascript
const svg = d3.select('svg');
svg.style('background-color', 'red');


--------
        .attr(
          "d",d3.symbol()
          .size(100)
          .type(function(d){
          if(d == "Others"){ return d3.symbolSquare
          } else if (d == "AWD"){ return d3.symbolTriangle
          } else if (d == "RWD"){ return d3.symbolCircle
          }})    
        )
        
          
         .attr(
          "d", d3.symbol()
          .size(100)
          .type(function(d) {
            if(d == "Others"){return d3.tymbolSquare
            } else if(d == "AWD"){return d3.symbolTriangle
            } else if(d == "RWD"){return d3.symbolCircle
          }}))


```

bundle.js

```javascript

```

注解：

- +... = parseFloat(...)
- 



Wie ich geschrieben habe, ich habe diese Woche Videoshop geschafft und ich habe auch prototype gemacht, aber es gibt noch einige



























