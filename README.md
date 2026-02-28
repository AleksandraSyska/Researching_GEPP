# Complex Linear System Solver (GEPP)

## 📌 Project Overview
[cite_start]This project provides a numerical implementation for solving complex systems of linear equations in MATLAB[cite: 1]. The primary focus is solving equations of the form:
$$Cz = c$$
[cite_start]where $C$ is a complex $n \times n$ matrix, and $z$ and $c$ are complex vectors[cite: 8]. [cite_start]The project implements this solution using **Gaussian Elimination with Partial Pivoting (GEPP)**[cite: 5].

## 🧮 Mathematical Model
[cite_start]To solve the complex system, the problem is transformed into an equivalent real-valued block system of dimension $2n \times 2n$[cite: 10, 57]. The components are defined as:
* [cite_start]**Matrix Components**: $C = A + iB$, where $A$ and $B$ are real $n \times n$ matrices[cite: 8, 61].
* [cite_start]**Unknowns**: $z = x + iy$, where $x$ and $y$ are real $n \times 1$ vectors[cite: 8].
* [cite_start]**Constants**: $c = a + ib$, where $a$ and $b$ are real $n \times 1$ vectors[cite: 8, 61].

The resulting block matrix system is:
[cite_start]$$\begin{bmatrix} A & -B \\ B & A \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} a \\ b \end{bmatrix}$$ 

## 🚀 Key Features
* [cite_start]**GEPP Algorithm**: Implements row swapping (pivoting) to place the largest absolute value on the diagonal, ensuring numerical stability[cite: 25, 28].
* [cite_start]**Singularity Handling**: The solver checks for singular or nearly-singular matrices by comparing pivot values to machine precision (`eps`)[cite: 79, 149].
* [cite_start]**Back Substitution**: Calculates the final solution from the upper triangular matrix[cite: 30, 48, 49].
* [cite_start]**Verification**: Includes a test script to compare results with MATLAB's built-in backslash (`\`) operator[cite: 11, 88, 97].

## 📂 Project Structure
* [cite_start]`solve_block_system.m`: The main solver function that manages the block transformation and GEPP algorithm[cite: 70, 71, 72].
* [cite_start]`create_equations.m`: A helper function that separates real and imaginary parts to build the $2n \times 2n$ system[cite: 52, 59, 60].
* [cite_start]`skrypt_testujacy.m`: A testing environment containing various test cases, including random, Hermitian, and ill-conditioned matrices[cite: 81, 113, 137].
* [cite_start]`gepp_raport_syska.pdf`: Detailed documentation, theoretical background, and analysis of results [cite: 1-242].

## 📊 Performance and Accuracy
Based on the benchmarks provided in the report:
* [cite_start]**Accuracy**: The custom solver maintains high precision, with relative errors typically between $10^{-16}$ and $10^{-10}$[cite: 167, 183].
* [cite_start]**Speed**: While numerically accurate, the custom GEPP implementation is significantly slower than MATLAB's built-in functions for large matrices ($n > 100$)[cite: 122, 172, 180].

## 💻 Usage Example
```matlab
% Define complex input
C = [3+2i, 1-1i; 2+0i, 4+2i];
c = [5+1i; 6-2i];

% Solve using GEPP block decomposition
z = solve_block_system(C, c);

% Display the complex result
disp('Solution z:');
disp(z);
