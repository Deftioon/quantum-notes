
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

>[!definition] Program
>A *program* for a Turing machine is a finite ordered list of *program lines* of the form $\langle q, x, q', x', s \rangle$. The first item, $q$ is a state of the internal states of the machine. The second, $x$, is taken from the alphabet of symbols which may appear on the tape, namely $\Gamma$.
>
>On every machine cycle, the Turing machine looks through the list of program lines in order, searching for a line $\langle q, x, \cdot, \cdot, \cdot \rangle$ such that the current state of the machine is $q$, and the symbol being read on the tape is $x$. If it doesn't find such a program line, then the state is set to the halting state $q_h$, and the machine halts operation. If such a line is found, then the line is *executed*.
>
>The execution is as follows:
>- The internal state of the machine is changed to $q'$.
>- The symbol $x$ on the tape is overwritten by the symbol $x'$.
>- The tape-head moves left, right, or stands still, depending on $s$:
>	- If $s = -1$, then it moves *left*.
>	- If $s = 0$, then it *stands still*.
>	- If $s = 1$, then it moves *right*.
>- The only exception to this rule is if the tape-head is at the left-most square, or if $x = \rhd$, and $s = -1$, in which case the tape-head stays put.
>^turing-program-definition

Now we can consider real Turing machines. Consider the following Turing machine:

>[!example]
>Consider the following Turing machine:
>- The machine starts with a binary number $x$ on the tape, followed by blanks, $b$.
>- The machine has three internal states, $q_1$, $q_2$, and $q_3$, in addition to the starting state $q_s$ and halting state $q_h$.
>- The program contains the following lines: 
>$$
>\begin{aligned}
>1: & \langle q_s, \rhd, q_1, \rhd, +1 \rangle \\
>2: & \langle q_1, 0, q_1, b, +1 \rangle \\
>3: & \langle q_1, 1, q_1, b, +1 \rangle \\
>4: & \langle q_1, b, q_2, b, -1 \rangle \\
>5: & \langle q_2, b, q_2, b, -1\rangle \\
>6: & \langle q_2, \rhd, q_3, \rhd, +1 \rangle \\
>7: & \langle q_3, b, q_h, 1, 0\rangle \\
>\end{aligned}
>$$
>
>Let's break this Turing machine down. 
>- Line 1 tells the Turing machine to move to the first square in the tape and change the state from the starting state $q_s$ to $q_1$. 
>- Lines 2 and 3 tell the Turing machine whenever it sees a non-blank square, to make it blank and move right. After some thought, this clears the entire tape. This keeps the state in $q_1$
>- Line 4 tells the Turing machine that if it is reading a blank, $b$, and it is in state $q_1$, that is, it is in "clearing squares mode", then transition to state $q_2$, and move to the left.
>- Line 5 tells the Turing machine that if we are in state $q_2$, then we keep moving left.
>- Line 6 tells the Turing machine to stop moving left when we hit the beginning of the tape, $\rhd$, and to move right. We transition to $q_3$ here, indicating that we have hit the end of the tape, or that we have come back to the beginning.
>- Line 7 tells the Turing machine that if we are reading a blank and are in $q_3$, then write $1$ on the tape, and halt. 
>Hence, this program first takes in a binary number $x$ as input on the tape, clears the tape, returns to the beginning, and prints $1$ on the tape. Hence, this Turing machine computes the constant function $f(x) = 1$. 

A natural question to then ask is: "What kinds of functions are computable on a Turing machine?" And the answer is all functions that are computable by an algorithm! This is known as the *Church-Turing Thesis*:

>[!theorem] The Church-Turing Thesis
>The class of functions computable by a Turing machine corresponds directly to the class of functions which we would naturally agree regard as being computable by an algortihm.
>^church-turing-thesis

The thesis asserts an equivalence between a rigorous, mathematical formalism and a loose, fuzzy concept of "computable by an algorithm". This thesis derives its importance from being able to study real world algorithms in a rigorous mathematical manner. 

>[!done] How might we recognize that a process in nature computes a function not computable by a Turing machine?
>We proceed by a proof by contradiction. We first assume that indeed, there exists a way to recognize a natural process is computable by Turing machine. By the Church-Turing Thesis, this algorithm must be computable by a Turing machine. 
>
>We denote this algorithm by the Turing machine $\mathcal{C(p)}$ for some program $p$, which outputs $1$ if it is computable by Turing machine, and $0$ if not.
>
>Then, we construct a physical process $P_{T, x}$ for a Turing machine $T$ and an input $x$. We define $P_{T, x}$ as follows:
>```py
>if the machine T with input x halts:
>	enter an infinite loop
>else:
>	halt and return 0
> ```
> We then run $P_{T, x}$ on itself. If this compounded machine returns $0$, then $P_{T, x}$




