![SLCBANNER](https://github.com/SkyPenguin-Solutions/SkyLine/blob/main/Documents/Designed/SL-0.0.5-release.png?raw=true "Title")


## SkyLine Documentation | What is this? ##

SkyLine is still in a very very experimental stage, because of this we can not truly provide documentation that people can rely on that is considered to be official because of the drastic and fluid changes happening during 0.10.0's development. However, to compensate for that, we have provided this repo which contains syntactic rule sets, plans and a whole basic documentation set of the language. This includes how to work with statements, functions, libraries and more.

## SkyLine Documentation | Variables ##

Variables in SkyLine are quite easy, each data type (`String, Float, Boolean, Error, Function, Array, Hash`) all have their own unique object call methods and all unique operators. Below you will find bullet points that talk about these data types and declaring them as variables and then modifying the values.

> Note: Keywords such as set, let, cause, allow are all doing the same thing, they all allow you to create and assign base variables into the environment of the language. SkyLine has some basic issues with only using one keyword because the developer firmly believes in fluidity. The mash and mix of keywords while all doing the same thing all allow the people and developers to use a specific style when in further development.

<br>

# Data types #

> ### Strings (Rules & Operators) | Module 0.1 ###

<br>

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
<br>

> ### Integers (Rules & Operators) | Module 0.2 ###

<br>

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
<br>

> ### Floats (Rules & Operators) | Module 0.3 ###

<br>

Floats on the backend are parsed as a float64 value. This means that the float values in SkyLine max out to ` 1.8 x 10^308` the IEEE 754 binary64 format. This will be a environment based constant in the future and floats in 0.10.0 will no longer be floats and rather be Float32 and Float64. You can declare a float like so in SkyLine.

> Note: Operators were not added here because they are the same as integers

<br>

```rs
allow age = 1.5;

println(age - 15)
```

Floats are pretty easy to understand and work the same as integers but are parsed and evaluated / treated differently.


<br>

> ### Booleans (Rules & Operators) | Module 0.4 ###

<br>


Booleans are easy to understand, as keywords build booleans such as `true` and `false`. Booleans only have one major operator to work with that is not a comparison operator. That operator / expression is `--`. Weird right? Most programming languages only reserve `++` and `--` as a expression for numerical data types. In SkyLine a `--` mixed with a variable with a true value will make it a false value. 

```rs
cause ofage := true;

ofage--

println(ofage)

//Result: false
```

The keys `++` Do not exist for true and false values right now. Booleans can also be declared using `BOOLEANF` and `BOOLEANT`

<br>

> ### Functions (Rules & Syntax) | Module 0.5 ###

<br>

Functions in SkyLine are still currently being worked on and actively being modified. However their syntax for a function will result in the same thing every time. One thing that SkyLine's design implies is that it looks like a compiled programming language and is still working to fill that. Right now, functions in SkyLine can do multiple things such as return any data type, take in as many arguments as possible and even take in any data type.

Below are some examples of data types

**Basic function**

```rs
cause Data := Func() {
  println("hello world")
};
```

Every function is defined in two ways `Func` or `function`. There is a reason there are two seperate keywords, this is because in later versions of the language, there will be rules for importing data. Currently, SkyLine allows you to import and export data such as variables, functions, hashes, results and outputs as long as the first value in the name is capitalized. This means in the future if you want to export a function you will need to use `Func` or make the first letter of the function name capitalized. Functions also MUST end with a semicolon, this is not optional.

**Subtraction function (Sample returns)**

```rs
cause subtract := Func(x, y) {
  ret x - y;
};

set cause := subtract(10, 20);

println(res)
```

This program is quite simple and allows users to understand how to return data. Returning data in SkyLine is quite easy as you can use both `ret` and `return` keywords to return a result. In some cases, depending on configuration you may not need to use return at all and can just produce an output like `x - y;` in the function and it will still print it out. You cann a function by calling the variable name followed by `()` and if there are arguments that need to be filled then you need to fill those arguments. 


<br>

> ### Hash Maps and Arrays (Rules & Syntax) | Module 0.6 ###

<br>

The first thing we will hop into is just hash maps. Hash maps in SkyLine are easy to understand and have their own unique parts to them such as the way you can store and return data. Hash maps are fluid which means they can take in any data type and output any data type. In future versions this will not exist by default and will be customizeable using the SLC ( SkyLine Configuration language ). Below are some examples of hash maps 

> #### Hash Maps ####

**Basic hash map and call**

```rs
{
  "hello": Func(x) {println("hello " + x )},
  "world": "hello"
}["hello"]("world");
```

This program is quite confusing to some people so let us break it down. SkyLine in itself does not have direct rules for how you can use hash maps other than the fact that hash maps require you to not use a comma after the last value in the map and also require that in some cases you end the braces with a semicolon. This program will declare a hash map using `{}`, it stores two values which are the input values. If the key `hello` is found in the map, then the function will be executed, and if the key is `world`, `hello` will output.

```rs
result: hello world
```

**Using hashes properly**

Typically you do not want the mess above, so we can declare a hash like this.

```rs
set MapofCommands := {
  "hello": 1,
  "t": true,
  "f": false,
  "age": 18,
  1.0: 1
};
```

which again notice how a semicolon ends the hash and the last key and value pair `1.0: 1` does not have a comma after it. 


> #### Arrays ####

Arrays in SkyLine are quite simple, SkyLine allows you to store any value and any result inside of an array. Arrays are defined with `[]` and have their values typically seperated by `,`. Below are some examples of arrays.

**Basic Array**

```rs
set x := ["name", "value", 1, 1.5, true, false];
```

**Array indexing**

Array indexing is quite easy and the only support for arrays right now is a numerical index which means that if you want to index the array, you have to index it based on the positions. For example if we wanted `name` out of `x` we need to index it by 0 like so.

```rs
set x := ["name", "value", 1, 1.5, true, false];

x[0]

//Result: String->name
```

**Calling functions from arrays**

Like the hash maps, functions are also supported

```rs
set NewArray := [
    "data",
    "newdata",
    Func(x, y) { return x - y; },
    "data2"
];

NewArray[2](10, 20)
```

# Object Call functions #

Each object within the SkyLine programming language is allowed to have their own unique object call functions otherwise known as invokes. These functions allow you to easily execute functions and get results quicker. Since there are only minimal data types we have listed a table below and all of their methods 

| Data Type / Ex | Object Call / Method / Invoke |
| -------------- | ----------------------------- |
| String         | Boolean, Float, Integer, Length, Lower, Methods, Ord, Split, Title, Trim, UnlinkRegistry, Upper, View |
| Boolean        | methods, View |
| Integer        | methods, View, chr |
| Float          | methods, View, chr |
| Array          | Append, Compare, Copy, Length, Less, Methods, PopL, PopR, Reverse, Swap, Typeof, View |
| Hash / Map     | keys |

> ### Object Call Functions ( Calling ) | Module 0.0 ###

Calling a standard library function and an object function is pretty easy. All you have to do is place the data type or value holding a specific data type followed by a period and the function you are calling. The function below will dump all of the keys to a hash map.

```rs
cause x := {
    "hey": "Hello there!",
    1: 2,
    1.5: 1
};

x.keys()

//result: Array->[hey, 1, 1.5]
```

Note that this list will go from the ones with the best methods and then go down to simplifying general methods.

> ### String methods | Module 0.1 ###

Strings have a ton of methods, especially conversion methods. Later on, similar to the Go programming language. These methods will be automatically pushed into a standard library due to the amount of methods that could be thrown into these data types especially Strings.

**Boolean**

The boolean function allows you to try to convert or parse a string value as a boolean value.

```rs
cause x := "true";

x.Boolean()
//Result: Boolean->true
```

**Float**

Float does the same thing as a boolean conversion function. It attempts to convert the string value to SkyLine's Float type.

```rs
set x := "1.5";

x.Float()
//Result: Float->1.5
```

**Integer**

String to Integer conversion.

```
set age := "16";

age.Integer()
//Result: Integer->16
```

**Length**

The length call will get you the length of the string 

```rs
set name := "Ryan age 16";

name.Length()
//Result:Integer->11
```

**Lower**

Will convert the string to all lowercase values 

```rs
set Name := "NaMe";

Name.Lower()
//Result:String->name
```

**Upper**

Opposite of lower, will make everything uppercase.

```rs
set Name := "ryan";

Name.Upper()

//Result:String->RYAN
```

**Ord**

Will getthe Unicode code point of a single character string. The term "ord" or 
"ordinal" refers to the position of a character in the Unicode character set


```rs
set a := "Hello world";

a.Ord()
//Result: Integer->72
```

If the string is longer than 1 then the first character will be called to return the value.

**Title**

Will make everythin capital 

```rs

set title := "hackers break into tesla!";

title.Title()
Result: String->HACKERS BREAK INTO TESLA!
```

**Split**

Splitting is quite easy to understand, it will split at a given point in the string or split the string by a given split set. Say we want to seperate `name,age,date,row,column_id` but can not get that data to be single so we can use split to seperate everything.

```rs
set data := "name,age,date,row,column_id";

data.Split(",")

//Result: Array -> [name, age, date, row, column_id]
```

**Trim**

Trims the string by a given cutset, trim is a bit broken right now and we will address this issue when 0.10.0 comes out.

**View**

Almost every data type has this in the language, but view is the view of what the AST has structured.

```rs
set v := "data".View();

v

//Result: String->data
```

> ### Array methods | Module 0.2 ###

Arrays have many methods that allow you to compare, copy, pop and even swap values within the array. Below these methods are shown and ran as an example below.

**Append**

Append data to arrays only exists within strings right now but a base example is shown below.

```rs
set x := [];

x.Append("hello")

x

//Result: Array->[hello]
```

**PopL**

PopL stands for pop left which will pop the left most value from the array, so anything that is the "first" rather zeroth value in the array will be popped.

```rs
set x := [1, 2, 3];

x.PopL()

x
//Result: Array->[2,3]
```

**PopR**

PopR stands for pop right. Similar to PopL, PopR will pop the rightmost value from the array.

```rs
set x := [1, 2, 3];

x.PopL()

x
//Result: Array->[1, 2]
```

**Reverse**

Will reverse the values of the array

```rs
set x := [1, 2, 3];

x.Reverse()

x
//Result: Array->[3, 2, 1]
```

**Swap**

Allows you to swap a value with another value within the array based on its position. 

```rs
set names := ["ryan", "bob", "ang", "kod"]

names.Swap(0, 3)

//Result: Array->["kod", "bob", "ang", "ryan"]
```

**Typeof**

Typeof is a method that is used to view the type of array, this goes based on the values. This is sadly not implemented into every data type.

```
set x := [];

x.Typeof()

//Result->SkyLine Object (Virtual) < Array >
```

**Prepend**

Prepend will prepend values to the array. This means that the values will be appended before any other values of the array rather than the front side of the array. For example if you have "hello" at the 0th position in the array and prepend to the array with "hi" then "hi" will be the value now in the 0th position and every other value will shift positions right by one.

```rs
set x := [1, 2, 3, 4, 5];

x.Prepend("hi")

x

//Result: Array->[hi, 1, 2, 3, 4, 5]
```

> ### Any methods | Module 0.3 ###

The `Any` method in SkyLine defines any and all data types or objects. For example, this means that functions, hashes, import calls, strings, integers, floats etc all will have these methods and calls set to them. These methods are cuurrently only stuck to `Length` and `Methods`. While `Length` is not directly put into every data type, `Methods are`.

**Methods**

The `Methods` function acts as a call to allow users to lookup what objects exist within the object. Not only can this be used as an alternative for type lookup but can also be allowed for users to look at methods or calls offline without having to look at man pages or go through documentations.

```
STRING.Methods()

//Result: Any(Array)->[Boolean, Float, Integer, Length, Lower, Methods, Ord, Split, Title, Trim, UnlinkRegistry, Upper, View]
```

**Length**

Returns the length of a value

```
STRING.Length()

//Result: Integer->6 ( because len(STRING)=6 )
```










