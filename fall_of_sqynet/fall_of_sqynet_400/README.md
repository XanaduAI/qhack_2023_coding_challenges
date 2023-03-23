### Backstory

With the resources available to them, Zenda and Reece decide that one single method is not enough to interfere with the correct functioning of Sqynet, since it can repair itself too quickly. It's time to resort to brute force methods. By firing missiles at the outer shell, they will introduce a considerable amount of depolarizing noise into Sqynet's hardware.  

### Trotterization of the Heisenberg model

An approximate way to model Sqynet is by considering it as a closed spin chain of length $N$. A spin chain contains particles of spin $1/2$ in each of its $N$ sites. We make this model more realistic by assuming that the spins may be pointing in any direction, and we consider that there may be an external magnetic field acting on the system.

When we model a closed spin chain of length $N$ in which spins can point in any direction, we need to use the Heisenberg Hamiltonian. 
In the presence of an external magnetic field of intensity $h$, the Hamiltonian is given by

$$ 
H = -\sum_{i=1}^{N}\left(J_x X_{i}\otimes X_{i+1}+J_y Y_{i}\otimes Y_{i+1}+J_z Z_{i}\otimes Z_{i+1}\right) - h\sum_{i=1}^N X_{i}.
$$

The subindices $i$ indicate the spin site where the operators act. In a closed spin chain, we identify site $N+1$ with the first site. The coefficients $J_x$, $J_y$ and $J_z$ are known as *coupling constants* and they measure the strength of the interaction between neighbouring spins. 

Sqynet's correct functioning relies on it being completely isolated from the environment, to avoid decoherence. Zenda and Reece think that, to tamper with Sqynet's correct functioning, the old way is the best way, so they'll shoot missiles at the tail of the spaceship, where the quantum device is. This will introduce noise into the gates that Sqynet executes. 

Zenda and Reece need to estimate how the noise affects Hamiltonian evolution. Your task is to build a Trotterization circuit that simulates $U=\exp{(-iHt)}$. This circuit must only contain $RX$, $RY$, $RZ$, and $CNOT$ gates. The missiles will introduce noise on the target qubit of every execution of a CNOT gate. We model this via a **Depolarizing Channel** with parameter $p$. To quantify the effects of noise, you are asked to find the fidelity between this noisy Trotterization and the noiseless one. 

## Challenge code

You must complete the `heisenberg_trotter` that implements the Trotterization of the Heisenberg Hamiltonian for $N=4$ using only the following PennyLane gates: `qml.RX` `qml.RY`, `qml.RZ`, `qml.CNOT`, and `qml.DepolarizingChannel`. This function will return a quantum state. You should also minimize the number of CNOT gates as much as you can, in order to avoid noise. To verify that the that the Trotterization that you proposed is not excessively noisy, we will calculate for you the fidelity of your output state with respect to the noiseless case using the `calculate_fidelity` function.

### Input

As input to this problem, you are given:

- `couplings` (`list(float)`): An array of length 4 that contains the coupling constants and the magnetic field strength, in the order $[J_x, J_y, J_z, h]$.
- `p` (`float`): The depolarization probability on the target qubit after each CNOT gate.
- `depth` (`int`): The Trotterization depth.
- `time` (`float`): Time during which the state evolves.
 
### Output

This code will output a `float` corresponding to the fidelity between the output states of the noisy and noiseless trotterizations, calculated from the output of `heisenberg_trotter.` The outputs in the test cases correspond to the minimal fidelity that you should achieve if you used a small enough amount of CNOT gates.

If your fidelity is larger, up to a tolerance of 0.005, of that specified in the output cases, your solution will be judged as `"Correct!"` Otherwise, you will receive a `"Wrong answer"` prompt.

Good luck!
