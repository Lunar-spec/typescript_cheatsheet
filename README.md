# TypeScript Cheat Sheet

This cheat sheet provides a quick reference guide for TypeScript syntax, features, and best practices.

## Table of Contents

1. [Introduction](#introduction)
2. [Variables](#variables)
3. [Arrays](#arrays)
4. [Objects](#objects)
5. [Functions](#functions)
6. [Type Aliases](#type-aliases)
7. [Interfaces](#interfaces)
8. [Generics](#generics)

---

## Introduction

Welcome to the TypeScript Cheat Sheet! This cheat sheet covers various aspects of TypeScript programming, including variables, arrays, objects, functions, type aliases, interfaces, and generics. Whether you're new to TypeScript or need a quick refresher, this document has got you covered.

## Variables

- Variable declarations and type annotations
  - `let a = "hello";` Type string
  - `let num: number = 34;` Type number
  - `let age: number = 34;` Defining the type explicitly
  - `let str: string = 'hello';`
  - `let email: boolean = false;`
  - `let two: string | number = 10;` Union type

## Arrays

- Array declarations and operations
  - `let ab = ['john', 'jane', 'alex'];` Array of strings
  - `ab.push('tom');` Push operation
  - `let num_a = [11, 12, 1];` Array of numbers
  - `let num_b: number[] = [11, 12, 1];` Type annotation for array of numbers

## Objects

- Object declarations and modifications
  - Define an object: `let user = { username: "jhon", age: 22, isAdmin: true };`
  - Modify object properties: `user.username = "jane";`

## Functions

- Function declarations and types
  - `const sayHi = () => { console.log("Hi") };`
  - `let funcReturn = (): string => { return 'Max' };`
  - `let multiple = (num: number) => { return num * 2 };`

## Type Aliases

- Type aliases for custom types
  - `type userType = { username: string; age: number; phone?: number; };`

## Interfaces

- Interface declarations and implementations
  - `interface IUser { username: string; email?: string; age: number; }`

## Generics

- Generic interfaces and implementations
  - `interface IPostBetter<T> { id: number; title: string; desc: string; extra: T[]; };`

This TypeScript Cheat Sheet provides examples and explanations for various TypeScript concepts. Use it as a quick reference guide to enhance your TypeScript programming skills.

#CheatSheet.ts
```typescript
let a = "hello" //type string
// a = 9

let num = 34 // type number
// num = 'nine'

let age: number = 34;//defining the type

let str: string = 'hello';

let email: boolean = false;

let two: string | number = 10; // union type
two = "hello";
// two = false //throws an error

////array
let ab = ['john', 'jane', 'alex'];
// ab.push(3)
ab.push('tom')

let num_a = [11, 12, 1]

let num_b: number[] = [11, 12, 1]

let ar_str: string[] = ['grey', 'red']

let ar_un: (string | number)[] = [1, "one", 2]

////object
let user = {
	username: "jhon",
	age: 22,
	isAdmin: true
}

user.username = "jane"
// user.age = 'jnjfnw'
// user.isAdmin = 'iii'

// user.phone = "0993939" <---can't do this because not defined

let userObj: {
	username: string,
	age: number,
	isAdmin: boolean,
}

userObj = {
	username: 'jhon',
	age: 19,
	isAdmin: true,
	// phone: '993949392' <--- still ain't allowed
} 
// must use all properties defined in the obj structure

let userObj2: {
	username: string,
	age: number,
	isAdmin: boolean,
	phone?: string,//condition, can be there can't be
}

userObj2 = {
	username: 'jane',
	age: 19,
	isAdmin: true,
}
userObj2 = {
	username: 'alex',
	age: 19,
	isAdmin: true,
	phone: '993949392'
}
//^ both objects are acceptable

////ANY
let testAny;

testAny = 12;
testAny = 'sting';

let anyArray: any[];

anyArray = [2, false, "two"]

//* Functions

const sayHi = () => {
	console.log("Hi")
}

let funcReturn = (): string => {
	return 'Max'
}

let multiple = (num: number) => {
	return num * 2;
}

let multiple2 = (num: number): number => {
	return num * 2;
}
//both are same

let multiple3 = (num: number): void => {
	//do something but don't return
}

//num1 & num2 mandatory but another isn't
let sum = (num1: number, num2: number, another?: number) => {
	return num1 + num2
}
sum(2, 4)

// kinda like structure for the parameter object
let func = (user: { username: string, age: number, phone?: number }) => {
	console.log(user.username)
}

//TYPE ALIASES
type userType = {
	username: string;
	age: number;
	phone?: number
}

let betterFunc = (user: userType) => {
	console.log(user.username)
}

//explaining a function skeleton
type myFunc = (a: number, b: string) => void
//implementing that skeleton
let write: myFunc = (num, str) => {
	console.log(num + " time " + str)
}

type userType2 = {
	username: string,
	age: number,
	phone?: string,
	theme: "dark" | "light" // enum type
}

const usertheme: userType2 = {
	username: 'jhon',
	age: 34,
	theme: "dark"
}

//INTERFACES
interface IUser {
	username: string;
	email?: string;
	age: number;
}

interface IEmployee extends IUser {
	emplId: number
}
//allows addition of more parameters than described

const emp: IEmployee = {
	username: 'tome',
	age: 24,
	emplId: 34
}

const client: IUser = {
	username: 'tome',
	age: 24
}

////GENERICS
interface IAuthor {
	id: number,
	name: string,
}

interface ICategory {
	id: number,
	title: string,
}

interface IPost {
	id: number,
	title: string,
	desc: string,
	extra: IAuthor[] | ICategory[]
}
//passing a type
interface IPostBetter<T> {
	id: number,
	title: string,
	desc: string,
	extra: T[] //utilizing the passed type
}
//string is passed
const testme: IPostBetter<string> = {
	id: 1,
	title: "post title",
	desc: "clean bad after damage",
	extra: ["Str", "str2"],
}
//extending it for further usage
interface IPostEvenBetter<T extends object> {
	id: number,
	title: string,
	desc: string,
	extra: T[]
}
//passing it an object type
const testme2: IPostEvenBetter<{ id: number, username: string }> = {
	id: 1,
	title: "post title",
	desc: "clean bad after damage",
	extra: [{
		id: 1,
		username: 'A'
	}],
}
// extending another interface
const testme3: IPostEvenBetter<IAuthor> = {
	id: 1,
	title: "post title",
	desc: "clean bad after damage",
	extra: [{
		id: 1,
		name: "abc"
	}],
}
```
