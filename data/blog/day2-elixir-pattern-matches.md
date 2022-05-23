---
title: "\"Iron Man\" - Elixir day 2: Pattern Matches Elixir"
date: '2022-05-23'
tags: ['elixir','anonymous variable', 'pattern', 'compound', 'match']
draft: false
summary: 'Usage of anonymus variable and matching constant during matching patterns'
---
# Anonymous variable
Beside those two uncommon data types in Elixir today I've learned about **anonymous variable**  which is used as an underscore sign `(_)` in a code. To clearly understand why this variable can be used is to understand how Elixir understands the `=` sign and how patterns are used which is described further.

# Matching constant
This `=` tries to match what's on the right-side to what's on the left-side but it could be exactly everything. On both sides can be values, variables, constants, functions. Take in mind that this equal `=` sign can be used more than once in a one line code. But exactly it behaves, which side is more important? Let's compare how will it behave.
```elixir
iex> (a = b = 1 + 3) === (a = (b = 1 + 3))
true
```
Because `=` is right-associative at the begining the expression `1 + 3` is calculated and then matched to the `b` variable.

# Variables in patterns
Patterns are very often using tuples which synatax are `{}`. Tuples are different than lists `[]`, not only becasue of the syntax signs, but the way of saving it in memory which makes an influence on the usage of them. The difference between them will be explained in the further posts. For example a function `:calendar.local_time/0` is returning a tuple `{date, time}`. What can be done, if we'd like to get only one value of this tuple, for example `time`? Take in mind that tuples doesn't have an index. With a lists it can be a little bit easier, to use `Enum.at()/2` function to get a value with a specified index, like below, but it would still require some libraries and other functions to be used. Is it necessary?
```elixir
iex()> a = Tuple.to_list(:calendar.local_time())
[{2022, 5, 23}, {23, 36, 17}]
iex()> Enum.at(a,1)        
{23, 36, 17}
```
It still requires two steps and with tuples it would be necessary to convert it to the list at the beginning. The way to solve it, to use it more efficient is to use a matching pattern.
```elixir
iex()> {_, time} = :calendar.local_time()
{2022, 5, 23}, {23, 36, 17}
iex()> time
{23, 36, 17}
```
The first value used in a matching pattern is an **anonymous variable**. It doesn't matter what exactly this function will return there - matching pattern doesn't care. It's a really good option, to use a function which returns some values, but we would like to see only one of them.