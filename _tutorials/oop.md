---
title: Object-Oriented Programming
layout: tutorial
pageId: oop
parentId: tech
usemathjax: true

published: false
---

{% include toc.html %}

Object-oriented programming is a large topic, with a lot of ideas bundled together. 

# Programming Goals

When we're writing software, we have multiple goals in mind, which can be summed up as follows:

- Performance
- Maintenance
- Ease of Development

*Performance* means that we want our software to produce precisely the result we want, every single time, with minimal memory usage, minimal processing time, etc.

*Maintenance* means that we want our software to be easy to edit, easy to adapt to a new context, easy to add features to, robust to changes, and simple to understand.

*Ease of Development* in this context usually means programmer time, and in many situations this is really another way to say we want the software to be inexpensive. We want our software to be able to be written quickly, and to not require endless tiny optimizations that take forever to find, and to only require the simplest of setups to compile, run, and test.

There are many things that are simultaneously optimized here and whenever that happens, there is no longer a unique solution. There are many reasonable ways people use to try to acheive these goals. One of them is OOP.

# OOP in a Nutshell

The idea behind OOP is to increase the abstraction in our code, moving away from a list of instructions to a machine, and toward a framework where the program is built up of *objects* that we can understand in analagous ways to how we view the real world. What these objects are and how they work can be a bit complicated, but a well-written OOP program is often much easier to understand and maintain than an equivalent program without these ideas.

As always with programming, it's often better to learn through examples. Let's pretend we want to write a program that allows us to play chess on a board displayed on the screen. One task we'd have to solve is to look at a specific square, determine what piece lies on that square, and draw it to the screen. In a functional programming style, you might imagine code to look like this:

```
int getPieceInSquare(int rank, int file, std::vector<std::tuple<int,int,int> > pieceLocations)
{
	for(std::vector<std::pair(int,int)>::iterator it = pieceLocations.begin(); it != pieceLocations.end(); ++it)
	{
		int pieceRank = std::get<1>(*it);
		int pieceFile = std::get<2>(*it);
		if(pieceRank == rank && pieceFile == file)
		{
			 return std::get<0>(*it);
		}
	}

}
```

This requires some extra book-keeping on our part keeping track of how the `pieceLocations` data is structured, passing it into this function, keeping track of how the ids work, etc. It might not be obvious what is happening here to someone who has never seen the code before.

Doing the same example in a OOP style might look like this:

```
Piece Board::getOccupyingPiece(int rank, int file)
{
	for(std::vector<Piece>::iterator it = pieceLocations.begin(); it != pieceLocations.end(); ++it)
	{
		Piece currentPiece = (*it);
		if(rank == currentPiece.location.rank && file == currentPiece.location.file)
		{
			return currentPiece
		}
	}
}
```

This example is a bit contrived... you'd probably use a map or something for this instead of this function, but hopefully the point about objects can come across regardless. In the OOP example, we see that `currentPiece` is an object which carries a lot of information, and "owns" this information in a logical way.

# Types, Structs, and Classes



# 
