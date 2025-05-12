A single qubit is a vector $\ket{\psi}=a\ket{0}+b\ket{1}$, where $a^2 + b^2 = 1$. Operations on a qubit must preserve this [[Linear Algebra#^norm-definition|norm]], and hence are described by $2 \times 2$ unitary matrices. Arguably the most important of these are the [[Nomenclature and Notation#^pauli-matrices-definition|Pauli matrices]]. Apart from those, the Hadamard $H$, the phase gate $S$, and $\pi/8$ gate  $T$:
$$
H=\frac{1}{\sqrt{2}}\begin{bmatrix}1  & 1 \\ 1 & -1\end{bmatrix}; \ \ S=\begin{bmatrix}1  & 0 \\ 0 & i\end{bmatrix}; \ \ T = \begin{bmatrix}1  & 0 \\ 0 & e^{i\frac{\pi}{4}}\end{bmatrix}
$$
These gates are closely related to the [[The ZX Calculus]]. 

>[!note]
>A single qubit state $a\ket{0}+b\ket{1}$ can be written as a point $(\theta,\phi)$ where $a=\cos(\frac{\theta}{2})$ and $b=e^{i\phi}\sin(\frac{\theta}{2})$.  This is called the Bloch sphere representation, and the vector $(\cos \phi \sin \theta, \sin \phi \sin \theta, \cos \theta)$ is called the Bloch vector.
>^bloch-sphere

The Pauli matrices give rise to the rotation operators defined as follows:
$$R_x(\theta)\equiv e^{i\theta X/2}$$ $$R_y(\theta)\equiv e^{i\theta Y/2}$$
$$R_z(\theta)\equiv e^{i\theta Z/2}$$
All unitary operators can be described  

