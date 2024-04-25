# Types

1. Adds Type Checking
2. Better Autocompletion and error tracking
3. we can use next-gen javascript features (compiled down for older browsers)
4. Meta-Programming Features like Decorators
5. Highly Configurable


### Core Types


| Type   | Value           | Description                                                                            |
|--------|-----------------|----------------------------------------------------------------------------------------|
| number | 1,5.3,-10       | All Numbers, no difference between integers or floats                                  |
| string | "hi",'hi',`hi`  | All Text Values                                                                        |
| boolean | true,false      | only two, no "truthy" or "falsy" values                                                |
| Object | \{age:30}       | Any javascript object,more specific types (type of object) are possible                |
| Array  | [1,2,3]         | Any javascript array, type can be flexible or strict (regarding the element types)     |
| Tuple  | [1,2]           | Added By TypeScript, Fixed length array with defined types                             |
| Enum   | enum \{NEW,OLD} | Added By TypeScript, Automatically enumerated global constant identifiers              |
| Any    | *               | any kind of value, no specific Type assigned                                           |
| unknown | *               | any kind of value as we don't know what is type of variable , no specific Type assigned |
| never  | -               | never produces value as function crashes script or throws error  or struck in loop     |


* **Type Inference** - typescript understands and identify it's type and automatically typecasts it to it's type

```typescript
// both are same as mynum type is const and cannot be changed
const mynum=30;
const mynum2:number=30; 


// throws error here
let mynum:number;
mynum='ssdsd;
```

* Here person.name throws an error because we are telling typescript that person is object but we haven't given any information about object Properties
```typescript
const person:object={
    name:"mani",
    age:17
}
// Error
console.log(person.name)

const person={
    name:"mani",
    age:17
}
// Works fine as type infered automatically
console.log(person.name)
```

* there is more specific and correct way of declaring object types
```typescript
const person:{
    name:string,
    age:number
} = {
    name:"mani",
    age:17
}
// works fine
console.log(person.name)
```

### Array Type Casting
* type[]-> examples number[],string[]
* to support any type we can declare as -> any[]
### Tuple
* array with types defined as number and string

```typescript
// Array type casting
let activities: string[];
activities = ['cricket', 'gym']
//error
activities = [1, 3, 4]

enum Desgination {ADMIN = "ADMIN", READ_ONLY = 100, AUTHOR = "AUTHOR"}

const person2: {
    name: string, // string
    age: number, // number
    hobbies: string[], // array
    role: [number, string] // tuple
    desgination:Desgination // enum type
} = {
    name: "mani",
    age: 17,
    hobbies: ['cricket', 'gym'],
    role: [2, "description"],
    desgination: Designation.ADMIN
}
```


### Union Types & Literal Types
* we specify multiple types by using pipe operator, but we need to handle cases separately for each data type if it deals with different operations supported by different types
* Literal Type is where we specify value should be one of the mentioned values with union types
```typescript

function add(
    n1: number | string, 
    n2: number | string, // union type
    resultConversion: 'as-number' | 'as-string' // literal type
){
    if (typeof n1==="number" && typeof n2==="number"){
        return n1+n2
    }
    return n1.toString()+n2.toString()
}
const result=add(20,30)
const result2=add("mani","teja")
```
### Type Alias and Custom types
* we can define custom type using type keyword and use it anywhere in your project
* we can write more clean an d understandable and readable code with custom types
```typescript
type AddParam=number | string
type ResultConvertion='as-number' | 'as-string'
function add(
    n1: AddParam, 
    n2: AddParam, // union type
    resultConversion: ResultConvertion // literal type
):number{
    return n1+n2
}

```
### Function Return Types, Function Callbacks
* we can specify return value type of function by adding : after function params and typescript automatically infers value if we haven't set return value
* in same way we can specify callback function parameters and  return value
````typescript
function addAndPrint(
    n1:number,
    n2:number,
    cb:(num:number)=>void
):number{
    const result=n1+n2
    cb(result)
    return result
}
addAndPrint(10,20,(result)=>{
    console.log(result)
})
````
