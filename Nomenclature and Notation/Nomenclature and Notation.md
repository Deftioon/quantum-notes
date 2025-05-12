# Linear  Algebra and Quantum Mechanics

>[!important]
>All vector spaces are assumed to be finite dimensional, unless otherwise noted. In many instances, this restriction is unnecessary, or can be removed with some additional technical work.
>^vector-spaces-notice

>[!Important]
>The notation $U$ (and often but not always $v$) will generically be used to denote a unitary operator or matrix.
>
>$H$ is usually used to denote a quantum logic gate, the *Hadamard Gate*, and sometimes to denote the *Hamiltonian* for a quantum system, with the meaning clear from context.
>^unitary-notice

>[!definition]
>A *positive* operator $A$ is one for which $\langle \psi \vert A \vert \psi \rangle \geq 0$ for all $\ket{\psi}$.
>^positive-operator-definition


>[!definition]
>A  *positive definite* operator $A$ is one for which $\langle \psi \vert A \vert \psi \rangle > 0$ for all $\ket{\psi}$.
>^positive-definite-operator-definition


>[!definition]
>The  *support* of an operator is defined to be the vector space orthogonal to its kernel.
>>[!info]
>>For a Hermitian Operator, this means the vector space spanned by eigenvectors of the operator with non-zero eigenvalues.\
>^support-definition


>[!important]
>We denote:
>$$
>\ket{0} = \begin{bmatrix} 1 \\ 0 \end{bmatrix}
>$$
>$$
>\ket{1} = \begin{bmatrix} 0 \\ 1 \end{bmatrix}
>$$
>^basis-states-definition


>[!important]
>We also denote the following *Pauli Matrices:*
>$$
>\sigma_0 \equiv I \equiv \begin{bmatrix} 1  & 0 \\ 0 & 1 \end{bmatrix}
>$$
>$$
>\sigma_1 \equiv \sigma_x \equiv X \equiv \begin{bmatrix} 0  & 1 \\ 1 & 0 \end{bmatrix}
>$$
>$$
>\sigma_2 \equiv \sigma_y \equiv Y \equiv \begin{bmatrix} 0  & -i \\ i & 0 \end{bmatrix}
>$$
>$$
>\sigma_3 \equiv \sigma_z \equiv Z \equiv \begin{bmatrix} 1  & 0 \\ 0 & -1 \end{bmatrix}
>$$
>^pauli-matrices-definition

# Information Theory and Probability

>[!warning]
>Logarithms are *always* taken to base 2, unless otherwise noted. $\log$ is used to denote base 2 logarithms and $\ln$ when the natural base $e$ logarithm is needed.

>[!definition]
> A probability distribution is a finite set of real numbers $p_x$ such that $p_x \geq 0$ and $\sum_x p_x= 1$
> ^probability-distribution-definition

>[!definition]
>The *relative entropy* of a [[Nomenclature and Notation#^positive-operator-definition|positive operator]] $A$ with respect to a [[Nomenclature and Notation#^positive-operator-definition|positive operator]] $B$ is defined  by $S(A \vert \vert B) \equiv \operatorname{tr}(A \log A) - \operatorname{tr}(A \log B)$
>^relative-entropy-definition

# Miscellanea
>[!definition]
>$\oplus$ denotes modulo two addition.

>[!definition]
>The Kronecker delta is defined as follows:  $$\delta_{ij}=\begin{cases}1, i=j \\ 0, i \neq j\end{cases}$$
>^kronecker-delta-definition

We then move on with [[Linear Algebra|Linear Algebra]]