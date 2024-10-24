# README

## **Project Title: Performance Optimization and Parallel Computing Exercise**

### **Overview**

This project focuses on optimizing and parallelizing a Python program that performs a large-scale simulation of a physical system involving intensive matrix operations. The aim is to improve the performance and scalability of the code while ensuring correctness and efficient memory usage.

## **Report on Python Code Optimization for Large-Scale Simulation**

### **Problem Statement:**

The current Python program simulates a large-scale physical system, performing intensive matrix operations (multiplication, element-wise, solving linear equations). It is slow and not optimized for multi-core systems, making it essential to improve performance.

### Part 1: Initial Profiling and Analysis

### 1. Profiling the Code:

- Used cProfile for profiling.

* Identified the time-consuming functions:
  - np.linalg.solve: Most time-consuming operation.
  - np.dot: Significant time consumption for matrix multiplication.
    
### 2. Memory Usage Analysis:

- Analyzed memory usage with memory_profiler.
- Peak memory usage was 23.27 MiB for simulate_physical_system(1000).
- Identified potential inefficiencies like large arrays.

###  Part 2: Code Optimization

### 1. Optimizations:

* **Lower Precision:**
Converted arrays to float32 to reduce memory usage and improve cache utilization.

* **Memory Management:**
Eliminated temporary arrays and unnecessary copies. For instance, deleted A, B, and C after operations.

* **Error Handling:**
Added regularization to avoid singular matrices during linear equation solving.

### 2. Results:

* **Time Reduction:**
Optimized function showed improved performance. The difference between original and optimized results was minimal.

* **Memory Improvement:**
Reduced peak memory usage, confirmed through memory profiling.

### Part 3: Parallelization

###  1. Parallelizing Code:

* Used Joblib for parallelizing matrix operations across multiple CPU cores.
* Matrix multiplication was parallelized by splitting matrices into chunks and processing them in parallel.

* Handling Synchronization:

  - Ensured no race conditions by using independent chunks for parallel operations.
  - Used backend threading to manage parallel execution efficiently.

###  2. Results:

* Parallelization Efficiency:

- With Joblib, the code scaled well with multiple cores, significantly improving performance over both the original and optimized versions.

* Time Improvement:
  - Parallelized function achieved further performance gains, particularly with larger matrix sizes.
  
### Part 4: Testing and Reporting

### 1. Performance Testing:

* Conducted tests on different input sizes (e.g., 500, 1000, 1500).
  
* Verified correctness by comparing results of optimized and parallel functions with the original implementation. The differences were negligible.

### 2. Profiling Outputs:

* Saved profiling results for original, optimized, and parallel functions using cProfile.
  
* Memory profiling for different input sizes confirmed the optimized and parallel versions use less memory and improve computational efficiency.

### 3. Visualization:

* Visualized profiling results using snakeviz for an interactive analysis of code performance bottlenecks.

### Conclusion:

* Performance Gains:
  
  - Optimization and parallelization led to significant improvements in both execution time and memory efficiency.
