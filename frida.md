![[frida.png]]
by Or Levy `ris:Award`
>ℹ️ **Reference**

 [Download Frida-Server](https://github.com/frida/frida/releases) 
 [Hooking Methods Examples](https://neo-geo2.gitbook.io/adventures-on-security/frida-scripting-guide/methods)
 [Frida Tutorial by hacktricks](https://book.hacktricks.xyz/mobile-apps-pentesting/android-app-pentesting/frida-tutorial) 
 [SSL Unpinning Js File](https://github.com/httptoolkit/frida-android-unpinning) 
 [Js Methods Templates](https://appsec-labs.com/portal/frida-cheatsheet-for-android/)
 [Examples](https://github.com/11x256/frida-android-examples)

<h2 style="color:#ffffff">Frida Installation</h2>

>**⚠️ Must install same version of Frida server and Frida client**
```bash
1. adb shell push <frida-server> /data/local/tmp/ (upload frida-server to device)
2. adb shell chmod 755 /data/local/tmp/<frida-server>
3. pip install frida-tools frida=<version>
4. Find location of frida-ps.py file, add the path to Enviorment Variables. 
```

<h2 style="color:#ffffff">Run Frida</h2>

```bash
1. ./data/local/tmp/<frida-server> (on device run frida-server)
2. frida-ps -U (On windows find app fullname)
3. frida -U -f <package_name> -l <fridascript.js> --no-pause (Inject with Frida)
```

<h2 style="color:#ffffff">Syntax</h2>
<h5 style="color:#ff99dd">Activity Usage</h5>

```java
var activity = Java.use('com.example.package.activity')
```

<h5 style="color:#ff99dd">Class Inside Class </h5> 

```java
var outsideClass = Java.use('com.example.package.activity');
var insideClass = outsideClass['inside_class_name']; 
var oneLiner = Java.use('com.example.package.activity$inside_class_name');
```

<h5 style="color:#ff99dd">Invoke a Constructor </h5>

```java
var javaString = Java.use('java.lang.String');
var myString = javaString.$new('New String Here');  
```

<h5 style="color:#ff99dd">Overload </h5>

> ℹ️ **If there are more than one function named func:** 
> we should use overload!

```java
activity.func.overload("int" , "int").implementation = function(x,y){

activity.func.overload("java.lang.String").implementation = function(x){
```

<h5 style="color:#ff99dd">this. Reference</h5>

> ℹ️ **this. ** : call the original implementation of the method, instead of reimplementing it

```java
activity.addTwoInts.implementation = function (var1,var2) {
    console.log("the method is being called");
    return this.addTwoInts(var1,var2);
}
```

<h5 style="color:#ff99dd">Accesing String attributes</h5>

```java
var activity = Java.use("com.example.package.activity");  
activity.function.implementation = function(){
	this.variable.value = 10000;
};
```

<h5 style="color:#ff99dd">.call function with arguments</h5>

> ℹ️ **call() function:** can use a method belong to another object


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

<h5 style="color:#ff99dd">Modify a Method - implementation</h5>

```java
Java.perform(function () {
	var activity = Java.use('com.example.package.activity');
	activity.function.overload().implementation = function()
	{
		var i = this.function(); //calling the original function
``` 


<h5 style="color:#ff99dd">PoC of decryption function:</h5>

![[example_decypt0 1.png|1000]]

![[example_decypt 2.png|1000]]
![[example_decypt1.png]]
After decrypted the string -k3FElEG9lnoWbOateGhj5pX6QsXRNJKh///8Jxi8KXW7iDpk2xRxhQ==
we get the flag **{This_Isn't_Where_I_Parked_My_Car} **
