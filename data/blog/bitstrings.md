---
title: Bitstrings - datatype in Elixir
date: '2022-05-22'
tags: ['elixir', 'bitstring', 'bits', 'bytes', 'storage']
draft: false
summary: 'A new datatype called bitstring used in Elixir to save a contiguous sequence of bits in memory.'
---

# Bitstrings
**Introduction** <br/>
It's a foundamental type of a data in Elixir which makes it possible to save a contignous sequence of bits in memory. The syntax of it looks like that starts with `<<` and ends with `>>`. Between those signs it's possible to write what has to be saved, and it's also possible, but not necessary to define inside after a sign `::` how many bits of memory will be used to save it. Let's use as an example an integer value <b>21</b>.

21₁₀ = 10101₂

This integer uses at least 5 bits in binary code, but if we use only 5 bits, is it exactly the same as a bitstring without declared size?

```shell
iex> <<21>> == <<21::8>> 
true
iex> <<21>> == <<21::5>>
false
```

When I started learning this high-level language, I haven't expected it will be possible to use this type of a data. To be clear, I still have no idea what is it used for, but the structure of it is really interesting. 