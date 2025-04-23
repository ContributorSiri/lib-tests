# Intro to Computer Systems: 2025 Spring Midterm

## General Information

- **Date**: 2025-04-18
- **Duration**: In class, 10:00 - 12:00
- **Answer**: In English
- Allow to bring a cheatsheet of A4 paper size.
- Allow to carry an unprogrammable calculator (though it should not be necessary)
- The total score is 110. Any score above 100 will be counted as 100.

## Problem 1: True or False

## Problem 2: Short Answer Problems

## Problem 3: Architecture

## Problem 4: Scheduling

## Problem 5: Synchronization

### 5.1 Reader-Writer Problem

In class, we have introduced a solution to the reader-writer problem using two condition variables. The code is as follows.

```cpp
void Reader() {
    lock.acquire();
    while (AW > 0) {
        WR++;
        okToRead.wait(&lock);
        WR--;
    }
    AR++;
    lock.release();
    access_database(READ_ONLY);
    lock.acquire();
    AR--;
    if (AR == 0 && WW > 0) {
        okToWrite.signal(); // A
    }
    lock.release();
}

void Writer() {
    lock.acquire();
    while ((AW + AR) > 0) {
        WW++;
        okToWrite.wait(&lock);
        WW--;
    }
    AW++;
    lock.release();
    access_database(READ_AND_WRITE);
    lock.acquire();
    AW--;
    if (WW > 0) {
        okToWrite.signal();
    } else if (WR > 0) {
        okToRead.broadcast(); // B
    }
    lock.release();
}
```

1. Your friend, Bob, is confused with the functions `signal()` and `broadcast()`. He claims that, since `signal()` only wakes up one waiter while `broadcast()` wakes up all waiters, using `broadcast()` is strictly better than using `signal()`. Please analyze the following two cases to show Bob about the functionality of these two functions.

    - What if we replace _line A_ to `okToWrite.broadcast()`? How does this effect correctness and performance of the program?
    - What if we replace _line B_ to `okToRead.signal()`? How does this effect correctness and performance of the program?

2. To elaborate on your claim in problem 1, please analyze a specific example for both two modifications. Suppose a writer `W1` came in first, and while `W1` is executing, other readers and writers come at almost the same time. The incoming stream is:

    ```
    R1 R2 R3 W2 W3 R4 R5 R6 W4 R7 W5 W6 R8 R9 W7 R10
    ```
    For two modifications, will the database accessing behavior change? If it changes, clarify the difference.

3. Suppose you are given another ISA architecture, which **does not support** `broadcast()`. Please design a solution to the reader-writer problem in this setting. You must ensure that your solution will not cause any deadlock or request miss. If your method causes performance degradation, please state it clearly to receive full score.

### 5.2 Synchronization

Suppose you have 2 concurrent programs:
```cpp
// program 1
for (int i = 0; i < 5; ++i) {
    x = x + 1;
}

// program 2
for (int j = 0; j < 5; ++j) {
    x = x + 1;
}
```

Two programs execute on the same `x` in the memory. The register is not shared. The following procedure will happen when executing `x = x + 1;`: the program read the value of `x` from the memory into the register; increment the value by 1; write the value back to the memory.

The read and write operations are atomic. Suppose the initial value of `x` is 0.

1. What is the **minimal** value of `x` after two programs complete? You need to provide a proof.
2. If we extend to 2025 concurrent programs, what is the minimal value? A single answer is sufficient.