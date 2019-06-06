This folder contains the spin-glass instances that were studied in the [paper](https://www.frontiersin.org/articles/10.3389/fphy.2019.00048/full): **Physics-Inspired Optimization for Quadratic Unconstrained Problems Using a Digital Annealer**

The problem instances are divided in four categories based on the couplers' adjacency and disorder: 
1. Two-dimensional spin-glass problems with bimodal disorder (2D-bimodal)
2. Two-dimensional spin-glass problems with Gaussian disorder (2D-Gaussian)
3. Fully connected spin-glass problems with bimodal disorder (SK-bimodal)
4. Fully connected spin-glass problems with Gaussian disorder (SK-Gaussian)

For a detailed description, see Section 5 of the paper. In each category there are nine sizes, from
64 variables to 1024 variables, and for each size there are 100 instances. The total number
of instances is 3600 (4 * 9 * 100).

Each of the category subdirectories is labelled by the size of the instances in it, and
includes 100 problem instance files (e.g. *problem_10.txt*) and a file with the best known
energies for each instance (_GSE.txt_). The format of the lines of _GSE.txt_ is:
```
[problem instance index] [best known energy]
```
For example, the line:
> 12 -84

indicates that the problem instance in the file *problem_12.txt* has a best known energy of -84.

The problem to be solved is a minimization problem, given by 
```
x = argmin[x^T Q x], x \in {0,1}^n 
```
The problem instance files contain the instances in their quadratic unconstrained binary optimization 
representation. Since the instances were created as Ising problems, they can have a constant term, 
which is given on the first line, even if it is zero. The lines after that give the entries of 
the _Q_ matrix in _x^T Q x_, as an upper triangular matrix with the format:

```
[variable_index1] [variable_index2] [coupling]
```
For example, the line:
> 1 64 -1

indicates that the matrix element _Q[1,64]_ is -1 and _Q[64,1]_ is 0. Diagonal elements are given in the same way,
with equal ```variable_index1``` and ```variable_index2```. 

Note that the elements of the _Q_ matrix, the energy offset, and therefore the best known energies
are all integer.
