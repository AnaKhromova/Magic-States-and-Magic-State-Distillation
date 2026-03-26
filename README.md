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

> Any circuit composed of CNOT, Hadamard, and phase gates can be efficiently simulated on a classical computer, even though such circuits can generate huge amounts of entanglement, and can be used for superdense coding, quantum teleportation, the GHZ paradox, quantum error-correcting codes, etc. - Gottesmann-Knill Theorem, Scott Aaronson Lectures, 008, https://ocw.mit.edu/courses/6-845-quantum-complexity-theory-fall-2010/b50fa65352113b1368ac6e81379c913b_MIT6_845F10_lec23.pdf

To perform arbitrary quantum computations, you need non-Clifford gates. The most common example is a T-gate (π/8 gate or a 45-degree rotation):

<div align="center">
  <img src="formula/T_gate_matrix.png">
</div>

Adding T to the Clifford group gives a universal set of {H, S, CNOT, T}.
To perform arbitrary, useful quantum algorithms, a quantum computer needs a universal gate set. Most error-correcting codes easily support Clifford gates, but they do not support non-Clifford gates like the T-gate mentioned above, which is necessary for the universal quantum computer. As a solution, non-Clifford gates can be teleported into a circuit using a specifically prepared, non-stabilizer state, a magic state. These states are called magical because they are not stabilizer states and cannot be efficiently created by Clifford circuits alone.

## Stabilizer states
Stabilizer states, known also as Clifford states, are a class of quantum states defined as the +1 eigenstates of a commutative subgroup S (the stabilizer group) of the n-qubit Pauli group (Gₙ), where -I ∉ S and |S|=2ⁿ. Any such state can be reached by applying Clifford group operations (H, S, CNOT) to the initial state

<div align="center">
  <img src="formula/initial_state.png">
</div>

This stabilizer formalism provides a highly efficient way to represent and simulate these states classically, as proven by the Gottesman-Knill theorem.
The Pauli group on one qubit, G₁, is the set of operators {±I, −pm iI, ±X, ± iX, ±Y, ± iY, ±Z, ± iZ} under matrix multiplication, where

<div align="center">
  <img src="formula/Pauli_operations.png">
</div>


<div align="center">
  <img src="formula/Pauli_group_operations.png">
</div>

The stabilizers of a state form the stabilizer group S, which is an abelian subgroup of the n-qubit Pauli group Gₙ. Conversely, any abelian subgroup of Gₙ that does not contain -I uniquely defines a stabilizer state. We explicitly exclude -I  from the stabilizer group because if -I were a stabilizer, the only solution to the eigenvalue equation −I |ψ⟩ = |ψ⟩ would be the zero vector, which is not a valid physical state.

In a single-qubit system, stabilizer states correspond to the six vertices of an octahedron inscribed within the Bloch sphere. These are the eigenstates of the Pauli matrices: |0⟩ and |1⟩ (poles, Z-axis), |+⟩ and |−⟩ (X-axis) and |+i⟩ and |−i⟩ (Y-axis). While a general quantum state can exist anywhere on the sphere's surface, Clifford group operations act as rotational symmetries of this octahedron, moving states only between these six cardinal positions. Applying Clifford gates to a stabilizer state results in a discrete walk between these vertices (six points on the sphere), never landing on the points in between.
