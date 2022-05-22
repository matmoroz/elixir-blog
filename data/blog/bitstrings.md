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

This integer uses at least **5 bits** in binary code, but if we use only **5 bits**, is it exactly the same as a bitstring without declared size? Let's check it. In the following command I'm using `==` equal to comparison operator.
```shell
iex> <<21>> == <<21::8>> 
true
iex> <<21>> == <<21::5>>
false
```
It means that a bitstring `<<21>>` without declared size is not equal to the bitstring of the same value `<<21::5>>`, but different size. Let's check how it will behave with values greater than `256`, so the greatest integer value using **8 bits**. Let's use `2137` - in binary it's using **12** bits.

2137₁₀ = 100001011001₂

```shell
iex> <<2137>> == <<2137::16>>
false
iex> <<2137>> == <<2137::12>> 
false
iex> <<2137>> == <<2137::8>>
true
```
It looks like that a bitstrings in default are using the **8 bits**, so **1 byte**, even if the values are higher. Does it mean, that `<<2137>>` is equal to `01011001` because only **8 bits** are stored?

```shell
iex> 0b01011001
89
iex> <<2137>> == <<89>>
true
```
It shows us that when we use a default size of a bitstring then everything what exceedes 256 is cut. It also can be checked using 257, which is just 1 more than 256.
```shell
iex> <<257>> == <<1>>
true
```


When I started learning this high-level language, I haven't expected it will be possible to use this type of a data. To be clear, I still have no idea what is it used for, but the structure of it is really interesting. 