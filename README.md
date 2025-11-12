# Assignment 6: Exploring Thread-Level Parallelism (TLP) in Shared-Memory Multiprocessors Using gem5
This project explores Thread-Level Parallelism (TLP) and its application in shared-memory multiprocessor systems using the gem5 simulator. The goal is to understand how different architectural parameters and design choices impact parallel performance, synchronization, and scalability in multi-core environments.
 Part 1: Understanding Thread-Level Parallelism
Research Literature Review
This section provides a critical synthesis of 3–5 recent peer-reviewed research papers (published within the last five years) from IEEE and ACM digital libraries. The review focuses on:

- The historical evolution of TLP and the transition from single-threaded to multi-core and heterogeneous architectures.  
- Analysis of parallel programming models, synchronization mechanisms, and scheduling strategies.  
- Exploration of contemporary challenges, including concurrency bugs, scalability limitations, energy efficiency, and heterogeneous processing.  
- Evaluation of novel techniques such as new programming models, compiler optimizations, runtime management systems, and hardware-level innovations that enhance TLP.  
- Discussion of future research directions, including many-core architectures, machine learning–guided parallelism, and specialized accelerators for TLP workloads.

Part 2: Exploring Shared-Memory Architectures with gem5
Overview
Using gem5’s MinorCPU model, this part investigates how the design of the `FloatSimdFU` (functional unit) affects the performance of a multi-threaded DAXPY kernel. The parameters under exploration are:

opLat (Operation Latency): Number of cycles an operation takes to complete.
issueLat (Issue Latency): Number of cycles before the next instruction can be issued.

The sum of both parameters is constrained to 7 cycles, with configurations such as:
Tasks Summary
1. MinorCPU Familiarization:
   Reviewed `MinorCPU.py` and `MinorDefaultFUPool.py` to understand the role of the FloatSimdFU and latency parameters.

2. FloatSimdFU Design Exploration: 
   Modified `MinorDefaultFUPool` to test different latency combinations.

3. Multi-Threaded DAXPY Simulation:  
   Implemented a multi-threaded DAXPY kernel where threads execute independent vector segments. Configured gem5 to simulate 2, 4, and 8 core systems.

4. Performance Analysis:
   Measured and compared:
   - Simulation time  
   - Parallel speedup (vs. single-threaded)  
   - Instructions per cycle (IPC) and cycles per instruction (CPI)  
   - FloatSimdFU utilization and synchronization overhead  

5. Comparison and Evaluation: 
   Created tables and visual graphs to illustrate trade-offs between different `(opLat, issueLat)` configurations.

6. Discussion: 
   Analyzed the relationship between functional unit design and TLP scalability, highlighting optimal trade-offs and observed bottlenecks.
