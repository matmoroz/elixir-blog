---
title: "\"Iron Man\" - Elixir day 10: Equality Operators"
date: '2022-05-31'
tags: ['elixir', 'operator', 'equality', `strong`, `weak`]
draft: false
summary: 'Difference between strong and weak equality operator'
---
# Equality operators
Main operators which are used in Elixir are:
1. Weak equality `==`, Weak inequality `!==`
2. Strong equality `===`, Strong inequality `!===`

The main difference between them is that weak equality will compare only the value, but strong equality would also check data type. It's relevant during comaprison between integer and float data.

Whenever you modify the *n*-th element of a list, all elements at indices `0` through `n-1` are copied and the rest can be reused.
```elixir
iex(1)> 1 == 1.0
true
iex(2)> 1 === 1.0
false
```
In this example the value `1` is an integer, and a value `1.0` is a float. Comparison of those values is `true`, but the data type is different. But what if there is even a small difference in data value? What is the range of tolerance?
```elixir
iex(3)> 1.9999999999999 == 2
false
iex(4)> 1.99999999999999 == 2
false
iex(5)> 1.999999999999999 == 2
false
iex(6)> 1.9999999999999999 == 2
true
iex(7)> 1.9999999999999998 == 2
false
iex(8)> 1.0000000000000001 == 1
true
```
As you can see above a value which is different in `0.0000000000000001` is still `true` for `==` weak equality, so I can sat that that's exactly a range of tolerance for it.