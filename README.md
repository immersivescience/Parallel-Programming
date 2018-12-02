# Parallel-Programming
Assignments:

1)Write a program to find all prime numbers up to some value M, using the Sieve of Eratosthenes algorithm we discussed in class (look up details on the web)
You will be parallelizing this algorithm using MPI, OpenMP and CUDA (details will be discussed, Week 2 we will discuss MPI, others lateri.
You want to evaluate difficulty of getting it to work and how long calculating takes under different methods and on different compute platforms (single 8 core machine, a set of machines on the network, a single GPU)

2) Same as above for a parallel optimization code: downhill simplex (see description of algorithm in link to "Numerical Recipes", above).

3) Alternative: write a program to model a cellular automaton (see links above on cellular automata). The grid should be at least 600x600, the neighborhood around each cell should be variable, allowing radius from 1 (3x3 square) to at least 3 (7x7 square centered on a cell).
Notes on parallelizing cellular automata 

Here is how to compile and link programs that combine MPI and CUDA code. In the example, the cuda code is "cuda.cu" and the mpi code is "mpi.c". The final executable is "cudaMPI"

nvcc -c cuda.cu // Makes cuda.o 
mpicc -c mpi.c // Makes mpi.o 
mpicc mpi.o cuda.o -o cudaMPI -lcudart -L /usr/local/cuda/lib64 
==> makes cudaMPI. Execute with mpirun or mpiexec, like a standard mpi program. With thanks to Ahmed Algadi, who figured out this sequence of instructions and in particular the library specifications.


Programming note: if programming in C or in C++, output from different processes may appear out of order, even if the processes are ordered, due to buffered standard output. When using printf to standard output, follow it with "fflush(stdio);" to force the buffers to empty. In C++, almays terminate COUT statements with "endl"
Only do this if output order from multiple processes is important, because it slows things down.

GRADING: TBA
