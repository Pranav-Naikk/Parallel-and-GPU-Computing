# Experiment 1 — Matrix Multiplication using CUDA

## 1. Experiment Title

**Matrix Multiplication using CUDA**

---

## 2. Aim

To implement matrix multiplication using CUDA parallel programming and analyze the execution performance of GPU-based matrix multiplication.

The experiment performs multiplication of two square matrices of size:

**4000 × 4000**

The CUDA implementation assigns the computation of individual elements of the result matrix to GPU threads.

---

## 3. Problem Statement

Given two matrices:

- Matrix A of size 4000 × 4000
- Matrix B of size 4000 × 4000

the objective is to compute:

$$
C = A \times B
$$

where:

$$
C[i][j] = \sum_{k=0}^{N-1} A[i][k] \times B[k][j]
$$

For this experiment:

$$
N = 4000
$$

All elements of matrices A and B are initialized to `1.0`.

Therefore, the expected value of every element of matrix C is:

$$
C[i][j] = 4000
$$

Hence, the expected verification result is:

```text
C[0][0] = 4000.00
```

---

## 4. CUDA Implementation

The matrix multiplication is parallelized using a **2D CUDA grid**.

Each CUDA thread is responsible for calculating one element of the output matrix `C`.

### CUDA Configuration

- GPU: `NVIDIA GeForce RTX 5060 Ti`
- Compute Capability: `12.0`
- Global Memory: `15.93 GB`
- Matrix size: `4000 × 4000`
- Block size: `16 × 16` threads
- Grid size: `250 × 250` blocks
- Threads per block: `256`
- Total logical CUDA threads: `16,000,000`

The CUDA kernel calculates each output element by performing the dot product of one row of matrix A with one column of matrix B.

---

## 5. Execution Results

The experiment was executed successfully on an **NVIDIA GeForce RTX 5060 Ti** GPU.

### Observed Output

```text
CUDA Matrix Multiplication
===========================
GPU = NVIDIA GeForce RTX 5060 Ti
Compute Capability = 12.0
Global Memory = 15.93 GB
Matrix Size = 4000 x 4000
Initializing matrices...
Allocating GPU memory...
Grid Size = 250 x 250 blocks
Block Size = 16 x 16 threads
Threads per Block = 256
Logical Threads = 16000000
Copying matrices to GPU...
Copying result from GPU...

===========================
CUDA Matrix Multiplication Completed
===========================
Matrix Size = 4000 x 4000
Grid Size = 250 x 250 blocks
Block Size = 16 x 16 threads
Kernel Execution Time = 0.088848 seconds
Total CUDA Phase Time = 0.118994 seconds
Verification C[0][0] = 4000.00
Verification Status = PASSED
```

### Performance Measurements

| Parameter | Result |
|---|---:|
| GPU | NVIDIA GeForce RTX 5060 Ti |
| Compute Capability | 12.0 |
| Global Memory | 15.93 GB |
| Matrix Size | 4000 × 4000 |
| Grid Size | 250 × 250 blocks |
| Block Size | 16 × 16 threads |
| Threads per Block | 256 |
| Total Logical Threads | 16,000,000 |
| Kernel Execution Time | **0.088848 s** |
| Total CUDA Phase Time | **0.118994 s** |
| Verification `C[0][0]` | **4000.00** |
| Verification Status | **PASSED** |

---

## 6. Result

The CUDA-based matrix multiplication was successfully executed for matrices of size **4000 × 4000** using a **16 × 16 thread block configuration**.

The measured GPU kernel execution time was:

$$
\boxed{0.088848\text{ seconds}}
$$

The total CUDA phase time was:

$$
\boxed{0.118994\text{ seconds}}
$$

The program completed successfully and produced the following verification output:

```text
Verification C[0][0] = 4000.00
```

Since all elements of matrices A and B are initialized to `1.0`, the mathematically expected value is:

```text
C[0][0] = 4000.00
```

The verification status is **PASSED**, confirming that the computed result matches the expected value.

---

## 7. Conclusion

The experiment demonstrates the use of **NVIDIA CUDA for parallel matrix multiplication**.

The computation is distributed across **16 million CUDA threads**, with each thread responsible for computing one element of the result matrix.

For the 4000 × 4000 matrix multiplication, the observed performance was:

- **GPU:** NVIDIA GeForce RTX 5060 Ti
- **Compute Capability:** `12.0`
- **Global Memory:** `15.93 GB`
- **Kernel Execution Time:** `0.088848 seconds`
- **Total CUDA Phase Time:** `0.118994 seconds`
- **Block Configuration:** `16 × 16`
- **Grid Configuration:** `250 × 250`
- **Verification Status:** `PASSED`

The experiment successfully demonstrates GPU-based parallel execution of matrix multiplication using CUDA, with the computed result correctly verified against the expected value.
