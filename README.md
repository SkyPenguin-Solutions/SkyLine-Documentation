![SLCBANNER](https://github.com/SkyPenguin-Solutions/SkyLine/blob/main/Documents/Designed/SL-0.0.5-release.png?raw=true "Title")


## SkyLine Documentation | What is this? ##

SkyLine is still in a very very experimental stage, because of this we can not truly provide documentation that people can rely on that is considered to be official because of the drastic and fluid changes happening during 0.10.0's development. However, to compensate for that, we have provided this repo which contains syntactic rule sets, plans and a whole basic documentation set of the language. This includes how to work with statements, functions, libraries and more.

## SkyLine Documentation | Variables ##

Variables in SkyLine are quite easy, each data type (`String, Float, Boolean, Error, Function, Array, Hash`) all have their own unique object call methods and all unique operators. Below you will find bullet points that talk about these data types and declaring them as variables and then modifying the values.

> Note: Keywords such as set, let, cause, allow are all doing the same thing, they all allow you to create and assign base variables into the environment of the language. SkyLine has some basic issues with only using one keyword because the developer firmly believes in fluidity. The mash and mix of keywords while all doing the same thing all allow the people and developers to use a specific style when in further development.

> ### Strings (Rules & Operators) | Module 0.1 ###

> **Strings**

Given that SkyLine is a dynamic programming language, a string data type is assumed with `""` which makes it pretty easy to understand 

```rs
set x := "data";
```

When working with strings, you may want to increase the value of the string, or manipulate it in some shape or form. Currently strings have the supported operators 

| Operator | Type    |
| -------- | ------- |
| =        | String  |
| +=       | String  |
| *=       | String  |
| :=       | Any     |

These are weird operators to see supported with a string data type, why does `*=` even exist? We will get to that in just a second but first lets see some base examples of a string 

<br>

**Operator(+=)**

<br>

```rs
set name := "Ryan";

Ryan += "20";

// Result: Ryan20
```

This program simply declares a string value and then adds the string value "20" to the string which results in `Ryan20`

<br>

**Operator(=)**

```rs
set name := "Ryan";

name = 10;

// Result: Integer->10
```

The `=` operator works the same as any other programming language, it does what it seems, assigns a new value to a variable. Because SkyLine is dynamic, you can assign any data type to an existing value. Unlike some languages which do not allow you to assign another value of another data type. In this case SkyLine changed the name variable from `String->Integer`

**Operator(*=)**

This one is going to be quite confusing for some people so we can make this as basic as possible. The **=* operator in this case is an operator that will multiple one string on the left side by the length of another string on the right side of the string. Lets write a simple program to demo this.

```rs
cause x := "hello world ";

x *= "aaaa";

// Result: hello world hello world hello world hello world hello world
```

This results in the phrase `hello world` to be added to the string value 4 times. This acts as a String.Repeat() function that will repeat the string based on the length of another string. Because the left of the operator `*=` is the value you are going to repeat, SkyLine will check the length of the string on the right side and use that as a count to multiply the strings. If the string on the right had one more `a` in it, then the length would be 5 which would tell SkyLine to repeat the string value of `x` 5 different times and append it to the current string.

**Operator(:=)**

This is just a bind operator, it assigns a value to the environment and creates a new variable.

```rs
cause x := 10; // Variable of type Integer
cause n := "hi"; // Variable of type String
```

**Rule (Special Characters / Unicode)**

Currently the `String` type in SkyLine does not have support for many unicode characters especially when working with other strings or values. However there are some in our case which work as follows 

```rs
allow value := "data2";

println("Value: \t " + value)
println("Value: \n " + value)
println("Value: \r " + value)
```

`\f` and `\v` also are very well used, however it has become apparent that using strings or values like `\n` at the end or beggining of the string or value will result in an error or a frozen parser. The freeze is NOT intentional but this is definitely in the rule sets to provide a much more slick ability for parsing on the backend. 

####Integers (Rules & Operators) | Module 0.2####

Integers in SkyLine ( 0.0.5 ) are defined as an integer64 data type on the backend. Which means that there is no other Integer data type in SkyLine since integer64 is the highest integer you can store. In this case, integers are quite easy to understand.

```rs
cause age = 18;

//Result: Integer->18
```

This is quite simple right?

When working with Integers, it becomes apparent that you will need quite some operators. Since SkyLine is working heavily on its backend and the actual design of the language has not been fully implemented, we only can provide you with a base chart of operators that exist for Integer data types.

| Operator | Type     | Operation / Computation |
| -------- | -------- | ----------------------- |
| =        | Integer  | Assignment              |
| *=       | Integer  | Multiplication equals   |
| -=       | Integer  | Subtraction equals      | 
| /=       | Integer  | Division equals         | 
| -        | Integer  | Subtraction             | 
| /        | Integer  | Division                | 
| *        | Integer  | Multiplication          | 
| **       | Integer  | Powerof                 |
| +        | Integer  | Addition                |
| :=       | Any      | Variable creation       |  
| --       | Integer  | Subtract one            |
| ++       | Integer  | Add one                 |  

These are weird operators to see supported with a string data type, why does `*=` even exist? We will get to that in just a second but first lets see some base examples of a string 

<br>

**Operator(=)**

<br>

This operator does the same thing as any other case, assigns a new value.

```rs
cause x := 10;

x = "hello";
```

<br>

**Operator(*=)**

<br>

This will multiply then add values to the current value. For example `20 += 40` will add 40 to 20, the left side of the operator is the value you are changing 

```rs
cause x := 10;

x *= 20

//Result: 200
```

<br>

**Operator(-=)**

<br>

This operation will subtract the left by the right side.

```rs
set x := 10;

x -= 5

//Result: 5
```
<br>

**Operator(/=)**

<br>

This operation will divide the left by the right side.

```rs
cause x := 10;

x /= 5

//Result: 2
```

<br>

**Operator(-- & ++)**

<br>

The operation `--` will subtract one from the current value ( in the case of integers ) and `++` will add one to the current value.

```rs
set age = 18;

age++

//Result: age=19

age--

//Result: age back to 18
```
<br>

**Operator(-, +, /, *, **) **

<br>

All of these operators work the same as any other language.

```rs

allow data := 10;

(data - 20)   // Result: -10
(data + 20)   // Result: 30
(data / 20)   // Result: 0
(data ** 20)  // Result: -9223372036854775808
(data * 20)   // Result: 200
```

####Floats (Rules & Operators) | Module 0.3####

Floats on the backend are parsed as a float64 value. This means that the float values in SkyLine max out to ` 1.8 x 10^308` the IEEE 754 binary64 format. This will be a environment based constant in the future and floats in 0.10.0 will no longer be floats and rather be Float32 and Float64. You can declare a float like so in SkyLine.

> Note: Operators were not added here because they are the same as integers

<br>

```rs
allow age = 1.5;

println(age - 15)
```

Floats are pretty easy to understand and work the same as integers but are parsed and evaluated / treated differently.


####Booleans (Rules & Operators) | Module 0.4####

Booleans are easy to understand, as keywords build booleans such as `true` and `false`. Booleans only have one major operator to work with that is not a comparison operator. That operator / expression is `--`. Weird right? Most programming languages only reserve `++` and `--` as a expression for numerical data types. In SkyLine a `--` mixed with a variable with a true value will make it a false value. 

```rs
cause ofage := true;

ofage--

println(ofage)

//Result: false
```

The keys `++` Do not exist for true and false values right now. Booleans can also be declared using `BOOLEANF` and `BOOLEANT`

>







