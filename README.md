# Radial Basis Function Collocation Method with Ghost Points

This project demonstrates the use of the ghost-point-based radial basis function (RBF) collocation method to solve a Poisson problem in a Cassini domain. The implementation uses Python and includes numerical solution evaluation and visualization.

## Problem Description

We aim to solve the Poisson problem:

\[
\mathcal{L} u(x, y) = f(x, y), \quad (x, y) \in \Omega,
\]
\[
u(x, y) = g(x, y), \quad (x, y) \in \partial\Omega,
\]

where:

- \(\mathcal{L}\) is the Laplacian operator.
- \(f(x, y)\) is the source term.
- \(g(x, y)\) is the boundary condition.
- \(\Omega\) is the Cassini domain.

The exact solution used for validation is:
\[
u(x, y) = e^{x + y}.
\]

## Methodology

### Key Features:

1. **Radial Basis Function (RBF):**

   - Multiquadric RBF: \( \phi(r) = \sqrt{1 + (c \cdot r)^2} \), where \(r = ||\mathbf{x} - \mathbf{x}_j||\) and \(c\) is the shape parameter.
2. **Ghost Points:**

   - Additional points distributed outside the domain to improve accuracy, especially near the boundaries.
3. **Point Distribution:**

   - Boundary points.
   - Interior points within the Cassini domain.
   - Ghost points distributed in a circular region around the domain.
4. **Error Evaluation:**

   - The absolute error is computed as:
     \[
     \text{Error}(x, y) = |u_{\text{exact}}(x, y) - u_{\text{computed}}(x, y)|.
     \]

### Steps:

1. Define the Cassini domain using its parametric equation.
2. Generate boundary, interior, and ghost points.
3. Construct the RBF collocation matrix.
4. Solve the system of equations to compute RBF coefficients.
5. Evaluate the solution and calculate errors at test points.
6. Visualize the results, including the exact solution and error distribution.

## Dependencies

Dependencies:

- `numpy`: For numerical computations.
- `matplotlib`: For plotting results.
- `scipy`: For constructing distance matrices and solving linear systems.

## Results

- **Exact Solution:** Visualizes the analytical solution \(u(x, y)\) over the Cassini domain.
- **Error Distribution:** Highlights the regions with higher numerical errors, often near boundaries.
- **Maximum Absolute Error:** A quantitative metric of solution accuracy.

## Example Output

### Plots:

1. **Exact Solution:**
   <img width="373" alt="Screenshot 2025-01-16 at 8 11 13 PM" src="https://github.com/user-attachments/assets/4e73d7c4-6396-43cb-8f61-597be633041c" />

2. **Error Distribution:**
 <img width="362" alt="Screenshot 2025-01-16 at 8 11 21 PM" src="https://github.com/user-attachments/assets/394f198c-51f2-4402-8f8a-1f7b788bc42a" />


### Numerical Values:

- Maximum Absolute Error: ~10.15 (depending on parameters).

## Future Improvements

- Optimize the choice of the shape parameter \(c\).
- Experiment with different ghost point distributions.
- Extend the implementation to solve higher-order PDEs.

## License

This project is licensed under the MIT License. See `LICENSE` for details.

## Acknowledgments

- Reference: **"Ghost-point based radial basis function collocation methods with variable shape parameters"** by Shin-Ruei Lin, D.L. Young, Chuin-Shan Chen. [Read the paper here](https://www.sciencedirect.com/science/article/pii/S0955799721001284#sec0002).
