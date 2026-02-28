# Complex Linear System Solver (GEPP)

## 📌 Project Overview
This project provides a numerical implementation for solving complex systems of linear equations in MATLAB. The primary focus is solving equations of the form:
$$Cz = c$$
where $C$ is a complex $n \times n$ matrix, and $z$ and $c$ are complex vectors. The project implements this solution using **Gaussian Elimination with Partial Pivoting (GEPP)**.

## 🧮 Mathematical Model
To solve the complex system, the problem is transformed into an equivalent real-valued block system of dimension $2n \times 2n$. The components are defined as:
**Matrix Components**: $C = A + iB$, where $A$ and $B$ are real $n \times n$ matrices.
**Unknowns**: $z = x + iy$, where $x$ and $y$ are real $n \times 1$ vectors.
**Constants**: $c = a + ib$, where $a$ and $b$ are real $n \times 1$ vectors.

The resulting block matrix system is:
$$\begin{bmatrix} A & -B \\ B & A \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} a \\ b \end{bmatrix}$$ 

## 🚀 Key Features
***GEPP Algorithm**: Implements row swapping (pivoting) to place the largest absolute value on the diagonal, ensuring numerical stability.
**Singularity Handling**: The solver checks for singular or nearly-singular matrices by comparing pivot values to machine precision (`eps`).
***Back Substitution**: Calculates the final solution from the upper triangular matrix.
**Verification**: Includes a test script to compare results with MATLAB's built-in backslash (`\`) operator.

## 📂 Project Structure
*`solve_block_system.m`: The main solver function that manages the block transformation and GEPP algorithm.
*`create_equations.m`: A helper function that separates real and imaginary parts to build the $2n \times 2n$ system.
*`skrypt_testujacy.m`: A testing environment containing various test cases, including random, Hermitian, and ill-conditioned matrices.
* `gepp_raport_syska.pdf`: Detailed documentation, theoretical background, and analysis of results .

## 📊 Performance and Accuracy
Based on the benchmarks provided in the report:
***Accuracy**: The custom solver maintains high precision, with relative errors typically between $10^{-16}$ and $10^{-10}$.
* **Speed**: While numerically accurate, the custom GEPP implementation is significantly slower than MATLAB's built-in functions for large matrices ($n > 100$).

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
