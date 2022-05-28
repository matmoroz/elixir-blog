---
title: "\"Iron Man\" - Elixir day 6: Tuple usage" 
date: '2022-05-27'
tags: ['elixir','tuple', 'index']
draft: false
summary: 'Explanation of a tuple usage, definition and functions'
---
# Tuple
One of the structure of the records is a tuple, which is very often used to group a fixed elements together. A tuple starts `{` and ends `}` with a brace character, and can be declared as a variable. In an example below a tuple `person` is declared with the name `"Mateusz"` and age `28`. 
```elixir
iex(1)> person = {"Mateusz", 28}
{"Mateusz", 28}
```
There are two main function which can cooperate with a tuple which are already auto-imported, so it's not necessary to use `Kernel` at the beginning.
1. `Kernel.elem/2` - used to obtain a value which in on the specified index of a tuple. The first value of a tuple has an index **0** so the index `1` is the second value from the beggining.
```elixir
iex(2)> elem(person,1) 
28
```
1. `Kernel.put_elem/3` - used to put an element on the following index of an existing tuple, but doesn't modify an existing one.
```elixir
iex(3)> put_elem(person,1,30)
{"Mateusz", 30} 
iex(4)> person
{"Mateusz", 28}
```
A variable `person` is still not modified, because of that a usage of a function `put_elem` requires an information to which variable this tupple should be assigned.
```elixir
iex(5)> older_person = put_elem(person,1,30)
{"Mateusz", 30} 
iex(6)> older_person                        
{"Mateusz", 30} 
```
At the beggining a new variable `older_person` was defined where based on the `person` tuple on index `1` a value 30 was assigned. Of course it's also possible to modify an existing tuple `person` 
```elixir
iex(5)> person = put_elem(person,0,"Karol")
{"Karol", 28} 
iex(6)> person                        
{"Karol", 28} 
```
By doing this, the `person` variable rebounded to the new memory location. The old location isn’t referenced by any other variable, so it’s eligible for garbage collection. Tuples are most appropriate for grouping a small, fixed number of elements together. When you need a dynamically sized collection, you can use lists, which will be explained further.
