---
title: Computer Architecture
description: How processors, memory, storage, and input-output systems work together to execute programs
date: 2026-08-26
author: as-folio
draft: false
tags:
  - computer-architecture
  - processors
  - memory
  - systems
  - computing
---

Computer architecture describes how a computer is organized and how its parts cooperate to execute instructions. It connects the abstract world of software with the physical mechanisms of hardware: logic gates, registers, caches, buses, storage devices, and input-output controllers.

A useful way to understand architecture is to follow a program as it runs. The operating system loads instructions and data from storage into memory. The processor fetches those instructions, decodes them, performs calculations, and stores the results. At the same time, the memory hierarchy and input-output system work to keep useful data close to the processor and move information between the computer and the outside world.

## The Stored-Program Model

Most modern computers follow the stored-program model associated with the von Neumann architecture. Instructions and data are represented as binary values and stored in memory. The processor uses a program counter to identify the next instruction, then repeats a cycle of fetching, decoding, and executing.

A simplified instruction cycle looks like this:

1. **Fetch:** Read the instruction at the address held by the program counter.
2. **Decode:** Determine the operation and identify its operands.
3. **Execute:** Perform an arithmetic, logical, memory, or control operation.
4. **Write back:** Store the result in a register or memory location.
5. **Advance:** Update the program counter, unless a branch changes it.

This model is simple, but real processors execute many instructions at once, predict branches, and reorder internal work. They preserve the behavior expected by software while using more complicated machinery underneath to improve throughput.

## The Processor

The central processing unit (CPU) contains several important structures.

### Registers

Registers are small, fast storage locations inside the processor. They hold operands, addresses, intermediate results, and control information. General-purpose registers are used by ordinary instructions, while special registers track values such as the program counter and condition flags.

The number and purpose of registers are part of an instruction set architecture (ISA). An ISA defines the instructions visible to software, the available registers, data types, memory rules, and how programs interact with the processor. Examples include x86-64, ARM64, and RISC-V.

### Arithmetic and Logic Units

An arithmetic and logic unit (ALU) performs integer operations such as addition, subtraction, comparison, and bitwise logic. Processors may also include floating-point units and vector units for scientific calculations, media processing, and machine learning workloads.

A processor's clock frequency describes how quickly its timing signal cycles, but frequency alone does not determine performance. The amount of useful work completed per cycle depends on the instruction set, pipeline design, cache behavior, branch prediction, and the program itself.

### The Control Unit and Pipeline

The control unit coordinates instruction execution. In a pipelined processor, different instructions occupy different stages simultaneously. While one instruction is being decoded, another may be executing and a third may be fetched.

Pipelining improves throughput, but it introduces hazards. A data hazard occurs when an instruction needs a result that a previous instruction has not finished producing. A control hazard occurs when the processor does not yet know which instruction follows a branch. Forwarding, instruction scheduling, and branch prediction help reduce these delays.

## The Memory Hierarchy

Memory is organized as a hierarchy because fast storage is expensive and limited, while large storage is slower and cheaper. The processor generally encounters data in this order:

- Registers
- Level 1 cache
- Level 2 cache
- Last-level cache
- Main memory
- Persistent storage

A cache stores recently used or nearby data. Programs often exhibit temporal locality, meaning that recently accessed data is likely to be used again, and spatial locality, meaning that data near a recent access is likely to be used soon.

When the processor finds requested data in a cache, it receives a cache hit. If the data is absent, a cache miss requires a slower lookup in the next level. Efficient software and hardware layouts try to increase the hit rate and reduce the cost of misses.

The gap between processor speed and memory speed is one of the defining challenges of modern architecture. Larger caches, prefetching, multiple memory channels, and careful data layout all help reduce the impact of that gap.

## Main Memory and Storage

Main memory, usually dynamic random-access memory (DRAM), holds the programs and data currently in use. DRAM is relatively fast but volatile: its contents disappear when power is removed.

Persistent storage, such as solid-state drives and hard disks, retains data without power. Storage is much larger than main memory but generally has higher access latency. The operating system uses virtual memory to give programs a large address space and to move less-active pages between memory and storage when necessary.

Solid-state drives use flash memory and have no moving parts. They provide lower latency than hard disks, although their performance depends on the controller, interface, workload, and amount of free space. Storage technology changes the balance between capacity, latency, endurance, and cost, but it does not remove the need for a memory hierarchy.

## Input and Output

Input-output (I/O) systems connect the processor and memory to devices such as keyboards, displays, networks, cameras, and sensors. A device controller translates between the device's protocol and the computer's internal communication mechanisms.

Polling asks the processor to check a device repeatedly. This is straightforward but can waste processing time. Interrupts allow a device to notify the processor when attention is needed. Direct memory access (DMA) lets a controller transfer blocks of data directly to memory, reducing the number of instructions required for large transfers.

Operating systems provide abstractions such as files, sockets, and device files so that applications do not need to understand every hardware protocol. These abstractions improve portability while preserving access to specialized capabilities when necessary.

## Parallelism and Multicore Design

As increasing clock frequency became more difficult because of power and heat limits, designers placed multiple processor cores on a single chip. Each core can execute its own instruction stream, allowing independent tasks to run in parallel.

Parallel systems can use several forms of concurrency:

- **Instruction-level parallelism:** Execute multiple independent instructions within one core.
- **Data-level parallelism:** Apply one operation to many values using vector instructions.
- **Task-level parallelism:** Run separate tasks or threads on different cores.
- **Distributed parallelism:** Coordinate work across multiple computers.

Parallelism is not automatic. A program must contain independent work, and coordinating threads introduces overhead. Shared data can also create race conditions, so synchronization mechanisms such as locks, atomic operations, and barriers are necessary.

## Performance and Energy

Computer performance is multidimensional. Latency measures how long one operation takes, while throughput measures how much work can be completed over time. A system may have high throughput but poor response time, or low latency for small tasks but limited capacity for sustained workloads.

Energy efficiency is equally important. Power consumption affects battery life, cooling requirements, operating cost, and the density of data centers. Modern processors use techniques such as dynamic voltage and frequency scaling, sleep states, specialized accelerators, and heterogeneous cores to match energy use to workload demands.

Benchmark results should be interpreted carefully. A benchmark may favor a particular cache size, instruction set, compiler, or access pattern. The most meaningful measurement resembles the real workload and records the metric that matters to its users.

## Abstraction and Tradeoffs

Computer architecture is a study of tradeoffs rather than a search for one universally best design. A processor may favor low power consumption, maximum single-thread performance, high parallel throughput, low manufacturing cost, or specialized acceleration.

Abstraction makes these tradeoffs manageable. Applications use programming languages and libraries. Operating systems manage processes, memory, and devices. The ISA provides a stable contract between software and processor implementations. Microarchitecture then determines how a particular chip fulfills that contract.

Understanding these layers helps programmers make better decisions. Data structures influence cache locality. Algorithms determine parallelism and memory traffic. System calls introduce transitions between application and operating-system code. Even a small change in data layout can affect performance when it changes which memory hierarchy levels are used.

## Conclusion

A computer is not a single fast machine. It is a coordinated set of storage, computation, communication, and control mechanisms with very different costs. The processor executes instructions, the memory hierarchy supplies data, I/O devices exchange information, and the operating system organizes the whole system for applications.

Computer architecture provides the vocabulary for reasoning about those interactions. Once the relationships between instructions, caches, memory, storage, and parallel hardware are clear, software performance becomes less mysterious and system design becomes easier to evaluate.