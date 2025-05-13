An alternate formulation of quantum mechanics is known as the *density operator* or *density matrix*, which is mathematically equivalent to the state vector formulation. It is also a tool for describing individual systems within a composite system.

## Ensembles of Quantum States

The density operator provides a language to describe systems in which the state is not entirely known. Suppose a quantum system is one of a number of states $\ket{\psi_i}$ where $i$ is an index, with respective probabilities $p_i$. We call $\{p_i, \ket{\psi_i}\}$ an ensemble of pure states. The density operator for the system is defined by the equation $$\rho \equiv \sum_i p_i \ket{\psi_i}\bra{\psi_i}.$$
Suppose that the evolution of a quantum system is described by the unitary operator $U$. Then, if the quantum system is in a quantum state $\ket{\psi_i}$ with probability $p_i$, the evolved state will be in probability $U\ket{\psi_i}$ with probability $p_i$. Hence, the evolution of the density operator is described by the equation $$\rho = \sum_i p_i \ket{\psi_i}\bra{\psi_i} \xrightarrow{U} \sum_i p_i U \ket{\psi_i}\bra{\psi_i}U^\dagger = U \rho U^\dagger.$$
Measurements are also easily described in the density operator language. Suppose we perform a measurement described by the measurement operators $M_m$. If the initial state was $\ket{\psi_i}$, then the probability of getting result $m$ is: $$p(m|i)=\bra{\psi_i}M_m^\dagger M_m \ket{\psi_i} = \operatorname{tr}\left(M_m^\dagger M_m \ket{\psi_i}\bra{\psi_i}\right),$$ where [[Linear Algebra#^983889|this equation]] to evaluate the probability. By the law of total probability, 
$$
\begin{aligned}
p(m)&=\sum_i p(m|i)p_i \\
&= \sum_i p_i \operatorname{tr}\left( M_m^\dagger M_m \ket{\psi_i}\bra{\psi_i} \right) \\
&= \operatorname{tr}\left( M_m^\dagger M_m \rho \right).
\end{aligned}
$$
To find the post-measurement density operator, first we consider the post-measurement state $\ket{\psi_i^m}$:
$$\ket{\psi_i^m}=\frac{M_m \ket{\psi_i}}{\sqrt{\bra{\psi_i}M_m^\dagger M_m \ket{\psi_i}}}.$$ The corresponding density operator is therefore:
$$
\begin{aligned}
\rho_m &= \sum_i p(i|m)\ket{\psi_i^m}\bra{\psi_i^m} \\
&= \sum_i p(i|m) \frac{M_m \ket{\psi_i}\bra{\psi_i}M_m^\dagger}{\operatorname{tr\left(M_m^\dagger M_m \rho\right)}} \\
&= \sum_i p_i \frac{M_m \ket{\psi_i}\bra{\psi_i}M_m^\dagger}{\operatorname{tr}\left(M_m^\dagger M_m \rho \right)} \\
&= \frac{M_m \rho M_m^\dagger}{\operatorname{tr}\left(M_m^\dagger M_m \rho \right)}
\end{aligned}
$$

It is useful to introduce some more language.

>[!definition] Pure and Mixed States
>A quantum system whose state is known exactly to be $\ket{\psi}$ is said to be in a *pure state*. The density operator for this system is therefore $\rho = \ket{\psi}\bra{\psi}$. Otherwise, $\rho$ is in a *mixed state*. 
>
>A pure state satisfies $\operatorname{tr}(\rho^2)=1$ while a mixed state satisfies $\operatorname{tr}(\rho^2) < 1$. 
>
>The term "pure state" is usually used to reference a state vector $\ket{\psi}$.
>^pure-and-mixed

Finally, we consider a system is prepared in a state $\rho_i$ with probability $p_i$. The system may be described as the density matrix $\sum_i p_i \rho_i$.  We say that this $\rho$ is a *mixture* of the states $\rho_i$. This concept of mixtures comes up repeatedly in analysis of problems like quantum noise, where the effect of noise is to introduce ignorance into our knowledge of the quantum state.

For example, consider we have lost the record of measurement $m$ in a quantum system. That is, we have a quantum system in the state $\rho_m$ with probability $p(m)$ but we no longer know the actual value of $m$. The state of the system is therefore described by the density operator:
$$
\begin{aligned}
\rho &= \sum_m p(m)\rho_m \\
&= \sum_m \operatorname{tr}(M_m^\dagger M_m \rho) \frac{M_m \rho M_m^\dagger}{\operatorname{tr}(M_m^\dagger M_m \rho)} \\
&= \sum_m M_m \rho M_m^\dagger
\end{aligned}
$$

## General Properties of Density Operators


The class of operators that are density operators are characterized by the following theorem:

>[!definition] Characterization of Density Operators
>An operator $\rho$ is the density operator associated to some ensemble $\{p_i, \ket{\psi_i}\}$ if and only if:
>- $\rho$ has trace equal to one.
>- $\rho$ is a positive operator.
>^density-operator-criterion

To complete our four postulates of quantum mechanics with density operators, we include the following:

The density operator corresponding to a composite system is the tensor product of each of the density operators. 

This along with our above derived properties complete the four postulates of quantum mechanics for density operators. Density operators allow us to describe quantum systems of unknown states, and also describe the specific states of subsystems in composite systems.

>[!proof] $\operatorname{tr}(\rho^2) \leq 1$ with equality if and only if $\rho$ is a pure state.
>Because $\rho$ is Hermitian, we can give it a spectral decomposition: $$\rho = \sum_i p_i \ket{\psi_i}\bra{\psi_i}.$$
>Hence, 
>$$
>\begin{aligned}
>\rho^2 &= \left(\sum_i p_i \ket{\psi_i}\bra{\psi_i}\right)\left(\sum_j p_j \ket{\psi_j}\bra{\psi_j}\right)\\
>&=\sum_i\sum_jp_ip_j \vert \psi_i \rangle \langle \psi_i \vert \psi_j \rangle \langle \psi_j \vert \\
>&= \sum_i p_i^2 \ket{\psi_i}\bra{\psi_i}
>\end{aligned}
>$$
>The trace of $\rho^2$ is: $$\operatorname{tr}(\sum_i p_i^2 \ket{\psi_i}\bra{\psi_i}) = \sum_i p_i^2 \operatorname{tr}(\ket{\psi_i}\bra{\psi_i}) = \sum_i p_i^2 \langle \psi_i \vert \psi_i \rangle = \sum_i p_i^2.$$ We know that $\operatorname{tr}(\rho) = \sum_i p_i = 1$, and hence $0 \leq p_i \leq 1$. This means that $p_i^2 \leq p_i$ for all $i$, and $\sum_i p_i^2 \leq \sum_i p_i$ which finally leads to $$\operatorname{tr}(\rho^2) \leq 1.$$ If $\rho$ is a pure state, then $\rho = \ket{\psi}\bra{\psi} = \rho^2$ and so $\operatorname{tr}(\rho^2)=1$.

In general, the eigenvectors and eigenvalues of a density operator just indicate one of many possible ensembles that may give rise to a specific operator. This means that two ensembles could generate the same density operator. For example, $\rho = \frac 34 \ket{0}\bra{0} + \frac 14 \ket{1}\bra{1}$ could have state $\ket{0}$ with $\frac 34$ probability and state $\ket{1}$ with $\frac 14$ probability, but it could also have state $\sqrt{\frac 34} \ket{0} + \sqrt{\frac 14}\ket{1}$ with probability $\frac 12$ and $\sqrt{\frac 34} \ket{0} - \sqrt{\frac 14}\ket{1}$ with probability $\frac 12$.

A natural question to ask in light of this is exactly when, or what class of ensembles, gives rise to a particular density matrix? The answer has many applications in quantum information and quantum computation, about quantum noise and quantum error-correction. 

> [!warning]
> To arrive at the situation we introduce notations! $\ket{\tilde{\psi_i}}$ are vectors that may not be normalized to unit length. We say the set $\ket{\tilde{\psi_i}}$ *generates* the operator $\rho \equiv \sum_i \ket{\tilde{\psi_i}} \bra{\tilde{\psi_i}}$ and thus the connection to regular familiar density operators is given by the relation $\ket{\tilde{\psi_i}} = \sqrt{p_i}\ket{\psi_i}$

When do two sets of vectors, $\ket{\tilde{\psi_i}}$ and $\ket{\tilde{\varphi_j}}$ generate the same operator $\rho$ ?

>[!theorem]
>The sets $\ket{\tilde{\psi_i}}$ and $\ket{\tilde{\varphi_j}}$ generate the same density operator if and only if $$\ket{\tilde{\psi_i}} = \sum_j u_{ij}\ket{\tilde{\varphi_j}}$$ where $u_{ij}$ is a unitary matrix of complex numbers, with indices $i$ and $j$, we 'pad' whichever set of vectors  $\ket{\tilde{\psi_i}}$ or $\ket{\tilde{\varphi_j}}$ is smaller with additional vectors $0$ so that the two sets have the same amount of elements. 
>
>As a consequence of the theorem, note that $\rho = \sum_i p_i \ket{\psi_i}\bra{\psi_i} = \sum_j q_j \ket{\varphi_j}\bra{\varphi_j}$ for *normalized* states $\ket{\psi_i}$, $\ket{\varphi_j}$ and probability distributions $p_i$ and $q_j$ if and only if $$\sqrt{p_i} \ket{\psi_i} = \sum_j u_{ij}\sqrt{q_j}\ket{\varphi_j},$$
>again for some unitary matrix $u_{ij}$, and we may pad the smaller ensemble with entries having probability zero in order to make them the same size. 
>^unitary-freedom-density-theorem

>[!proof]



