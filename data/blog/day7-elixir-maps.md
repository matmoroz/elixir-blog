---
title: "\"Iron Man\" - Elixir day 7: Tuple {} and a map %{} difference" 
date: '2022-05-28'
tags: ['elixir','map', 'difference', 'tuple', '%']
draft: false
summary: 'Difference between a tuple {} and a map %{} '
---
# Map
Maps can also use braces `{` `}` a characters which are at the beggining of the values inside, but the first character is a percent `%`. The structure of an example map is described below.
```elixir
iex(1)> empty_map = %{}
```
So the structrue is quite simmilar to tuple, because it also uses the braces. They’re used to power dynamically sized key/value structures, but they’re also used to manage simple records — a couple of well-defined named fields bundled together. But what is the main difference between map and a tuple? In a tuple an index depends on the place where it is. In a **map** an index can be every value and is defined just before `=>` and it cooperates with a function `Map.get/2` or `['index']` where a value of an index is used.
```elixir
iex(2)> squares = %{1 => 1, 2 => 4, 3 => 9}
%{1 => 1, 2 => 4, 3 => 9}
iex(3)> squares[2]
4
```
In a **map** an index can be every value and is defined just before `=>`. It cooperates with a function `Map.get/2`, `Map.get/3` or `['index']` where a value of an index is used.
```elixir
iex(4)> even_squares = %{2 => 4, 4 => 16, 6 => 36}
%{2 => 4, 4 => 16, 6 => 36}
iex(5)> even_squares[6]
36
iex(6)> even_squares[0]
nil
```
Take in mind that in `even_squares` an indexes are `2`, `4` and `6` and because of that a command `even_squares[0]` returns `nil`, because there is no index in this map.
```elixir
iex(7)> Map.get(even_squares, 4)
16
iex(8)> Map.get(even_squares, 5)
nil
iex(9)> Map.get(even_squares, 5, :nothing_found)
:nothing_found
```
A function `Map.get/2`, `Map.get/3` can use two or three attributes. `Map.get(even_squares, 5)` returns `nil` because nothing's found with an index 5, but `Map.get(even_squares, 5, :nothing_found)` returns `:nothing_found` because a third attribute is a value which is returned if there is no value of an index which is defined on the second attribute of a function.

# Difference between a map and a tuple
-- to be further described --