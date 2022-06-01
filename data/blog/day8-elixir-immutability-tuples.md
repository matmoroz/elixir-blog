---
title: "\"Iron Man\" - Elixir day 8: Immutability - Tuples"
date: '2022-05-29'
tags: ['elixir', 'immutability', 'tuple', 'modification']
draft: false
summary: 'Description why data in elixir is immutable - tuples'
---
# Tuples - immutability
In my previous post **\"Iron Man\" - Elixir day 6: Tuple usage {}** I've mentioned that after a usage of a function `Kernel.put_elem/3` a variable `person` is still not modified and because of that a usage of a function `put_elem` requires an information to which variable this tupple should be assigned. That's because a data in Elixir can't be modified and every data returned by a function is new modified version of an input data. It's necessary to created data another variable and assign it to it or retake it to same variable. Result of a function is always resides to another memory location, but does it look like that the every value returned by a function is resided? Take in mind that most of the values returned by a function are the same as they were before, especially during the modification of a tuple. A function `put_elem` is using all the same values which were before, beside this one which is added to the tuple, so the memory addresses can be used the same as they were used before. Further explanation can explain more doubts.
```elixir
iex(1)> student = {"Mateusz", 28, "Politechnika"}
{"Mateusz", 28, "Politechnika"}
iex(2)> worker = put_elem(student, 2, "Bosch")
{"Mateusz", 28, "Bosch"}
```
In an example above, in a second command a function `put_elem/3` based on existing tuple modified a value of an index **2** and all the others remained the same. A tuple doesn't contain a values, but a memory address where those values can be found, but when we are using a tuple we see a values which are on those memory addresses. A function `put_elem/3` created a new tuple `worker` and a new string `"Bosch"`, both with the new memory addresses, but a new tuple `worker` refers to the values which were exactly the same as on tuple `student`.

But what happens when a function return addresses to the same variable?
```elixir
iex(1)> mateusz = {"Mateusz", 28, "Politechnika"}
{"Mateusz", 28, "Politechnika"}
iex(2)> mateusz = put_elem(student, 2, "Bosch")
{"Mateusz", 28, "Bosch"}
```
 A new tuple with the same name `mateusz`, is copied and the old location of tuple `mateusz` is not accesible, and the same happens to the variable `b`, but does it mean that the old value `"Politechnika"` is not accessible? If we know the exact memory location of a value "Politechnika", or we assign there a value - it's still accessible. To the new tuple `mateusz` a value "Bosch" is assigned. Tuples are always duplicated, but it can lead to the problems with a memory. Lists behave in a different way, and the knowledge is really useful to decide what will be more efficient in a code.