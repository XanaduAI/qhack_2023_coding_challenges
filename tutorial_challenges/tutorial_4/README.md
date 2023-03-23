Welcome to the QHack 2023 tutorial challenges! These challenges are worth no points — they are specifically designed to get your brain active and into the right mindset for the competition. You will also learn about various aspects of PennyLane that are essential to quantum computing, quantum machine learning, and quantum chemistry. Have fun!

### Tutorial \#4 — Product states

Entanglement is a quantum phenomenon that leads to unique statistical properties. We can harness it to do seemingly far-fetched tasks like quantum teleportation! 

Given a multi-qubit *pure* state (i.e., does not need to be described
by a density operator), the presence of entanglement boils down to
whether or not the state is a *product* state. Given a two-qubit state where the qubits are labelled by $A$ and $B$, a general *pure* quantum state can be written as 

$$
\vert \psi \rangle_{AB} = \sum_{i,j} c_{ij} \vert i \rangle_A \otimes \vert j \rangle_B .
$$

$\vert \psi \rangle_{AB}$ is said to be a *product* state for subsystems
$A$ and $B$ if it can be written as a tensor product

$$
\vert \psi \rangle_{AB} = \vert \psi \rangle_A \otimes \vert \psi \rangle_B.
$$

For example, the well-known Bell states cannot be written as product states 
between the two qubits.

Your job is to create a function that can tell whether or not a pure state can 
be written as a product state between a subsystem and its complement (e.g., if 
$A$ is the subsystem, then $B = \bar{A}$, meaning that system $B$ is the set of qubits that are not in $A$).

## Challenge code

In the notebook `product_management.ipynb`, you are given a function called `is_product`. This function will output `"yes"` or `"no"` correspondingly. **You must complete this function.**

Here are some helpful resources:

- [Separable quantum states](https://en.wikipedia.org/wiki/Separable_state)
- [`qml.density_matrix`](https://docs.pennylane.ai/en/stable/code/api/pennylane.density_matrix.html)

### Input 

As input to this problem, you are given:

- `state` (`list(float)`): this defines $\vert \psi \rangle_{AB}$ (pure quantum state in question).
- `subsystem` (`list(int)`): the subsystem that defines the subsystem of qubits $A$ 
  and $B = \bar{A}$. I.e., the two groups of qubits that you will
  determine if a state can be written as a product state.
- `wires` (`list(int)`): the wire labels associated to the qubit state of interest.

### Output

This code must output `"yes"` or `"no"` if the state $\vert \psi
\rangle_{AB}$ is a product state (with respect to $A$ and $B$).

If your solution matches the correct one, the output will be `"Correct!"` Otherwise, you will receive a `"Wrong answer"` prompt.

Good luck!
