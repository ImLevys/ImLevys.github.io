---
title: Frida
---


![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/frida.png?raw=true) 

by Or Levy 

![alt text](https://raw.githubusercontent.com/ImLevys/ImLevys.github.io/0833398999c052a6a875dbd5fdc42bd5d0a706dc/Android/images/reference.svg)

 [Download Frida-Server](https://github.com/frida/frida/releases) 
 
 [Hooking Methods Examples](https://neo-geo2.gitbook.io/adventures-on-security/frida-scripting-guide/methods)
 
 [Frida Tutorial by hacktricks](https://book.hacktricks.xyz/mobile-apps-pentesting/android-app-pentesting/frida-tutorial) 
 
 [SSL Unpinning Js File](https://github.com/httptoolkit/frida-android-unpinning) 
 
 [Js Methods Templates](https://appsec-labs.com/portal/frida-cheatsheet-for-android/)
 
 [Examples](https://github.com/11x256/frida-android-examples)

<h2 style="color:#000000">Frida Installation</h2>

![alt text](https://raw.githubusercontent.com/ImLevys/ImLevys.github.io/c575f9cfff34f358725a559b7351a6496e23bd70/Android/images/warning-markup.svg)
```bash
1. adb shell push <frida-server> /data/local/tmp/ (upload frida-server to device)
2. adb shell chmod 755 /data/local/tmp/<frida-server>
3. pip install frida-tools frida=<version>
4. Find location of frida-ps.py file, add the path to Enviorment Variables. 
```

<h2 style="color:#000000">Run Frida</h2>

```bash
1. ./data/local/tmp/<frida-server> (on device run frida-server)
2. frida-ps -U (On windows find app fullname)
3. frida -U -f <package_name> -l <fridascript.js> --no-pause (Inject with Frida)
```

<h2 style="color:#000000">Syntax</h2>
<h4 style="color:#008B8B">Activity Usage</h4>

```java
var activity = Java.use('com.example.package.activity')
```

<h4 style="color:#008B8B">Class Inside Class </h4> 

```java
var outsideClass = Java.use('com.example.package.activity');
var insideClass = outsideClass['inside_class_name']; 
var oneLiner = Java.use('com.example.package.activity$inside_class_name');
```

<h4 style="color:#008B8B">Invoke a Constructor </h4>

```java
var javaString = Java.use('java.lang.String');
var myString = javaString.$new('New String Here');  
```

<h4 style="color:#008B8B">Overload </h4>

> **If there are more than one function named func:** 
> we should use overload!

```java
activity.func.overload("int" , "int").implementation = function(x,y){

activity.func.overload("java.lang.String").implementation = function(x){
```

<h4 style="color:#008B8B">this. Reference</h4>

> **this.** : call the original implementation of the method, instead of reimplementing it

```java
activity.addTwoInts.implementation = function (var1,var2) {
    console.log("the method is being called");
    return this.addTwoInts(var1,var2);
}
```

<h4 style="color:#008B8B">Accesing String attributes</h4>

```java
var activity = Java.use("com.example.package.activity");  
activity.function.implementation = function(){
	this.variable.value = 10000;
};
```

<h4 style="color:#008B8B">.call function with arguments</h4>

> **call() function:** can use a method belong to another object


```java
const person = {  
	fullName: function(city, country) {  
	return this.firstName + " " + this.lastName + "," + city + "," + country;  
 }  
}  
  
const person1 = {  
	firstName:"John",  
	lastName: "Doe"  
}  
//This will return "John Doe,Oslo,Norway":
person.fullName.call(person1, "Oslo", "Norway");
```

<h4 style="color:#008B8B">Modify a Method - implementation</h4>

```java
Java.perform(function () {
	var activity = Java.use('com.example.package.activity');
	activity.function.overload().implementation = function()
	{
		var i = this.function(); //calling the original function
``` 


<h4 style="color:#008B8B">PoC of decryption function:</h4>

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/example_decypt0%201.png?raw=true)

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/example_decypt%202.png?raw=true)
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/example_decypt1.png?raw=true)

After decrypted the string -k3FElEG9lnoWbOateGhj5pX6QsXRNJKh///8Jxi8KXW7iDpk2xRxhQ==

we get the flag **{This_Isn't_Where_I_Parked_My_Car} **
