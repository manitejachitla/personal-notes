# Classes and Interfaces

* classes declarations and syntax are same as un javascript with type declarations and type checking
* we can extend classes to access parent classname and super class constructor must be called first before accessing any this properties
* getters and setter are functions still they are accessible like functions
* static methods are directly accessible without class instantiation like (Math.pow(1,2))

### Class Important keywords
* **private** -> accessible by current class
* **public** -> by default everything is public and accessible outside class
* **protected** -> accessible by current class and extended class
* **readonly** -> cannot be changed
* **static** -> we can access any property or function without instantiation
* **abstract** ->  abstract methods will not have any implementation on base class but you have to implement that method in inherited classes

```typescript
abstract class Department {
    name: string; // public
    static EstYear=2020;
    private employee: string[] = [] // private property
    constructor(name: string) {
        this.name = name;
    }

    // getter
    get name(): string {
        return this.name
    }

    describe(this: Department) {
        console.log("name of department" + this.name);
    }

    // setter
    set setName(name: string) {
        this.name = name;
    }
    abstract customDescribe():void;
    static createEmployee(name: string) {
        return {name}
    }
}

const myDepartment = new Department('engineering')
myDepartment.getName // engineering
myDepartment.setName = "frontend-engineering" // engineering
myDepartment.name = 'frontend-engineering'
myDepartment.employee = ['epm1', 'emp2'] // Error


const emp1 = Department.createEmployee("maniteja")
console.log(Department.EstYear) // 2020
console.log(emp1) // {name:"maniteja"}
```

### Interfaces
* interface is a keyword in typescript and doesn't exist in javascript and it's a pure development feature
* Describes a structure of an object
* Interface Can't have intializer or any values
* used to specify type for objects 
* Interfaces can be inherited and 
```typescript
interface Person{
    name: string;
    age: number;
    greet(name:string):void;
}
let user:Person={
    name:"mani",
    age:20,
    greet:(n)=>{
        console.log("Welcome "+n)
    }
}
user.greet("mani")
```

* same like "**type**" in typescript but only difference is we can implement interfaces for classes
* this ensures that classes should have methods and we can tell user to add method if it's missing
* we can implement more than one interface for a single class
* we can extend(inherit) one interface with other interface to merge functionalities
* we cannot use public or private keywords in interfaces but we can declare a variable as readonly
```typescript
interface PersonInterface{
    readonly name: string; // this cannot edited
    age: number;
    nickName?:string; // optional property
    greet(name:string):void;
}
interface Employee extends PersonInterface{
    salary:number;
}
class Person implements PersonInterface{
    age: number=30;
    name: string;
    constructor(name:string) {
        this.name=name;
        this.age=age;
    }
    greet(name: string): void {
    }
}
const myPerson:PersonInterface=new Person('mani')
myPerson.name= 'teka' // error -  Cannot assign to 'name' because it is a read-only property.
```
* we can use interface to add type checking to functions as well
```typescript
interface AddFn {
    (a:number,b:number):number
}
const AddFunction:AddFn=(a:number,b:number)=>{
    return a+b
}
```

* we can Add Optional Parameter in Interface by Adding **?** after property name
* this tells typescript that this property is optional and may or maynot exist
* we can have optional parameters in functions and other type casting as well
```typescript
interface PersonInterface{
    readonly name: string; // this cannot edited
    age: number;
    nickName?:string; // optional property
    greet(name:string):void;
}
```