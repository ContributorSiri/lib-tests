# Intro to Computer Systems Midterm 2024 Spring
## General Information
- **Date**: 2024-04-19
- **Duration**: In class, but append 5 minutes (9:50 - 12:20)
- **Answer**: In English
- **May Bring Calculators and a cheat sheet**

*Side Notes:* it's may not be us to remember the problems in the correct order.

## Problem 1: True Or False
## Problem 2: Short Answer Problems
Your answers should be concise e.g. 3-4 sentences.

1. Which lines does the following regular expression match? 
```text
^[a-f]\)[a-z]{4}\d?(-{A-Z}+)?$
```
`a)`

`b)`

`c)`

`d)four2-ABC`

`e)`


## Problem 3: Architecture
### 3.1 Amahal's Law

### 3.2 Build a Cache
1. A cache has __ storage, block size __, can it be 64-set associative?

## Problem 4: Scheduling (9 pts)
Fill in blanks in the following table (including the question marks):
| Current Time | FCFS | ? | ? | 
|--------------|------|---|---|
| 1            | A   |  A | A  |
| 2            | A   |  B |  B |
| 3            | A   |  B |  A |
| 4            | A   |   |   |
| 5            | B   |   |   |
| 6            | B   |   |   |
| 7            | C   |   |   |
| 8            | D   |   |   |
| 9            | D  |   |   |
| 10            | D  |   |   |
| Average Turnaround Time | 4.25 |  |  |

The turnaround time is defined as the time difference between the completion time and the arrival time of a process. 

Hint: you should first fill in the arriving time table below.
| Process | Arrival Time |
|---------|--------------|
| A       | 1            |
| B       | 2            |
| C       | ?            |
| D       | 8            |

## Problem 5: Synchronization (23 pts)
### 5.1 Polite Writers (8 pts)
Rewrite the reader-writer problem code, so that the writers give priority to readers
### 5.2 Synchronization Queue (15 pts)
```cpp
class SyncQueue{
    private: 
        Lock lock_;
        ConditionVariable cv_;
    public: 
        void Init(){

        }
        void Push(void* item){

        }
        void* Pop(){

        }
};
```

1. What's the problem if the queue is used at the following producer & consumer queue:
```cpp


```
2. Fix the bug.
3. Implement a semaphore using the synchronization queue. 
4. What's the *semantic* difference between your implementation of the semaphore and the semaphore defined in class? The word *semantic* means that you may not say about the implementation/performance differences.