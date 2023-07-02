## Inferring Types in TypeScript

### 1 - Get the Return Type of a Function

**Overview:**
In TypeScript, you can retrieve the return type of a function using the `ReturnType` utility type. This is particularly useful when you want to extract and utilize the return type of a function dynamically.

**Syntax:**
```typescript
ReturnType<T>
```
``` typescript
function greet(): string {
  return 'Hello, world!';
}

type GreetingReturnType = ReturnType<typeof greet>; // string

console.log(GreetingReturnType); // Output: string

```

### 2 - typeof Keyword and Type Level

**Overview:**
The `typeof` keyword in TypeScript is used to obtain the type of a value or a variable at the type level. It allows you to extract and manipulate the types themselves, rather than working with values.

**Syntax:**
```typescript
typeof valueOrVariable
```
Example:
```typescript
let name = 'John';
type NameType = typeof name; // string

function greet(): typeof name {
    return 'Hello, ' + name;
}

console.log(greet()); // Output: Hello, John


```

### 3 - Extract Function Parameters Into A Type

**Overview:**
TypeScript allows you to extract the parameter types of a function into a separate type using the `Parameters` utility type. This is helpful when you want to work with the types of a function's parameters separately.

**Syntax:**
```typescript
Parameters<T>
```
Example:
```typescript
function add(a: number, b: number): number {
    return a + b;
}

type AddParameters = Parameters<typeof add>; // [number, number]

const params: AddParameters = [2, 3];
console.log(add(...params)); // Output: 5

```

### 4 - Extract The Awaited Result of a Promise

**Overview:**
When working with asynchronous code in TypeScript, you may need to extract the type of the value that a promise resolves to. The `Awaited` utility type allows you to do this, making it easier to handle promise resolutions.

**Syntax:**
```typescript
Awaited<T>
```
Example:
```typescript
async function fetchData(): Promise<string> {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
}

type FetchDataResult = Awaited<ReturnType<typeof fetchData>>; // string

async function process(): Promise<void> {
    const result: FetchDataResult = await fetchData();
    console.log(result);
}

process();


```

### 5 - Create a Union Type From an Object's Keys

**Overview:**
In TypeScript, you can generate a union type from an object's keys using the keyof keyword and the `typeof` operator. This allows you to create a type that represents all possible keys of an object.

**Syntax:**
```typescript
keyof typeof object

```
Example:
```typescript
const colors = {
    red: '#FF0000',
    green: '#00FF00',
    blue: '#0000FF',
};

type ColorKeys = keyof typeof colors; // 'red' | 'green' | 'blue'

function getColor(key: ColorKeys): string {
    return colors[key];
}

console.log(getColor('red')); // Output: #FF0000



```

## Exercises


### Exercise 1: Get the Return Type of a Function
Write a TypeScript function called multiply that takes two parameters of type number and returns their product. Use the ReturnType utility type to extract and log the return type of the multiply function.

### Exercise 2: typeof Keyword and Type Level
Create a TypeScript variable called user and assign it an object with the following properties: name of type string, age of type number, and isAdmin of type boolean. Use the typeof keyword to extract the type of the user variable and assign it to a new type called UserType. Log the UserType to the console.

### Exercise 3: Extract Function Parameters Into A Type
Write a TypeScript function called combineStrings that takes three parameters, all of type string. Use the Parameters utility type to extract the parameter types of the combineStrings function and assign them to a new type called CombineStringsParams. Create a variable of type CombineStringsParams and assign it an array of three strings. Log the array to the console.

### Exercise 4: Extract The Awaited Result of a Promise
Create a TypeScript async function called fetchData that returns a Promise of type number. Use the Awaited utility type to extract the awaited result type of the fetchData function and assign it to a new type called FetchDataResult. Create a constant of type FetchDataResult and assign it the resolved value of fetchData. Log the constant to the console.

### Exercise 5: Create a Union Type From an Object's Keys
Create a TypeScript constant called fruits and assign it an object with the following properties: apple, banana, and orange, each with a string value representing their color. Use the keyof typeof approach to generate a union type of all the keys of the fruits object and assign it to a new type called FruitKeys. Write a function called getFruitColor that takes a parameter of type FruitKeys and returns the corresponding color from the fruits object. Call the getFruitColor function with each fruit key and log the results to the console.
