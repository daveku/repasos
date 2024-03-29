# Quiz - JavaScript Avanzado

​

### Self-Evaluation

​

#### Name: David Ku

---

​

### Section: Functions As Values

## ​

​

##### 1. Complete the sentence

​
Functions are the primary mechanism of **\_** in JS.
​

> de cumplir una tarea en especifico, puede o no tener parametros de entrada y parametros de salida
> ​

##### 2. Create a function `square` that takes one parameter `number` that returns the result of that `number` multiplied by itself. You need to perform this in `3` different ways

​

###### 2.1. by using `function declaration` syntax.

​
Solution:
​

```js
function square(number) {
  return number * number;
}
```

​

###### 2.2. by using `function expression with an anonymous function` syntax.

​
Solution:
​

```js
const square = function (number) {
  return number * number;
};
```

​

###### 2.3 by using `function expression with a named function` syntax.

​
Solution:
​

```js
const square = function square(number) {
  return number * number;
};
```

​

##### 3. What's an `IIFE`? Give an example.

​

> es una funcion que se ejecuta inmediatamente​

```js
(function () {
  var x = "Hello";
  console.log(x);
})();
```

​

##### 4. What's a `closure` in JS?

​

> Es una funcion que tiene declarada dentro otra funcion y esta segunda funcion puede acceder a las variables de la funcion padre.
> ​Tambien se puede retornar la funcion interna.
> ​

### Section: Strict Mode

## ​

​

##### 1. In your own words, what's `use strict;`?

​

> hace que el codigo tenga que ser escrito de una manera que cumpla con los estandares de JS.
> ​

##### 2. Use Strict. Write the output for the following code snippets

​

###### Snippet

​

```js
function yummy () {
  a = 50
}
​
yummy();
​
console.log(a);
```

​

> 50
> ​

###### Snippet

​

```js
'use strict';
​
function yummy () {
  a = 50
}
​
yummy();
​
console.log(a);
```

​

> error de variable no definida "a"
> ​
> ​

### Section: Scope & Closures

## ​

​

##### 1. Nested Scopes, `var` & `let`. Write the output for the following code snippets

​

###### Snippet

​

```js
var a = 1;
​
function foo () {
  if (a == 1) {
    var b = 2;
  }
​
  console.log(b);
}
​
foo();
```

​

> 2
> ​

###### Snippet

​

```js
var a = 1;
​
function foo () {
  if (a == 1) {
    let b = 2;
  }
​
  console.log(b);
}
​
foo();
```

​

> error de variable no definida "b"
> ​

##### 2. Accodingly to the author, what are the core concepts you will learn with the `Scope & Closures` book?

​

> _your answer here_
> ​
> ​

#### 3. Closure. What would be the output for the following code?

​

###### Snippet

​

```js
function createHello (greeting) {
  return function greet (name) {
    return greeting + " " + name + "!";
  }
}
​
var greetInSpanish = createHello('Hola');
​
console.log(greetInSpanish("Pedro"));
console.log(createHello('Hi')("Mike"));
```

​

> "Hola Pedro!"
> ​"Hi Mike!"

#### 4. Hoisting. What will be logged to the console upon execution of the code below:

​

```js
a = 3
​
var a;
​
console.log(a)
```

> 3
> ​
> ​

### Section: `this` Keyword

## ​

​

##### 1. `this`. Write the output for the following code

​

###### Snippet

​

```js
// Kitties
function sayHello() {
  console.log("Hello " + this.name);
}
​
var name = "Fluffy";
​
sayHello();
​
var kitty = {
  name: "Buttercup",
  sayHello: sayHello
};
​
kitty.sayHello();
​
sayHello.call({ name: "Cocoa" });
​
new sayHello();
```

​

> "Hello Fluffy"
> ​"Hello Buttercup"
> ​"Hello Cocoa"

##### 2. What is String in JavaScript?

​

> Es una cadena de caracteres.
> ​
> ​

##### 3. In objects, property names are always strings?

​

> Si, todas las propiedades son strings.
> ​
> ​

#### Section: Prototypes

## ​

​

##### 1. `Prototypes`. Write the output for the following code

​

###### Snippet

​

```js
var animal = {
  walk: "I'm walking!"
};
​
var bird = Object.create(animal);
​
bird.fly = "I'm flying!";
​
var penguin = Object.create(bird);
​
penguin.fly = "I can't fly :(";
penguin.swim = "I'm swimming!";
​
var canary = Object.create(bird);
​
var tiger = Object.create(animal);
​
console.log(tiger.walk);
console.log(tiger.fly);
console.log(canary.fly);
console.log(canary.walk);
console.log(canary.swim);
console.log(penguin.fly);
console.log(penguin.walk);
console.log(penguin.swim);
```

> "I'm walking!"
> Undefined​
> "I'm flying!"
> "I'm walking!"
> Undefined​​
> "I can't fly :(​"
> "I'm walking!"
> "I'm swimming!"

### Section: Challenge

## ​

​

##### 2.1 Create a module in an `IIFE` stored in a variable `calculator` that exposes 4 methods: `plus`, `minus`, `times` and `dividedBy`. Each method should receive one parameter `firstNumber` and return a function that receives another parameter `secondNumber`. Every method should perform the operation it describes, for example, it's expected that `plus` adds the `firstNumber` to the `secondNumber`, `dividedBy` should divide the `secondNumber` by the `firstNumber` and so on. The idea is to have "stored" the `firstNumber` to perform the next operations with it.

​
_**TIP:**_ You can create a `script.js`file and test your code in the browser or node.js.
​
Solution:
​

```js
// create your calculator module here
var calculator = (function(){
  return {
     plus(firstNumber){
       return function(secondNumber){
         return firstNumber + secondNumber;
       }
     },
     minus(firstNumber){
       return function(secondNumber){
         return secondNumber - firstNumber;
       }
     },
     times(firstNumber){
       return function(secondNumber){
         return firstNumber * secondNumber;
       }
     },
     dividedBy(firstNumber){
       return function(secondNumber){
         return secondNumber / firstNumber;
       }
     }
  }
})();
​
// Do NOT touch this code
const testCases = [
  { type: "plus", n1: 3, n2: [1, 2, 3], expected: [4, 5, 6] },
  { type: "minus", n1: 1, n2: [1, 0, -1], expected: [0, -1, -2] },
  { type: "times", n1: 5, n2: [2, 5, 10], expected: [10, 25, 50] },
  { type: "dividedBy", n1: 10, n2: [10, 100, 1000], expected: [1, 10, 100] }
];
​
const result = testCases.every(test => {
  const operation = calculator[test.type](test.n1);
  return test.n2.every((number, i) => {
    const testPassed = operation(number) === test.expected[i];
    if (!testPassed) {
      console.log(`Expected: ${operation(number)} to be: ${test.expected[i]}. Operation: secondNumber(${number}) ${test.type} firstNumber(${test.n1})`);
    }
    return testPassed;
  });
});
​
console.log("All tests passed: ", result);
```

​

### Section: `this` & Object Prototypes

## ​

​

##### 1. When this is used in a function, it refers to that function itself? True or false? Why?

​

> Si, es una referencia a el mismo.
> ​
> ​

##### 2. Why is this helpful?

> Como es una referencia a si mismo podemos acceder a los metodos de la clase.
> ​
> ​

##### 3. What will be logged to the console when the following code is executed:

```js
var Dog = {
  speak: function () {
    console.log("Bark");
  },
  sleep: function () {
    console.log('sleeping...')
  }
};
​
var Cat = Object.create(Dog);
​
Cat.speak = function () {
  console.log("Meow")
};
Cat.speak()
Cat.sleep()
```

> "Meow"
> ​"sleeping..."

### Section: Async & Performance

## ​

​

##### 1. `console.log()` is always executed synchronously?

​

> si
> ​

##### 2. What is a Promise?

​

> es un objeto que tardara un cierto tiempo pero concluir y dar una la respuesta.
> ​

#### 3. What data structure best explains the event loop?

​

> _your answer here_
> ​

#### 4. What is "callback hell" all about?

​

> Es cuando una funcion llama a otra funcion y esta llama a otra y ahi sucesibmente.
> ​Esto puede ser muy complicado de leer y mantener.

#### 5. What will be logged to the console when the following code is executed:

​

```js
var a = 1;
setTimeout(() => console.log(a), 0);
for (let i = 0; i < 1000; i++) {}
a++;
```

​

> 1
> ​

### Section: ES6 & Beyond

## ​

​

##### 1. Mention some of the new `ES6` features:

​

> arround function
> let y const
