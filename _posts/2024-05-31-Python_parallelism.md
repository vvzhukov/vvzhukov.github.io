---
layout: post
title: Parallelism in Python
subtitle: Recap of MultiThreading, MultiProcessing, Async
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Python, Parallelism, Threads, Processes, Async]
comments: true
---

{: .box-note}

# Parallelism in Python

If you've ever considered speeding up your application by running some routines simultaneously, parallelism might be the solution you're looking for. Python offers several ways to run tasks in parallel,
making your code faster and more efficient. This post will walk you through threading, multiprocessing, and asynchronous programming in Python, and briefly review how parallelism techniques are used in 
popular libraries focused on machine learning (ML) and large language models (LLMs).  

It is worth mentioning that on a high level of abstraction, Python converts the source code to bytecode using the interpreter and then executes the bytecode using the Python Virtual Machine, which translates it into machine code instructions for the processor to execute. Global Interpreter Lock (GIL) is a component of the Python virtual machine, specifically in the CPython implementation, which is the reference implementation of Python. The GIL is a mutex (or a lock) that protects access to Python objects, preventing multiple native threads from executing Python bytecodes at once in CPython. This ensures that only one thread executes in the Python interpreter at any given time, making memory management and execution safe in a multi-threaded environment. GIL can limit the performance gains from parallelism in some scenarios. We'll explore how each parallelism technique handles the GIL and manages resources to maximize performance. Additionally, we'll touch on environment variables like `OMP_NUM_THREADS`, `MPI_NUM_THREADS`, `MKL_NUM_THREADS`, and `OPENBLAS_NUM_THREADS`, which control the number of threads used by various parallel computing libraries.  

## Threading  

### Definition  
Threading allows you to run multiple threads (smaller units of a process) concurrently within the same program. Each thread operates in the same memory space, making it easier to share data between threads.
Again, thread is a smallest series of related instructions involved in a process, which can involve many threads.

### Pros
- **Low Overhead:** Threads are lightweight and quick to create.
- **Shared Memory:** Easier data sharing and communication since threads share the same memory space.
- **Good for I/O-bound Tasks:** Ideal for tasks involving waiting for I/O operations (e.g., reading files, network requests).

### Cons
- **Global Interpreter Lock (GIL):** The GIL prevents true parallel execution of threads for CPU-bound tasks.
- **Complex Debugging:** Managing threads can be tricky and error-prone, with issues like race conditions and deadlocks.

### Popular Libraries in Python
- `threading`: Basic threading support.
- `concurrent.futures.ThreadPoolExecutor`: Higher-level interface for managing threads.

### Code Example

```python
import threading

def print_numbers():
    for i in range(5):
        print(i)

# Creating threads
thread1 = threading.Thread(target=print_numbers)
thread2 = threading.Thread(target=print_numbers)

# Starting threads
thread1.start()
thread2.start()

# Joining threads to the main thread
thread1.join()
thread2.join()
```
In this example, two threads are created and started, both executing the print_numbers function. The join method ensures that the main thread waits for both threads to complete before proceeding.

## Multiprocessing  

### Definition
Multiprocessing runs multiple processes concurrently, each with its own memory space. This method bypasses the GIL, allowing true parallel execution on multi-core CPUs.
Similarly to the thread definition, process is the instance of a computer program that is being executed by one or many threads.

### Pros  
- True Parallelism: Ideal for CPU-bound tasks as it avoids the GIL.
- Isolation: Each process has its own memory space, reducing risks of data corruption.  

### Cons  
- Higher Overhead: Processes are heavier and consume more resources compared to threads.
- Complex Communication: Inter-process communication (IPC) is slower and more complex than thread communication.

### Popular Libraries in Python
- multiprocessing: Core library for process-based parallelism.
- concurrent.futures.ProcessPoolExecutor: Higher-level interface for managing processes.

### Code Example  
```python
from multiprocessing import Process

def print_numbers():
    for i in range(5):
        print(i)

# Creating processes
process1 = Process(target=print_numbers)
process2 = Process(target=print_numbers)

# Starting processes
process1.start()
process2.start()

# Joining processes to the main process
process1.join()
process2.join()
```
Here, two processes are created and run concurrently. Each process executes the print_numbers function independently, leveraging multiple CPU cores for true parallel execution.

## Async  

### Definition
Asynchronous programming allows for non-blocking operations, where tasks can run concurrently without waiting for others to complete. It's particularly useful for handling I/O-bound and network operations.

### Pros
- Efficiency: Excellent for I/O-bound tasks, allowing other tasks to proceed while waiting.
- Scalability: Can handle many tasks concurrently without the overhead of threads or processes.

### Cons
- Complexity: Managing asynchronous code can be tricky due to callbacks and the event loop.
- Less Effective for CPU-bound Tasks: Not as useful for CPU-intensive tasks compared to threading and multiprocessing.

### Popular Libraries in Python
- asyncio: Core library for asynchronous programming.
- aiohttp: Asynchronous HTTP client/server.

```python
import asyncio

async def print_numbers():
    for i in range(5):
        print(i)
        await asyncio.sleep(1)  # Simulating an I/O-bound operation

# Running the async function
async def main():
    await asyncio.gather(print_numbers(), print_numbers())

asyncio.run(main())
```
This example uses asyncio to run the print_numbers function concurrently. The await keyword pauses the function execution, allowing other tasks to run.

## Environment Variables for Thread Control
Python's performance can be further tuned using environment variables that control the number of threads used by various parallel computing libraries:

- OMP_NUM_THREADS: Sets the number of threads for OpenMP, a widely used API for parallel programming.
- MPI_NUM_THREADS: Sets the number of threads for MPI (Message Passing Interface) implementations.
- MKL_NUM_THREADS: Sets the number of threads for Intel's Math Kernel Library (MKL), which is often used for linear algebra operations.
- OPENBLAS_NUM_THREADS: Sets the number of threads for OpenBLAS, an optimized BLAS library used for linear algebra operations.
These environment variables can be set in your code or your shell environment. For example:

```bash
export OMP_NUM_THREADS=4
export MKL_NUM_THREADS=4
```
Or within a Python script:
```python
import os
os.environ['OMP_NUM_THREADS'] = '4'
os.environ['MKL_NUM_THREADS'] = '4'
```

## Parallelism for Machine Learning and Large Language Models
### Definition
In ML and LLMs, parallelism is crucial for handling vast datasets and complex computations. Parallelism can be implemented at different levels, such as data parallelism, model parallelism, and pipelining.

### Data Parallelism
In data parallelism, the same model is replicated across multiple processors, and different subsets of data are processed simultaneously. This is useful for training models on large datasets.

### Model Parallelism
Model parallelism involves splitting a model across multiple processors. Each processor handles different parts of the model, making it suitable for very large models that don't fit into a single processor's memory.

### Pipelining
Pipelining breaks down the ML training process into different stages, with each stage handled by a different processor. This technique improves throughput by ensuring all processors are continuously working on different parts of the task.

### Popular Libraries in Python
- Dask: Parallel computing with task scheduling.
- Ray: Distributed computing framework.
- TensorFlow: Popular ML library with built-in support for parallelism.
- PyTorch: Another leading ML library with robust parallelism capabilities.

### Code Examples

Using Dask for Parallel Computing:
```python
import dask.array as da

# Creating a large Dask array
x = da.random.random((10000, 10000), chunks=(1000, 1000))

# Performing computation in parallel
result = x.mean().compute()
print(result)
```
In this Dask example, a large array is created and divided into chunks. The compute method performs the mean calculation in parallel across these chunks, leveraging multiple CPU cores.

Using PyTorch for Model Training:
```python
import torch
import torch.nn as nn
import torch.optim as optim

# Defining a simple neural network
class SimpleNN(nn.Module):
    def __init__(self):
        super(SimpleNN, self).__init__()
        self.fc = nn.Linear(10, 1)

    def forward(self, x):
        return self.fc(x)

# Creating a model and moving it to GPU if available
model = SimpleNN()
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model.to(device)

# Dummy input and target
input = torch.randn(64, 10).to(device)
target = torch.randn(64, 1).to(device)

# Loss function and optimizer
criterion = nn.MSELoss()
optimizer = optim.SGD(model.parameters(), lr=0.01)

# Training loop
for epoch in range(10):
    optimizer.zero_grad()         # Clear the gradients
    output = model(input)         # Forward pass
    loss = criterion(output, target)  # Compute the loss
    loss.backward()               # Backward pass (compute gradients)
    optimizer.step()              # Update the weights
    print(f'Epoch {epoch+1}, Loss: {loss.item()}')
```
In this PyTorch example, the model is trained on a GPU if available. Here's how parallelism works under the hood:
- Data Parallelism: During the forward pass, input data is divided into batches, and each batch is processed in parallel on the GPU.
- Backpropagation: Gradients for each batch are computed in parallel, leveraging the GPU's multiple cores.
- Weight Update: After backpropagation, the optimizer updates the model's weights based on the computed gradients.
- Pros and Cons of Parallelism in ML and LLMs

### Pros:
- Speed: Significant reduction in training and inference times.
- Scalability: Ability to handle larger datasets and more complex models.
- Resource Utilization: Efficient use of available hardware resources (GPUs, TPUs).

### Cons:
- Complexity: More complex setup and debugging.
- Resource Management
