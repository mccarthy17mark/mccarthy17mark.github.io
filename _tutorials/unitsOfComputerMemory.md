---
title: Units of Computer Memory
layout: tutorial
pageId: unitsOfComputerMemory
parentId: tech
usemathjax: true

published: false
---

{% include toc.html %}

# What do I mean by "Memory"?

We often think of hard drive disk space as our computer's memory. This is indeed memory, but there are many other types, and I don't feel like listing them here. Memory has to do with how the computer stores information, whether it be for long-term storage, or while it's actively working on things. These units affect more than just storage, but how a computer thinks and functions. They dictate the sizes of information that a computer will handle at any given time, and it becomes a pretty important concept in most programming languages.

# Bits

Ultimately, all information is stored as bits. These are the iconic `1`s and `0`s that we associate with computers. Typically I imagine memory as being a sequence of slots, each of which can be filled with one bit of memory: a `1` or a `0`. Since there are only two options that can fill those slots, this system is referred to as binary. Fundamentally, all information, whether it's stored in a computer or not, is often thought of in terms of bits. This has some deep connections to the physics concepts of entropy and microstates as well, but that's for another article.

The bit is a very small amount of information. There's not much that can be done with this. Naively we would imagine that a `bool` type variable, something with only `true` and `false` as possible values, would be just one bit. While some extremely optimized implementations do this, it is typically not done.

## Memory Addresses

For a computer to make use of its memory, it's not enough to just fill it with values. It also needs to be able to search to a specific point and read or overwrite the values it finds there. To know which section of the memory stores some important information, it uses an *address*. Memory is broken up into equal-sized pieces (1 byte each) and the location of that first bit is provided by an address. This means most bits are unaddressed, and are therefore not useful on their own, but only useful in conjunction with their neighbours.

# Bytes

This is the smallest addressable region in memory, usually 8 bits. It's also usually the size of a char and a bool.

# Words

This is the size of an address, but also usually the size of most registers, and most actual work that occurs. Ints are usually this size. Most variables are this size or some multiple of this size. It's traditionally 4 bytes or 32 bits, the int size. But other computers use 8 bytes or 64 bits, and this is better in almost every way except cost.
