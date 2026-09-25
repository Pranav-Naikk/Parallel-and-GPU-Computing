# MPI Matrix Multiplication

## Overview

This experiment implements matrix multiplication using the Message Passing Interface (MPI).

MPI is used to distribute the matrix multiplication workload among multiple processes.

## Matrix Configuration

- Matrix size: 4000 × 4000
- Data type: double
- Matrix A initial value: 1.0
- Matrix B initial value: 1.0
- Expected verification value: C[0][0] = 4000.00

## MPI Execution Model

```text
                    Process 0
                       |
                 Matrix A and B
                       |
              +--------+--------+
              |                 |
          MPI_Scatter        MPI_Bcast
              |                 |
              v                 v
        Local rows of A     Matrix B
              |                 |
              +--------+--------+
                       |
             Parallel Computation
                       |
                  MPI_Gather
                       |
                       v
                 Matrix C