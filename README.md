# TypeScript

## Why TS ?

- Detect Errors without running the code by `Static Type Check (STC)`.
- Gives some features like Interface, Generics and Decorators.

## How it work ?

- Transpiler to compile TS code to JS code.
- Workaround for adding the features to js

## How to start ?

- install <pre> npm i -g typescript </pre>
- check for the version <pre> tsc -v </pre>
- compile the TS file <pre> tsc 'file name' </pre>
- compile and watch the TS file <pre> tsc -w 'file name' </pre>
- Start the config file <pre> tsc --init' </pre>

## Examples :

- Vars
<pre>
  JS 
    let x = 5;
    let k = 'meow';
  TS
    let x:number = 5;
    let k:string = 'meow';
    let m:any = 'enter any data type as js';
    let t ==> will typed as any if we dont assign a value;
    note : if i assing a value the type will be as the value type even if i dont type it 
    let three : (string | number) = 5; ==> this variable accepts two types of data
</pre>
- function
<pre>

  function addTwo(n1:number,n2:number){
    return n1+n2;
  } // this function with no return type

  function meow(x: number, y: string ):string {
  return y;
  } //this function must return a string

  function meow(x: number, y: string ):number {
  return x;
  } //this function must return a number

  function moew(name:string,age:number,cont?:string){
    return 'heeey cont parameter is an optional';
  } // cont parameter is optional and it's like that cause i added '?' and optional params must be at the end

  function meow(...numbers:number[]):number{
    let result = 0;
    numbers.foreach(num=>result+=num);
    return result;
  } // example for rest parameter using

</pre>

- arrays
<pre>
  let arrayOfStrings:string[] = ['one','two','three'];
  let arrayOfNumbers:number[] = [1,2,3];
  let mex: (string | number)[] =[1,'moew'];
  let multiArr: (string | number | string[]| (string|number|number[])[])[] = ['a', ['two'], 3,[1,[2],'six']];
</pre>

- objects 
<pre>
let myObject: {
  readonly username: string, //cant change it after assgin it
  id: number,
  hire?: boolean,  //optional
  skills: {
    one: string,
    two: string
  }
} = {
  username: "haimo",
  id: 100,
  hire: true,
  skills: {
    one: "HTML",
    two: "CSS"
  }
};
</pre>

- classes 
<pre>
  class User {
    u: string;
    s: number;
    msg: () => string;
    constructor(username: string, salary: number) {
      this.u = username;
      this.s = salary;
      this.msg = function () {
        return `Hello ${this.u} Your Salary Is ${this.s}`;
      }
    }
    sayMsg() {
      return `Hello ${this.u} Your Salary Is ${this.s}`;
    }
  }

  let userOne = new User("Haimouni", 6000);
</pre>

## Config file (Type Checking)

- noImplicitAny ==> gives an error if i dont mention the type of thing.
- noImplicitReturns ==> gives an error if the function doesnt return a value.
- noUnusedParameters ==> gives an error if we didnt add all the function parameters.
- noUnusedLocals ==> gives an error if we declare local variable and didint use it.

## Create alias
<pre>
type 'alias name'

type st = string;
type stAndNum = string | number

let x:st = 'Meow';
let y:stAndNums = 10 ;

</pre>

## Tuple Datatype
<pre>
-- Is Another Sort Of Array Type
-- We knows Exactly How Many Elements It Contains
-- We Knows Which Types It Contains At Specific Positions

let article: [number, string, boolean] = [11, "Title One", true];
article = [12, "Title Two", false];
article = [12, "Title Two", false,100]; // gives error
article.push(100); i can push to it if i want to disaple this i use 
let article: readonly [number, string, boolean] = [11, "Title One", true];

</pre>

## void and never Datatypes
<pre>
  - Void
  --- Function That Will Return Nothing
  --- Function In JavaScript That Not Return A Value Will Show undefined
  --- undefined is not void

  - Never
  --- Return Type Never Returns
  --- The Function Doesn't Have A Normal Completion
  --- It Throws An Error Or Never Finishes Running At All "Infinite Loop"


function logging(msg: string) : void {
  console.log(msg);
  return;
}

console.log(logging("Iam A Message"));
console.log("Test");

const fail = (msg: string) => {
  throw new Error(msg);
  // return 10;
}

function alwaysLog(name: string) : never {
  while(true) {
    console.log(name);
  }
  return 'meow' // this is unreachable code
}

alwaysLog("Osama");
console.log("Test");  // this is unreachable code
</pre>

## Enums 
<pre>
  - Enums => Enumerations (تعداد)
  --- Allow Us To Declare A Set Of Named Constants
  --- Used For Logical Grouping Collection Of Constants "Collection Of Related Values"
  --- It Organize Your Code
  --- By Default Enums Are Number-Based, First Element Is 0
  --- Theres A Numeric Enums
  --- Theres A String-Based Enums
  --- Theres Heterogeneous Enums [String + Number]
*/

const KIDS = 15;
const EASY = 9;
const MEDIUM = 6;
const HARD = 3;

enum Level {
  Kids = 15,
  Easy = 9,
  Medium = 6,
  Hard = 3
}

let lvl: string = "Easy";

if (lvl === "Easy") {
  console.log(`The Level Is ${lvl} And Number Of Seconds Is ${Level.Easy}`);
}
</pre>

## Assertions DataTypes 
<pre>
- Sometime Compiler Doesnt Know The Information We Do
- TypeScript Is Not Performing Any Check To Make Sure Type Assertion Is Valid

let myImg = document.getElementById("my-img") as HTMLImageElement;
console.log(myImg.src);
or 
let myImg = '<HTMLImageElement>' document.getElementById("my-img");
console.log(myImg.src);

let data: any = 1000;
console.log((data as string).repeat(3)); // no error check if i do assertion
</pre>


## Interface 
- its like type but in more fatured way
<pre>
interface User {
  id?: number;
  readonly username: string;
  country: string;
  sayHello() : string; // method return type
  sayWelcome: () => string;
  getDouble(num: number) : number;
}

let user: User = {
  id: 100,
  username: "Hemo",
  country: "Jordan",
  sayHello() {
    return `Hello ${this.username}`;
  },
  sayWelcome: () => {
    return `Welcome ${user.username}`;
  },
  getDouble(n) {
    return n * 2;
  }
}

console.log(user.id);
console.log(user.sayHello());
console.log(user.sayWelcome());
console.log(user.getDouble(100));
</pre>
- i can reOPEN it to add more featurs like 
<pre>
// Homepage
interface Settings {
  readonly theme: boolean;
  font: string;
}

// Articles Page
interface Settings {
  sidebar: boolean;
}

// Contact Page
interface Settings {
  external: boolean;
}

let userSettings: Settings = {
  theme: true,
  font: "Open Sans",
  sidebar: false,
  external: true
}
</pre>
- i can extend values from interface to another 
<pre>
interface User {
  id: number;
  username: string;
  country: string;
}

interface Moderator {
  role: string | number;
}

interface Admin extends User,Moderator {
  protect?: boolean;
}

let user: Admin = {
  id: 100,
  username: "Elzero",
  country: "Egypt",
  role: "Mod",
  protect: true
}
</pre>

## Data Access Modifiers & Parameters Properties
<pre>
  --- Public
  ------ All Members Of A Class In TypeScript Are Public
  ------ All Public Members Can Be Accessed Anywhere Without Any Restrictions
  --- Private
  ------ Members Are Visible Only To That Class And Are Not Accessible Outside The Class
  --- Protected
  ------ Same Like Private But Can Be Accessed Using The Deriving Class

  - TypeScript Is A Layer On Top Of JavaScript
  - It Should Remove All Annotations And Although Access Modifiers "Private For Example"

  class User {
    msg: () => string;
    constructor(private username: string, protected salary: number,public readonly address: string) {
      this.msg = function () {
        return `Hello ${this.username} Your Salary Is ${this.salary}`;
      }
    }
    sayMsg() {
      return `Hello ${this.username} Your Salary Is ${this.salary}`;
    }
  }

  let userOne = new User("hai", 6000, "amman");

  // console.log(userOne.username);
  // console.log(userOne.salary);
  console.log(userOne.msg());
  console.log(userOne.sayMsg());
</pre>

## Getter and Setter in classes 
- we used this when we apply incapsulation on a property at a class
- used to access it from outside the class it self
<pre>
class User {

  msg: () => string;
  constructor(private _username: string, public salary: number, public readonly address: string) {
    this.msg = function () {
      return `Hello ${this._username} Your Salary Is ${this.salary}`;
    }
  }
  sayMsg() {
    return `Hello ${this._username} Your Salary Is ${this.salary}`;
  }

  get username() : string{
    return this._username;
  }

  set username(value: string){
    this._username = value;
  }
}

let userOne = new User("Elzero", 6000, "Cairo");

console.log(userOne.username);
userOne.username = "Ahmed";
console.log(userOne.username);
console.log(userOne.salary);
console.log(userOne.msg());
console.log(userOne.sayMsg());
</pre>

## Statics in classes
- properties and method for the class it self
- keep away from reserved words like (length, name ..etc)
<pre>
  class User {
    static created: number = 0;
    static getCount() : void {
      console.log(`${this.created} Objects Created`);
    }
    constructor(public username: string) {
      User.created++;
    }
  }

  let u1 = new User("mohammad");
  let u2 = new User("jehad");
  let u3 = new User("haimopuni");
  console.log(User.created); 
  User.getCount();
</pre>

## Class implements interface 
<pre>
  interface Settings {
  theme: boolean;
  font: string;
  save(): void;
}

class User implements Settings {
  constructor(public username: string, public theme: boolean, public font: string) {}
  save(): void {
    console.log(`Saved`);
  }
  update(): void {
    console.log(`Updated`);
  }
}

let userOne = new User("Haimouni", true, "Open Sans");

console.log(userOne.username);
console.log(userOne.font);

userOne.save();
userOne.update();
</pre>

## Class abstraction 
- We Cannot Create An Instance Of An Abstract Class
<pre>
abstract class Food {
  constructor(public title: string) {}
  abstract getCookingTime() : void;
}

class Pizza extends Food {
  constructor(title: string, public price: number) {
    super(title);
  }
  getCookingTime() : void {
    console.log(`Cooking Time For Pizza Is 1 Hour`);
  }
}

class Burger extends Food {
  constructor(title: string, public price: number) {
    super(title);
  }
  getCookingTime() : void {
    console.log(`Cooking Time For Burger Is Half Hour`);
  }
}

let pizzaOne = new Pizza("Awesome Pizza", 100);

console.log(pizzaOne.title);
console.log(pizzaOne.price);
pizzaOne.getCookingTime();
</pre>

## Polymorphism & Method Override 
  - Polymorphism
  - Classes Have The Same Methods But Different Implementations
  - Method Override
  - Allowing Child Class To Provide Implementation Of A Method In Parent Class
  - A Method In Child Class Must Have Same Name As Parent Class
  - noImplicitOverride
<pre>
  class Player {
  constructor(public name: string) {}
  attack() : void {
    console.log("Attacking Now");
  }
}

class Amazon extends Player {
  constructor(name: string, public spears: number) {
    super(name);
  }
  override attack(): void {
    // super.attack();
    console.log("Attacking With Spear");
    this.spears -= 1;
  }
}

class Barbarian extends Player {
  constructor(name: string, public axeDurability: number) {
    super(name);
  }
  override attack(): void {
    // super.attack();
    console.log("Attacking With Axe");
    this.axeDurability -= 1;
  }
}

let barOne = new Barbarian("Elzero", 100);

console.log(barOne.name);
barOne.attack();
console.log(barOne.axeDurability);
</pre>

## Generics 
  - Help Write A Reusable Code
  - Allow To Pass Type As A Parameter To Another Type
  - You Will Be Able To Deal With Multiple Types Without Using ": Any Type"
  - We Can Create:
   Generic Classes
   Generic Functions
   Generic Methods
   Generic Interfaces
<pre>
function returnNumber(val: number) : number {
  return val;
}
function returnString(val: string) : string {
  return val;
}
function returnBoolean(val: boolean) : boolean {
  return val;
}

console.log(returnNumber(100));
console.log(returnString("Elzero"));
console.log(returnBoolean(true));

function returnType<Gnrc>(val: Gnrc) : Gnrc {
  return val;
}

console.log(returnType<number>(100));
console.log(returnType<string>("Hemo"));
console.log(returnType<boolean>(true));
console.log(returnType<number[]>([1, 2, 3, 4]));
</pre>

  - Arrow Function
  <pre>
    function returnType<T>(val: T): T {
      return val;
    }

  console.log(returnType<number>(100));
  console.log(returnType<string>("Haimoni"));

  const returnTypeArrowSyntax = <T>(val: T): T => val;

  console.log(returnTypeArrowSyntax<number>(100));
  console.log(returnTypeArrowSyntax<string>("Haimoni"));
  </pre>

  - Multiple Types
  <pre>
    function testType<T>(val: T): string {
      return `The Value Is ${val} And Type Is ${typeof val}`;
    }
   
    console.log(testType<number>(100));
    console.log(testType<string>("Elzero"));
   
    function multipleTypes<T, S>(valueOne: T, valueTwo: S): string {
      return `The First Value Is ${valueOne} And Second Value ${valueTwo}`;
    }
   
    console.log(multipleTypes<string, number>("mhmd", 100));
    console.log(multipleTypes<string, boolean>("haimouni", true));
  </pre>

  ## Genecic with Classes 
  <pre>
  class User<T = string> {
  constructor(public value: T) {}
  show(msg: T) : void {
    console.log(`${msg} - ${this.value}`);
    }
  }

let userOne = new User<string>("haimouni");
console.log(userOne.value);
userOne.show("Message");

let userTwo = new User<number | string>(100);
console.log(userTwo.value);
userTwo.show("Message");
</pre>

  ## Genecic with Interfaces
  <pre>
      interface Book {
    itemType: string;
    title: string;
    isbn: number;
  }

  interface Game {
    itemType: string;
    title: string;
    style: string;
    price: number;
  }

  class Collection<T> {
    public data: T[] = [];
    add(item: T) : void {
      this.data.push(item);
    }
  }

  let itemOne = new Collection<Book>();
  itemOne.add({ itemType: "Book", title: "Atomic Habits", isbn: 150510 });
  itemOne.add({ itemType: "Book", title: "Follow Your Heart", isbn: 650650 });
  console.log(itemOne);

  let itemTwo = new Collection<Game>();
  itemTwo.add({ itemType: "Game", title: "Uncharted", style: "Action", price: 150 });
  console.log(itemTwo);
  </pre> 