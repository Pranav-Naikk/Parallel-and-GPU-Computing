# OpenMP Matrix Multiplication

## Overview

This experiment implements matrix multiplication using OpenMP-based CPU parallelism.

OpenMP allows the matrix multiplication workload to be divided among multiple CPU threads while using shared memory.

## OpenMP Execution Model

The rows of the result matrix are distributed among multiple OpenMP threads.

```text
                 Matrix C
                    |
        +-----------+-----------+
        |           |           |
        v           v           v
     Thread 0    Thread 1    Thread 2 ...
        |           |           |
        v           v           v
      Rows        Rows        Rows
        |           |           |
        +-----------+-----------+
                    |
                    v
              Final Matrix