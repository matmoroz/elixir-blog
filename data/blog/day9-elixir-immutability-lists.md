---
title: "\"Iron Man\" - Elixir day 9: Immutability - Lists"
date: '2022-05-30'
tags: ['elixir', 'immutability', 'list', 'modification']
draft: false
summary: 'Description why data in elixir is immutable - lists'
---
# Lists - immutability
Whenever you modify the *n*-th element of a list, all elements at indices `0` through `n-1` are copied and the rest can be reused.
```elixir
iex(1)> list = [1, 2, 3, 4, 5]        
[1, 2, 3, 4, 5]
iex(2)> list = List.insert_at(list, 3, 0)
[1, 2, 3, 0, 4, 5]
```
In this example the value `0` is inserted at the index `3` and all values before that index, i. e. `[1, 2, 3]`, had to be copied. Only the part following `0` (`[4, 5]`) can be reused. The more elements are copied during the modification of a list, the more garbage values need to be collected. That's the reason why lists should be modified at the beginning, not at the end of them. Moreover, modifying the head of a list does not require any garbage collection. Of course it won't be easy to modify an existing list efficiently, when it's necessary to add a value in the middle of a list but understanding the way of saving this data will be really useful, to think through an algoritm during coding.
```elixir
iex(3)> [0 | list] 
[0, 1, 2, 3, 4, 5]
iex(4)>  list ++ [0]
[1, 2, 3, 4, 5, 0]
```
The way of adding 0 at the beggining of a list was much faster than adding a `0` to `list`, because it required none garbage data to be created.