---
title: "\"Iron Man\" - Elixir day 5: Ampersand character"
date: '2022-05-26'
tags: ['elixir','ampersand']
draft: false
summary: 'A meaning of an ampersand character'
---
# Ampersand character
An example use of a function `Enum.sort/2` on an site about Elixir shows a use of it with a following function `&(&1 >= &2)` instead of `:asc` and `:desc`. The first character used before variables is an **ampersand** `&`.
```elixir
iex(1)> Enum.sort([1, 2, 3], &(&1 >= &2))
[3, 2, 1]
```
Lambda is a name used for an anonymous defined function. Let's define a variable with a function for an trapeze_area.
```elixir
iex(1)> trapeze_area = fn a, b, h -> (a + b) *h /2 end
```
An **ampersand** character makes it easier to define a lambda function which can be used inside another function without a definition in another line of code. For example the same function definition as above can be done easier.
```elixir
iex(1)> trapeze_area = &((&1 + &2) *&3 /2)
```
Instead of a declaration of all variables in this syntax we define the numer of a variable in a function with a `&(number_of_variable)` as shown below. For example value `&3` refers to the third variable in a function so `h`. An **ampersand** character before a bracket is an info, that it's a lambda definition. It means that `&(&1 >= &2))` means exactly the same as `fn a, b -> a >= b end`. Let's try to use it.
```elixir
iex(1)> lambda = fn a, b -> a >= b end
Enum.sort([1, 2, 3], lambda)
[3, 2, 1]
```
It looks like that in a code, that it works exactly the same as before with a usage of lamba. As I understood, the following code works in the following way with the `lambda` function.
```elixir
iex(3)> 1 >= 2
false
iex(4)> 2 >= 3 
false
iex(5)> 3 >= 1
true
iex(6)> 1 >= 2
false
iex(7)> 2 >= 1
true
```
When a value is true, then this value is put on a first index. The first value with 3, then 2 and then 1. Take in mind, that the returned list will return true from the beggining.
