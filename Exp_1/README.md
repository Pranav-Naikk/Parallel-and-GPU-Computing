# Experiment 1 — Analysis of Performance for Matrix Multiplication

## 1. Experiment Title

**Analysis of Performance for Matrix Multiplication**

## 2. Aim

To implement matrix multiplication using Sequential, OpenMP, MPI, and CUDA approaches and compare their execution performance for a 4000 × 4000 matrix.

## 3. Problem Statement

Matrix multiplication is computationally intensive because it requires a large number of arithmetic operations. The experiment implements the same matrix multiplication problem using different execution models and compares their execution times.

All implementations use a **4000 × 4000** matrix and verify the result using:

**C[0][0] = 4000.00**

---

## 4. Sequential Matrix Multiplication

The sequential implementation performs matrix multiplication using a single CPU execution flow.

### Configuration

| Parameter | Value |
|---|---:|
| Matrix Size | 4000 × 4000 |
| Execution Model | Sequential CPU |
| Data Type | double |
| Initial A and B values | 1.0 |
| Expected C[0][0] | 4000.00 |
| Verification | PASSED |
| Execution Time | **339.308583 s** |

### Characteristics

The sequential implementation serves as the baseline for comparing the parallel implementations.

---

## 5. OpenMP Matrix Multiplication

OpenMP parallelizes the matrix multiplication across multiple CPU threads.

### Configuration

| Parameter | Value |
|---|---:|
| Matrix Size | 4000 × 4000 |
| Execution Model | OpenMP |
| Threads | 8 |
| Expected C[0][0] | 4000.00 |
| Verification | PASSED |
| Execution Time | **30.830434 s** |

### Speedup over Sequential

Speedup is calculated as:

**Speedup = Sequential Execution Time / OpenMP Execution Time**

Using the measured results:

**Speedup = 339.308583 / 30.830434 = 11.01×**

The OpenMP implementation reduces execution time by distributing the matrix multiplication workload across 8 CPU threads.

---

## 6. MPI Matrix Multiplication

MPI distributes the matrix multiplication workload among multiple processes. The implementation uses communication operations to distribute input data and collect the resulting matrix.

### Configuration

| Parameter | Value |
|---|---:|
| Matrix Size | 4000 × 4000 |
| Execution Model | MPI |
| MPI Processes | 4 |
| Data Type | double |
| Initial A and B values | 1.0 |
| Expected C[0][0] | 4000.00 |
| Verification | PASSED |
| Execution Time | **92.979510 s** |

### Speedup over Sequential

Speedup is calculated as:

**Speedup = Sequential Execution Time / MPI Execution Time**

Using the measured results:

**Speedup = 339.308583 / 92.979510 = 3.65×**

MPI introduces communication and synchronization overhead because the computation is distributed between separate processes.

---

## 7. CUDA Matrix Multiplication

CUDA performs the matrix multiplication on the NVIDIA GPU. Each output element is computed by GPU threads organized into blocks and a grid.

### GPU Configuration

| Parameter | Value |
|---|---:|
| GPU | NVIDIA GeForce RTX 5060 Ti |
| Compute Capability | 12.0 |
| Global Memory | 15.93 GB |
| Matrix Size | 4000 × 4000 |
| Block Size | 16 × 16 threads |
| Threads per Block | 256 |
| Grid Size | 250 × 250 blocks |
| Logical Threads | 16,000,000 |

### CUDA Result

| Parameter | Result |
|---|---:|
| Kernel Execution Time | **0.088848 s** |
| Total CUDA Phase Time | **0.118994 s** |
| C[0][0] | **4000.00** |
| Verification | **PASSED** |

### Speedup over Sequential

For the GPU kernel comparison:

**Speedup = Sequential Execution Time / CUDA Kernel Execution Time**

Using the measured results:

**Speedup = 339.308583 / 0.088848 = 3818.98×**

The CUDA kernel execution time is reported separately from the total CUDA phase time because GPU memory transfers and other CUDA operations contribute to the total phase time.

Using the total CUDA phase time instead:

**339.308583 / 0.118994 = 2851.45×**

---

## 8. Overall Performance Comparison

| Implementation | Execution Time (s) | Speedup vs Sequential |
|---|---:|---:|
| Sequential | 339.308583 | 1.00× |
| OpenMP | 30.830434 | 11.01× |
| MPI | 92.979510 | 3.65× |
| CUDA Kernel | 0.088848 | 3818.98× |
| CUDA Total Phase | 0.118994 | 2851.45× |

### Execution Time Order

Based on the measured execution times:

1. **CUDA Kernel** — 0.088848 s
2. **OpenMP** — 30.830434 s
3. **MPI** — 92.979510 s
4. **Sequential** — 339.308583 s

The ordering above is based strictly on the measured execution times. CUDA kernel time and total CUDA phase time represent different portions of the CUDA execution and should therefore be interpreted separately.

---

## 9. Performance Analysis Graph

The following graph compares the execution times of the four matrix multiplication approaches.

![Performance Comparison](performance_comparison.png)

Because the execution times span several orders of magnitude, the graph uses a logarithmic Y-axis.

---

## 10. Verification

All four implementations produced the expected matrix multiplication result:

**C[0][0] = 4000.00**

| Implementation | Verification |
|---|---|
| Sequential | PASSED |
| OpenMP | PASSED |
| MPI | PASSED |
| CUDA | PASSED |

---

## 11. Conclusion

The experiment demonstrates the performance differences between sequential and parallel matrix multiplication approaches.

- **Sequential** provides the baseline CPU execution time.
- **OpenMP** reduces execution time by using multiple CPU threads.
- **MPI** distributes computation among multiple processes, with communication and synchronization overhead.
- **CUDA** executes the matrix multiplication on the GPU and reports substantially lower measured execution time for the kernel.

The comparison demonstrates how parallel execution can reduce the time required for computationally intensive matrix multiplication.
