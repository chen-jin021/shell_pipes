# shell_pipes
Concurrent Reverse Index Searching Engine with interprocess communication via pipes

# Introduction

Sequential programs execute instructions one at a time in a specific order. With the aid of multiple processes, however, we can also have concurrent programs. Concurrent programs execute in parallel, either on multiple processors in your computer or in a time-sliced way on a single processor.
One benefit to concurrent programming is that it can improve program performance by splitting one big task into smaller subtasks which can be executed at the same time rather than sequentially (assuming you’re running on a multiprocessor computer). However, since multiple processes exist in distinct virtual address spaces, the data in one process’s address space is not visible to any other process. 
Therefore, we will share data between processes via pipes. A pipe is a one-way channel in which data can be sent and received between processes. On Linux, it is represented as an array of two file descriptors with the first (element 0) representing the file descriptor for the read end of the pipe, and the second (element 1) representing the file descriptor for the write end of the pipe. Data can be read from and written to pipes using the standard `read` and `write` system calls.

# Specifications

Implementations includes: multiple processes to implement a reverse index program, which takes in a word and produces a list of the occurrences of the word in a corpus of documents.
This is the essence of how a search engine like Google works! When you type a keyword into Google, the Google servers look up your keyword in a giant reverse index, finding the web pages that mention this keyword. It then ranks the results according to a highly secret algorithm.
Google’s reverse index is split over many servers, and speeds up lookups using concurrency. For this assignment, you will build a more modest, single-machine reverse index, but concurrency will still help speed it up!

- `wordindex.h`: This file contains all shared functions and data structures. This includes the `wordindex` class for storing the results of a search, all functions involving reading files and directories, and functions to print out the results.
- `revindex_sequential.cpp`: This file contains a single-threaded, sequential implementation of a reverse index search.
- `revindex_procs.cpp`: This file contains a multiple process implementation of a reverse index search.

## Testing
- The `books` directory containing a series of `.txt` files of classic novels.
- `input.txt`: This file contains a series of search terms separated by a newline. It can be used for testing purposes to execute multiple
