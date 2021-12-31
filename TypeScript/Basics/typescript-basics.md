# TypeScript basics

---

## Basic types

-   **boolean** <br>

```ts
const isLoading: boolean = true;
```

-   **string** <br>

```ts
const message: string = "Hello World!";
```

-   **number** <br>

```ts
const year: number = 2022;
const exp: number = 2.718;
```

-   **array** <br>
    _There are some ways to declare an array_

```ts
const nums: number[] = [1, 2, 3, 4, 5]; // only numbers
const products: Array<string> = ["bread", "milk"]; // only strings
const someValues: [string, boolean] = ["ts", true]; // only 1 string and 1 boolean
```

-   **any** <br>
    _Allows to disable type checking, as a result the variable can dynamically change it's type. Avoid `any` in your code._

```ts
let value: any = "this is string";
value = 107;
value = false;
value = [1, 2, "a", "b", true];
```

---

## Custom types and interfaces

-   **Type Aliases** <br>
    _Good for describing types in simple objects or for variables that may have more than one type._

```ts
type Animal = {
    name: string;
    age: number;
};

const animal: Animal = {
    name: "Fluffy",
    age: 4,
};
```

_You can extending a type_

```ts
type Cat = Animal & {
    color: string;
};
```

```ts
type ID = string | number;

const userId: ID = 239053;
const itemId: ID = "A934VL";
```

-   **Interfaces** <br>
    _An interface declaration is another way to name an object type. Interfaces support a more convenient extension and are used more often._

```ts
interface IPerson {
    firstName: string;
    lastName?: string; // an optional parameter
    gender: "female" | "male"; // only certain values
    isMarried: boolean;
}

//Extending an interface
interface IWorker extends IPerson {
    job: string;
}

const someone: IWorker = {
    firstName: "Alex",
    gender: "male",
    isMarried: true,
    job: "engineer",
};
```

---

## Functions

-   **Basic usage** <br>
    _We can describe the types of function arguments as well as the return value_

```ts
// type "void" means that our function does not return anything
function logInfo(name: string, age: number): void {
    console.log(`My name is ${name}, I'm ${age} y.o.`);
}

// Arrow function
const square = (x: number): number => x * x;
```

-   **Default arguments** <br>
    _When default parameters are specified, their types are automatically determined by the set values_

```ts
function getNumbers(max = 99, min = 0): void {}
```

-   **Optional arguments** <br>

```ts
function greeting(name?: string): void {
    if (name) {
        console.log(`Welcome, ${name}!`);
    } else {
        console.log(`Welcome, annonymous user!`);
    }
}
```

-   **Unlimited arguments** <br>
    _You can describe an indefinite number of arguments of the same type using spread operator_

```ts
const logValues = (x: number, ...values: string[]): void =>
    console.log(x, ...values);

logValues(77, "one", "two", "three", "...");
```

-   **Function type** <br>
    _Use function type to describe methods_

```ts
interface IService {
    calcSum: (a: number, b: number) => number;
    getBalance: () => string;
    sendFeedback: (mes: string) => void;
}
```

---

## Classes