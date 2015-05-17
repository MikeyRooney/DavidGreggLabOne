#About


A program to speed up matrix multiplication.


Uses OpenMP to compute results in parallel and transposing to optimise cache usage (see http://www.akkadia.org/drepper/cpumemory.pdf Section 6.2.1)


The dimensions of the matrices are passed as arguments to the program, in the form: "./matmul -A rows -A cols -B rows -B cols"


#Timings

Timed using an Intel i5 2500k CPU (http://ark.intel.com/products/52210/Intel-Core-i5-2500K-Processor-6M-Cache-up-to-3_70-GHz) with turbo frequency disabled to ensure fair timing.


Each category was run 10 times and the given result is an average of the timings.


In all categories two 1000x1000 matrices were multiplied.


Compiled with "gcc -fopenmp matmul.c"


	Normal: 10.31 seconds
	Using a transposed matrix: 3.53 seconds
	Using OpenMP: 2.91 seconds
	Using OpenMP and a transposed matrix: 1.13 seconds


These numbers show that using OpenMP and transposing results a program that on average runs 9.1x faster

#Issues

Running this program with very small matrices will result in the "optimised" version being slower.


This is due to the overhead of creating threads and transposing the matrix being larger than the time saved.



