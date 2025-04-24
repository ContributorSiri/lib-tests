# Intro to Computer Systems: 2025 Spring Midterm

## General Information

- **Date**: 2025-04-18
- **Duration**: In class, 10:00 - 12:00
- **Answer**: In English
- Allow to bring a cheatsheet of A4 paper size.
- Allow to carry an unprogrammable calculator (though it should not be necessary)
- The total score is 110. Any score above 100 will be counted as 100.

> Note: The problems below are **not exactly the same** as the real exam. However, they share the same knowledge and key points.

## Problem 1: True or False

1. In Makefile, a tab character is mandatory at the beginning of each command line within a rule.
2. In RISC-V, `jal ra foo` jumps the program execution to the target label `foo`.
3. When a child process terminates before the parent calls `wait()` (or other similar functions like `waitpid()`), it becomes a zombie process.
4. The regular expression `\d{4}-\d{2}-\d{2}` matches all date in the format `YYYY-MM-DD`.
5. In a single-core machine, using multi-thread will not give any performance gain.
6. The hardware implementation cost and performance are both better for a fully-associative cache comparing with a direct-mapping cache.
7. In a recursive program, the callee cannot access the saved register of the caller.
8. A lock is not needed if the shared data is read-only for all users.

## Problem 2: Short Answer Problems

1. Can we construct an OR gate only using the NAND gate? Please give an example if we can. 
    
    **NOTE**: The truth table of a NAND gate is:
    | A | B | A NAND B |
    |---|---|----------|
    | 0 | 0 | 1        |
    | 0 | 1 | 1        |
    | 1 | 0 | 1        |
    | 1 | 1 | 0        |
2. Draw an illustration of the Von Neumann architecture. You need to use text to mark each necessary components.
3. What does the command `cat >> ~/backup.txt` do? What should you do to kill this process while preserving the parent shell? You **should not use** `Ctrl+C`.
4. Suppose you are connecting a remote machine, but the system keeps saying that your `ssh` file `~/.ssh/id_rsa` is too permissive. Please write a **one-line** bash command to solve this problem. Note that this `ssh` file is private, so no one should be able to access it except yourself.
5. For the regular expression `^[b-f]\)[a-zA-Z]{4,}\d?(-[A-Z]+)+$`, which of the following line(s) can it match with?
    ```
    a)PleaseStar123-LIB-TEST
    b)CAT-DOG-FISH-BIRD
    c)regex001-PERFECT
    d) there-IS-A-SPACE
    e)CallMeAtPhoneNumber110
    f)TheLab2-OF-THIS-COURSE-IS-TOO-HARD
    ```
6. Explain a scenario where the Hoare monitor fails but the Mesa monitor works.
7. Enumerate all possible output sequence of the following code.
    ```cpp
    printf("L0\n");
    if (fork() != 0) {
        printf("L1\n");
        if (fork() != 0) {
            int cstatus;
            int cpid = wait(&cstatus);
            printf("L2\n");
        }
    }
    printf("Bye\n");
    ```

## Problem 3: Architecture

### 3.1 Hardware and Program Optimization

MISSING. You can refer to [2024 Spring Midterm](./2024_spring_midterm-answer.md) as exercise.

### 3.2 Cache

MISSING. You can refer to [2024 Spring Midterm](./2024_spring_midterm-answer.md) as exercise.

### 3.3 Assembly Code

Assume that we are executing the following assembly snippet on a RISC-V 32-bit processor. Here, `a0`, `t0`, `s0` and `m0` are just register names, similar to `x0` to `x31` which we discussed in the lecture. The instruction `li` (load immediate) loads the 32-bit immediate value into the destination register.
The instruction `blt` (branch-if-less-than) branches to the target label if the first source is less than the second source.

```assembly
init:
    li  a0, 0x10000000
    li  a1, 0x100
    li  a2, 0x8
    add s0, x0, a0
    add t0, x0, x0
    add m0, x0, x0
L1:
    lw  s1, 0(s0)
    add m0, m0, s1
    blt s1, a2, L3
L2:
    addi s0, s0, 4
    addi t0, t0, 1
    blt t0, a1, L1
    j done
L3:
    sw a2, 0(s0)
    j L2
done:
```

1. Rewrite the above assembly code into C language. We have provided you the sketch. Please fill in the blanks.

```cpp
int *x = 0x10000000;
int s = 0x100;
int a = 0x8;
int m = 0;
int *u;
________________________
for (________________________) {
    ________________________
    ________________________{
        ________________________
    }
}
```

2. Use natural language (English) to describe the functionality of this code, as briefly as possible.

## Problem 4: Scheduling

Different scheduling policies give different process execution order. Consider an example of 4 processes. The following table lists the order under 3 scheduling policies (FCFS, SJF, SRTF, or RR). Assume that:

- All timeslice-based policies have timeslice of 1 unit.
- Each process arrives exactly between timeslice $j$ and $j+1$ for some natural number $j$. The arrival time is defined as $j$.
- An incoming process will be place at the front of the waiting queue, i.e., it will be executed first if the policy allows it.

1. Please fill in the blanks.

    | Process | Arrival Time |
    |---------|--------------|
    | A       |      ?      |
    | B       |       ?     |
    | C       |        ?    |
    | D       |         ?   |

    | Current Time | FCFS | ? | ? | 
    |--------------|------|---|---|
    | 1            | A   |  A | A  |
    | 2            | A   |  B |  B |
    | 3            | A   |  A |  A |
    | 4            | A   |  A |  C |
    | 5            | B   |  ? |   ?|
    | 6            | C   |  ? |   ?|
    | 7            | C   |  ? |   ?|
    | 8            | C   |  ? |   ?|
    | 9            | D  |   ?|   C|
    | 10            | D  |  ? |  ? |


2. The time-to-first-token (TTFT) is a criterion for a LLM server. Suppose now that each process is a user calling for a reply of the LLM, and during each timeslice, the ongoing process will output 1 token at the end of the timeslice. The TTFT of this process is defined as the difference between the arrival time and the time to generate the first token. Please calculate the **average TTFT** of four processes for each scheduling policy. Which policy gives the worst TTFT and which one gives the best? Does this performance order always hold? Please explain why.

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