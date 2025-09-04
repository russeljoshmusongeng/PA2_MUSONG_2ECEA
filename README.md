#### PA2_MUSONG_2ECEA

#### Problem 1 — Normalization

Goal: Generate a random 5×5 array, compute mean and standard deviation, then normalize.

````
import numpy as np

# Optional: fix randomness for reproducible results in demos/regrading
# np.random.seed(0)

# Create random 5x5 ndarray
X = np.random.rand(5, 5)                 # values in [0, 1)

# Compute mean and standard deviation (population)
mean = X.mean()
std = X.std()

# Normalize: Z = (X - mean) / std
X_normalized = (X - mean) / std

# Save artifact (NO SPACE in filename)
np.save("X_normalized.npy", X_normalized)

# (Optional) Display results
print("Original X:\n", X)
print("\nMean:", mean, "  Std:", std)
print("\nNormalized X:\n", X_normalized)
````
Line-by-line (quick)

np.random.rand(5, 5) → 5×5 matrix of floats in [0, 1).

.mean() / .std() → scalar mean and population std of all 25 elements.

(X - mean) / std → centers at 0 and scales so spread is roughly 1.

np.save("X_normalized.npy", X_normalized) → writes a binary .npy array file.

Use X_normalized.npy.

#### Problem 2 — Divisible by 3

Goal: Build a 10×10 matrix of squares of 1..100, then filter numbers divisible by 3.

```
import numpy as np

# Create squares of 1..100, then reshape to 10x10
A = np.arange(1, 101) ** 2
A = A.reshape(10, 10)

# Boolean mask for divisibility by 3
div_by_3 = A[A % 3 == 0]

# Save artifact
np.save("div_by_3.npy", div_by_3)

# (Optional) Display results
print("\nA (10x10 squares):\n", A)
print("\nValues divisible by 3:\n", div_by_3)
````
#### How does it work?

np.arange(1, 101) → array [1, 2, ..., 100].

** 2 → elementwise squares → [1, 4, 9, ..., 10000].

.reshape(10, 10) → turns 1D → 2D matrix (10 rows × 10 cols).

A % 3 == 0 → boolean mask for divisibility by 3.

A[mask] → filters only elements where mask is True.

np.save("div_by_3.npy", div_by_3) → saves the filtered 1D array.

#### Output Artifacts to Submit

X_normalized.npy – normalized 5×5 array (float64 by default)

div_by_3.npy – 1D array of all squared numbers (from 1..100) divisible by 3
