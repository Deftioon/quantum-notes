Linear  algebra is the study of [[Nomenclature and Notation#^vector-spaces-notice|vector spaces]] and of linear operations on those vector spaces. Quantum mechanics is based off elementary linear algebra. 

## Vectors and Vector Spaces

The basic objects of linear algebra are [[Nomenclature and Notation#^vector-spaces-notice|vector spaces]]. The vector space of most interest to us is $\mathbb{C^n}$ , the space of all $n$-tuples of complex numbers $(z_1, \ldots, z_n)$. 

The elements of a vector space are called *vectors*. We use the column notation:
$$
\begin{bmatrix} z_1 \\ \vdots \\ z_n \end{bmatrix}
$$
There are addition and multiplication operations defined:
$$ \begin{bmatrix} z_1 \\ \vdots \\ z_n \end{bmatrix} +
 \begin{bmatrix} z'_1 \\ \vdots \\ z'_n \end{bmatrix} =
 \begin{bmatrix} z_1 + z'_1 \\ \vdots \\ z_n + z'_n \end{bmatrix}$$
 $$z\begin{bmatrix} z_1 \\ \vdots \\ z_n \end{bmatrix}=\begin{bmatrix} zz_1 \\ \vdots \\ zz_n \end{bmatrix}$$
 where $z$ is a *scalar*. 
 
 >[!important]
 >The standard quantum mechanics notation for a vector in a vector space is in *Dirac Notation*, in *bras* and *kets*:
 >$$\ket{\psi}$$
 >^standard-kets
 
 $\psi$ is a label for the vector.  The $\ket{\cdot}$ notation is used to indicate an object is a vector. 

A vector space must contain a special  *zero vector* , denoted as $0$. It satisfies the property that for any vector $\ket{v}$, $\ket{v} + 0 = \ket{v}$. It is known as the additive identity. 

>[!warning]
>We do not use ket notation for $0$ as it has other meanings in quantum computing.
>^zero-ket-warning

Before we go deep into linear algebra, some notation:

> [!info]
> 
| Notation                                  | Description                                                                                      | Notes                                                                                                                 |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| $z^*$                                     | Complex conjugate of the complex number $z$.<br>If $z = a+bi$, then the conjugate $z^* = a - bi$ | The complex conjugate distributes <br>over multiplication and addition.<br>i.e. $(ab)^*=a^*b^*$ and $(a+b)^*=a^*+b^*$ |
| $\ket{\psi}$                              | A vector, in *ket* notation                                                                      | This is often a column vector.                                                                                        |
| $\bra{\psi}$                              | Vector dual to $\ket{v}$                                                                         | $\bra{v}=\ket{v}^\dagger$                                                                                             |
| $\langle \phi \vert \psi \rangle$         | Inner product of the vectors $\ket{\phi}$ and $\ket{\psi}$                                       | $\langle \phi \vert \psi \rangle = \bra{\phi} \ket{\psi} = \ket{\phi}^\dagger \ket{\psi}$                             |
| $\ket{\phi} \otimes \ket{\psi}$           | Tensor product of $\ket{\phi}$ and $\ket{\psi}$                                                  | Often abbreviated to $\ket{\phi}\ket{\psi}$                                                                           |
| $A^*$                                     | Complex conjugate of the matrix $A$.                                                             | Conjugate every entry in  $A$                                                                                         |
| $A^T$                                     | Transpose  of matrix $A$                                                                         | Swap rows and columns                                                                                                 |
| $A^\dagger$                               | Hermitian conjugate, or adjoint, of the matrix $A$                                               | $A^\dagger=(A^T)^*$                                                                                                   |
| $\langle \phi \vert A \vert \psi \rangle$ | Inner product between $\ket{\phi}$ and $A\ket{\psi}$.                                            | Equivalently, the inner product between $A^\dagger\ket{\phi}$ and $\ket{\psi}$                                        |  ^linalg-notation-table


## Bases and Linear Independence

>[!definition]
>A  *spanning set* for a vector space is a set of vectors $\ket{v_1} \ldots \ket{v_n}$ such that any vector $\ket{v}$ in the  vector space can be written as a linear combination $\ket{v}=\sum_ia_i\ket{v_i}$ of vectors in the spanning set. 
>^spanning-set-definition

>[!example]
>A spanning set for the vector space $\mathbb{C}^2$ is the set $$\ket{v_1} \equiv \begin{bmatrix}1 \\ 0\end{bmatrix}$$ $$\ket{v_2} \equiv \begin{bmatrix}0 \\ 1\end{bmatrix}$$ 
>
>This is because $$\begin{bmatrix}a \\ b\end{bmatrix} = a\begin{bmatrix}1 \\ 0\end{bmatrix} + b\begin{bmatrix}0 \\ 1\end{bmatrix}$$

A vector space may have many different spanning sets. Another spanning set for $\mathbb{C}^2$ is the set $$\ket{v_1} \equiv \frac{1}{\sqrt{2}}\begin{bmatrix}1 \\ 1\end{bmatrix}$$$$\ket{v_1} \equiv \frac{1}{\sqrt{2}}\begin{bmatrix}1 \\ -1\end{bmatrix}$$
>[!proof]
>A linear combination of these two vectors is: $$\frac{a}{\sqrt{2}}\begin{bmatrix}1 \\ 1\end{bmatrix} + \frac{b}{\sqrt{2}}\begin{bmatrix}1 \\ -1\end{bmatrix}$$
>This is equal to: $$\begin{bmatrix}\frac{a}{\sqrt{2}} \\ \frac{a}{\sqrt{2}}\end{bmatrix}+\begin{bmatrix}\frac{b}{\sqrt{2}} \\ -\frac{b}{\sqrt{2}}\end{bmatrix}$$
>This is a spanning set because any vector  $\ket{v}$ can be written in the form:
>$$\frac{a+b}{\sqrt{2}}\ket{v_1} + \frac{a-b}{\sqrt{2}}\ket{v_2}$$

We can now arrive at linear independence and bases.

>[!definition]
>A set of non-zero vectors $\ket{v_1},\ldots,\ket{v_n}$ are *linearly dependent* if there exists a set of complex numbers  $\alpha_1,\ldots,\alpha_n$ with at least one  $\alpha_i \neq 0$ such that $$\alpha_1\ket{v_1}+\alpha_2\ket{v_2}+\ldots+\alpha_n\ket{v_n}=0$$ In other words, a set of vectors is linearly dependent if any one vector of the set can be written as a linear combination of the rest.
>
>A set of vectors is *linearly dependent* if it is not not linearly dependent (wow shocker I know).
>^linear-independence-definition

>[!example]
>$\begin{bmatrix} 1 \\ -1 \end{bmatrix}, \begin{bmatrix} 1 \\ 2 \end{bmatrix}, \begin{bmatrix} 2 \\ 1 \end{bmatrix}$ are linearly dependent because $\begin{bmatrix} 1 \\ -1 \end{bmatrix} + \begin{bmatrix} 1 \\ 2 \end{bmatrix} = \begin{bmatrix} 2 \\ 1 \end{bmatrix}$

It can be shown that any two sets of linearly independent vectors which [[Linear Algebra#^spanning-set-definition|span]] a vector space $V$ contain the same number of elements. To do this, we must first prove the **Exchange  Lemma**.

>[!proof] Proof: **The Exchange Lemma**
>**Statement**:
>Let $U$ and $W$ be finite subsets of a vector space  $V$. If $U$ is a set of [[#^linear-independence-definition|linearly independent]] vectors, and $W$ [[Linear Algebra#^spanning-set-definition|spans]] $V$, then:
>1. $\vert U \vert \leq \vert W \vert$,
>2. There is a set $W' \subset W$ with $\vert W' \vert = \vert W \vert - \vert U \vert$ such that $U \cup W'$ spans $V$
>   
> **Proof:**
>   Suppose $U = \{\ket{u_1},\ldots,\ket{u_m}\}$ and $W = \{\ket{w_1},\ldots,\ket{w_m}\}$. We want to show that $m \leq n$ and that rearranging the $w_j$ if necessary, the set $\{\ket{u_1},\ldots,\ket{u_m},\ket{w_{m+1}},\ldots\ket{w_n}\}$ spans $V$. The proof given by [wikipedia](https://en.wikipedia.org/wiki/Steinitz_exchange_lemma) is one by induction.
>   
>   For the base case, suppose $m = 0$. In this case, the lemma holds because there are no vectors in $U$ and the set spans $\{\ket{w_1},\ldots,\ket{w_m}\}$ by hypothesis.
>   
>   For the inductive step, we assume the proposition is true for $m-1$. That is, we can reorder the $w_i$ such that $\{\ket{u_1},\ldots,\ket{u_{m-1}},\ket{w_{m}},\ldots\ket{w_n}\}$ spans $V$. Since $u_m \in V$, and $\{\ket{u_1},\ldots,\ket{u_{m-1}},\ket{w_{m}},\ldots\ket{w_n}\}$ spans $V$, there exists coefficients $\mu_1,\ldots,\mu_n$ such that  $$u_m = \sum^{m-1}_{i=0}\mu_iu_i + \sum^n_{j=m}\mu_jw_j$$  Because $\{\ket{u_1},\ldots,\ket{u_m}\}$ is [[Linear Algebra#^linear-independence-definition|linearly independent]], $u_m \neq \sum^{m-1}_{i=1}\mu_iu_i$. Hence, at least one of the $\mu_j$'s must be non-zero. Therefore, $m \leq n$. 
>   
>   The rest of the proof is not needed to prove unique length of basis vectors. Go do it yourself somewhere else.
>   ^exchange-lemma-proof

We can now prove that any two sets of linearly independent vectors that span a vector space contain the same number of elements. 

>[!proof]
>**Statement:**
>Let $U$ and $W$ be finite subsets of a vector space $V$, consisting of linearly independent vectors. If $U$ spans $V$, and $W$ spans $V$, then  $\vert U \vert$ = $\vert W \vert$.
>
>**Proof:**
>We proceed by contradiction. We assume that $U$ spans the vector space, and $W$ is linearly independent. By the exchange lemma, $|W| \leq |U|$.
>
>We then assume that  $W$ spans the vector space, and $U$ is linearly independent. By the exchange lemma, $|U| \leq |W|$. 
>
>We know both are true. Therefore, $|U| = |W|$.
>^dim-size-proof

>[!note]
>These linear independent vectors that span a vector space are called **Basis** vectors, and they form a **Basis** for $V$. The size of the basis is known as the dimension of the vector space
>^basis-definition


## Linear Operators and Matrices

>[!definition]
>A *linear operator* between vector spaces $V$ and $W$ is defined to be any function $A: V \to W$ which is linear in its inputs: $$A(\sum_ia_i\ket{v_i})=\sum_ia_iA(\ket{v_i})$$
>^linear-operator-definition

Usually, we write $A\ket{v}$ to $A(\ket{v})$. If a linear operator $A$ is defined *on* a vector space $V$, that actually means $A$ is a linear operator from $V$ to $V$.  ^adcdec

An important linear operator in any vector space $V$ is the identity operator, $I_V$, which has a property that $I_V\ket{v}=\ket{v}$ for all vectors $\ket{v}$. This is written as $I$. 

Another important linear operator is the *zero operator*. This one maps all vectors $\ket{v}$ to the [[Linear Algebra#^zero-ket-warning|zero vector]], $0$. 

Once the action of a linear operator of a linear operator $A$ on a basis of $V$ is specified, the action of $A$ is completely determined on all inputs. This is because when we take $\ket{v_i}$ to be vectors of a [[Linear Algebra#^basis-definition|basis]], all vectors in $V$ can be written as a linear combination $\sum_ia_i\ket{v_i}$ . Due to the linearity of a linear operator, this is equal to $\sum_ia_iA(\ket{v_i})$ , where $A(\ket{v_i})$ is the action of the linear operator on the basis. 

> [!note] Linear Operators are Matrices. 
> An  $m \times n$ complex matrix is a linear operator that sends vectors from $\mathbb{C}^m$ to $\mathbb{C}^n$. Suppose $A: V \to W$ is a linear operator between vector spaces $V$ and $W$. Suppose $\ket{v_1}, \ldots, \ket{v_m}$ is a basis for $V$ and $\ket{w_1}, \ldots, \ket{w_n}$ is a basis for $W$. Then for each $j$ in the range $1, \ldots, m$ there exist complex numbers $A_{1j}$ through $A_{nj}$ such that $$A\ket{v_j}=\sum_iA_{ij}\ket{w_i}$$Note that to make the connection between matrices and linear operators we must specify a set of input and output basis states for the input and output vector spaces of the linear operator.
> ^matrix-note

>[!example]
>Suppose V is a vector space with basis vectors  $\ket{0}$ and $\ket{1}$, and $A$ is a linear operator from  $V$ to $V$ such that $A\ket{0} = \ket{1}$ and $A\ket{1}=\ket{0}$. 
>The matrix representation of $A$:
>
>We first use the aforementioned matrix representation of a linear operator $A$: $$A\ket{v_j}=\sum_iA_{ij}\ket{w_i}$$ We have that
>$$
>\begin{aligned}
>A\ket{0} &\equiv \sum_iA_{i1}\ket{w_i} \\
>\ket{1} &= A_{11}\ket{0} + A_{21}\ket{1} \\
>&\Rightarrow A_{11} = 0, \ A_{21} = 1 \\ \\
>A\ket{1} &\equiv \sum_iA_{i2}\ket{w_i} \\
>\ket{0} &= A_{12}\ket{0} + A_{22}\ket{1} \\
>&\Rightarrow A_{12} = 1, \ A_{22} = 0
>\end{aligned}
>$$
>$$
>\Rightarrow A = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
>$$

>[!example]
>Suppose $A$ is a vector space from $V$ to $W$, and $B$ is a linear operator from vector space $W$ to $X$. Let $\ket{v_i}$, $\ket{w_j}$ and $\ket{x_k}$ be the bases for $V$, $W$, and $X$ respectively. Also, we assume they are the standard basis vectors. We will show that the matrix representation for the linear transformation $BA$ is the matrix product of the matrix representations of $B$ and $A$.
>
>$$
>\begin{aligned}
>(BA)\ket{v_i}&=B(\sum_jA_{ji}\ket{w_j}) \\
>&=\sum_jA_{ji}B\ket{w_j} \\
>&=\sum_jA_{ji}\sum_kB_{kj}\ket{x_k} \\
>&=\sum_{j, k}B_{kj}A_{ji}\ket{x_k}
>\end{aligned}
>$$
>Which is the matrix multiplication.

>[!example]
>The identity operator on a vector space $V$ , $I_V$, has a matrix representation which is $1$ along the diagonal and $0$ everywhere else.
>
>Let $\ket{v_i}$ be the basis vectors for $V$. We have that for $k$ spanning from $0, \ldots, j$:
>$$
>\begin{aligned}
>I\ket{v_k}&=\sum_{i=1}^jI_{ik}\ket{v_i} \\
>\ket{v_k} &= \sum_{i=1}^jI_{ik}\ket{v_i} \\
>\end{aligned}
>$$
>All vectors in the basis must be non-zero, and they must all be linearly independent. Hence,
>$$
>\begin{aligned}
>\ket{v_k} = I_{1k}\ket{v_1} + \ldots + I_{kk}\ket{v_k} + \ldots + I_{jk}\ket{v_j}
>\end{aligned}
>$$
>Hence,
>$$
>I_{ij} = \delta_{ij}
>$$
>^identity-example

## Inner Products

^e2db3c

An *Inner Product* is a function which takes two input vectors $\ket{v}$ and $\ket{u}$ and produces a complex number as an output. For now, we write the inner product to be $(\ket{v}, \ket{u})$. As covered [[Linear Algebra#^linalg-notation-table|before]], in quantum mechanics the inner product is denoted as $\langle v \vert u \rangle$.  ^d695c5

The aforementioned *dual* is a linear operator. It is a linear operator from the inner product space $V$ to the complex numbers  $\mathbb{C}$.

>[!definition]
>A function $(\cdot, \cdot)$ from $V \times V$ to $\mathbb{C}$ is an inner product if it satisfies the following requirements:
>1. $(\cdot, \cdot)$ is linear in the second argument. This means that  $$(\ket{v}, \sum_i \lambda_i\ket{w_i}) = \sum_i\lambda_i(\ket{v},\ket{w_i})$$
>2. $(\ket{v}, \ket{w}) = (\ket{w}, \ket{v})^*$
>3. $(\ket{v},\ket{v}) \geq 0$ with equality if and only if $\ket{v}=0$
>^inner-product-definition

^a74762

>[!note]
>In $\mathbb{C}^n$, the inner product is defined by $$(\ket{v}, \ket{w}) \equiv \sum_i v_i^*w_i = \ket{v}^\dagger \ket{w} = \bra{v}\ket{w}$$

The inner product is conjugate-linear in the first argument: $$(\sum_i\lambda_i\ket{w_i},\ket{v})=\sum_i\lambda_i^*(\ket{w_i},\ket{v})$$
>[!proof]
>$$
>\begin{aligned} & (\sum_i \lambda_i \ket{w_i}, \ket{v}) \\ &= (\ket{v}, \sum_i \lambda_i \ket{w_i})^* \\ &= (\sum_i \lambda_i (\ket{v}, \ket{w_i}))^* \\ &= \sum_i \lambda_i^* (\ket{v}, \ket{w_i})^* \\ &= \sum_i \lambda_i^* (\ket{w_i}, \ket{v}) \end{aligned}
>$$
>^conjugate-linear-proof

Everything in quantum mechanics is in a Hilbert Space. For the scope of these notes, a Hilbert Space is *exactly the same* as an inner product space.  ^ad6c5b

Vectors $\ket{v}$ and $\ket{w}$ are orthogonal if their inner product is zero. 

>[!definition]
>We define the norm of a vector by: $$||\ket{v}||=\sqrt{\langle v \vert v \rangle}$$
>^norm-definition

>[!note]
>A unit vector is  a  vector $\ket{v}$ such that $||\ket{v}||=1$. We say that such a vector is *normalised*. A set of vectors is *orthonormal* if each vector is a unit vector and distinct vectors in the set are orthogonal.  These vectors satisfy $\langle i \vert j \rangle = \delta_{ij}$ where $\delta_ij$ is the [[Nomenclature and Notation#^kronecker-delta-definition|Kronecker delta]].
>^orthonormal-note

### Gram-Schmidt Procedure

Suppose $\ket{w_1},\ldots,\ket{w_d}$ is a [[Linear Algebra#^basis-definition|basis set]] for some [[Nomenclature and Notation#^vector-spaces-notice|vector space]] $V$ with an [[Linear Algebra#^d695c5|inner product]]. 

The *Gram-Schmidt Procedure* produces an [[Linear Algebra#^orthonormal-note|orthonormal]] basis set $\ket{v_1},\ldots,\ket{v_d}$: $$\ket{v_{k+1}}=\frac{\ket{w_{k+1}}-\sum^k_{i=1}\langle v_i \vert w_{k+1}\rangle\ket{v_i}}{||\ket{w_{k+1}}-\sum^k_{i=1}\langle v_i \vert w_{k+1}\rangle\ket{v_i}||}$$
By using the  Gram-Schmidt Procedure, it can be shown that any finite dimensional vector space of dimension $d$ has an orthonormal basis. 

>[!warning]
>From now on, when we speak of a matrix representation for a linear operator, we mean a matrix representation with respect to orthonormal input and output bases. We also use the convention that if the input and output spaces for a linear operator are the same, then the input and output bases are the same, unless noted otherwise.
>^matrix-representation-notice

With these conventions,  the inner product on a Hilbert Space can be given a convenient matrix representation. Let $\ket{w}=\sum_iw_i\ket{i}$ and $\ket{v}=\sum_jv_j\ket{j}$ be representations of vectors  $\ket{w}$ and $\ket{v}$ with respect to some orthonormal basis  $\ket{i}$. Then, since $\langle i \vert j \rangle = \delta_{ij}$ :
$$
\begin{aligned}
\langle v \vert w \rangle &=  (\sum_iv_i\ket{i},\sum_jw_j\ket{j}) \\
&= \sum_i\sum_jv_i^*w_j(\ket{i},\ket{j}) = \sum_i\sum_jv_i^*w_j\langle i\vert j \rangle\\
&= \sum_iv_i^*w_i \\
&=
\begin{bmatrix}v_1^* \ldots v_n^*\end{bmatrix}\begin{bmatrix}w_1\\ \vdots \\ w_n\end{bmatrix}
\end{aligned}
$$
## Outer Products
>[!note]
>[[Linear Algebra#^linear-operator-definition|Linear operators]] can also be represented as an outer product. Suppose $\ket{v}$ is a vector in the [[Linear Algebra#^ad6c5b|inner product space]] $V$ and $\ket{w}$ is a vector in the inner product space $W$. We define $\ket{w}\bra{v}$ to be the linear operator acting from $V$ to  $W$ whose action is defined by  $$(\ket{w}\bra{v})(\ket{s})\equiv\ket{w}\langle v \vert s \rangle = \langle v \vert s \rangle\ket{w}$$
>^outer-product-definition

>[!note]
>By definition, $\sum_ia_i\ket{w_i}\bra{v_i}$ is the linear operator which produces $\sum_ia_i\ket{w_i}\langle v_i \vert s \rangle$ as output when applied on $\ket{s}$
>^outer-product-note

### Completeness Relation

Let $\ket{i}$ be any orthonormal basis for the vector space $V$ such that any vector $\ket{v}$ can be written as $\ket{v}=\sum_iv_i\ket{i}$ for some complex numbers $v_i$. Note that because it is an [[Linear Algebra#^orthonormal-note|orthonormal basis]], $\langle i \vert v \rangle = v_i$ and therefore
$$
(\sum_i\ket{i}\bra{i})\ket{v}=\sum_i\ket{i}\langle i \vert v \rangle = \sum_iv_i\ket{i}=\ket{v}
$$
Since the last equation is true for all $\ket{v}$, $$\sum_i\ket{i}\bra{i}=I$$What this says is that the sum of the outer products of the orthonormal basis is the identity. This gives us a means of representing every  linear operator  $A$ from $V$ to  $W$, or  $A: I \to  W$ . Suppose $\ket{v_i}$ is an orthonormal basis for $V$ and $\ket{w_i}$ is an orthonormal basis for $W$. Using the  completeness relation twice we obtain  $$A=I_WAI_V$$
>[!warning]
>It might be  confusing for some as in the general sense multiplication is read and done from left to right.  However, recalling to our definition of linear operators and matrices, those familiar with matrices should be able to realize that $I_WAI_V=I_W(A(I_V))$. Hence, we apply $A$ onto $I_V$ first to send the basis into the vector space $W$, and then apply $I_W$, which is [[Linear Algebra#^adcdec|defined on]] $W$.

This is equal to:
$$
\begin{aligned}
&=\sum_{i, j}\ket{w_j}\langle w_j \vert A  \vert v_i \rangle \bra{v_i} \\
&=\sum_{i, j}\langle w_j \vert A  \vert v_i \rangle \ket{w_j}\bra{v_i}
\end{aligned}
$$
And this is the matrix representation of a linear operator. We exploited the completeness relation and how scalar multiplication is commutative. 



The completeness relation is also used to prove the very famous Cauchy-Schwarz inequality that every competition mathematician knows: ^6a978f
$$
\begin{aligned}
\langle v \vert v \rangle \langle w \vert w \rangle  &= \sum^i \langle v \vert i \rangle \langle i \vert v \rangle \langle w \vert w \rangle \\
&\geq \frac{\langle v \vert w \rangle \langle w \vert v \rangle}{\langle w \vert w \rangle}\langle w \vert w \rangle =\langle v \vert w \rangle \langle w \vert v \rangle =|\langle v \vert w \rangle|^2 
\end{aligned}
$$
With equality when $\ket{v}$ and  $\ket{w}$ when $\ket{v}$ and $\ket{w}$ are linearly related (parallel). In other words, equality is achieved when  $\ket{v}=z\ket{w}$  for some scalar $z$.

## Eigenthings: Eigenvectors and Eigenvalues

>[!definition] Definition: Eigenvectors and Eigenvalues
>An *eigenvector* of a [[Linear Algebra#^linear-operator-definition|linear operator]] $A$ on a [[Nomenclature and Notation#^vector-spaces-notice|vector space]] is a non-zero vector $\ket{v}$ such that $A\ket{v}=v\ket{v}$ where $v$ is a complex number known as the *eigenvalue* of A corresponding to $\ket{v}$
>^eigen-definition

>[!definition] Definition:  Characteristic Function
>The *characteristic function* is defined to be $c(\lambda)\equiv \operatorname{det}|A-\lambda I|$ where  $\operatorname{det}$ is the *determinant* function for matrices. 
>
>The characteristic function depends only on the operator $A$ and not the matrix representation. 
>
>The solutions of the *characteristic equation* $c(\lambda) = 0$ are the eigenvalues of the operator $A$. Every operator $A$ has at least one eigenvalue (fundamental theorem of algebra), and a corresponding eigenvector.
>^characteristic-function-definition

>[!definition]  Definition: Eigenspaces
>The *eigenspace* corresponding to an eigenvalue $v$ is the set of vectors which have eigenvalue $v$. It is a subspace of the subspace on which $A$ acts, by the previous definitions. 

>[!note]
>A *diagonal representation* for an operator $A$ on a vector space $V$ is a representation $$A=\sum_i\lambda_i\ket{i}\bra{i}$$, where the vectors  $\ket{i}$ form an orthonormal set of eigenvectors for $A$, with corresponding eigenvalues $\lambda_i$.  These representations are also sometimes known as *orthonormal decompositions*.
>^diagonal-note

When an eigenspace has more than one dimension we say it is *degenerate*.  Funny I know. ^941241

>[!example]
>Lets find the eigenvalues and eigenvectors of the matrix,
>$$
>A = \begin{bmatrix}
>2 & 0 & 0 \\
>0 & 2 & 0 \\
>0 & 0 & 0
>\end{bmatrix}
>$$ 
>The characteristic function is,
>$$
>c(\lambda) := \begin{vmatrix}
>2 - \lambda & 0 & 0 \\
>0  & 2 - \lambda & 0 \\
>0 & 0 & -\lambda
>\end{vmatrix} = 0
>$$
>The determinant is easy to compute,
>$$
>\begin{vmatrix}
>2 - \lambda & 0 & 0 \\
>0  & 2 - \lambda & 0 \\
>0 & 0 & -\lambda
>\end{vmatrix} = (2-\lambda)\begin{vmatrix}2 - \lambda & 0 \\ 0 & -\lambda \end{vmatrix} = (2-\lambda)(2-\lambda)(-\lambda)
>$$
>Hence, the eigenvalues are:  $$\lambda_1 = 2, \ \lambda_2 = 0$$
>
>We will now find the eigenvectors corresponding to the eigenvalue  $\lambda_1 = 2$. We solve the characteristic equation $(A-\lambda I)\ket{v}=0$:
>$$
>\begin{bmatrix}
>0 & 0 & 0 \\
>0 & 0 & 0 \\
>0 & 0 & -2
>\end{bmatrix}
>\begin{bmatrix}
>v_1 \\ v_2 \\ v_3
>\end{bmatrix}
>= 0
>$$
>From this we obtain:
>$$
>v_3 = 0, \ v_1, v_2 \in \mathbb{C}
>$$
>Hence the eigenspace is spanned by two vectors $\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$ and $\begin{bmatrix}0 \\ 1 \\ 0\end{bmatrix}$. This eigenspace has a dimension of $2$ and is therefore degenerate.
>

## Adjoint and Hermitian Operators

Suppose $A$ is a linear operator [[Linear Algebra#^adcdec|on]] a Hilbert Space, $V$. There exists a unique linear operator $A^\dagger$ on  $V$ such that for all vectors $\ket{v},\ket{w} \in V$: $$(\ket{v},A\ket{w})=(A^\dagger\ket{v},\ket{w})$$ This $A^\dagger$ linear operator is known as the *adjoint* or *Hermitian conjugate* of the operator $A$. It is defined as $A^\dagger=(A^T)^*$.Furthermore, $(AB)^\dagger=B^\dagger A^\dagger$: 
$$
(\ket{v}, (BA)\ket{w})= ((BA)^\dagger \ket{v}, \ket{w})

$$

$$
\begin{aligned}
(\ket{v}, (BA)\ket{w}) &= (B^\dagger \ket{v}, A\ket{w}) \\
&= ((A^\dagger B^\dagger)\ket{v}, \ket{w})
\end{aligned}
$$

>[!note]
>$(A\ket{v})^\dagger = \bra{v}A^\dagger$


>[!note]
>If $\ket{v}$ and $\ket{w}$ are any two vectors, $(\ket{w}\bra{v})^\dagger=\ket{v}\bra{w}$
>^hermitian-swapping-note


>[!note]
>The adjoint is anti-linear:
>$$(\sum_ia_iA_i)^\dagger=\sum_ia_i^*A_i^\dagger$$


>[!proof] Proof: $(A^\dagger)^\dagger=A$
>By definition, the adjoint satisfies $$(\ket{v},A\ket{w})=(A^\dagger\ket{v},\ket{w})$$ $$ \begin{aligned} (\ket{v}, A\ket{w}) &= (A^\dagger \ket{v}, \ket{w}) \\ &= (\ket{v}, (A^\dagger)^\dagger\ket{w}) \end{aligned} $$
>


>[!definition]
>An operator  $A$ whose adjoint is itself is known as a  *Hermitian* or *self-adjoint* operator.
>
>A unitary matrix is a complex square matrix where the inverse is equal to its Hermitian transpose, or $$U^{-1}=U^\dagger$$

An important class of Hermitian Operators are the Projectors. Suppose $V$ is a $d$ dimensional vector space, and $W$ is a $k$ dimensional vector subspace of $V$. Using the Gram-Schmidt procedure produces an orthonormal basis $\ket{1},\ldots,\ket{d}$ for $v$ such that $\ket{1},\ldots,\ket{k}$ is an orthonormal basis for $W$. We define the projectors to be $$P \equiv\sum_{i=1}^k\ket{i}\bra{i}$$ This definition is independent of the orthonormal basis used for $W$. 

>[!proof] For all vectors $\ket{v}$, $\ket{v}\bra{v}$ is Hermitian
>Consider another arbitrary vector $\ket{w}$. Because $(\ket{v}\bra{w})^\dagger = (\ket{w}\bra{v})$ then $$(\ket{v}\bra{v})^\dagger = (\ket{v}\bra{v})$$
>Because any hermitian operator $A$ satisfies $A^\dagger = A$, $\ket{v}\bra{v}$ is also hermitian.

Using the above, we can conclude that projectors are also Hermitian operators.

Sometimes the 'vector space' $P$ is used to mean the vector space onto which $P$ is a projector, i.e. the $W$ where $P: I \to W$.

The *orthogonal complement* of $P$ is the operator $Q \equiv I - P$. Because $I = \sum_{i=0}^d \ket{i}\bra{i}$, it is easy to see that $Q$ is a projector onto the vector space spanned by $\ket{k+1},\ldots,\ket{d}$, or in other words, $Q\equiv \sum^d_{i=k+1}\ket{i}\bra{i}$.


>[!proof] All Projectors $P$ satisfy $P^2 = P$
>Using the definition $P\equiv \sum^k_{i=1}\ket{i}\bra{i}$, we can expand $P^2$ into 
>$$
>\begin{aligned}
>P^2 &= (\sum^k_{i=1}\ket{i}\bra{i})(\sum^k_{j=1}\ket{j}\bra{j}) \\
>P^2 &= \sum^k_{i=1}\sum^k_{j=1}\ket{i}\bra{i}\ket{j}\bra{j}
>\end{aligned}
>$$
>Because each basis vector $\ket{i}$ is part of an orthonormal basis:
>$$\langle i \vert j \rangle = \delta_{ij}$$
>Hence,
>$$
>\begin{aligned}
>P^2 &= \sum^k_{i=1}\sum^k_{j=1}\ket{i} \langle i \vert j \rangle \bra{j} \\
>&= \sum^k_{i=1}\sum^k_{j=1} \ket{i}\delta_{ij}\bra{j} \\
>&= \sum^k_{i=1}\ket{i}\bra{i} \\
>&= P
>\end{aligned}
>$$

An operator is said to be normal if $AA^\dagger = A^\dagger A$. An operator which is Hermitian is also normal.

>[!proof] An operator which is Hermitian is also normal
>This is because Hermitian operators satisfy $A = A^\dagger$ so $AA^\dagger = AA = A^\dagger A$

There is something called *spectral decomposition* for normal operators, which states that an operator is a normal operator *if and only if* it is [[Linear Algebra#^diagonal-note|diagonalizable]]. 

>[!proof] Spectral Decomposition
>**Theorem**: Any normal operator $M$ on a vector space $V$ is diagonal with respect to some orthonormal basis for $V$. Conversely, any diagonalizable operator is normal.
>
>We will first prove the converse due to its simplicity. A diagonalizable operator has a diagonal matrix representation, lets call this $X$. From the definition of a diagonal matrix, $A^\dagger = (A^T)^* = A^*$, where $A^*$ is also a diagonal matrix. Again, because diagonal matrices commute, $AA^\dagger = A^\dagger A$ so diagonalizable operators are normal.
>
>We then prove the forward implication. Suppose the dimension of $V$ is $d$. We proceed  by induction.
>
>>[!proof] The Base Case: $d = 1$. 
>>This is trivial. A $1$ dimensional vector space contains all the scalars, so of course any normal operator on the scalars is diagonalizable because the matrix will only have one entry.
>
>We let:
>- $\lambda$ be an eigenvalue of the normal operator $M$
>- $P$ be the projector onto the eigenspace of $\lambda$. That is, if the dimension of the eigenspace of $\lambda$ is $k$, equivalently the eigenspace of $\lambda$ can be spanned by $k$ linearly independent vectors, then $P\equiv \sum_{i=1}^k \ket{i}\bra{i}$ where $\ket{i}$ forms an orthonormal basis for $V$.
>  
> Then, because $P+Q=I$, $$\begin{aligned}M &= (P+Q)M(P+Q) \\ &= PMP + QMP + PMQ + QMQ\end{aligned}$$
> 
> $PMP=\lambda P$ because the eigenspace consists of all vectors satisfying $M\ket{v}=\lambda \ket{v}$. Because the projector $P$ maps any vector $\ket{v}$ into this eigenspace, $P\ket{v}$ is in the eigenspace. Hence $MP\ket{v}=\lambda P\ket{v}$. Therefore $PMP = P\lambda P = \lambda P^2 = \lambda P$.
> 
> $QMP = 0$ because $MP = \lambda P$, so $QMP = \lambda QP$. Because $Q$ is the orthogonal complement to $P$, $QP = 0$ and thus $QMP = 0$.
> 
> Furthermore, $PMQ = 0$. 
> >[!proof] $PMQ = 0$
> >Let $\ket{v}$ be an element of the subspace $P$. Then,
> >$$
> >\begin{aligned}
> > MM^\dagger \ket{v} &= M^\dagger M\ket{v} &\text{Because $M$ is normal} \\
> > &= \lambda M^\dagger \ket{v} &\text{Hence, $M^\dagger$ has eigenvalue $\lambda$ and is a member of the subspace $P$}
> >\end{aligned}
> >$$
> >Through the same reasoning as to why $QMP = 0$, it follows that $QM^\dagger P = 0$.  Taking the adjoint of both sides gives $PMQ = 0$ because $(QM^\dagger P)^\dagger = (M^\dagger P)^\dagger Q^\dagger = P^\dagger {M^\dagger}^\dagger Q^\dagger$. Because $P$ and $Q$ are both Projectors and therefore Hermitian, $(QM^\dagger P)^\dagger = PMQ$
> 
> Hence, $M = PMP + QMQ$. Next, we prove that $QMQ$ is normal.
> >[!proof] $QMQ$ is Normal
> >Note that $$QM = QMI = QM(P+Q)=QMP + QMQ = 0 + QMQ =  QMQ$$ and
> >$$QM^\dagger = QM^\dagger I = QM^\dagger (P + Q) = QM^\dagger P + QM^\dagger Q = QM^\dagger Q$$ We proceed by considering $QMQ \ QM^\dagger Q$, and we aim to show it equals the adjoint of itself, $QM^\dagger Q \ QMQ$
> >$$
> >\begin{aligned}
> >QMQQM^\dagger Q &= QMQM^\dagger Q \\
> >&= QMM^\dagger Q \\
> >&= QM^\dagger Q MQ \\
> >&= QM^\dagger Q QMQ
> >\end{aligned}
> >$$
> >So $QMQ$ is normal. 
>
> The inductive hypothesis assumes that all normal operators on vector spaces of dimension $< d$ are diagonalizable. By induction, $QMQ$ is diagonal with respect to some orthonormal basis for the subspace $Q$, because the dimension of $Q$ is strictly less than $d$. Also, $PMP$ is already diagonal with respect to some orthonormal basis for P, because $PMP = \lambda P$, so in any orthonormal basis $PMP = \lambda I$ because $PMP$ acts as scalar multiplication on any vector in the subspace $P$, i.e. $PMP\ket{v} = \lambda \ket{v}$. It follows that $M = PMP + QMQ$ is also diagonal with respect to some orthonormal basis for the total vector space.

^fd210b

In terms of the outer product representation, this means that $M$ can be written as $M=\sum_i \lambda_i \ket{i}\bra{i}$, where $\lambda_i$ are the eigenvalues of $M$, $\ket{i}$ is an orthonormal basis for $V$, and each $\ket{i}$ and eigenvector of $M$ with eigenvalue $\lambda_i$. In terms of projectors, $M = \sum_i \lambda_i P_i$ where $\lambda_i$ are again the eigenvalues of $M$, and $P_i$ the projector onto the $\lambda_i$ eigenspace of $M$. These projectors satisfy the completeness relation $\sum_i P_i = I$ and the orthonormality relation $P_iP_j = \delta_{ij}P_i$

>[!proof] A normal matrix is Hermitian if and only if it has real eigenvalues
>We first prove the forward implication that a normal matrix that is Hermitian means it has real eigenvalues.
>
>Let $M$ be Hermitian, that $M = M^\dagger$, and normal, that $MM^\dagger = M^\dagger M$. For any eigenvalue $\lambda$ of $M$ with eigenvector $\ket{v}$:
>$$Mv = \lambda \ket{v} \Longrightarrow \bra{v}M^\dagger = \lambda^* \bra{v}$$
>By taking the Hermitian transpose on both sides. Substituting $M = M^\dagger$ gives: 
>$$\bra{v}M = \lambda^* \bra{v}$$
>Multiplying $M\ket{v}=\lambda \ket{v}$ by $\bra{v}$:
>$$
>\begin{aligned}
>&\bra{v}M\ket{v} &\text{and} &\bra{v}M\ket{v}=\lambda^*\bra{v}\ket{v}
>\end{aligned}
>$$
>Therefore, $\lambda^* = \lambda$ and so $\lambda$ must be real.
>
>Then, we prove the converse, that a normal operator with real eigenvalues is Hermitian. Let $M$ be normal with all real eigenvalues. By the spectral decomposition, it is also diagonalizable: $$M = UXU^\dagger$$ Taking the Hermitian transpose of both sides yields: $$M^\dagger = (UXU^\dagger)^\dagger = UX^\dagger U^\dagger$$ Because $X$ is real (since it contains the eigenvalues) and is diagonalizable, $X^\dagger = X$. Thus: $$M^\dagger = UXU^\dagger = M$$ And so a normal operator with real eigenvalues is Hermitian.

>[!definition]
>A operator, or matrix, $U$ is said to be *unitary* if $U^\dagger U = I$. An operator is unitary if and only if each of its matrix representations is unitary.
>
>A unitary operator also satisfies $UU^\dagger = I$, and therefore $UU^\dagger = U^\dagger U = I$ and therefore $U$ is normal and has a spectral decomposition. 
>^unitary-definition

>[!note]
>Unitary Operators preserve inner products between vectors. Let $\ket{v}$ and $\ket{w}$ be any two vectors. Then the inner product of $U\ket{v}$ and $U\ket{w}$ is the same as the inner product of $\ket{v}$ and $\ket{w}$: $$(U\ket{v}, U\ket{w}) = \langle v \vert U^\dagger U \vert w \rangle = \langle v \vert I \vert w \rangle = \langle v \vert w \rangle$$
>^preserve-inner-product-note

This brings about a rather elegant outer product representation of any unitary $U$. Let $\ket{v_i}$ be any orthonormal basis set. Define $\ket{w_i}\equiv U\ket{v_i}$ so $\ket{w_i}$ is also an orthonormal basis set, since unitary operators preserve inner products. A unitary can be expressed as: $$U \equiv \sum_i \ket{w_i} \bra{v_i}$$
>[!proof] $U \equiv \sum_i \ket{w_i} \bra{v_i}$ is Unitary
>[[Linear Algebra#^hermitian-swapping-note|Because the Hermitian transpose swaps the order of the outer product]], $U^\dagger = \sum_i \ket{v_i} \bra{w_i}$. By multiplying $U^\dagger$ and $U$:
>$$
>\begin{aligned}
>U^\dagger U &= (\sum_i \ket{v_i}\bra{w_i})(\sum_j \ket{w_j}\bra{v_j}) \\
>&= \sum_{i, j} \ket{v_i} \underbrace{\langle w_i \vert w_j \rangle}_{\delta_{ij}} \bra{v_j} \\
>&= \sum_i \ket{v_i}\bra{v_i} \\
>&= I \quad \text{(Completeness Relation)} \\
>\end{aligned}
>$$

>[!proof] All eigenvalues of a unitary matrix have modulus 1
>Consider an eigenvalue $\lambda$ of unitary operator $U$ and its corresponding eigenvector $\ket{v}$. These values satisfy $U\ket{v}=\lambda\ket{v}$.
>
>Because unitary operators preserve inner products, $(U\ket{v}, U\ket{v}) = \langle v \vert v \rangle$. Substituting $U\ket{v}=\lambda\ket{v}$ gives: 
>$$
>\begin{aligned}
>(U\ket{v}, U\ket{v}) &= $(\lambda \ket{v}, \lambda \ket{v}) \\
>&= \lambda^2 \langle v \vert v \rangle \\
>&\Longrightarrow \lambda^2 \langle v \vert v \rangle = \langle v \vert v \rangle \\
>&\Longrightarrow \lambda^2 = 1 \\
>&\Longrightarrow |\lambda| = 1 \\
>\end{aligned}
>$$

>[!note] Basis Changes
> Suppose $A'$ and $A''$ are matrix representations on a vector space V with respect to two orthonormal bases, $\ket{v_i}$ and $\ket{w_i}$. Then the elements of $A'$ and $A''$ are $A'_{ij}=\langle v_i \vert A \vert v_j \rangle$ and $A''_{ij}=\langle w_i \vert A \vert w_j \rangle$. Using unitary operators, $\ket{w_i} \equiv U\ket{v_i}$. Then,
> $$
> \begin{aligned}
> A''_{ij} &= \langle w_i \vert A \vert w_j \rangle \\
> &= \langle Uv_i \vert A \vert Uv_j \rangle \\
> &= \langle v_i \vert U^\dagger A U \vert v_j \rangle \\
> &= (U^\dagger A' U)_{ij}
> \end{aligned}
> $$
> Hence, $A'' = U^\dagger A' U$

>[!proof] Eigenvectors of different eigenvalues of Hermitian Operators are necessarily orthogonal.
>Consider a Hermitian Operator $H$, so $H^\dagger = H$, with eigenvectors $\ket{v_1}$, $\ket{v_2}$ corresponding to eigenvalues $\lambda_1$ and $\lambda_2$ such that $\lambda_1 \neq \lambda_2$. Then:
>$$
>\begin{aligned}
>\langle v_1 \vert H \vert v_2 \rangle &= \lambda_2 \langle v_1 \vert v_2 \rangle \\
>\langle v_1 \vert H \vert v_2 \rangle &= \langle H^\dagger v_1 \vert v_2 \rangle = \lambda_1 \langle v_1 \vert v_2 \rangle \\
>\text{Taking the difference yields:} \\
>(\lambda_1 - \lambda_2)\langle v_1  \vert v_2 \rangle &= 0
>\end{aligned}
>$$
>Since $\lambda_1 \neq \lambda_2$, it follows that $\langle v_1 \vert v_2 \rangle$ = 0. Hence, $\ket{v_1}$ and $\ket{v_2}$ are orthogonal.

>[!proof] Eigenvalues of a Projector $P$ are all either 0 or 1.
>We consider a projector $P$ ($P^2 = P$) and an eigenvector  $\ket{v}$ with eigenvalue $\lambda$, so $P\ket{v} = \lambda \ket{v}$. Applying $P$ again gives $P^2 \ket{v} = \lambda^2 \ket{v}$. Hence, $\lambda^2 \ket{v} = \lambda \ket{v} \Longrightarrow \lambda (\lambda - 1) = 0$, so either $\lambda = 0$ or $\lambda = 1$

	A special subclass of Hermitian operators is extremely important. These are the *positive operators*.

>[!definition] Positive Operators
>A positive operator $A$ is defined to be an operator such that for any vector $\ket{v}$, $(\ket{v}, A\ket{v})$ is a real, non-negative number.
>
>If $(\ket{v}, A\ket{v})$ is strictly greater than zero for all $\ket{v} \neq 0$, then we say that $A$ is *positive definite*. Any positive operator is automatically Hermitian, and therefore by [[Linear Algebra#^6b5ff1|spectral decomposition]] has [[Linear Algebra#^diagonal-note|diagonal representation]] with non-negative eigenvalues.

^da9bf1

>[!proof] Positive operators are necessarily Hermitian.
>We know that every operator has a matrix representation $$A\ket{v_j}=\sum_iA_{ij}\ket{w_i}$$
>Because $A_{ij} \in \mathbb{C}$, $A_{ij} = B_{ij} + iC_{ij}$ for $B_{ij}, C_{ij} \in \mathbb{R}$.
>
>We use the construction that $B = \frac{A+A^\dagger}{2}$ and $C = \frac{A-A^\dagger}{2i}$. Hence, $$A = \frac{A+A^\dagger}{2} + \frac{A-A^\dagger}{2} = A$$
>
>We will then prove $B$ and $C$ are Hermitian. $$B^\dagger = \frac{A^\dagger + A}{2} = B$$ $$C^\dagger = \frac{A - A^\dagger}{2i} = C$$
>
>$A$ is positive, and $B$ and $C$ are Hermitian operators defined as above. $$\langle x|C x \rangle=\langle C^\dagger x| x\rangle = \langle C x|x \rangle=\langle x|C x \rangle^* \; \Rightarrow \; \langle x|C x \rangle \in \mathbb{R}$$
>Since $A$ is positive $\langle x \vert Ax \rangle = \langle x \vert Bx \rangle + i \langle x \vert Cx \rangle$, so $\langle x| C x\rangle = 0$ for all $\ket{x} \in V$ and thus $C = 0$ Therefore $A = B$, which is Hermitian.

>[!proof] For any operator $A$, $A^\dagger A$ is positive.
> We compute the inner product with a vector $\ket{v}$, $(\ket{v}, A^\dagger A \ket{v})$.
> 
> $$
> \begin{aligned}
> (\ket{v}, A^\dagger A \ket{v}) &= \langle v \vert A^\dagger A v \rangle \\
> &= \langle Av \vert Av \rangle \\
> &= ||A\ket{v}|| \geq 0
> \end{aligned}
> $$
> Which is the squared [[Linear Algebra#^norm-definition|norm]] of the vector $A\ket{v}$, which is always non-negative. Hence, for any operator, $A^\dagger A$ is [[Linear Algebra#^da9bf1|positive]].
> 

## Tensor Products

The *tensor product* is a way of putting vector spaces together to form larger vector spaces. 

>[!definition]
>Suppose $V$ and $W$ are Hilbert spaces of dimension $m$ and $n$ respectively. $V \otimes W$ is an $mn$ dimensional vector space. The elements of $V \otimes W$ are linear combinations of $\ket{v} \otimes \ket{w}$ where $\ket{v} \in V$ and $\ket{w} \in W$. If $\ket{i}$ and $\ket{j}$ are orthonormal bases for $V$ and $W$ then $\ket{i} \otimes \ket{j}$ is a basis for $V \otimes W$.
>
>The tensor product is often abbreviated as $\ket{v}\ket{w}$, $\ket{v, w}$ or $\ket{vw}$.

>[!note] The tensor product satisfies the following properties:
>For arbitrary scalar $z \in \mathbb{C}$ and vectors $\ket{v} \in V$ and $\ket{w} \in W$: 
>$$z(\ket{v} \otimes \ket{w})= (z\ket{v}) \otimes (z\ket{w})$$
>For arbitrary vectors $\ket{v_1}, \ket{v_2} \in V$ and $\ket{w} \in W$:
>$$(\ket{v_1}+\ket{v_2}) \otimes \ket{w} = \ket{v_1} \otimes \ket{w} + \ket{v_2} \otimes \ket{w}$$
>For arbitrary vectors $\ket{v} \in V$ and $\ket{w_1}, \ket{w_2} \in W$:
>$$\ket{v} \otimes (\ket{w_1} + \ket{w_2}) = \ket{v} \otimes \ket{w_1} + \ket{v} \otimes \ket{w_2}$$

Linear operators can also act on the tensor product vector space $V \otimes W$. Suppose $\ket{v}$ and $\ket{w}$ are vectors in $V$ and $W$, and $A$ and $B$ are linear operators on $V$ and $W$ respectively. Then we can define a linear operator $A \otimes B$ on $V \otimes W$ by: $$(A \otimes B)(\ket{v} \otimes \ket{w})\equiv A\ket{v} \otimes B\ket{w}$$
This definition is extended linearly, such that:
$$(A \otimes B)(\sum_i a_i\ket{v_i} \otimes \ket{w_i})\equiv \sum_i a_iA\ket{v_i} \otimes B\ket{w_i}$$
$A \otimes B$ defined in this way is a well defined linear operator. This extends to the case where $A: V \to V'$ and $B: W \to W'$ map between different vector spaces. 

An arbitrary linear operator $C$ mapping $V \otimes W$ to $V' \otimes W'$ can be represented as a linear combination of tensor products of operators mapping $V$ to $V'$ and $W$ to $W'$: $$\sum_i c_iA_i \otimes B_i$$
>[!definition]
The inner products on the spaces $V$ and $W$ can be used to define an inner product on $V \otimes W$. We define
$$(\sum_ia_i\ket{v_i}\otimes\ket{w_i},\sum_ib_j\ket{v'_j}\otimes\ket{w'_j})\equiv\sum_{i,j}a^*_ib_j\langle v_i\vert v'_j \rangle \langle w_i \vert w'_j \rangle$$
>
This is also a well defined inner product. this inherits ideas of an adjoint, unitarity, normality, and Hermicity.
>^tensor-inner-product-definition


The tensor product can be made more concrete through the *Kronecker Product*. Suppose $A$ is an $m$ by $n$ matrix, and $B$ is a $p$ by $q$ matrix. Then we have the matrix representation:
$$A \otimes B = \overbrace{\left.\begin{bmatrix}A_{11}B & A_{12}B & \cdots & A_{1n}B \\ A_{21}B & A_{22}B & \cdots & A_{2n}B  \\ \vdots & \vdots & \ddots & \vdots \\ A_{m1}B & A_{m2}B & \cdots & A_{mn}B \end{bmatrix} \right\}}^{nq}mp$$
For example,
$$\ket{01}=\ket{0}\otimes\ket{1}=\begin{bmatrix}1 \\ 0\end{bmatrix} \otimes \begin{bmatrix}0 \\ 1\end{bmatrix} = \begin{bmatrix}1 \times \begin{bmatrix}0 \\ 1\end{bmatrix} \\ \\ 0 \times \begin{bmatrix}0 \\ 1\end{bmatrix}\end{bmatrix}= \begin{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix} \\ \\ \begin{bmatrix}0 \\ 0\end{bmatrix}\end{bmatrix}=\begin{bmatrix}0 \\ 1 \\ 0 \\ \end{bmatrix}$$

>[!note]
>The notation $\ket{\varphi}^{\otimes k}$ means $\ket{\varphi}$ tensored with itself $k$ times.
>^tensor-notation-note

>[!proof] The Hadamard Transform $H^{\otimes n}$ can we written as $\frac{1}{\sqrt{2^n}}\sum_{x,y}(-1)^{x \cdot y} \ket{x}\bra{y}$
>
>We proceed by a proof by induction. For the base case, where $n = 1$: $$\begin{aligned} \frac{1}{\sqrt{2}}\sum_{x,y}(-1)^{x \cdot y} \ket{x}\bra{y} &= \frac{1}{\sqrt{2}}\left(\ket{0}\bra{0} + \ket{0}\bra{1} + \ket{1}\bra{0} - \ket{1}\bra{1}\right) \\ &= \frac{1}{\sqrt{2}}\left[\left(\ket{0} + \ket{1}\right)\bra{0} + \left(\ket{0} - \ket{1}\right)\bra{1}\right] \\ &= H \end{aligned}$$
>
>For the inductive step, we assume it is true for $n = k$, and wish to prove it is true for $n = k + 1$.
>$$
>\begin{aligned}
>H^{\otimes k+1} &= H^{\otimes k} \otimes H \\
>&\text{By the inductive hypothesis} \\
>&= \left( \frac{1}{\sqrt{2^k}}\sum_{m,n}\left(-1\right)^{m \cdot n}\ket{m}\bra{n} \right) \otimes \left( \frac{1}{\sqrt{2}}\sum_{p, q} \left( -1 \right)^{p \cdot q}\ket{p}\bra{q} \right) \\
>&= \frac{1}{\sqrt{2^{k+1}}} \sum_{\substack{p, q \\ m, n}} \left( -1 \right)^{m \cdot n + p \cdot q} \ket{mp}\bra{nq}
>\end{aligned}
>$$


## Operator Functions

There are many important functions that are defined on operators and matrices. Generally speaking, given a function $f$ from the complex numbers to the complex numbers, it is possible to construct a corresponding matrix function on normal matrices (or some subclass, like Hermitian matrices) by the following construction. Let $A = \sum_a a\ket{a}\bra{a}$ be a spectral decomposition for a normal operator. Then, we define $f(A) = \sum_a f(a)\ket{a}\bra{a}$. This 
procedure can be used to define the square root of a positive operator.

For example, $$\operatorname{exp}(\theta Z) = \begin{bmatrix}e^\theta & 0 \\ 0 & e^{-\theta}\end{bmatrix}$$
>[!proof] Square Root and Logarithm of $M = \begin{bmatrix}4 & 3 \\ 3 & 4\end{bmatrix}$
>
>First, we will solve for its eigenvalues. We solve for the characteristic equation $\operatorname{det}(M - \lambda I) = 0$: 
>$$
>\begin{aligned}
>\begin{vmatrix}
>4 - \lambda & 3 \\ 
>3 & 4 - \lambda
>\end{vmatrix} = (4-\lambda)^2 - 9 &= 0 \\
>(4-\lambda)^2 &= 9 \\
>4-\lambda &= \pm 3 \\
>& \lambda = 7, \ \lambda = 1
>\end{aligned}
>$$
>
>Then we will solve for the eigenvectors of each eigenvalue. We solve the characteristic equation $(A-\lambda I)\ket{v}=0$. 
>$$
>A - \lambda I = \begin{bmatrix} 4 - \lambda & 3 \\ 3 & 4 - \lambda\end{bmatrix}
>$$
>$$
>\begin{aligned}
>\begin{bmatrix} 4 - 1 & 3 \\ 3 & 4 - 1 \end{bmatrix} &= \begin{bmatrix} 3 & 3 \\ 3 & 3 \end{bmatrix} \\ \\
>\begin{bmatrix} 3 & 3 \\ 3 & 3 \end{bmatrix} \begin{bmatrix} v_1 \\ v_2 \end{bmatrix} &= 0 \\ \\
>\Rightarrow \begin{bmatrix} 3v_1 + 3v_2 \\ 3v_1 + 3v_2 \end{bmatrix} &= 0 \\ \\
>\Rightarrow v_1 = -v_2, \ \text{and hence an eigenbasis is $\begin{bmatrix}1 \\ -1\end{bmatrix}$.}
>\end{aligned}
>$$
>A similar process is done to obtain the other eigenvector for $\lambda = 7$, $\begin{bmatrix}1 \\ 1\end{bmatrix}$.  Hence, the spectral decomposition is $A = \frac{7}{2} \begin{bmatrix}1 & 1 \\ 1 & 1\end{bmatrix} + \frac{1}{2}\begin{bmatrix}1 & -1 \\ -1 & 1\end{bmatrix}$
>
>Hence, the square root is applied to the eigenvalues and we obtain $$\sqrt{A} = \frac{\sqrt{7}}{2} \begin{bmatrix}1 & 1 \\ 1 & 1\end{bmatrix} + \frac{1}{2}\begin{bmatrix}1 & -1 \\ -1 & 1\end{bmatrix} \\ = \frac{1}{2} \begin{bmatrix} \sqrt{7} + 1 & \sqrt{7} - 1 \\ \sqrt{7} - 1 & \sqrt{7} + 1 \end{bmatrix}$$
>
>Similarly, the logarithm is applied to the eigenvalues.

>[!proof] $\operatorname{exp}(i\theta \vec{v}\cdot\vec{\sigma}) = \cos(\theta)I + i\sin(\theta)\vec{v}\cdot\vec{\sigma}$ where $\vec{v}\cdot\vec{\sigma} \equiv \sum_{i=1}^3 v_i \sigma_i$ and $\vec{v}$ is a three dimensional real unit vector.
>We will first proceed by proving that $\vec{v}\cdot\vec{\sigma}$ is a unitary matrix with eigenvalues $-1$ and $1$. 
>Listing out the Pauli Matrices:
>$$
>\begin{aligned}
>\sigma_1  = \sigma_x = \begin{bmatrix}0 & 1 \\ 1 & 0\end{bmatrix} \\
>\sigma_2  = \sigma_y = \begin{bmatrix}0 & -i \\ i & 0\end{bmatrix} \\
>\sigma_3  = \sigma_z = \begin{bmatrix}1 & 0 \\ 0 & -1\end{bmatrix}
>\end{aligned}
>$$
>By explicitly writing out $\sum_{i=1}^3 v_i \sigma_i$:
>$$
>\begin{aligned}
>\sum_{i=1}^3 v_i \sigma_i &= v_1 \sigma_x + v_2 \sigma_y + v_3 \sigma_z \\ \\
>&= v_1 \begin{bmatrix}0 & 1 \\ 1 & 0\end{bmatrix} + v_2 \begin{bmatrix}0 & -i \\ i & 0\end{bmatrix} + v_3 \begin{bmatrix}1 & 0 \\ 0 & -1\end{bmatrix} \\ \\
>&= \begin{bmatrix} v_3 & v_1 - i v_2 \\ v_1 + i v_2 & -v_3 \end{bmatrix}
>\end{aligned}
>$$
>We then compute the adjoint of this matrix:
>$$
>\begin{bmatrix} v_3 & v_1 - i v_2 \\ v_1 + i v_2 & -v_3 \end{bmatrix}^\dagger = \begin{bmatrix} v_3 & v_1 - i v_2 \\ v_1 + i v_2 & -v_3 \end{bmatrix}
>$$
>Hence, $(\vec{v}\cdot\vec{\sigma})^\dagger = \vec{v}\cdot\vec{\sigma}$, so it is Hermitian. Therefore, it is normal and has a spectral decomposition. Then we compute $(\vec{v}\cdot\vec{\sigma})^\dagger(\vec{v}\cdot\vec{\sigma}) = (\vec{v}\cdot\vec{\sigma})(\vec{v}\cdot\vec{\sigma}) = (\vec{v}\cdot\vec{\sigma})^2$:
>$$
>\begin{aligned}
>& \begin{bmatrix} v_3 & v_1 - i v_2 \\ v_1 + i v_2 & -v_3 \end{bmatrix} \begin{bmatrix} v_3 & v_1 - i v_2 \\ v_1 + i v_2 & -v_3 \end{bmatrix} \\ \\
>&= \begin{bmatrix} v_3^2 + (v_1 - i v_2)(v_1 + i v_2) & v_3(v_1 - i v_2) + (v_1 - i v_2)(-v_3) \\ (v_1 + i v_2)v_3 + (-v_3)(v_1 + i v_2) & (v_1 + i v_2)(v_1 - i v_2) + (-v_3)^2 \end{bmatrix} \\ \\
>&= \begin{bmatrix} v_3^2 + (v_1^2 + v_2^2) & v_3 v_1 - i v_3 v_2 - v_1 v_3 + i v_2 v_3 \\ v_1 v_3 + i v_2 v_3 - v_3 v_1 - i v_3 v_2 & (v_1^2 + v_2^2) + v_3^2 \end{bmatrix} \\ \\
>&= \begin{bmatrix} v_1^2 + v_2^2 + v_3^2 & 0 \\ 0 & v_1^2 + v_2^2 + v_3^2 \end{bmatrix}
>\end{aligned}
>$$
>Because $\vec{v}$ is a real unit vector, $v_1^2 + v_2^2 + v_3^2 = 1$. Hence $(\vec{v}\cdot\vec{\sigma})^2 = \begin{bmatrix}1 & 0 \\ 0 & 1\end{bmatrix} = I$. Hence, it is unitary also.
>
>We then find the eigenvalues of $\vec{v}\cdot\vec{\sigma}$. Let $\lambda$ be an eigenvalue of $\vec{v}\cdot\vec{\sigma}$:
>$$
>(\vec{v}\cdot\vec{\sigma})\ket{\varphi} = \lambda \ket{\varphi}
>$$
>Applying $\vec{v}\cdot\vec{\sigma}$ again yields:
>$$
>\begin{aligned}
>(\vec{v}\cdot\vec{\sigma})^2 \ket{\varphi} &= (\vec{v}\cdot\vec{\sigma})\lambda \ket{\varphi} = \lambda (\vec{v}\cdot\vec{\sigma}) \ket{\varphi} \\
>I \ket{\varphi} &= \lambda^2 \ket{\varphi} \\
>\lambda = \pm 1
>\end{aligned}
>$$
>
>Hence, $(\vec{v}\cdot\vec{\sigma})$ has eigenvalues $-1$ and $1$. Therefore, it has a spectral decomposition $\vec{v}\cdot\vec{\sigma} = \ket{a}\bra{a} - \ket{b}\bra{b}$ for some orthonormal eigenbasis $\ket{a}$ and $\ket{b}$. Applying the operator function yields:
>$$
>\begin{aligned}
>\operatorname{exp}(i\theta \vec{v}\cdot\vec{\sigma}) &= e^{i\theta}\ket{a}\bra{a} + e^{-i\theta}\ket{b}\bra{b} \\
>&\text{By Euler's formula $e^{i\theta} = \cos \theta + i\sin \theta$:} \\
>&= (\cos \theta + i\sin \theta) \ket{a}\bra{a} + (\cos \theta - i\sin \theta) \ket{b}\bra{b} \\
>&= (\ket{a}\bra{a} + \ket{b}\bra{b})\cos \theta + i(\ket{a}\bra{a}-\ket{b}\bra{b})\sin \theta \\
>&\text{By the completeness relation $\ket{a}\bra{a} + \ket{b}\bra{b} = I$,} \\
>&\text{And substituting $\ket{a}\bra{a}-\ket{b}\bra{b} = \vec{v}\cdot\vec{\sigma}$:} \\
>&= \cos(\theta) I + i\sin(\theta) \vec{v}\cdot\vec{\sigma}
>\end{aligned}
>$$

An important matrix function is the *trace* of a matrix. The trace of $A$ is the sum of its diagonal elements: $$\operatorname{tr}(A)=\sum_iA_{ii}$$
The trace is cyclic, as in $\operatorname{tr}(AB) = \operatorname{tr}(BA)$ and linear, $\operatorname{tr}(A+B) = \operatorname{tr}(A) + \operatorname{tr}(B)$

>[!proof] The trace is cyclic
>$$
>\operatorname{tr}(AB)=\sum_{m} \sum_{k} A_{mk}B_{km} = \sum_{m} \sum_{k} B_{km}A_{mk} = \operatorname{tr}(BA)
>$$

The linearity of the trace is trivial.

The trace is invariant under the unitary similarity transformation $A \to U A U^\dagger$, as $\operatorname{tr}(UAU^\dagger) = \operatorname{tr}(UU^\dagger A) = \operatorname{tr}(A)$. Hence, the trace of an operator is the trace of any matrix representation of the operator. 

As an example, consider arbitrary unit vector vector $\ket{\psi}$ and any operator $A$. Use the Gram-Schmidt procedure to extend $\ket{\psi}$ to an orthonormal basis $\ket{i}$ with $\ket{\psi}$ as the first element. Then we have $$\begin{aligned}\operatorname{tr}(A\ket{\psi}\bra{\psi}) &= \sum_i \langle i  \vert A \vert i \rangle \langle \psi \vert i \rangle \\ &=\langle \psi \vert A \vert \psi \rangle \end{aligned}$$ 
This is a very powerful result that lets us evaluate the trace of an operator. ^983889

The set $L_V$ of linear operators on a Hilbert Space $V$ is a vector space:
- The sum of linear operators is a linear operator.
- $zA$ is a linear operator if $A$ is a linear operator and $z$ is a complex number.
- There is a zero element $0$.

The function $(A, B) \equiv \operatorname{tr}(A^\dagger B)$ is an inner product on $L_V$:

>[!definition]
>A function $(\cdot, \cdot)$ from $V \times V$ to $\mathbb{C}$ is an inner product if it satisfies the following requirements:
>1. $(\cdot, \cdot)$ is linear in the second argument. This means that  $$(\ket{v}, \sum_i \lambda_i\ket{w_i}) = \sum_i\lambda_i(\ket{v},\ket{w_i})$$
>2. $(\ket{v}, \ket{w}) = (\ket{w}, \ket{v})^*$
>3. $(\ket{v},\ket{v}) \geq 0$ with equality if and only if $\ket{v}=0$

We will first show that it is linear in the first argument:
$$
\begin{aligned}
\operatorname{tr}(A^\dagger \sum_i \lambda_i B_i) &= \sum_m \left(A^\dagger \sum_i \lambda_iB_i \right)_{mm} \\
&= \sum_m \sum_i \lambda_i \left(A^\dagger B_i\right)_{mm} \\
&= \sum_i \lambda_i \sum_m \left(A^\dagger B_i\right)_{mm} \\
&= \sum_i \lambda_i \operatorname{tr}(A^\dagger B_i)
\end{aligned}
$$
And then show the complex conjugate swaps order:
$$
\begin{aligned}
\operatorname{tr}(A^\dagger B)^* &= \operatorname{tr}(A^\dagger B)^\dagger \\
&= \operatorname{tr}\left(\left[ A^\dagger B \right]^\dagger\right) \\
&= \operatorname{tr}(B^\dagger A)
\end{aligned}
$$
And finally the last property. All linear operators can be expressed as $A = \sum_i a_i \ket{\psi}\bra{\psi}$, so:
$$
\begin{aligned}
\operatorname{tr}(A^\dagger A) &= \sum_i A^\dagger_iA_i \\
&= \sum_i ||A_i||^2 \\
& \geq 0 \text{, with equality only when $A_i=0 \Rightarrow A=0$}
\end{aligned}
$$

If $V$ has $d$ dimensions, $L_V$ has dimension $d^2$.

The dimension of a vector space is defined by the size of the basis, so we fix a basis $\{ e_1, e_2, \ldots e_d \}$. We construct the matrices $E_{ij}$ such that $E_{ij}: V \to V$ maps $e_i \to e_j$ and any other vector to $0$. Recall $A\ket{e_j}=\sum_iA_{ij}\ket{e_i}$ as the matrix representation of any operator $A$. Hence, each $E_{ij}$ is $1$ in the $(i, j)\text{th}$ entry and $0$ elsewhere. There are $d^2$ such matrices. 


## The Commutator and Anti-Commutator

>[!define] Commutator
>The *commutator* between two operators $A$ and $B$ is defined to be $$[A, B] = AB - BA$$ If $[A, B] = 0$, that is, $AB = BA$, then we say that $A$ commutes with $B$.
>^commutator-definition

>[!define] Anti-Commutator
>The *anti-commutator* between two operators $A$ and $B$ is defined to be $$\{A, B\} = AB + BA$$ If $\{A, B\} = 0$, that is, $AB = -BA$, then we say that $A$ anti-commutes with $B$.

It turns out that many important properties of pairs of operators can be deduced from their commutator and anti-commutator. The book didn't mention any properties except being able to simultaneously diagonalize Hermitian operators $A$ and $B$, or writing $A = \sum_i a_i \ket{i}\bra{i}$ and $B = \sum_i b_i \ket{i}\bra{i}$ where $\ket{i}$ is some common orthonormal set of eigenvectors for $A$ and $B$.

>[!proof] Simultaneous Diagonalization Theorem: Suppose $A$ and $B$ are Hermitian operators. Then $[A, B] = 0$ if and only if there exists an orthonormal basis such that both $A$ and $B$ are *simultaneously diagonalizable* in this case.
>
>We will first verify that if $A$ and $B$ are simultaneously diagonalizable, then $[A, B] = 0$. We first compute $AB$:
>$$
>\begin{aligned}
>AB &= \left( \sum_i a_i \ket{i}\bra{i} \right) \left( \sum_j b_j \ket{j}\bra{j} \right) \\
>&= \sum_i \sum_j a_i b_j \ket{i} \underbrace{\langle i \vert j \rangle}_{\delta_{ij}} \bra{j} \\
>&= \sum_i a_i b_i \ket{i}\bra{i}
>\end{aligned}
>$$
>And for $BA$:
>$$
>\begin{aligned}
>BA &= \left(\sum_j b_j \ket{j} \bra{j} \right) \left(\sum_i a_i \ket{i}\bra{i}  \right) \\
>&= \sum_j \sum_i b_j a_i \ket{j} \underbrace{\langle j \vert i \rangle}_{\delta_{ij}} \bra{i} \\
>&= \sum_i a_i b_j \ket{i} \bra{i}
>\end{aligned}
>$$
>Hence, $AB = BA$ and $[A, B] = 0$.
>
>Then we proceed the prove the converse, that any two operators that commute are simultaneously diagonalizable.
>
>First, let $\ket{a, j}$ be an orthonormal basis for the eigenspace $V_a$ of $A$ with eigenvalue $a$. The index $j$ is used to label possible [[Linear Algebra#^941241|degeneracies]]. Note that 
>$$
>AB\ket{a, j} = BA{\ket{a,j}} = aB\ket{a,j}
>$$
>This means that $B\ket{a, j}$ is an eigenvector of $A$ with eigenvector $a$ and is therefore a member of $V_a$. Let $P_a$ be the projector onto $V_a$ and define $B_a = P_a B P_a$. The restriction of $B_a$ to the space $V_a$ is Hermitian on $V_a$, and therefore has a spectral decomposition in terms of an orthonormal set of eigenvectors that span $V_a$. Denote these eigenvectors as $\ket{a, b, k}$, where the indices $a$ and $b$ label the eigenvalues of $A$ and $B_a$, and $k$ to label possible degeneracies. $B\ket{a, b, k}$ is an element of $V_a$, so $B\ket{a, b, k} = P_a B\ket{a, b, k}$. Furthermore, $P_a\ket{a, b, k} = \ket{a, b, k}$, so $$B\ket{a,b,k} = P_a B P_a \ket{a, b, k} = b \ket{a, b, k}$$
>
>Hence, $\ket{a, b, k}$ is an eigenvector of $B$ with eigenvalue $b$, and therefore $\ket{a, b, k}$ is an orthonormal set of eigenvectors of both $A$ and $B$. Therefore, they are simultaneously diagonalizable.

^80eb10


## Polar and Singular Value Decompositions

>[!proof] Polar Decomposition: Let $A$ be a linear operator on a vector space $V$. Then there exists unitary $U$ and positive operators $J$ and $K$ such that $A = UJ = KU$, where the unique positive operators $J$ and $K$ are defined by $J \equiv \sqrt{A^\dagger A}$ and $K \equiv \sqrt{AA^\dagger}$. Moreover, if $A$ is invertible then $U$ is unique.
>
>Note that $J \equiv \sqrt{A^\dagger A}$ is a positive operator, so it can be given a spectral decomposition $J = \sum_i \lambda_i \ket{i}\bra{i}$ where $\lambda_i \geq 0$. We define $\ket{\psi_i} = A\ket{i}$. From the definition, we see that $\langle \psi_i \vert \psi_i \rangle = \lambda_i^2$. 
>
>For $\lambda_i > 0$ we define $\ket{e_i} \equiv \frac{1}{\lambda_i}\ket{\psi_i}$ so that $\ket{e_i}$ is normalized. Furthermore, they are orthogonal since if $i \neq j$ then $\langle e_i \vert e_j \rangle = \frac{1}{\lambda_i \lambda_j}\langle i \vert A^\dagger A \vert j \rangle = \frac{1}{\lambda_i \lambda_j} \langle i \vert J^2 \vert j \rangle = 0$.
>
>Now we use the Gram-Schmidt procedure to extend the orthogonal set $\ket{e_i}$ so it forms an orthonormal basis, which is also labelled $\ket{e_i}$. We define a unitary operator $U = \sum_i \ket{e_i}\ket{i}$. Therefore we have $UJ\ket{i} = \lambda_i\ket{e_i} = \ket{\psi_i} = A\ket{i}$. When $\lambda_i = 0$ we have $UJ\ket{i} = 0 = \ket{\psi_i}$. Hence, $A = UJ$ as the action on the basis is identical.
>
>$J$ is unique, since multiplying $A=UJ$ on both on the left by $A^\dagger = JU^\dagger$ gives $J^2 = A^\dagger A$, from which $J = \sqrt{A^\dagger A}$ uniquely. If $A$ is invertible, then so is $J$, so $U$ is uniquely determined through $U=AJ^{-1}$. 
>
>The proof of the right decomposition follows, since $A = UJ = UJUU^\dagger U = KU$, where $K \equiv UJU^\dagger$ is a positive operator. Since $AA^\dagger = KUU^\dagger K = K^2$ we must have $K = \sqrt{AA^\dagger}$.
  
>[!proof] Singular Value Decomposition: Let $A$ be a square matrix. Then there exist unitary matrices $U$ and $V$, and a diagonal matrix $D$ with non-negative entries such that $A = UDV$. The diagonal elements of $D$ are called the *singular values* of $A$.
>
>By Polar  Decomposition, $A = SJ$ for unitary $S$ and positive $J$. By the spectral theorem, $J = TDT^\dagger$, for unitary $T$ and diagonal $D$ with non-negative entries. Setting $U=ST$ and $V \equiv T^\dagger$

Finally, we can move onto [[The Postulates of Quantum Mechanics]]