# Intro to Computer Systems Final 2024 Spring
## General Information
- **Date**: 2024-06-15
- **Duration**: 19:00 - 21:00
- **Answer**: In English
- **May Bring Calculators and a cheat sheet**
- The total score is 110. Any score above 100 will be counted as 100.

## Problem 1: True or False (3 pts * 10 = 30 pts)

For "true" answers, you don't need to give reason; for "false" answers, you must give a reason.

1. An array `a[10000]` in C language locate in contiguous physical memory space.
2. It is not possible that two distinct processes have different virtual memory mapping to a same physical memory.
3. Page fault in VM system is always handled by the hardware.
4. The performance of SSD may degenerate when it is near full.
5. `git commit` requires a network connection, since it send changes to the remote server.
6. Since CPU cache is transparent to software, software engineers can forget about CPU caches.
7. For disk scheduling policies, C-SCAN is always better than SCAN, since it don't cause starvation.
8. Internet don't have deadlock since there is always enough bandwidth than demands by hosts.
9. When we perform memory-mapped I/O, the I/O devices have to be attached directly to Memory Bus.
10. When thrashing (a problem caused by having too much processes), both the I/O rate and CPU utilization is high.

## Problem 2: Short Answer Problems (3 pts * 7 = 21 pts)

Answer shortly, i.e. no more than 3-4 sentences

1. Evaluate `(unsigned int)-2` in a 32 bit system. Answer in hex decimals.
2. Give 2 reasons that running too much threads are bad.
3. Why a `wait()` operation on a conditional variable must happen within a monitor lock? What would happen if we omit the lock?
4. List one disadavantage and one adavantage for having a large page size.
5. Give 2 differences between MAC address and IP address.
6. What happens if a AFS server crash and lost all callback states?
7. Someone transfer a integer (4 bytes) from an ARM machine to a RISC-V machine through socket, but the recieved result is wrong. What may cause the problem? What part in RPC helps solving the problem?

## Problem 3 (32 pts) Virtual Memory and File System

### Problem 3.1 : Virtual Memory (18 pts)

Consider a virtual memory system. The virtual address is 40 bits, and the physical address is 36 bits. Each block is 4kB. The page table is organized in two levels, with the address separated as (18bit + 10bit + 12 bit), 18 bits for first level and 10 bits for second level.

Besides from the address, PTE also contain 6 bits: V (valid), D (dirty), R (read permission), W (write permission), X (execute permission), U (user mode).

1. Someone want to run a costly AI program which use 4TB memory. Why can't the system support it?
2. Find the size of PTE, and write your answer in *bytes*. Round up the answer to integer, so that the PTEs can be aligned in bytes.
3. If the system load a word (4 bytes), how many memory accesses does it take? You may assume that the address for the first-level page table is already in the CPU register.
4. To support some applications with large RAM requirements, some OS support a thing called "huge page". That is, for entries in the first-level page table, if `V==1` and `(R|W|X)!=0`, then the entry isn't the address of second-level page table, but instead the physical address of the "huge page". In other words, before, we access the entry in first-level page table to find the address of second-level page table; but now for some entries, we instead find the physical address of the "huge page". What is a proper size of the "huge page"? Why?

### Problem 3.2 : File System (14 pts)

Consider a file system with the disk being a magnetic disk. The average seek time and rotational delay is both 10 ms. The data transfer time from the disk to memory is 4MB/s. Assume a 4kB block size.

Moreover, we make an assumption: each time a block of data or inode is loaded into memory, it always take 1 ms for the file system to process the content and then decide what to do next. This time is independent to how many information it need to gain.

1. Find the time to access inode for root directory (`/`). You can assume that the inumber for root directory is known.
2. Find the time to read the first byte in the file `/a/b/c`. Hint: first list how many disk accesses you need.
3. Find the time to read additional 5MB data from that file. Note that you should **exclude** the time in the previous question.

## Problem 4: Transaction (10 pts)

Consider 4 concurrent transactions listed below.

| Time | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|------|---|---|---|---|---|---|---|---|---|----|
| T1   | R(A) |  | | | | | W(A)| R(C)| | |
| T2   | | R(A) | |  | | | | |  R(C)||
| T3   | | | | R(C) | R(B)  |  | | | |W(B) |
| T4   | | | R(C) | | |  W(C) | | | | |

1. Draw the dependency graph for the transactions.
2. Which order(s) below is conflict equivalent to the above schedule?
   - T4, T2, T1, T3
   - T3, T2, T4, T1
   - T3, T4, T2, T1
   - T1, T2, T4, T3
   - T1, T4, T2, T3
   - None of the above

3. Implement a 2-phase locking (2PL) for the schedule above. You can use the following notations:
    - `S(Y)`: Acquire shared lock on Y
    - `X(Y)`: Acquire exclusive lock on Y
    - `US(Y)`: Release shared lock on Y
    - `UX(Y)`: Release exclusive lock on Y

## Problem 5: Networking and RPC (17 pts)

### Problem 5.1: Networking

Consider this scenario: Tom is downloading a high-quality AI model from the Internet. He thinks that he has a 1Gbps (around 100MB+/s) network, but in fact, he find that the real download speed is really slow, around 1MB/s.

1. He checked the packet drop rate, and found that there is only less than 0.5% packet drop. His roommate, John, suggests that the packet drop has a nelegible effect. However, Tom doesn't think so. Who is correct and why?
2. Tom remembered that in the class, the teacher mentioned that changing from TCP to UDP can increase the network speed. He then change it and indeed find that the speed is increased. What may happen to his file and why? How can he solve the problem? (You only need to give an idea, but no code or details are required.)
3. Tom want to be further faster, so he decided to use a wired network with no packet loss. Will the transmission be faster? Why?
4. Tom's method attracted many people in the same building and they all follow him. Soon, someone complains that he even can't connect to websites normally. Why is that?

### Problem 5.2: RPC and Network File Systems

1. Someone opened a large file and randomly modified all blocks in the file. After modifications, he closed the file. Is the performance better if he is using NFS or AFS?

2. There are two users collaborating on a same file. Initially, only user1 modifies the file, and user2 doesn't do anything. After user1 has done his job, he told user2 to see, but user2 don't find any changes. Then user1 closes the file, and user2 soon find that the file is changed. Is they using NFS or AFS? What happened before and after user1 closes the file?

3. If user1 is using the other file system (i.e. different from the answer of the previous problem), then what will they observe? Explain your answers.