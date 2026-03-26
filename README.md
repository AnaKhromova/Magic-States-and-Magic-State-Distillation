<font face="Arial" size="4" color="black">
  
# Magic States in Universal Quantum Computer with QuTiP

In a quantum computer, quantum gates can be classified into two categories: *Clifford gates* and *non-Clifford gates*. It separates the gates that are physically easy to implement and simulate classically from those that are physically hard and require the power of quantum mechanics to solve problems efficiently.
What are the Clifford Gates? They are the elements of the Clifford group, a set of mathematical transformations that normalize the n-qubit Pauli group, i.e., map tensor products of Pauli matrices to tensor products of Pauli matrices through conjugation.

If U is a Clifford gate, the conjugation operation

<div align="center">
  <img src="formula/conjunction_operation.png">
</div>

where P is a Pauli operator, like X, Y, or Z, always yields another Pauli operator:

<div align="center">
  <img src="formula/Pauli_operations.png">
</div>

The three fundamental Clifford gates are the Hadamard (H), Phase (S), and CNOT gates:

<div align="center">
  <img src="formula/Clifford_gates.png">
</div>

For example, H is a member of a Clifford group because:

<div align="center">
  <img src="formula/Clifford_group.png">
</div>

Quantum circuits that consist of only Clifford gates can be efficiently simulated with a classical computer due to the Gottesman–Knill theorem, so they are not a universal set of quantum gates.

> Any circuit composed of CNOT, Hadamard, and phase gates can be efficiently simulated on a classical computer even though such circuits can generate huge amounts of entanglement, and can be used for superdense coding, quantum teleportation, the GHZ paradox, quantum error-correcting codes, etc.
- Gottesmann-Knill Theorem, Scott Aaronson Lectures, 008, https://ocw.mit.edu/courses/6-845-quantum-complexity-theory-fall-2010/b50fa65352113b1368ac6e81379c913b_MIT6_845F10_lec23.pdf
