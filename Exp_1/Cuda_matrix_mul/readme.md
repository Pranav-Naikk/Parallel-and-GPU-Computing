# CUDA Matrix Multiplication

## Overview

CUDA is NVIDIA's parallel computing platform that allows computation to be performed using NVIDIA GPUs.

Matrix multiplication can be parallelized by distributing calculations among a large number of GPU threads.

## Matrix Multiplication

For matrices A and B:

C[i][j] = Σ A[i][k] × B[k][j]

Different GPU threads can calculate different elements of the output matrix.

## CUDA Execution Model

```text
                    CPU / Host
                        |
                 CUDA Kernel Launch
                        |
                        v
                   GPU / Device
                        |
              +---------+---------+
              |         |         |
            Block     Block     Block
              |         |         |
           Threads   Threads   Threads
              |         |         |
              +---------+---------+
                        |
                        v
                  Matrix C