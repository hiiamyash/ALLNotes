
![[../../../attchments/Pasted image 20250403100519.png]]


![[../../../attchments/Pasted image 20250403100627.png]]


```js
// var str="JavaScript"

// console.log(str)

  

// var str1=str.length

// console.log(str1)

  

// var str2 =str.charAt(4)

// console.log(str2)

// var str3 =str.charCodeAt(3)

// console.log(str3)

  

// var str4 = str.at(11)

// console.log(str4)

  

// var str5 = str[6]

// console.log(str5)

  
  

// //slice method

  

// var str6=str.slice(5,9);

// console.log(str6)

  

// //substring method

  

// var str7=str.substring(-1,5)

  
  

// console.log(str7)

  

// var str8 = str.substr(2,4)

// console.log(str8)

  

// var str9 = str.toUpperCase()

// console.log(str9)

  

// var str9 = str.toLowerCase()

// console.log(str9)

  

// var str10 = "char"

// var str11 = " mander"

  

// var str12 = str10.concat(str11)

// console.log(str12)

  

// // var x1 = " Pu "

// // console.log(x1)

// // var str_len = x1.length

// // console.log(str_len)

// // var x2=x1.trim()

// // console.log(x2)

  

// // var x1 = " Pu "

// // console.log(x1)

// // var str_len = x1.length

// // console.log(str_len)

// // var x2=x1.trimStart()

// // console.log(x2)

  
  
  

// // padstart

  

// // var x1 = "SSk"

// // var x2=x1.padStart(9,"Hi")

// // console.log(x2)

  

// //repeat

  

// // var x1="SSk"

// // var x2=x1.repeat(4.7)

// // console.log(x2)

  
  

// //replace

  

// // var x1="I am llearning javascript"

// // console.log(x1)

// // var x2=x1.replace("java","Bash")

// // console.log(x2)

  

// //replaeall

  

// // var x1="I am llearning javascript i love java"

// // console.log(x1)

// // var x2=x1.replaceAll("java","Bash")

// // console.log(x2)

  
  

// //split

// // var x1= "html-javascript-css-python-java"

// // var x2=x1.split("s")

// // console.log(x2)

  
  

// //indexof

  

// // var x1="I am learning Javascript"

// // var x2=x1.indexOf("huhu");

// // console.log(x2)

  
  
  

// //lastindexof

  

// // var x1="I am learning Javascript Javascript"

// // var x2=x1.lastIndexOf("Javascript",15);

// // console.log(x2)

  
  
  

// //search

  

// // var x1="Helloo World ,I am learning Hello World program"

// // var x2=x1.search("o")

// // console.log(x2)

  
  
  
  
  
  
  

// //match

  
  
  

// // var x1="The price of pizza iss $100 but the discounted prize is $50"

// // var x2=x1.match(/\$\d+/g)

// // console.log(x2)

  
  
  

// //include

  

// // var x1 = "Hello world ,welcome to my "

// // var x2=x1.includes("world",8)

// // console.log(x2)

  
  
  
  

// //Startswith

  

// var x1 = "Hello world ,welcome to my "

// var x2=x1.startsWith("Hello")

// console.log(x2)

  

// var x1 = "Hello world ,welcome to my "

// var x2=x1.endsWith("world",8)

// console.log(x2)

  
  
  

// console.log("the result is:"+10+20)

// console.log(10+20+"is the result")

// console.log(10+"20"+"is the result")

// console.log(10+"20"+20)

// console.log(10+"20"+20+"heloo")

  
  

// console.log(10+20+"30")

// console.log("100"/"10")

// console.log("100"/"10"+"30")

// console.log("100"/"10"+30)

// console.log("100"*"10")

// console.log("100"-"10")

// console.log("100"-10)

// console.log("100"*10)

  
  
  
  

// var y=0.2 +0.1

  

// console.log(y)

  
  

// var z=234*0.44

// var t=z.toPrecision(5)

// console.log(t)

  
  
  

console.log(Number(true))

console.log(Number(false))

console.log(Number("10"))

console.log(Number(" 10"))

console.log(Number("10 "))

console.log(Number(" 10 "))

console.log(Number("10.33"))

console.log(Number("10,33"))

console.log(Number("10 33"))

console.log(Number("John"))
```



![[../../../attchments/Pasted image 20250403104951.png]]


```js
// var student={

// name_1:"yash",

// roll_no:65,

// branch:"CSE",

// isstudent:true

  

// }

  

// console.log(student.branch)

// student.roll_no = 100

// console.log(student.roll_no)

// student.hobby = "Study"

  
  

// for (let a in student) {

// console.log("The Details are " +a+ " : "+student[a])

// }

  
  

// let x = new Object();

// console.log(x)

// x.name="yash"

// console.log(x)

// x.roll_no=3

// console.log(x)

  

// let person ={

// name:"Jhon",

// tech:"JS",

// laptop:{

// cpu:"i7",

// ram:"4GB",

// brand:"dell"

// }

// }

// console.log(person)

// console.log(person.laptop.brand)

// console.log(person.laptop.cpu)

  

// console.log("Double ")

  

let branch=["CSE","AI","ML","Cyber Secutity"]

  

console.log(branch)

var b1=branch[2]

console.log(b1)

  

var x =new Array(5)

console.log(x)

x[0]= "hi"

x[1] = "hello"

x[2] = "Bye"

console.log(x)

x[2] = "Pu"

console.log(x)

var x6 = x.toString()

console.log(x6)

  

var x_len = x6.length;

console.log(x_len)

  

x.push("Parul University")

console.log(x)

  

x.pop()

console.log(x)

  

x.shift()

console.log(x)

x.unshift("Varodara")

console.log(x)

delete x[2]

console.log(x)

  
  

var y = [1,4,2,7,6,3,8]

console.log(y)

var x2 = x.concat(y)

console.log(x2)

```


![[../../../attchments/Pasted image 20250403134851.png]]


![[../../../attchments/Pasted image 20250403135658.png]]

![[../../../attchments/Pasted image 20250403141525.png]]


![[../../../attchments/Pasted image 20250403150347.png]]





