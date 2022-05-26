---
title: "\"Iron Man\" - Elixir day 4: Definition of a first class function"
date: '2022-05-25'
tags: ['elixir','function', 'definition']
draft: false
summary: 'Definition of a first class function with syntax explanation and example use'
---
Last day I've used a function `Enum.sort/2` which could be used with one or two arguments. I've used `:asc` and `:desc` but there also can be used a function which was declared using an **ampersand** character. More information about it can be found in the next day post.
```elixir
iex(1)> Enum.sort([1, 2, 3], &(&1 >= &2))
[3, 2, 1]
```

The usage of this function let me to two questions:
1. How to define a function?
2. What exactly mean an ampersand?
The answers for those both questions can be found in the following text.

# Function definition
The definition of a function can be done in a one command line, which is show below as a example of a function to calculate the area of a triangle as a `traingle_area` when we know the length of a traingle base `a` and a triangle height `h`. 
```elixir
iex(1)> triangle_area = fn a, h -> a * h / 2 end 
#Function<43.65746770/2 in :erl_eval.expr/5>
```

It requires the following information:
1. What is the name of a funtion (`triangle_area`)
2. What are the used variables `a, h` will be used and also the most important, 
3. What will be executed with the variables in a funtion? `a * h / 2`
The character `->` devides the definiton of used variables with a declaration what function has to do.
If we'd like to use a anonymous function, which is not defined in a module it's necessary to use a `.` character between a function name and a used variables. Without `.` dot operator Elixir wouldn't use an anonymous function and will try to find it in a module. Anonymous function can be also called **lambda**.
```elixir
iex(2)> triangle_area.(2,1)
1.0
iex(3)> triangle_area.(3,1)
1.5
```