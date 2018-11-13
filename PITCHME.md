@title[Fearless concurrency with Rust]

@snap[midpoint slide1 span-60]
<h1>Fearless concurrency</h1>
Using Rust for concurrent programs
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

First let us clear up the nomenclature.

Multi-threading
Parallel execution
Concurrent programming

---

Multi-threading
===============

Multi-threading is more of an OS Concept.

The classic example of web-server.
There is a process/thread waiting for new connection.
When a connection is made, waits for a request and responds back.
Close the connection.
Go back to waiting for a new connection.

Here the server, whether running on a single core or multi-core machine,
don't have to be blocked on request or any other I/O. Having this whole logic
single threaded with make the whole server blocked on a single I/O.

---

Parallel execution
==================

This nomenclature is more applicable for CPU bound applications that can
be pipelined, to increase the application's CPU utilization.

Classic example is MP3 decoder, list the stages in MP3 decoding,
create a thread pool for each stage in the pipepline wire up message
passing between each stage/thread so the o/p of the first stage feeds
i/p of second stage and so on..

---

Concurrent programming
======================

Concurrent programming means more than multi-threading or increasing the
CPU utilization.

An example would be Backtracking algorithm.

Needs green threads, fast spawn and exit time for threads. Language syntax
to enable concurrency to blend into the algorithm.

---

Share data by communicating
Communicate data by sharing.

---

shared borrow
mutable borrow
lifetime and ownership
compile time verification of data race

---

Lock contention between threads

---

MVCC and Lockless algorithms

---

Transactional memory
