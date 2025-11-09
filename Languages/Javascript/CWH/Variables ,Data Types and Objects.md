
![[Pasted image 20250401184429.png]]

**javascript allows to change the type of interger during thee runtime

#### **Three types of varuable definer

- **Const
- **Var
- **let

![[Pasted image 20250401184953.png]]

![[Pasted image 20250401185125.png]]

**let ki madad se Block ke ander ki baat block mai hi rahti hai 
agar humne block me andar b ki value change ki using let then uski value sirf block mai hi change hogi globally nahi while agar var use kiya tho block mai bhi change ho gi and globlaay bhii**


![[Pasted image 20250401185552.png]]
**you can do this with let 


![[Pasted image 20250401185813.png]]

**const can not be undefined
```js
const x; //this will thorw error

const x =3; // tthis will not throw error

```

---

### **7 Types of primitive data types


![[Pasted image 20250401190550.png]]

![[Pasted image 20250401190920.png]]

```js
// nn bb ss u primitive data types in js
let a =null;
let b=455;
let c=true; // can also be false
let d=BigInt("567")
let e="Harry";
let f=Symbol("I am a nice symbol)
let g=undefined

console.log(a,b,c,d,e,f,g)
console.log(typeof b) // this will print what 
// null
// number
// bloolean
// bigint
// string
// Symbol
// undefined

// nn bb ss u
```


### **Objects in JS

![[Pasted image 20250401203555.png]]
```js
// Non -primitive data type in python is Objects
const item={
	"Harry": true,
	"Shubh": false,
	"Lovish":67,
	"rohan":undefined

}
console.log(item["Harry"])

```

**Objets are used to make key value pairs


---

## Questions


![[Pasted image 20250401204447.png]]


![[Pasted image 20250401204433.png]]

**in the above image you can see the output

```js

//Chapter 1 Q1

let a = "harry"
let b = 6
console.log(a+b)

/*Output: harry6*/

//chapter 1 Q2
console.log(typeof (a+b))

// Output: string

//Chapter 1 Q3

const a1= {
	name:"harry",
	Section:1,
	inPrinciple:false
	
}
a1 = 45
// You cannot change 


//Chaptter 1 Q4

const a1= {
	name:"harry",
	Section:1,
	inPrinciple:false
	
}
a1['friend'] = "Harry" //here you aare adding an new key value pair
a1['name'] = "lovish" //here you are editing an existing key value pair

// chapter 1 Q5




```

![[Pasted image 20250401221426.png]]
this wil print the value of yaka 

another way would be
```js
console.log(dict[yakka])
```












