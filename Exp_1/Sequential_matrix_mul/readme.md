# Sequential Matrix Multiplication

## Overview

This experiment implements matrix multiplication using the traditional sequential CPU approach without parallel processing.

The sequential implementation serves as the baseline for comparing different parallel computing approaches such as OpenMP, MPI and CUDA.

## Matrix Multiplication

For matrices A and B, the resulting matrix C is calculated as:

C[i][j] = S A[i][k] × B[k][j]

## Execution Model

The computation is performed sequentially using three nested loops:

1. Select a row of matrix A.
2. Select a column of matrix B.
3. Calculate the dot product of the row and column.
4. Store the result in matrix C.

## Results

The existing experiment results are included in this folder.

- `Sequential1.png` – Sequential execution
- `Sequential_result.png` – Sequential result

## Purpose

The sequential implementation provides a baseline for comparison with OpenMP, MPI and CUDA implementations.