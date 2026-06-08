# Eigen-spy: eigenvectors and eigenvalues

Spy on your matrices, detect eigenvectors and visualize eigenvalue transformations in Python. 🥇

This is a Python implementation that checks whether a vector is an eigenvector of a matrix, computes the corresponding eigenvalue, and visualizes the result.

Built for learners who want to see the math come alive in code.

## Concept

When you multiply a matrix **A** by a special vector **v**, the result is the same vector scaled by a number λ (the eigenvalue):

$$Av = \lambda v$$

An eigenvector only stretches or shrinks — it never rotates. The eigenvalue tells you by how much.

## Features

- Check if a given vector is an eigenvector of a matrix
- Compute the corresponding eigenvalue λ
- Plot the original vector and its transformed version side by side

## Requirements

```
numpy
matplotlib
```

Install with:

```bash
pip install numpy matplotlib
```

## Usage

Open `Eigenvectors-Eigenvalues.ipynb` in Jupyter and run the cells, or use the `Value` class directly:

```python
import numpy as np
from your_module import Value

# Define a matrix and a vector
A = Value(np.array([[1, 2], [2, 1]]))   # matrix
v = Value(np.array([[3], [3]]))          # vector

# Check if v is an eigenvector of A
is_eigen, eigenvalue = v.is_eigenvector(A)
print(is_eigen, eigenvalue)  # True, eigenvalue is 3.0

# Plot the original vector and its transformation
v.plot_vectors(A)
```

## Class: `Value`

| Method | Description |
|---|---|
| `transform_vector(matrix)` | Computes `A @ v` and returns the result as a `Value` |
| `is_eigenvector(matrix, tol=1e-6)` | Returns `(True, "eigenvalue is λ")` if the vector is an eigenvector, otherwise `(False, None)` |
| `plot_vectors(matrix)` | Plots the original vector and transformed vector; annotates eigenvalue if one exists |

## How It Works

The eigenvector check works by computing the ratio `(A @ v) / v` for each non-zero component. If all ratios are equal (within tolerance), the vector is an eigenvector and that ratio is the eigenvalue λ.

## Example Output

The plot shows:
- **Orange arrow** — the original vector `v`
- **Blue arrow** — the transformed vector `Av`

If `v` is an eigenvector, the two arrows point in the same direction and the eigenvalue λ is annotated on the plot.
