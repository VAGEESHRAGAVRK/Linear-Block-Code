# Linear Block Code

# Aim
To write a simple Python program to:
- Generate Generator Matrix
- Generate Codeword
- Find Hamming Weight
- Generate Syndrome Matrix
- Detect error in the received codeword using Linear Block Code

---

# Tools Required
- Python 3.x
- NumPy Library
- Jupyter Notebook / VS Code / Google Colab

Install required library:

```bash
pip install numpy
```

---

# Theory

## Linear Block Code
Linear Block Codes are error-detecting and error-correcting codes used in digital communication systems.

A message of length `k` bits is converted into a codeword of length `n` bits using:
- Generator Matrix (G)
- Parity Check Matrix (H)

---

## Hamming Weight
Hamming weight is the number of 1’s present in the codeword.

---

## Syndrome Matrix
The syndrome is calculated using:

\[
S = r \times H^T
\]

Where:
- \(r\) = received codeword
- \(H^T\) = transpose of parity check matrix

If syndrome = 0 → No Error  
Else → Error detected

---

# Program

```python
import numpy as np

# ----------------------------------------
# Generator Matrix (G)
# ----------------------------------------

G = np.array([
    [1, 0, 0, 0, 1, 1, 0],
    [0, 1, 0, 0, 1, 0, 1],
    [0, 0, 1, 0, 0, 1, 1],
    [0, 0, 0, 1, 1, 1, 1]
])

# ----------------------------------------
# Message Bits
# ----------------------------------------

message = np.array([1, 0, 1, 1])

# ----------------------------------------
# Generate Codeword
# ----------------------------------------

codeword = np.dot(message, G) % 2

# ----------------------------------------
# Hamming Weight
# ----------------------------------------

hamming_weight = np.sum(codeword)

# ----------------------------------------
# Parity Check Matrix (H)
# ----------------------------------------

H = np.array([
    [1, 1, 0, 1, 1, 0, 0],
    [1, 0, 1, 1, 0, 1, 0],
    [0, 1, 1, 1, 0, 0, 1]
])

# ----------------------------------------
# Received Codeword with Error
# ----------------------------------------

received = np.array([1, 0, 1, 0, 0, 1, 0])

# ----------------------------------------
# Syndrome Calculation
# ----------------------------------------

syndrome = np.dot(received, H.T) % 2

# ----------------------------------------
# Display Results
# ----------------------------------------

print("Generator Matrix (G):")
print(G)

print("\nMessage Bits:")
print(message)

print("\nGenerated Codeword:")
print(codeword)

print("\nHamming Weight:")
print(hamming_weight)

print("\nParity Check Matrix (H):")
print(H)

print("\nReceived Codeword:")
print(received)

print("\nSyndrome Matrix:")
print(syndrome)

# ----------------------------------------
# Error Detection
# ----------------------------------------

if np.all(syndrome == 0):
    print("\nNo Error in Received Codeword")
else:
    print("\nError Detected in Received Codeword")
```

---

# Output

```text
Generator Matrix (G):
[[1 0 0 0 1 1 0]
 [0 1 0 0 1 0 1]
 [0 0 1 0 0 1 1]
 [0 0 0 1 1 1 1]]

Message Bits:
[1 0 1 1]

Generated Codeword:
[1 0 1 1 0 1 0]

Hamming Weight:
4

Parity Check Matrix (H):
[[1 1 0 1 1 0 0]
 [1 0 1 1 0 1 0]
 [0 1 1 1 0 0 1]]

Received Codeword:
[1 0 1 0 0 1 0]

Syndrome Matrix:
[1 0 1]

Error Detected in Received Codeword
```

---

# Output Waveform / Screenshot

Attach the program output screenshot here.

Example:

<img width="479" height="615" alt="image" src="https://github.com/user-attachments/assets/a62d0956-4cc0-4f09-938f-25a3102a948c" />

---

# Results

Thus, the Generator Matrix, Codeword, Hamming Weight, and Syndrome Matrix were successfully generated using Python. The error present in the received codeword was detected successfully using Linear Block Code.

---

# Applications
- Error Detection
- Error Correction
- Digital Communication
- Data Transmission
- Satellite Communication

---

# Author
R.K. Vageesh Ragav  
B.E. Electronics and Communication Engineering (ECE)  
Saveetha Engineering College
