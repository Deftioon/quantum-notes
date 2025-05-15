We interpret objects of categories as systems and the morphisms as the processes in between them. A monoidal category has additional structure allowing us to consider processes that occur in *parallel*, as well as sequentially. One could interpret this in the following ways:
- letting independent physical systems evolve simultaneously;
- running computer algorithms in parallel;
- taking products or sums of algebraic or geometric structures;
- using separate proofs of $P$ and $Q$ to construct a proof of the conjunction ($P$ and $Q$).

## Monoidal Structure

### Monoidal Categories

It is perhaps surprising that a non-trivial theory can be developed from such simple intuition. But, in fact, some interesting general issues quickly arise. For example, let $A$, $B$, and $C$ be processes, and write $\otimes$ for parallel composition. One might say that $(A \otimes B) \otimes C$ should be equal to $A \otimes (B \otimes C)$, as they are different ways to express the same arrangement of systems. 

However, this is too strong and might not be the case. For example, if $A$, $B$, and $C$ are [[Basics#^hilbert-space-definition|Hilbert spaces]], and $\otimes$ is the usual [[Basics#^tensor-product-functor-definition|tensor product]], then these two composite Hilbert spaces are not *exactly equal*, they are only *isomorphic*. 

Now we have a new problem, what equations should these isomorphisms satisfy? The theory of monoidal categories is formulated to deal with these issues. ^fc4b85

>[!definition] Monoidal Category
>A *monoidal category* is a [[Basics#^category-definition|category]] equipped with the following data:
>- A *tensor product* [[Basics#^functor-definition|functor]] $\otimes: \textbf{C} \times \textbf{C} \to \textbf{C}$.
>- A *unit object* $I \in \operatorname{Ob}(\textbf{C})$.
>- An *associator* [[Basics#^natural-transformation-definition|natural isomorphism]] $(A \otimes B) \otimes C \xrightarrow{\alpha_{A, B, C}} A \otimes (B \otimes C)$.
>- A *left unitor* [[Basics#^natural-transformation-definition|natural isomorphism]] $I \otimes A \xrightarrow{\lambda_A} A$.
>- A *right unitor* [[Basics#^natural-transformation-definition|natural isomorphism]] $A \otimes I \xrightarrow{\rho_A} A$ 
>
>This data must satisfy the triangle and pentagon equations:
>
>![[Pasted image 20250513112528.png|center|500]]
>
>The naturality conditions for $\alpha$, $\lambda$, and $\rho$ are shown also, diagrammatically:
>
>![[Pasted image 20250513150754.png|center|500]]
>
>The tensor unit object $I$ represents the 'trivial' or 'empty' system. This interpretation comes from the unitors $\lambda_A$ and $\rho_A$, which witness the fact that the object $A$ is 'just as good as', or [[Basics#^isomorphism-retraction-definition|isomorphic]] to, the objects $A \otimes I$ and $I \otimes A$.
>
>Each of the triangle and pentagon equations say that two particular ways of 'reorganizing' a system is equal. Surprisingly, this implies that *any* two 'reorganizations' are equal. This is the content of the coherence theorem detailed below.
>
>What the pentagon equation tells us is that the two ways of essentially "rebracketing" the expression both compose into the same object. It also tells us that there are two isomorphisms between $((A \otimes B) \otimes C) \otimes D$ and $A \otimes(B \otimes (C \otimes D))$, but these two isomorphisms are equal and compose to the same object.
>
>The triangle equation says that inserting *units* into this is compatible with the content of the pentagon equation too. For example, you can insert or remove the empty string from any word, and that's okay.
>^monoidal-category-definition

>[!theorem] Coherence for Monoidal Categories
>Given the data of a monoidal category, if the pentagon and triangle equations hold, then any well-typed equation built from $\alpha$, $\lambda$, $\rho$, and their inverses hold. 
>
>In particular, the pentagon and triangle equations imply $\rho_I = \lambda_I$
>^coherence-theorem

>[!example] Coherence
>An intuitive example for the coherence theorem is that if I can prove that $(x + y) + z = x + (y + z)$, then I can deduce that I can change the brackets however I want on $(((((a + b) + c) + d) + e) + f) + g$.

Coherence is the fundamental motivating idea for monoidal categories, and gives an answer to the question we posed [[Monoidal Categories#^fc4b85|earlier]].

Let's take a look at the monoidal structure we can give to [[Basics#^hilb-definition|$\textbf{Hilb}$]].

>[!definition] Monoidal Structure in $\textbf{Hilb}$.
>In the monoidal category $\textbf{Hilb}$, and by restriction $\textbf{FHilb}$:
>- **The Tensor Product** $\otimes: \textbf{Hilb} \times \textbf{Hilb} \to \textbf{Hilb}$ is the tensor product of Hilbert spaces, as defined [[Basics#^tensor-product-hilb-definition|earlier]].
>- **The Unit Object** $I$ is the one dimensional Hilbert space $\mathbb{C}$.
>- **Associators** $(H \otimes J) \otimes K \xrightarrow{\alpha_{H, J, K}} H \otimes (J \otimes K)$ are the unique linear maps satisfying $(a \otimes b) \otimes c \mapsto a \otimes (b \otimes c)$ for all $a \in H$, $b \in J$, $c \in K$.
>- **Left Unitors** $\mathbb{C} \otimes H \xrightarrow{\lambda_H} H$ are the unique linear maps with $1 \otimes a \mapsto a$ for all $a \in H$.
>- **Right Unitors** $H \otimes \mathbb{C} \xrightarrow{\rho_H} H$ are the unique linear maps with $a \otimes 1 \mapsto a$ for all $a \in H$.
>
>Although we call the functor $\otimes$ of a monoidal category a tensor product, that does not mean we have to choose the actual [[Basics#^tensor-product-hilb-definition|tensor product]] of a Hilbert space. There are other monoidal structures we could choose; a good example is the [[Basics#^hilb-direct-sum-definition|direct sum]] of Hilbert Spaces. However, the tensor product we have defined previously has a special status, since [[The Postulates of Quantum Mechanics#^postulate-4|it describes the state space of a composite system in quantum theory]].
>^monoid-hilb-definition

While $\textbf{Hilb}$ is relevant for *quantum* computation, the monoidal category [[Basics#^set-cat-definition|$\textbf{Set}$]] is relevant for *classical* computation. We now add the monoidal structure:

>[!definition] Monoidal Structure in $\textbf{Set}$
>In the monoidal category $\textbf{Set}$, and by restriction $\textbf{FSet}$:
>- **The Tensor Product** is the Cartesian product of sets, written $\times$, acting on functions $A \xrightarrow{f} B$ and $C \xrightarrow{g} D$ as $(f \times g)(a, c) = (f(a), g(c))$.
>- **The Unit Object** is a chosen singleton set $\{\cdot\}$.
>- **Left Unitors** $I \times A \xrightarrow{\lambda_A} A$ are the functions $(\cdot, a) \mapsto a$.
>- **Right Unitors** $I \times A \xrightarrow{\rho_A}$ are the functions $(a, \cdot) \mapsto a$.
>
>The Cartesian product in $\textbf{Set}$ is a [[Basics#^product-category-definition|categorical product]]. This is an example of a general phenomenon: if a category has [[Basics#^product-coproduct-definition|products]] and a [[Basics#^terminal-initial-definition|terminal object]], then these furnish the category with monoidal structure. The same is true for [[Basics#^product-coproduct-definition|coproducts]] and [[Basics#^terminal-initial-definition|initial objects]], which in $\textbf{Set}$ are given by disjoint union.
>^monoid-set-definition

This highlights a big difference between $\textbf{Hilb}$ and $\textbf{Set}$. The tensor product on $\textbf{Set}$ comes from a categorical product, while the tensor product on $\textbf{Hilb}$ is not. Many more differences exist, all of which provide insight into the differences between classical and quantum information.

There is also a monoidal structure on the category of [[Basics#^rel-cat-definition|$\textbf{Rel}$]]:

>[!definition] Monoidal Structure in $\textbf{Rel}$
>In the monoidal category $\textbf{Rel}$:
>- **The Tensor Product** is given by the Cartesian product of sets, written $\times$, acting on relations $A \xrightarrow{R} B$ and $C \xrightarrow{S} D$ by setting $(a, c)(R \times S)(b, d)$ if and only if $aRb$ and $cSd$.
>- **The Unit Object** is a chosen singleton set $\{\cdot\}$
>- **Associators** $(A \times B) \times C \xrightarrow{\alpha_{A, B, C}} A \times (B \times C)$ are the relations defined by $((a,b),c) \sim (a, (b, c))$ for all $a \in A$, $B \in B$, and $c \in C$.
>- **Left Unitors** $I \times A \xrightarrow{\lambda_A} A$ are the relations defined by $(\cdot, a) \sim a$ for all $a \in A$.
>- **Right Unitors** $A \times I \xrightarrow{\rho_A} A$ are the relations defined by $(a, \cdot) \sim a$ for all $a \in A$.
>
>The Cartesian product *is not* a categorical product in $\textbf{Rel}$, despite its similarity with $\textbf{Set}$. It is actually more similar to $\textbf{Hilb}$ as briefly mentioned at the beginning of the book. 
>^monoid-rel-definition

>[!example] Opposites
>If $\textbf{C}$ is a monoidal category, then so is its [[Basics#^opposite-category-definition|opposite]] $\textbf{C}^\text{op}$. The tensor unit $I$ in $\textbf{C}^\text{op}$ is the same as that in $\textbf{C}$, whereas the tensor product $A \otimes B$ in $\textbf{C}^\text{op}$ is given by $B \otimes A$ in $\textbf{C}$, the associators in $\textbf{C}^\text{op}$ are the inverses of those morphisms in $\textbf{C}$, and the left and right unitors swap roles in $\textbf{C}^\text{op}$
>^opposite-monoid-example

Monoidal categories have an important property called the *interchange law*, which governs the interaction between categorical composition and tensor product.

>[!theorem] Interchange Law
>Any morphisms $A \xrightarrow{f} B$, $B \xrightarrow{g} C$, $D \xrightarrow{h} E$ and $E \xrightarrow{j} F$ in a monoidal category satisfy the interchange law: $$(g \circ f) \otimes (j \circ h) = (g \otimes j) \circ (f \otimes h)$$
>^interchange-law

>[!proof] Interchange Law
>$$
>\begin{aligned}
>(g \circ f) \otimes (j \circ h) &\equiv \otimes (g \circ f, j \circ h) \\
>&= \otimes \left(\left( g, j \right) \circ \left( f, h \right)\right) & \text{(Composition in $\textbf{C} \times \textbf{C}$)} \\
>&= \left(\otimes \left( g, j \right) \right) \circ \left(\otimes \left( f, h \right)\right) & \text{(Functoriality of $\otimes$, that $F(f \circ g) = F(f) \circ F(g)$)} \\
>&= (g \otimes j) \circ (f \otimes h)
>\end{aligned}
>$$


### Graphical Calculus

A monoidal structure allows us to interpret multiple processes in our category taking place at the same time. For morphisms $A \xrightarrow{f} B$ and $C \xrightarrow{g} D$, it therefore seems natural to depict monoidal categories as such, extending the graphical notation in [[Basics#Graphical Notation]] seen earlier:

![[Pasted image 20250513185509.png|center|300]]

The idea is that $f$ and $g$ act at the same time on distinct systems. Similarly, time moves upwards, with inputs on the bottom and outputs on the top. Whereas the graphical calculus for normal categories is one dimensional, or *linear*, the graphical calculus for monoidal categories is two dimensional, or *planar*. 

This is very useful for working with monoidal categories. In fact, the graphical language describes monoidal categories *completely*.

The (identity on, remember we're talking about morphisms here,) monoidal unit object $I$ is drawn by the empty diagram:

![[Pasted image 20250513190121.png|center|500]]

The left unitor, right unitor, and the associator are not depicted:

![[Pasted image 20250513190511.png|center|500]]

The coherence of $\alpha$, $\lambda$, and $\rho$ is therefore important for the graphical calculus to function. Since there can only be a single morphism built from their components of any given type by [[Monoidal Categories#^coherence-theorem|the coherence theorem]], it does not matter that their graphical counterparts encode no information.

Now consider the graphical version of the interchange law:

![[Pasted image 20250513190646.png|center|500]]

Where the brackets are used to indicate how the diagrams are being formed. In the first image, we compose the morphisms and then tensor them together, but in the second image we tensor them first and then compose the morphisms together. Clearly, these are the same image, and such the interchange law comes rather naturally from the graphical calculus. 

All the complicated algebraic definitions have disappeared! This is the power of the graphical calculus!!!!!!!!!!! They're still there, but they're part of the graphical representation, which is much more intuitive.

>[!theorem] The Correctness of the Graphical Calculus for Monoidal Categories
>A well-typed equation between morphisms in a monoidal category follows from the axioms if and only if it holds in the graphical language up to planar isotopy.
>^graphical-calculus-correctness-theorem

>[!definition] Planar Isotopy
>Two diagrams are *planar isotopic* when one can be deformed continuously into the other within some rectangular region of the plane, with the input and output wires terminating at the top and bottom of the rectangle, *without introducing any intersections of the components*. The following diagram gives an example:
>
>![[Pasted image 20250513192524.png|center|500]]
>
>From the first image to the second, the $\boxed{h}$ can move under the $\boxed{f}$ to be put into where it is. From the second to the third, it cannot move there without intersecting with a wire or a box, so the third is not isotopic to the first two.
>^planar-isotopy-definition

The correctness theorem is saying two things: That the graphical calculus is *sound*, and that it is *complete*. To intuit these concepts, consider two morphisms $f$ and $g$ such that the equation $f = g$ is well-typed, and the following statements:
- $P(f, g)$: "Under the axioms of a monoidal category, $f = g$".
- $Q(f,g)$: "The graphical representations of $f$ and $g$ are planar isotopic".
*Soundness* is the assertion that $P(f, g) \Rightarrow Q(f, g)$, while *Completeness* is the opposite, that $Q(f,g) \Rightarrow P(f,g)$. 


### States and Effects

If a mathematical structure lives as an object inside a category, and we want to learn something about its structure, we must find a way to do it using the morphisms of the category only. 

