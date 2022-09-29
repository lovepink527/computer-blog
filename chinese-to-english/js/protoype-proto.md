### The orginal link: https://github.com/mqyqingfeng/Blog/issues/2

## the constructor creates an object
-----
We start by creating an object using the constructor
```javascript
function Person() {

}
var person = new Person()
person.name = 'jianghuihui'
console.log(person.name) // jianghuihui
```
In this example,Person is a constructor, and we create an instance Person using new.
Pertty simple,right? Let's get down to business:
## prototype
Each function has a prototype property,the prototype we often see in various examples,sush as:
```javascript
function Person() {

}
// Prototype is a function property
Person.prototype.name = 'jianghuihui';
var person1 = new Person();
var person2 = new Person();
console.log(person1.name) // jianghuihui
console.log(person2.name) // jianghuihui
```
Prototype is a function property so what does the prototype property of this function refer to? Is that the prototype for this function?

In fact,the prototype property of the function points to an object that is the prototype of the instance created by calling the constructor,which is the prototype of Person1 and Person2 in this example.

So what is a prototype? You can think of it this way: every javascript object(except the null) is associated with another object when it is created.This object is called a stereotype, and every object "inherits" properties from the stereotype.

Let's use a diagram to show the relationship between a constructor and instance stereotype:
![image](https://camo.githubusercontent.com/02789d6806b75d34b2017021f58efa3aa7a2ee6be8a0c05fb3293438884b9ec0/68747470733a2f2f63646e2e6a7364656c6976722e6e65742f67682f6d717971696e6766656e672f426c6f672f496d616765732f70726f746f74797065312e706e67)

In this diagram we use Object.prototype to denote an instance prototype.

So how do we represent the relationship between an instance and its prototype, namely Person and Person.prototype, which brings us to the second property:

## _proto_

This is a property that every javascript object(except null)has called _proto_, which points to the prototype of the object.

To prove this, type in Firefox or Google:

```javascript
function Person() {

}
var person = new Person();
console.log(person.__proto__ === Person.prototype); // true
```

So let's update the diagram:

![image](https://camo.githubusercontent.com/3dde335faa15d03ffe3b907f6e5c2b5f4d2183caa4c47ac7486794bc407f663c/68747470733a2f2f63646e2e6a7364656c6976722e6e65742f67682f6d717971696e6766656e672f426c6f672f496d616765732f70726f746f74797065322e706e67)

Since instance objects and constructors can point to a stereotype, does the stereotype have properties that point to constructor or instance?



