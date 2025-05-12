Superdense coding allows two parties, say Alice and Bob, to send two classical bits of information over a very long distance. But Alice is only allowed to send one qubit over to Bob.

Some third party can prepare the maximally entangled bell state $\ket{\psi}=\frac{\ket{00}+\ket{11}}{\sqrt{2}}$, sending one of the qubits to Alice and the other to Bob. 

If she wishes to send the bit string "00" to Bob, she does nothing at all to her qubit. If she wishes to send the string "01", she applies the phase flip $Z$ gate to her qubit. If she wishes to send the string "10", she applies the $NOT$ gate $X$. If she wanted to send the string "11", she applies the $iY$ gate. The states are mapped as follows:
$$
\begin{aligned}
& 00: \ket{\psi} \to \frac{\ket{00}+\ket{11}}{\sqrt{2}} \\
& 01: \ket{\psi} \to \frac{\ket{00}-\ket{11}}{\sqrt{2}} \\
& 10: \ket{\psi} \to \frac{\ket{10}+\ket{01}}{\sqrt{2}} \\
& 11: \ket{\psi} \to \frac{\ket{01}-\ket{10}}{\sqrt{2}} \\
\end{aligned}
$$
These four states are known as the *Bell Basis*, *Bell States*, or *EPR Pairs*. These form an orthonormal basis and can hence be distinguished by quantum measurement. If Alice sends her qubit to Bob, then by doing a measurement [[The Postulates of Quantum Mechanics#^measure-in-basis-note|in the Bell basis]] Bob can determine which of the four possible bit strings Alice sent.

Alice, interacting only with one qubit, can send two classical bits to Bob through using this qubit.

[[Density Operators]]