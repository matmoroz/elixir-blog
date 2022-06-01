---
title: "\"Iron Man\" - Elixir day 11: && and || - Operators"
date: '2022-06-01'
tags: ['elixir', 'operator', 'and', `or`]
draft: false
summary: '&& and || operators description'
---
# && and || operators
I think that the logic is quite easy, when we use a binary values, so just `1` and `0`, but it's necessary to take in mind that operators in elixir are cooperating with atoms, where there are only `false` and `nil` which are treated as **falsy** but the others, so also `0` value are treated as **truthy**. The main two logical operators are **AND** `&&` and **OR** `||`. When there are so many values to be used, which value will be returned when both values are truthy, or both values are falsy? Let's check **AND** operator.

**AND**
The easiest way to describe what is returned after the usage of **AND** is that the second value is returned only if the first value is **truthy**. If the first value is **falsy**, then it's returned. If both values are falsy it returns first value. If both values are truely, it returns second value.
```elixir
iex(1)> nil && false
nil
iex(2)> nil && true
nil
iex(2)> false && true  
false
iex(3)> 0 && 3   
3
iex(4)> 4 && nil
nil
iex(5)> 0 && false
false
iex(6)> true && 2
2
```

**OR**
During the usage of `||` operator I've found that it returns the second value only if the first value is **falsy**. If both values are falsy, it returns second value. If both values are truely, it returns first value.
```elixir
iex(7)> nil || false
false
iex(8)> nil || true
true
iex(9)> false || true
true
iex(10)> 0 || 3
0
iex(11)> 4 || nil
4
iex(12)> 0 || false
0
iex(13)> true || 2
true
```
