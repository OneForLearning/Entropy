# Entropy

## Overview

**Entropy** is a research-oriented Python project that explores the relationship between **decryption execution time** and the **number of encrypted bits** through polynomial modeling.

For cryptographic implementations that are **not constant-time**, execution time may leak information about secret values. Such timing variations can be exploited through **side-channel attacks**.

This project provides a simple mathematical model based on **quadratic polynomial regression** to approximate the dependency between these two variables and to study the resulting entropy.

---

## Motivation

Many cryptographic algorithms are vulnerable to timing attacks when their execution time depends on secret data.

Typical attack scenarios include:

* Timing attacks
* Side-channel analysis
* Leakage assessment
* Cryptographic implementation evaluation

The objective of this project is to build a mathematical approximation of the function:

```
(Number of encrypted bits)  --->  (Decryption time)
```

and to analyze whether observable timing information could reveal useful information about the underlying cryptographic process.

---

## Mathematical Model

Given a set of experimental observations:

* `X`: Number of encrypted bits
* `Y`: Measured decryption time

the project computes a quadratic polynomial:

[
y = ax^2 + bx + c
]

using least-squares polynomial regression.

The polynomial coefficients are estimated with:

```python
numpy.polyfit(X, Y, 2)
```

This model can then be used to approximate the behavior of the measured system.

---

## Project Structure

```
Entropy/
│
├── README.md
└── RefressionQuadratique.py
```

### RefressionQuadratique.py

This script:

1. Defines the experimental dataset.
2. Performs a second-order polynomial regression.
3. Computes the polynomial coefficients.
4. Displays the resulting mathematical expression.

Example:

```python
X_i = np.array([4, 12, 13, 14, 14])
Y_i = np.array([250, 320, 250, 380, 260])

coefficients = np.polyfit(X_i, Y_i, 2)
```

---

## Requirements

* Python 3.9+
* NumPy

Installation:

```bash
pip install numpy
```

---

## Usage

Run the script:

```bash
python RefressionQuadratique.py
```

Example output:

```
Polynomial expression:
y = ax² + bx + c
```

where `a`, `b`, and `c` are computed from the experimental dataset.

---

## Research Applications

This project may serve as a foundation for research in:

* Cryptographic side-channel analysis
* Timing attacks
* Information leakage quantification
* Entropy modeling
* Post-quantum cryptography implementation analysis
* Secure software engineering

---

## Possible Extensions

Future improvements could include:

* Data visualization with Matplotlib
* Higher-order polynomial models
* Entropy computation metrics
* Statistical confidence intervals
* Machine learning regression models
* Real-world cryptographic benchmark datasets
* Comparison between constant-time and non-constant-time implementations

---

## Academic Context

This repository is intended for educational and research purposes. It provides a simple mathematical framework for studying timing behavior in cryptographic systems and evaluating potential side-channel leakage.

---

## License

This project is intended for academic and research use.
Please cite the repository if it contributes to your work.
