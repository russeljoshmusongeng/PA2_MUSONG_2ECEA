#### PA2_MUSONG_2ECEA

#### Problem 1 — Normalization

Goal: Generate a random 5×5 array, compute mean and standard deviation, then normalize.

````
# Library to open mathematical and logical functions
import numpy as np

# Create random 5x5 ndarray
X = np.random.rand(5, 5)       

# Compute mean and standard deviation (population)
mean = X.mean()
std = X.std()

# Normalize: Z = (X - mean) / std
X_normalized = (X - mean) / std

# Save file
np.save("X_normalized.npy", X_normalized)

# (Optional) Display results
print("Original X:\n", X)
print("\nNormalized X:\n", X_normalized)
````
### How does it work?

np.random.rand(5, 5)
This makes a 5×5 table (matrix) filled with random numbers between 0 and 1.
Example: 0.23, 0.78, etc.

.mean() and .std()

Mean: the “average” of all 25 numbers.

Standard deviation (std): tells how “spread out” the numbers are around the average.

(X - mean) / std

First, subtract the average from every number. This makes the data “centered” at 0.

Then, divide by the standard deviation so the values aren’t too spread out or too squished.
Result: a new version of the table where the average = 0 and the “spread” = about 1.

np.save("X_normalized.npy", X_normalized)
Finally, it saves the normalized table into a file named X_normalized.npy so you can load it later without recomputing.

 In short: You make a random 5×5 table → find its average and spread → adjust the numbers so they’re centered at 0 with a spread of 1 → save the result into a file.

#### Problem 2 — Divisible by 3

Goal: Build a 10×10 matrix of squares of 1..100, then filter numbers divisible by 3.

```
# Library to open mathematical and logical functions
import numpy as np

# Create squares of 1..100, then reshape to 10x10
A = np.arange(1, 101) ** 2
A = A.reshape(10, 10)

# Boolean mask for divisibility by 3
div_by_3 = A[A % 3 == 0]

# Save artifact
np.save("div_by_3.npy", div_by_3)

# (Optional) Display results
print("\n", A)
print("\nValues divisible by 3:\n", div_by_3)
````
### How does it work?

np.arange(1, 101)
Think of this like writing numbers from 1 up to 100 in a straight line.

** 2 (squaring)
Each number is then squared (multiplied by itself).
Example: 2 → 4, 3 → 9, …, 100 → 10,000.
So now you’ve got 100 squared numbers in a row.

.reshape(10, 10)
Instead of keeping them in one long line, we arrange them into a table with 10 rows and 10 columns.
Imagine turning a list into a neat 10×10 grid.

A % 3 == 0
This checks which numbers in the grid can be divided evenly by 3.
It creates a map of “True” (yes, divisible) and “False” (no, not divisible).

A[mask]
Using that map, we pick out only the numbers that are divisible by 3.
The result is just a smaller list of those “good” numbers.

np.save("div_by_3.npy", div_by_3)
Finally, we save this smaller list into a file called div_by_3.npy so it can be loaded again later.

In short:
You make numbers 1–100 → square them → arrange into a 10×10 grid → select only the multiples of 3 → save them in a file.


#### Outputs

X_normalized.npy – normalized 5×5 array

div_by_3.npy – 1D array of all squared numbers (from 1..100) divisible by 3

For more details, refer to the file codes, thank you!
