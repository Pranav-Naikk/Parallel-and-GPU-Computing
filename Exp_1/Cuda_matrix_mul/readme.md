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

\[
C = A \times B
\]

where:

\[
C[i][j] = \sum_{k=0}^{N-1} A[i][k] \times B[k][j]
\]

For this experiment:

\[
N = 4000
\]

All elements of matrices A and B are initialized to `1.0`.

Therefore, the expected value of every element of matrix C is:

\[
C[i][j] = 4000
\]

Hence, the expected verification result is:

```text
C[0][0] = 4000.00
