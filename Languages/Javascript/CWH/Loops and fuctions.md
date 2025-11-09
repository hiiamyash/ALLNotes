
![Pasted image 20250402081710](Pasted%20image%2020250402081710.png)

```js
for(i=0 ;i<555 ;i++){

console.log(i)

}
//output will be 0 to 554 numbers

for(i=0 ;i<555 ;i++){

console.log(i+1)

}
//output will be number form 1 to 554
```
![Pasted image 20250402082236](Pasted%20image%2020250402082236.png)

```js
let sum=0
let n=prompt("Enter the Number : ")

n=Number.parseInt(n)

for(i=0 ;i<n ;i++){

    sum+=(i+1)
    
}
console.log("SUm of "+n+" is "+sum)

//above program is used to find the sum of first natural numbers
```

![Pasted image 20250402083704](Pasted%20image%2020250402083704.png)

for-in loop **loops through only the keys in an object

```js
let obj={

ritik: 90,

harry: 99,

aayush:87,

ishika: 90,

janvi:77,

ashutosh:88

}

  

for(let a in obj){

  

console.log("Marks of "+a+" is " +obj[a])

}

/*This will be the output

Marks of ritik is 90
Marks of harry is 99
Marks of aayush is 87
Marks of ishika is 90
Marks of janvi is 77
Marks of ashutosh is 88

*/

```


![Pasted image 20250402084517](Pasted%20image%2020250402084517.png)

for-of loop will print the object value if it is itrable

```js
// For of loop
for (let b of "Harry") {
  console.log(b)
}
```
