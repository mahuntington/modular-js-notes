# Intro to JS

## Lesson Objectives

1. Add comments to code
1. Describe the basic data types of JS
1. Assign values to variables
1. Concatenate values
1. Boolean expressions
1. Operators
1. Write a While loop
1. Write a For loop

## Add comments to code

single line comment:

```
// this is a single line comment
```

multi-line comment:

```
/*
this is
a mult-line
comment
 */
```

## Describe the basic data types of JS

Strings:

```javascript
console.log("hello world");
```

Numbers:

```javascript
console.log(100);
```

## Assign values to variables

```javascript
var phrase = 'In my room is a chair and a table';
console.log(phrase);
```

**We will not be using `var`** (it's a bit out of date), instead we will be using **`let`** and **`const`**.

Let's use `const` here:

```javascript
const phrase = 'In my room is a chair and a table';
const sum = 99 + 1;
```

`const` variables are **constant** and do not change.  Now that the phrase is saved to a variable, we can call it whenever.

```javascript
console.log(phrase);
console.log(sum);
```

### Variable re-assignment

With `const`, you cannot reassign a variable. It is CONSTANT.

```javascript
const item = ' chair';
item = 'eclair';
```

You can re-assign variables with `let`:

```javascript
let item = 'chair';
item = 'eclair';
console.log(item);
```

## Concatenate values

JavaScript allows us to add strings together with `+`:

```javascript
console.log('hello' + ' world');
```
We can insert values of variables into our strings:

```javascript
const adjective = 'beautiful';
console.log('What a ' + adjective + ' day!!');
```

## Boolean expressions

Test various kinds of equality

* `>` greater than
* `<` less than
* `==` equal to
* `>=` greater than or equal to
* `<=` less than or equal to
* `!=` is not equal

```javascript
console.log(5 <= 10);
console.log("asdf" != "fun");
```

## Operators

### Math

We can do arithmetic with numbers:

```javascript
console.log(100 + 100);
console.log(100 - 50);
console.log(100 * 10);
console.log(100 / 10);
```

#### Postfix operator

```javascript
i++;
i--;
```

is the same as

```javascript
i = i + 1;
i = i - 1;
```

#### Compound assignment operator `+=`

```javascript
i += 3; //increments by 3
i -= 3; //decrement by 3
```

is the same as

```javascript
i = i + 3;
i = i - 3;
```

## Write a While loop

```javascript
let num = 1;

while (num <= 1000) {
	console.log('The number is: ' + num);
	num++;
}
```

## Write a For loop

```javascript
for (let i=1; i <= 1000; i++) {
	console.log('The number is: ' + i);
}
```

There are three parts to the 'control panel' of the loop, delimited by the semicolon:

```javascript
for (initial condition; while condition; repeating expression) {

}
```

1. some initial code supplied to the loop -- usually a numerical starting value of the loop
2. the condition under which the loop runs -- it will run while the expression is true
3. a repeating expression that runs at the end of each loop -- usually an instruction to increase the numerical starting value
