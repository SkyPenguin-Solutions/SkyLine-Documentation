![SLCBANNER](https://github.com/SkyPenguin-Solutions/SkyLine/blob/main/Documents/Designed/SL-0.0.5-release.png?raw=true "Title")


## SkyLine Documentation | What is this? ##

SkyLine is still in a very very experimental stage, because of this we can not truly provide documentation that people can rely on that is considered to be official because of the drastic and fluid changes happening during 0.10.0's development. However, to compensate for that, we have provided this repo which contains syntactic rule sets, plans and a whole basic documentation set of the language. This includes how to work with statements, functions, libraries and more.

## SkyLine Documentation | Variables ##

Variables in SkyLine are quite easy, each data type (`String, Float, Boolean, Error, Funciton, Array, Hash`) all have their own unique object call methods and all unique operators. Below you will find bullet points that talk about these data types and declaring them as variables and then modifying the values.

> Note: Keywords such as set, let, cause, allow are all doing the same thing, they all allow you to create and assign base variables into the environment of the language. SkyLine has some basic issues with only using one keyword because the developer firmly believes in fluidity. The mash and mix of keywords while all doing the same thing all allow the people and developers to use a specific style when in further development.

> **Strings**

Given that SkyLine is a dynamic programming language, a string data type is assumed with `""` which makes it pretty easy to understand 

```rs
set x := "data";
```

> **Strings (Operators) | Module 0.1**

When working with strings, you may want to increase the value of the string, or manipulate it in some shape or form. Currently strings have the supported operators 

| Operator | Type    |
| -------- | ------- |
| =        | String  |
| +=       | String  |
| *=       | String  |

These are weird operators to see supported with a string data type, why does `*=` even exist? We will get to that in just a second but first lets see some base examples of a string 

```rs
set name := "Ryan";

Ryan += "20";

// Result: Ryan20
```

This program simply declares a string value and then adds the string value "20" to the string which results in `Ryan20`

