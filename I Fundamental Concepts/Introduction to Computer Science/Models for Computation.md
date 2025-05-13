
Hilbert asked whether or not there was an algorithm which could be used, in principle, to solve all mathematical problems. Hilbert expected the answer to this problem, sometimes known as the *entscheidungsproblem*, would be yes. 

However, Alonzo Church and Alan Turing proved that the answer would be no, and in the process introducing the fundamental notions of the modern theory of algorithms, and thus of computation. They laid the foundations of computer science.

We consider two very different models of computation. The first the Turing machine, the second the *circuit model* of computation. Although these seem to be different on the surface, they are actually equivalent. Some models of computation may yield different insights into the same problem, which is why we introduce two of them. Two ways of thinking about a problem is better than one.

## Turing Machines

>[!definition] Turing Machines
>A Turing machine contains four main elements:
>- A *program*, similar to those in an ordinary computer.
>- A *finite state control*, which acts like a stripped down microprocessor, coordinating the other operations of the machine.
>- A *tape*, essentially acting as the memory of the machine.
>- A *read-write tape-head*, which points to the position on the tape that is currently readable or writable. 
>
>This structure is shown below:
>
>![[Pasted image 20250512204301.png|center|500]]
>^turing-machine-definition

The *finite state control* for a Turing machine consists of a finite set of *internal states*, $q_1, \ldots, q_m$. The number $m$ is allowed to be varied, and in fact for sufficiently large values, the size of $m$ does not affect the power of the machine in any essential way, so without loss of generality we can assume $m$ to be a fixed constant.

The best way to think of the finite state control is as a microprocessor, coordinating the Turing machine's operation. It provides temporary storage off-tape, and a central place where all the processing takes place. 

In addition to the states $q_1, \ldots q_m$, there are also two special marked states, labelled $q_s$ and $q_h$, for the *starting state* and *halting state*, respectively. The idea is that at the beginning of computation, the Turing machine is in its starting state $q_s$, and computation changes the internal state. If the computation ever finishes, the Turing machine ends up in the state $q_h$ to indicate that it has finished computation.

The Turing machine *tape* is a one-dimensional object, which stretches off into infinity in *one direction*. The tape consists of an infinite sequence of *tape squares*. We number the tape squares $0, 1, 2, \ldots$. The tape squares contain one symbol drawn from some *alphabet*, $\Gamma$, which contains a finite amount of distinct symbols. For now, we assume the alphabet contains four symbols, $0, 1, b$ (the blank symbol), and $\rhd$, to mark the left hand edge of the tape. Initially, the tape contains a $\rhd$ on the left end, a finite number of $0$s and $1$s, and the rest of the tape contains blanks. The *read-write tape-head* identifies a single square on the Turing machine tape as the square that is currently being accessed by the machine.


