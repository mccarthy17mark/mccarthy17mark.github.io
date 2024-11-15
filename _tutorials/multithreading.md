---
title: Multithreading
layout: tutorial
pageId: multithreading
parentId: tech
---

{% include toc.html %}

### Introduction

Concurrent programming is a big topic, and tough to summarize in a tutorial like this. The central idea is that a computer task can be run faster if several parts of the task are run at the same time. This can become quite complex as there are many different ways things can go wrong.

To reduce the scope of the topic, let's split it up into parts. Approaching this problem by focussing on the computing clusters, hardware, and OS-level architecture is a big topic with a nice introduction [here](https://hpc.llnl.gov/documentation/tutorials/introduction-parallel-computing-tutorial), and I won't go into any further detail on this approach. 

When creating software, this issue shows up in a different manner, where we need to make sure our code can take advantage of parallel processing while avoiding any related problems. The specifics of how to accomplish this are often unique to each language, but the core ideas are common. I'll go into as much detail as I can using `C++`, since it's the language I know best.

### A Note on Terminology

**Concurrent programming** refers to having a computing task broken up into independent sections which could be run in any order, by different processes, including but not necessarily at the same time. This is probably the most general term describing the topic as a whole.

**Parallel computing** refers to having multiple tasks being performed at the same time, which is usually the whole point.

**Multiprocessing** refers to having multiple processes accomplishing a single task. Processes are independent. They each use their own protected memory and are generally unaware of the workings of other processes.

**Multithreading** refers to one single process using several threads to accomplish a single task. These threads act mostly independently, but ultimately they all share the same process, the same memory space, and if there is a crash then the whole process will terminate. Multithreading is a bit simpler to set up than multiprocessing, but has limitations arising from all threads being from the same process.

### Challenges with Concurrent Programming

#### Race Conditions

A race condition exists when the result of a program, or rather a specific operation that happens while running that program, depends solely on which thread reaches some execution point first. This makes for inconsistent and often undefined results, and can be a big headache to diagnose.

The classic example discusses software that manages bank accounts, with multiple threads independently handling each access to a database that stores the information about those accounts. Imagine that a user has $10 in their account. They send a request to transfer $20 into that account from somewhere else, and shortly afterward request to withdraw $15. We now have two threads, one trying to increment the balance by $20, and one trying to decrement it by $15. If the depositing thread acts first, then the balance rises to $30 before being reduced to $15 by the withdrawal. If the withdrawal thread acts first, then the software will complain that the withdrawal cannot be performed since there are insufficient funds. The behaviour of the software is not known in advance and all sorts of strange things can occur, especially if these two threads accomplish parts of their task at the same time.

#### Shared Resources

A more general problem highlighted by our race condition example is the problem of shared resources. When multiple threads are accessing the same section of memory, then we need to be very careful about ensuring that each threads actions do not impact others. Having multiple threads reading and writing from the same addresses can be very problematic, but there are other issues as well. If a thread allows some memory to be `delete`d or to go out of scope while it is still being accessed by another thread, then we have memory corruption issues. Another common situation is when multiple threads are writing output (either to a terminal or to a file) at the same time, which can cause them to overwrite each other or to have a chaotic, undefined writing order.

#### Resource Starvation

Soon I will introduce the tools we use to resolve these issues, usually by restricting multiple threads from interacting with a shared resource at the same time. However, poorly implementing such restrictions can lead to threads which have to wait forever for their turn, or threads that can never have access to the resources they require to perform their task. This can lead to some threads that have to wait for all other threads to finish before proceeding, defeating the whole point of multithreading, or it can also lead to something more sinister: the deadlock.

#### Deadlocks

A famous thought-experiment involving this idea is that of the [Dining Philosophers](https://en.wikipedia.org/wiki/Dining_philosophers_problem). Imagine a table with multiple, uncommunicative philosophers seated around it. Between each adjacent pair of diners is a fork. For some outlandish reason, the philosophers can only eat if they use both forks at once... the forks are a shared resouce. The philosophers sit in silence for some random time period, then try to acquire both forks, eat for some time, then put the forks down. Without any coordination, it's possible the diners to wind up all having grabbed their left fork, and to all sit patiently waiting for the right fork to be free, until they all begin starving.

This situation is called a deadlock. Multiple threads are occupying some shared resources while waiting for other shared resources to become available, and being unable to access them, they wait patiently forever. This is another tricky problem to encounter because deadlocks usually involve some unlucky random chance to occur, and don't result in easy-to-diagnose crashes.

---

### Mutexes

The name "Mutex" comes from **MUT**ual **EX**clusion, which should give a strong hint as to how they work. A mutex variable is one that can only be used by one thread at a time, and by locking these variables within a block of code, we can ensure that that block will not be run by a second thread while the first thread is still acting within it.

In `C++` one way this can work is with `std::mutex` and `std::lock_guard`. The mutex is a singleton (an object which can only have one instance) with near-global scope, and the lock is confined to a small block of critical code where only one thread may access at a time.

For example, some thread-safe functions that print to the console could look something like this:

```
// One mutex per shared resource (in this case, the output)
std::mutex mtx_o; 

// The std::lock_guard will prevent multiple usages of the  mutex until it leaves scope
void printOutput(const std::string output){
  std::lock_guard<std::mutex> lock(mtx_o);
  std::cout<<output<<std::endl;
}

// Reusing the mutex ensures both functions respect the same shared resource.
void printGreeting(){
  std::lock_guard<std::mutex> lock(mtx_o);
  std::cout<<"Hello user! Check out this code!"<<std::endl;
}
```

Mutexes are definitely the default choice for most multi-threading problems, as they are fairly simple and can address most shared resource problems by serializing the code (making the code no longer parallel/concurrent).

There are drawbacks to mutexes unfortunately. They can be cumbersome to maintain across a large codebase. The locks function until they go out of scope, which can mean a lot of extra meaningless code blocks `{}`. But perhaps most importantly mutexes can lead to too much unnecessary serialization. 

### Atomicity

The original idea of an atom comes from the concept of making something so small that it eventually becomes indivisible. This idea applied to concurrent programming is that the simplest actions are too small to be useful and we want to bundle them together to make a larger set of actions that can be performed as if it was one indivisible action. When we acheive this, the set of actions is called *atomic*.

For example, incrementing a counter is an extremely common action, takes only a single line of code with a single operator `x++;`, but it is not actually atomic. To increment a counter, we first *read* the value, *modify* that reading, then *write* the new value back into memory. These are three separate atomic actions and issues can arise when there are multiple threads incrementing the same counter.

Imagine two threads, `A` and `B` and a counter with a value `2`. If both threads increment this counter, we expect a value of `4`. Now supposethe threads do the following: `A` reads `2` from the counter's memory, `A` increments `2` to `3`, `B` reads `2` from the counter's memory, `A` writes `3` into the counter's memory, `B` increments `2` to `3`, `B` writes `3` into the counter's memory. We expected to get `4` but we got `3` instead. Depending on what this counter represents and how often this happens, this can cause major troubles.

In `C++`, there is an [`<atomic>` library](https://cplusplus.com/reference/atomic/) which will allow threads to atomically modify variables through things like addition, subtraction, and exchanging with another variable. There's also an atomic flag which can be set by one thread and then ignored by the other threads, although there are more creative uses for this.

### Semaphores

Semaphores are best thought of as signalling flags, or perhaps a more generalized traffic light. They reflect the state of the code and can notify several threads about how to proceed.

An example of when semaphores are useful would be when there's some shared memory that is often read and overwritten. Many threads can read from the memory simultaneously without issue. Only one thread should be able to write at a time, and it should only be able to write while there are no readers. We can handle this by creating two semaphores. One semaphore signals that it is okay to proceed with reading, is set when there are no threads waiting to write and there are no current writers. Another semaphore signals that it is okay to acquire (or wait for) a writing mutex when there are no current readers. This could have been accomplished with a mutex on this shared memory, but then only one thread would be able to access the memory at a time, regardless of whether they wanted to read or write.

### Condition Variables

I admit I don't fully get what makes a condition variable different from a mutex.
