---
title: "\"Iron Man\" - Elixir day 3: Signs before variables Elixir"
date: '2022-05-24'
tags: ['elixir','anonymous variable', 'pin operator', 'matching list']
draft: false
summary: 'Further usage of an anonymus variable and a pin operator'
---
# Anonymous variable in pattern - further explanation
Very often in Elixir the first sign in a syntax of a value says how program should understand it. One of the sign which was mentioned before is an **anonymous variable** `_` which can also be used with other signs further. For example it could be defined as `_name_of_variable`, but it still will indicate that it should be ignored.
```elixir
iex()> {_, {hour, _minute, _second}} = :calendar.local_time()
{{2022, 5, 24}, {21, 54, 15}}
iex()> _minute
warning: the underscored variable "_minute" is used after being set. A leading underscore indicates that the value of the variable should be ignored. If this is intended please rename the variable to remove the underscore
  iex:4

54
```
During the usage of a variable `_minute` Elixir warns us that the value with the sign `_` at the beginning is ignored. It's a good option to use, just to proof, that the pattern is properly set, or when a developer is not sure if this value will be used further. 
# Pin operator
There are also other signs, which also explains the program how to understand the values. Another sign is a **pin operator** `^`, which is used at the beginning of a variable. It tells the program, to use exactly the value of this variable. The best to understand it is an example.
```elixir
iex(1)> {food, market} = {"Kaszanka","Biedronka"}
{"Kaszanka", "Biedronka"}
iex(2)> {^food, market} = {"Kaszanka","Netto"}    
{"Kaszanka", "Netto"}
iex(3)> {^food, ^market} = {"Kaszanka","Biedronka"}
** (MatchError) no match of right hand side value: {"Kaszanka", "Biedronka"}
```
# Matching lists
To match a pattern build on a list works quite similar to tuples. It's just necessary to remember that the both sides should match each other.
```elixir
iex()> [first,  second, third] = [1,    2,     3]
[1, 2, 3]
iex()> [first,  first,  first] = [1,    1,     1] 
[1, 1, 1]
iex()> [1,      second, third] = [1,    2,^third]    
[1, 2, 3]
iex()> [^first, second,   _  ] = [first,2,     3]
[1, 2, 3]
```
Lists can be quite easily dived to two elements using a list form `[head | tail]`. Take in mind that in this syntax the part of a list which is it's `head`, can be used as a different variable, like `[beggining | end]`.
```elixir
iex(9)> table = [1,2,3]
[1, 2, 3]
iex(10)> [first | rest] = table
[1, 2, 3]
iex(11)> first
1
iex(12)> rest
[2, 3]
```
One of the useful usages of this is `Enum.sort` function which makes it possible to find the lowest or highest value from a list. This function `Enum.sort/1` can also be `Enum.sort/2`, and on the place of the other argument of this function.
```elixir
iex(15)> [lowest | _ ] = Enum.sort(table, :asc)
[1, 2, 3]
iex(16)> lowest                              
1
iex(17)> [highest | _ ] = Enum.sort(table, :desc)
[3, 2, 1]
iex(18)> highest
3
```