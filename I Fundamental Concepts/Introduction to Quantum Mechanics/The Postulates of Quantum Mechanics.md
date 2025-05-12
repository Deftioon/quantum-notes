Quantum Mechanics is a mathematical framework for the development of physical theories. On its own it does not tell you what laws a physical system must obey, but it provides a mathematical and conceptual framework for the development of these laws. The postulates of Quantum Mechanics provide a connection between the physical world and the mathematical formulation of Quantum Mechanics. 

The postulates were derived after a long process of trial and error, which involved a considerable amount of guessing and fumbling by the originators of the theory. 

## State Space

The first postulate of quantum mechanics sets up the arena in which quantum mechanics takes place. The arena is our familiar friend from linear algebra, Hilbert space.

>[!note] Postulate 1
>Associated to any isolated physical system is a complex vector space with inner product (that is, a Hilbert Space) known as the *state space* of the system. The system is completely described by its *state vector*, which is a unit vector in the system's state space.
>^postulate-1

The simplest quantum mechanical system, and the system which we will be most concerned with, is the *qubit*. A qubit has a two-dimensional state space. Suppose $\ket{0}$ and $\ket{1}$ form an orthonormal basis for this state space. Then an arbitrary vector in the state space can be written $$\ket{\psi}=a\ket{0}+b\ket{1}$$ where $a$ and $b$ are complex numbers. The condition that $\ket{\psi}$ be a a unit vector, or $\langle \psi \vert \psi \rangle = 1$ is therefore $|a|^2 + |b|^2 = 1$. This condition is known as the normalization condition for state vectors. 

Intuitively, the states $\ket{0}$ and $\ket{1}$ are analogous to the two values a classical  bit can take, $1$ and $0$. The way a qubit differs from a bit is that *superpositions* of these two states of the form $a\ket{0} + b\ket{1}$ can also exist, in which it is not possible to say that the qubit is definitely in one state or another, it is in a superposition of both states.

We say that any linear combination $\sum_i \alpha_i \ket{\psi_i}$ is a superposition of the states $\ket{\psi_i}$ with amplitude $\alpha_i$ for the state $\ket{\psi_i}$. 


## Evolution

The second postulate describes how a state changes over time.

>[!note] Postulate 2
>The evolution of a closed quantum system is described by a unitary transformation. That is, the state $\ket{\psi}$ of the system at time $t_1$ is related to the state $\ket{\psi'}$ of the system at time $t_2$ by a unitary operator which depends only on the times $t_1$ and $t_2$, $$\ket{\psi'} = U\ket{\psi}$$
>^postulate-2

Similar to how the first postulate does not tell us exactly what state space or quantum state of a particular quantum system, the second postulate does not tell us which unitary operators $U$ describe real-world quantum dynamics. It merely ensures that the evolution of any closed system is described in such a way. 

**In the case of single qubits, it turns out that any unitary operator at call can be realized in realistic systems.**

For example, the Pauli Matrices are very useful unitary operators. The $X$ matrix is often known as the quantum $NOT$ gate, as it flips $\ket{0}$ to $\ket{1}$ and $\ket{1}$ to $\ket{0}$. This is also why it is known as the bit flip. The $Z$ matrix is unconventionally known as the phase flip, the $Z$ matrix leaves $\ket{0}$ invariant and takes $\ket{1}$ to $-\ket{1}$, with the factor of $-1$ known as the phase factor. 

Another interesting unitary operator is the Hadamard gate, denoted as $H$. This has the action $$\begin{aligned} H\ket{0} &\equiv \frac{1}{\sqrt{2}}\left(\ket{0} + \ket{1}\right) \\ H\ket{1} &\equiv \frac{1}{\sqrt{2}}\left(\ket{0} - \ket{1}\right)\end{aligned}$$
Which results in the following matrix representation: $$H = \frac{1}{\sqrt{2}}\begin{bmatrix}1 & 1 \\ 1& -1\end{bmatrix}$$
Postulate 2 requires the system being described to be closed. That is, it is not interacting in any way with other systems. In reality, of course, all systems interact at least somewhat with other systems. Nevertheless, there are interesting systems that can be described to a good approximation as being closed, and which are described by a unitary transformation to some good approximation.

In principle, every open system can be described to be part of a closed system which is undergoing unitary transformation.

Postulate 2 describes how the quantum states of a closed quantum system at two different times are related. This can be refined into continuous time, given by the Schrödinger Equation.

>[!note] Postulate 2, REFINED!
>The time evolution of a state of a closed quantum system is described by the Schrödinger Equation, $$i \hbar \frac{\text{d}\ket{\psi}}{\text{d}t} = H\ket{\psi}$$
>In this equation, $\hbar$ is the Planck's constant. The value is not important, so it is common to absorb the factor $\hbar$ into $H$, effectively setting $\hbar = 1$. $H$ is a fixed Hermitian operator known as the Hamiltonian of the closed system.
>^schrodinger-equation

If we know the Hamiltonian of a system and the Planck's constant, then we understand its dynamics completely, at least in principle. Figuring out the Hamiltonian is a very difficult problem, much of twentieth century physics has been concerned with this problem. 

Because the Hamiltonian is a Hermitian operator it has a spectral decomposition: $$H = \sum_E E \ket{E}\bra{E}$$with eigenvalues $E$ and the corresponding normalized eigenvectors $\ket{E}$. The states $\ket{E}$ are conventionally known as the energy eigenstates, or sometimes as stationary states, and $E$ is the energy of state $\ket{E}$. The lowest energy is known as the ground state energy of the system, and the corresponding energy eigenstate (or eigenspace) is known as the ground state. 

The reason the states $\ket{E}$ are known as the stationary states is because their change in time is only to get an overall numerical factor, $$\ket{E}\to e^{-\tfrac{iEt}{\hbar}}\ket{E}$$For example, suppose a single qubit has a Hamiltonian $H=  \hbar \omega X$ where $\omega$ needs to be experimentally determined. The energy eigenstates of this Hamiltonian are obviously the same as the eigenstates of $X$, with corresponding energies $\hbar \omega$ and $-\hbar \omega$ corresponding to the eigenvalues $1$ and $-1$.

Postulate 2 can be easily verified from the Schrödinger Equation: 
$$
\ket{\psi(t_2)} = \operatorname{exp}\left(\frac{-iH(t_2-t_1)}{\hbar}\right)\ket{\psi(t_1)} = U(t_1, t_2)\ket{t_1}
$$
where we define $$U(t_1, t_2) = \operatorname{exp}\left(\frac{-iH(t_2-t_1)}{\hbar}\right)$$
This operator is unitary, and furthermore, that any unitary operator can be realized in the form of $U = \operatorname{exp}(iK)$ for some Hermitian operator $K$. There is therefore a one-to-one correspondence between the discrete-time description with unitary operators  and the continuous time description with the Hamiltonian. 

>[!proof] Suppose $A$ and $B$ are commuting Hermitian operators. Prove that $\operatorname{exp}(A)\operatorname{exp}(B)=\operatorname{exp}(A+B)$
>
>As in the proof of [[Linear Algebra#^80eb10|Simultaneous Diagonalization]], as $A$ and $B$ are commuting Hermitian operators, they both can be written as a diagonalization with respect to the same orthonormal eigenvectors, as in $A = \sum_i a_i\ket{i}\bra{i}$ and $B = \sum_i b_i\ket{i}\bra{i}$ . Hence,
>$$
>\begin{aligned}
>\operatorname{exp}(A)\operatorname{exp}(B) &= \operatorname{exp}\left(\sum_i a_i\ket{i}\bra{i}\right)\operatorname{exp}\left(\sum_j b_j\ket{j}\bra{j}\right) \\
>&= \left(\sum_i e^{a_i}\ket{i}\bra{i}\right) \left(\sum_j e^{b_j}\ket{j}\bra{j}\right) \\
>&= \sum_i \sum_j e^{a_i + b_j} \ket{i} \overbrace{\bra{i}\ket{j}}^{\delta_{ij}} \bra{j} \\
>&= \sum_i e^{a_i + b_i} \ket{i}\bra{i} \\
>&= \operatorname{exp}(A + B)
>\end{aligned}
>$$

>[!proof] $U(t_1, t_2)$ is unitary.
> We want to prove $\operatorname{exp}\left(\frac{-iH(t_2-t_1)}{\hbar}\right)$ is unitary. We will compute the adjoint first:
> $$
> \begin{aligned}
> U^\dagger &= \left[\operatorname{exp}\left( \frac{-iH \left(t_2 - t_1\right)}{\hbar} \right)\right]^\dagger \\
> U^\dagger &= \operatorname{exp}\left(\left[ \frac{-iH \left(t_2 - t_1\right)}{\hbar} \right]^\dagger \right) \\
> &\text{The scalar term $\tfrac{-i(t_2-t_1)}{\hbar}$ becomes $\tfrac{i(t_2-t_1)}{\hbar}$ under complex conjugation.} \\
> U^\dagger &= \operatorname{exp}\left( \frac{iH\left( t_2 - t_1 \right)}{\hbar} \right)
> \end{aligned}
> $$
> We will then compute the inverse $U^{-1}$. Using the result from above, the inverse of $\operatorname{exp}(A)$ is $\operatorname{exp}(-A)$ as $\operatorname{exp}(A)\operatorname{exp}(-A) = \operatorname{exp}(A-A) = \sum_i \ket{i}\bra{i} = I$ by the completeness relation. 
> 
> Hence, the inverse $U^{-1}$ is also $\operatorname{exp}\left( \frac{iH\left( t_2 - t_1 \right)}{\hbar} \right)$. We have shown that $U^{-1} = U^\dagger$ and hence $U(t_2, t_1)$ is unitary.

>[!proof] $K = -i \log(U)$ is Hermitian for any unitary $U$, and thus $U = \exp{iK}$ for some Hermitian $K$.
>Using the [[Linear Algebra#^fd210b|spectral decomposition]], we have that $U = \sum_j \lambda_j \ket{j}\bra{j}$ and hence $K = \sum_j -i \log\left(\lambda_j \right) \ket{j}\bra{j}$. We write each $\lambda_j$ as $e^{i\theta_j}$ to get $$K = \sum_j -i \log \left( e^{i \theta_j} \right) \ket{j}\bra{j} = \sum_j \theta_j \ket{j}\bra{j}$$ which is Hermitian as $\theta_j$ is real.

For many systems it is possible to write a *time-varying* Hamiltonian for a quantum system, in which the Hamiltonian for the system is not a constant, but varies according to some parameters which are under the experimentalist's control. The system is therefore not closed, as the experimentalist can interact with it, but it evolves according to the Schrödinger Equation.


## Quantum Measurement

There are times the experimentalist and their experimental equipment, or external systems in other words, observes the system to find out what is going on. This observation is an interaction that makes this system no longer closed, and does not evolve according to a unitary transform anymore. Postulate 3 describes the effect of measurement.

>[!note] Postulate 3
>Quantum Measurements are described by a collection $\{M_m\}$ of *measurement operators*. These are the operators acting on state space of the system being observed. The index $m$ refers to the outcomes that may occur in the experiment. If the state of the system is $\ket{\psi}$ immediately before measurement then the probability that result $m$ occurs is given by $$p(m) = \langle \psi \vert M_m^\dagger M_m \vert \psi \rangle$$ and the state of the system after measurement is $$\frac{M_m \ket{\psi}}{\sqrt{\langle \psi \vert M_m^\dagger M_m \vert \psi \rangle}}$$
>
>The measurement operators satisfy the completeness relation $$\sum_m M_m^\dagger M_m = I$$ The completeness relation expresses the fact that probabilities sum to one: $$1 = \sum_m p(m) = \sum_m \langle \psi \vert M_m^\dagger M_m \vert \psi \rangle$$
>^postulate-3

An important example of measurement is the measurement of a qubit in  the computational basis. This is a measurement on a single qubit with two outcomes defined by the two measurement operators $M_0 = \ket{0}\bra{0}$ and $M_1 = \ket{1}\bra{1}$. Each measurement operator is Hermitian, and that $M_0^2 = M_0$ and $M_1^2 = M_1$, so the completeness relation is obeyed, $I = M_0M^\dagger_0 + M_1M^\dagger_1 = M_0 + M_1$. Then the probability of obtaining measurement outcome $0$ on the system $\ket{\psi} = a\ket{0} + b\ket{1}$ is $$p(0) = \langle \psi \vert M_0^\dagger M_0 \vert \psi \rangle = \langle \psi \vert M_0 \vert \psi \rangle = |a|^2$$
Similarly the probability of measuring measurement outcome $1$ is $|b|^2$. The state after the two measurements is therefore 
$$
\begin{aligned}
\frac{M_0 \ket{\psi}}{|a|} &= \frac{a}{|a|}\ket{0} \\
\frac{M_0 \ket{\psi}}{|b|} &= \frac{b}{|b|}\ket{1}
\end{aligned}
$$
We will see in the later postulates that multipliers like $\tfrac{a}{|a|}$, which have modulus one, can effectively be ignored, so the two post-measurement states are $\ket{0}$ and $\ket{1}$. 

>[!proof] Suppose $\{L_l\}$ and $\{M_m\}$ are two sets of measurement operators. A measurement defined by the measurement operators $\{L_l\}$ followed by a measurement defined by the measurement operators $\{M_m\}$ is physically equivalent to a single measurement defined by the measurement operators $\{N_{lm}\}$ given by $N_{lm} \equiv M_mL_l$.
>
>We will first verify the completeness relation for $N_{lm}$:
>$$
>\begin{aligned}
>\sum_{l, m} N_{lm}^\dagger N_{lm} &= \sum_{l, m} (M_mL_l)^\dagger (M_mL_l) \\
>&= \sum_{l, m} L_l^\dagger M_m^\dagger M_m L_l \\
>&= \sum_l L_l^\dagger L_l \\
>&= I 
>\end{aligned}
>$$
>Then, we will verify the probabilities. We denote the probability of the first measurement yielding outcome $l$ to be $p_l = \langle \psi \vert L_l^\dagger L_l \vert \psi \rangle$, and the probability of yielding $m$ after the second measurement to be the conditional probability $$p_{m \vert l} = \frac{\langle \psi \vert L_l^\dagger M_m^\dagger M_m L_l \vert \psi \rangle}{p_l}$$. By the law of conditional probability, 
>$$p_{lm} = p_{l} \cdot p_{m \vert l} = \langle \psi \vert L_l^\dagger M_m^\dagger M_m L_l \vert \psi \rangle = \langle \psi \vert N_{lm}^\dagger N_{lm} \vert \psi \rangle$$
>Which fits. The post-measurement state is $$\frac{M_mL_l\ket{\psi}}{\sqrt{p_l \cdot p_{m \vert l}}} = \frac{M_mL_l\ket{\psi}}{\sqrt{p_{lm}}} = \frac{N_{lm}\ket{\psi}}{\sqrt{p_{lm}}}$$


## Distinguishing Quantum States

In the classical world, we can distinguish states rather easily. We can always identify whether or not a coin has landed heads or tails. In quantum mechanics, this is more complicated. 

Distinguishability can best be understood using the metaphor of a game involving two parties, Alice and Bob. Alice chooses a state $\ket{\psi_i}$ where $1 \leq i \leq n$ from some fixed states known to both parties. She gives the state $\ket{\psi_i}$ to Bob, whose task is to identify the index $i$ of the state Alice has given to him.

Suppose the states $\ket{\psi_i}$ are orthonormal. Then Bob can do a quantum measurement to distinguish these states, using the following procedure:
- Define measurement operators $M_i = \ket{\psi_i}\bra{\psi_i}$, one for each positive index $i$.
- Add an additional measurement operator $M_0$ defined as the positive square root of the operator $I - \sum_{i \neq 0} \ket{\psi_i}\bra{\psi_i}$.
These operators satisfy the completeness relation, as $$\sum_{i=1}^n \ket{\psi_i}\bra{\psi_i} + M_0^\dagger M_0 = \sum_{i=1}^n \ket{\psi_i}\bra{\psi_i} + I - \sum_{i=1}^n \ket{\psi_i}\bra{\psi_i} = 1$$and if state $\ket{\psi_i}$ is prepared, then $p(i) = \langle \psi_i \vert M_i \vert \psi_i \rangle = \langle \psi_i \vert \psi_i \rangle \langle \psi_i \vert \psi_i \rangle = 1$, as so the result $i$ occurs with certainty. Hence, you can reliably distinguish the states.

In contrast, we can prove that if the states are not orthogonal, then you cannot distinguish the states. The idea is that Bob will do a measurement described by the measurement operators $M_j$ with outcome $j$. Depending on the outcome of the measurement Bob tries to guess what the index $i$ was based on some rule $i = f(j)$ where $f(\cdot)$ is the rule he uses to make the guess. 

Intuitively, the states $\ket{\psi_1}$ and $\ket{\psi_2}$ cannot be distinguished because $\ket{\psi_2}$ can be decomposed into a component parallel to $\ket{\psi_1}$ and a component orthogonal. Suppose $j$ is a measurement outcome such that $f(j)=1$, that is, Bob guesses $\ket{\psi_j}$ when he observes $j$. But because of the component of $\ket{\psi_2}$ parallel to $\ket{\psi_1}$, there is a non-zero probability of obtaining result $j$ when $\ket{\psi_2}$ is prepared. 

This is proven by contradiction. We assume such measurement to distinguish the two states is possible. That is, if the state $\ket{\psi_1}$, or equivalently $\ket{\psi_2}$, is prepared, then the probability of measuring $f(j)=1$ (or equivalently $f(j)=2$) must be $1$. We define $E_i \equiv \sum_{j: f(j)=i} M_j^\dagger M_j$. Hence, $$\begin{align} & \langle \psi_1 \vert E_1 \vert \psi_1 \rangle = 1; & \langle \psi_2 \vert E_2 \vert \psi_2 \rangle = 1\end{align}.$$ Since $\sum_i E_i = I$ it follows that $\sum_i \langle \psi_1 \vert E_i \vert \psi_1 \rangle$, and since $\langle \psi_1 \vert E_1 \vert \psi_1 \rangle = 1$ we must have $\langle \psi_1 \vert E_2 \vert \psi_1 = 0$ and thus $\sqrt{E_2}\ket{\psi_1}=0$. 

If we decompose $\ket{\psi_2} = \alpha \ket{\psi_1} + \beta \ket{\varphi}$, where $\ket{\varphi}$ is orthonormal to $\ket{\psi_1}$, $|\alpha|^2 + |\beta|^2 = 1$ and $|\beta| < 1$ as $\ket{\psi_1}$ and $\ket{\psi_2}$ are not orthogonal. Then $\sqrt{E_2}\ket{\psi_2} = \beta \sqrt{E_2}\ket{\varphi}$, which contradicts our original statement.

Note that $$\langle \varphi \vert E_2 \vert \varphi \rangle \leq \sum_i \langle \varphi \vert E_i \vert \varphi \rangle = \langle \varphi \vert \varphi \rangle = 1$$ Hence, $$\langle \psi_2 \vert E_2 \vert \psi_2 \rangle = |\beta|^2 \langle \varphi \vert E_2 \vert \varphi \rangle \leq |\beta|^2 < 1$$ And thus contradiction is reached. Hence, it is impossible to distinguish two non-orthonormal quantum states.


## Projective Measurements

Projective measurements are an important special case of the third postulate. For the applications of quantum computation and quantum information we mostly concern ourselves with projective measurements. 

>[!note] Projective Measurements
>A projective measurement is described by an  observable, $M$, which is a Hermitian operator on the state space of the quantum system being observed. The observable has a spectral decomposition $$M = \sum_m mP_m$$ where $P_m$ is the projector onto the eigenspace of $M$ with eigenvalue $m$. The possible outcomes of the measurement correspond to the eigenvalues $m$ of the observable. Upon measuring the state $\ket{\psi}$, the probability of getting result $m$ is given by $$p(m)=\langle \psi \vert P_m \vert \psi \rangle$$ Given that outcome $m$  occurred, the state of the quantum system immediately after measurement is $$\frac{P_m\ket{\psi}}{\sqrt{p(m)}}$$

When we restrict Postulate 3's measurement operators such that the operators are orthogonal projectors, that is that $M_m$ are Hermitian, and $M_mM_{m'} = \delta_{m, m'}M_m$, Postulate 3 reduces to a projective measurement. 

These projective measurements have a lot of very nice properties. For example, it is very easy to calculate average values for projective measurements: 
$$
\begin{aligned}
\textbf{E}(M) &= \sum_m m\ p(m) \\
&= \sum_m m \ \langle \psi \vert P_m \vert \psi \rangle \\
&= \bra{\psi} \left(\sum_m m \ P_m \right) \ket{\psi} \\
&= \langle \psi \vert M \vert \psi \rangle
\end{aligned}
$$
This formula is useful to simplify calculations. The average value of the observable $M$ is often written as $\langle M \rangle \equiv \langle \psi \vert M \vert \psi \rangle$. From this formula we can also derive the standard deviation associated to observations of $M$: 
$$
\begin{aligned} \
[\Delta(M)]^2 &= \left\langle \left(M - \left\langle M \right\rangle \right)^2 \right\rangle \\
&= \langle M^2 \rangle - \langle M \rangle^2
\end{aligned}
$$
The standard deviation is a measure of the typical spread of the observed values upon measurement of $M$. In particular, if we perform a large number of observations in which the state $\ket{\psi}$ is prepared and the observable $M$ is measured, then the standard deviation $\Delta (M)$ of the observed values is determined by the formula $\Delta (M) = \sqrt{\langle M^2 \rangle - \langle M \rangle^2}$. This formulation of measurement and standard deviations in terms of observables gives rise to results such as the Heisenberg Uncertainty Principle.

>[!note] The Heisenberg Uncertainty Principle
>This is perhaps the best known result, but also a widely misinterpreted result in quantum mechanics. Suppose $A$ and $B$ are two Hermitian operators, and $\ket{\psi}$ is a quantum state. Suppose $\langle \psi \vert AB \vert \psi \rangle = x + iy$ where $x$ and $y$ are real. Note that $\bra{\psi} [A, B] \ket{\psi} = 2iy$ and $\bra{\psi} \{ A, B \} \ket{\psi} = 2x$. This implies that $$\left| \bra{\psi} \left[ A, B \right] \ket{\psi} \right|^2 + \left| \bra{\psi} \left\{ A, B \right\} \ket{\psi} \right|^2 = 4\left|\langle \psi \vert AB \vert \psi \rangle\right|^2$$ By the Cauchy-Schwarz inequality $$\left|\langle \psi \vert AB \vert \psi \rangle\right|^2 \leq \langle \psi \vert A^2 \vert \psi \rangle \langle \psi \vert B^2 \vert \psi \rangle$$ When combined with the previous, and dropping a non-negative term, gives $$\left| \bra{\psi} \left[ A, B \right] \ket{\psi} \right|^2 \leq 4\langle \psi \vert A^2 \vert \psi \rangle \langle \psi \vert B^2 \vert \psi \rangle$$
>Suppose $C$ and $D$ are two observables. Substituting $A = C - \langle C \rangle$ and $B=  D - \langle D \rangle$ into the above, we  get Heisneberg's Uncertainty Principle as it is usually stated: $$\Delta (C) \Delta (D) \geq \frac{\left| \bra{\psi} \left[ C, D \right] \ket{\psi} \right|}{2}$$
>
>A common misconception of the Heisenberg Uncertainty Principle, that measuring an observable $C$ to some "accuracy" $\Delta (C)$ causes the value of $D$ to be "disturbed" by an amount $\Delta (D)$ in such a way that some sort of inequality is satisfied. While it is true that a measurement in quantum mechanics causes a disturbance to the system being measured, this is most emphatically not the content of the uncertainty principle.
>
>The correct interpretation is that if we prepare a set of identical states $\ket{\psi}$ and then perform measurements on $C$ on some of those systems, and $D$ in others, then the standard deviation $\Delta (C)$ of the $C$ results times the standard deviation $\Delta (D)$ of the $D$ results will satisfy the inequality. 

>[!warning] Nomenclature
>Some notations and nomenclature should be noted. Rather than giving an observable to describe a projective measurement, often people simply list a set of orthogonal projectors $P_m$ satisfying the completeness relation  $\sum_m  P_m = I$ and $P_mP_{m'} = \delta_{mm'}P_m$. The corresponding observable implicit in this usage is  $M = \sum_m mP_m$. 
>
>A widely used phrase is to "measure in a basis $\ket{m}$" where $\ket{m}$ form an orthonormal basis, simply means to perform the projective measurement with projectors $P_m = \ket{m}\bra{m}$. 
>^measure-in-basis-note

For example, we measure the observable $Z$ on $\ket{\psi} = \frac{1}{\sqrt{2}}(\ket{0}+\ket{1})$ gives the result $+1$ with probability $\langle \psi \vert 0 \rangle \langle 0 \vert \psi \rangle = \frac 12$ and similarly result $-1$ with probability $-1$. 

More generally, suppose $\vec{v}$ is any real three-dimensional unit vector. Then we can define an observable $\vec{v} \cdot \vec{\sigma} \equiv v_1 \sigma_1 + v_2 \sigma_2 + v_3 \sigma_3$. The measurement of this observable is often referred to as a measurement of spin along the $\vec{v}$ axis for historical reasons. 

>[!proof] Suppose we prepare a quantum system in an eigenstate $\ket{\psi}$ of some observable $M$, with corresponding eigenvalue $m$. What is the average observed value of $M$ and what is the standard deviation?
>The average value is $$\langle M \rangle = \langle \psi \vert M \vert \psi \rangle = m \cdot \langle \psi \vert \psi \rangle = m$$
>And hence the standard deviation is $m^2- m^2 = 0$

>[!proof] Suppose we have a qubit in the state $\ket{0}$, and we measure the observable $X$. What is the average value of $X$? What about the standard deviation?
>The average value is $\langle 0 \vert X \vert 0 \rangle = 0$.
>The standard deviation is $\sqrt{\langle X^2 \rangle - \langle X \rangle}$. Because $X^2 = I$, $\langle X^2 \rangle = 1$ and $\langle X \rangle = 0$, so the standard deviation is $1$.


## POVM Measurements

The third postulate tells us two things: the statistics of a measurement and the post-measurement state. However, in a lot of scenarios only the probabilities of the outcomes of measurement matter and not the post-measurement state, for example in an experiment where the system is only measured once, upon conclusion of the experimnent. 

In these circumstances there is a mathematical tool known as the *POVM* formalism which is especially adapted to the analysis of the measurements. 

Suppose a measurement described by the measurement operators $M_m$ is performed upon the quantum state $\ket{\psi}$. Then the probability of outcome $m$ is given by $p(m)=\langle \psi \vert M^\dagger_m M_m \vert \psi \rangle$. Suppose we define $$E_m = M^\dagger_m M_m$$ Then $E_m$ is a positive operator such that $\sum_m E_m = I$ and $p(m) = \langle \psi \vert E_m \vert \psi \rangle$. Thus the set of operators $E_m$ is sufficient to determine the probabilities of each outcome. 

For example, consider a projective measurement described by the measurement operators $P_m$ where $P_mP_{m'} = \delta_{mm'}P_m$ and $\sum_m P_m = I$. In this instance all the POVM operators are the same as the measurement operators as $E_m = P_m^\dagger P_m = P_m$. 

>[!warning]
>Most introductions to quantum mechanics only describe projective measurements, so the measurements described in [[The Postulates of Quantum Mechanics#^postulate-3|Postulate 3]] might be a little foreign. This is because most physical systems can only be measured in a very coarse manner. In quantum computation and information though, we aim for a higher degree of control. 
>
>Starting with Postulate 3 tends to have easier mathematics, as there are less mathematical restrictions. Furthermore, in quantum computing and information there are problems that are solved with only general measurements, like the optimal way to distinguish quantum states.
>
>Another reason for preferring Postulate 3 as a starting point is related to a property of projective measurements known as repeatability. If we perform a projective measurement once, and perform it again, it does not change the state and outcome. 
>
>This repeatability shows how many important measurements in quantum mechanics are not projective. Many quantum measurements are not repeatable in the same sense as a projective measurement. 
>
>POVMs are viewed as a special case of the general measurement formalism, providing the simplest means to which someone can study the general measurement statistics.

It is possible to use POVMs that distinguishes states some of the time, but never makes an error of misidentification.

## Phase

Phase is a commonly used term in quantum mechanics, with several different meanings depending on context. 

Consider the state $e^{i\theta}\ket{\psi}$ where $\ket{\psi}$ is a state factor, and $\theta$ is a real number. We say that $e^{i\theta}\ket{\psi}$ is equal to $\ket{\psi}$, up to the *global phase factor*. The statistics of measurement predicted for these two states are the same. 

There is another kind of phase known as the *relative phase*. We say that two amplitudes *differ by a relative phase* if there is a real $\theta$ such that $a = e^{i\theta}b$. Two states are said to *differ by a relative phase* in some basis if each of the amplitudes in that basis is related by such a phase factor. Relative phase is a basis-dependent concept while global phase is not. As a result, states which differ only by relative phases in some basis give rise to physically observable differences in measurement statistics, and it is not possible to regard these states as physically equivalent, as we do with states differing by a global phase factor.


## Composite Systems

>[!note] Postulate 4
>FINALLY another postulate after so much about measurements. The state space of a composite physical system is the tensor product of the state spaces of the component physical systems. Moreover, if we have systems numbered $1$ through $n$, and the system number $i$ is prepared in the state $\ket{\psi_i}$, then the joint state of the system is $\ket{\psi_1} \otimes \ket{\psi_2} \otimes \cdots \otimes \ket{\psi_n}$.

Projective measurements together with unitary dynamics are sufficient to implement a general measurement. The proof of this makes use of composite systems, and shows postulate 4 in action. 

Suppose we have a quantum system with state space $Q$, and we want to perform a measurement described by the measurement operators $M_m$ on the system $Q$. To do this, we introduce an *ancilla* system, with the state space $M$, having an orthonormal basis $\ket{m}$ with a one-to-one correspondence with the possible outcomes of the measurement we wish to implement. This ancilla system can be regarded as a mathematical device or it can be interpreted physically as another quantum system introduced in the problem.

Letting $\ket{0}$ be any fixed state of $M$, we define an operator $U$ on the tensor product $\ket{\psi}\ket{0}$ of states $\ket{\psi}$ from $Q$ with the state $\ket{0}$ by $U\ket{\psi}\ket{0} \equiv \sum_m M_m \ket{\psi}\ket{m}$. We can see that $U$ preserves the inner products between states of the form $\ket{\psi}\ket{0}$,
$$
\begin{aligned}
\bra{\varphi} \langle 0 \vert U^\dagger U \vert \psi \rangle \ket{0} &= \sum_{m, m'} \langle \varphi \vert M_m^\dagger M_{m'} \vert \psi \rangle \langle m \vert m' \rangle \\
&= \sum_m \langle \varphi \vert M_m^\dagger M_{m'} \vert \psi \rangle \\
&= \langle \varphi \vert \psi \rangle
\end{aligned}
$$
It follows that $U$ can be extended to a unitary operator on the space $Q \otimes M$, which we also denote by $U$.  Suppose we perform a projective measurement on the two systems described by the measurement operators $P_m = I_Q \otimes \ket{m}\bra{m}$. The probability and the post-measurement joint state all match up with those defined in [[The Postulates of Quantum Mechanics#^postulate-3|Postulate 3]]. Hence, with unitary dynamics, projective measurements, and ancilla systems, we can perform any measurement as defined in Postulate 3.

Postulate 4 also lets us define an enthralling concept in quantum mechanics, entanglement. Consider the two qubit state $$\ket{\psi}=\frac{\ket{00}+\ket{11}}{\sqrt{2}}$$ This state has the property that there are no single qubit states such that $\ket{\psi}=\ket{a}\ket{b}$. 

We can apply this property in [[Superdense Coding]].