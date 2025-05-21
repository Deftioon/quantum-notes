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

If a mathematical structure lives as an object inside a category, and we want to learn something about its structure, we must find a way to do it using the morphisms of the category only. For example, consider a set $A \in \text{Ob}(\textbf{Set})$ with a chosen element $a \in A$. We can represent this with the function $\{\cdot \} \to A$ defined by $\cdot \mapsto A$. This inspires the following definition, which generalizes the notion of a set-theoretical state.

>[!definition] State
>In a monoidal category, a *state* of an object $A$ is a morphism $I \to A$ where $I$ is the [[Monoidal Categories#^monoidal-category-definition|unit object]] of the monoidal category.
>
>Since the unit object represents the trivial or empty system, a state $I \to A$ of a system can be thought of the system being brought into being.
>^state-definition

>[!example] States in our example categories.
>- In $\textbf{Hilb}$, states of a Hilbert space $H$ are the linear functions $\mathbb{C} \to H$, which correspond to elements of $H$ by considering the image of $1 \in \mathbb{C}$. For example, the map $1 \to \psi$ defines the state $\psi$.
>- In $\textbf{Set}$, states of a set $A$ are the functions $\{\cdot \} \to A$, which correspond to elements of $A$ by considering the image of $\cdot$. 
>- In $\textbf{Rel}$, states of a set $A$ are the relations $\{\cdot \} \xrightarrow{R} A$, which correspond to elements of $A$ by considering all elements related to $\cdot$.
>^state-example

>[!definition] Well-Pointed Categories
>A monoidal category is *well-pointed* if for all parallel pairs of morphisms $A \xrightarrow{f, g} B$, we have $f = g$ when $f \circ a = g \circ a$ for all states $I \xrightarrow{a} A$. In other words, they act identically on all states. 
>
>A monoidal category is *monoidally well-pointed* if for all parallel pairs of morphisms $A_1 \otimes \cdots \otimes A_n \xrightarrow{f, g} B$, we have $f = g$ when $f \circ (a_1 \otimes \ldots \otimes a_n) = g \circ (a_1 \otimes \ldots \otimes a_n)$ for all states $I \xrightarrow{a_1} A_1, \ldots, I \xrightarrow{a_n} A_n$. In other words, they act identically on all tensor product states. For example, for parallel systems composed with the tensor product $\otimes$, it's sufficient to check equality of $f$ and $g$ on *separable states* (the combination of states of the individual components), instead of all entangled states.
>^well-pointed-categories

The idea is that in a well-pointed category, we can determine whether or not morphisms are equal by only looking at how they affect the states of their domains. In a monoidally well-pointed category, we only have to consider the product states to tell whether or not morphisms are equal out of a compound object. The categories $\textbf{Set}$, $\textbf{Rel}$, $\textbf{Vect}$ and $\textbf{Hilb}$ are all monoidally well-pointed. For the last two categories, it can be observed because if $\{d_i\}$ is a basis for $H$ and $\{e_j\}$ is a basis for $K$, then $\{d_i \otimes e_j\}$ is a basis for $H \otimes K$.

In the graphical calculus, to emphasize that states $I \xrightarrow{a} A$ have the empty picture as their domain, states are drawn as triangles:
![[Pasted image 20250516152859.png|center|75]]

### Product States and Entangled States

>[!definition] Joint States, Product States, Entangled States
>For objects $A$ and $B$ in a monoidal category, a morphism $I \xrightarrow{c} A \otimes B$ is a *joint state* of $A$ and $B$, depicted graphically as:
>
>![[Pasted image 20250516153122.png|center|150]]
>
>A joint state is a *product state* when it is of the form $I \xrightarrow{\lambda_I^{-1}} I \otimes I \xrightarrow{a \otimes b} A \otimes B$ for $I \xrightarrow{a} A$ and $I \xrightarrow{b} B$:
>
>![[Pasted image 20250516153355.png|center|300]]
>
>A joint state is *entangled* when it is not a product state. These represent preparations of  $A \otimes B$ that cannot be decomposed as a preparation of $A$ alongside a preparation of $B$. In this case, there is some special connection between $A$ and $B$, which means they cannot have been prepared independently.
>
>In $\textbf{Hilb}$, joint states of $H$ and $K$ are the elements of $H \otimes K$. Product states are factorizable states, and entangled states are elements of $H \otimes K$ which are not factorizable. For example, the [[The Postulates of Quantum Mechanics#^469e2c|maximally entangled bell states]]. 
>^joint-product-entangled-state-definition

In our other examples:
- In $\textbf{Set}$, joint states of $A$ and $B$ are the elements of $A \times B$. Product states are the elements of $A \times B$, and entangled states *do not exist*.
- In $\textbf{Rel}$, joint states of $A$ and $B$ are the subsets of $A \times B$. Product states are the "square subsets" $U \subseteq A \times B$, where for some $V \subseteq A$ and $W \subseteq B$, $(a, b) \in U$ if and only if $a \in V$ and $b \in W$.  Entangled states are the subsets of $A \times B$ that are not of this form.

This hints at why entanglement occurs only in quantum mechanics. It cannot occur classically in the deterministic processes encoded in $\textbf{Set}$, it can only occur if we allow nondeterministic behaviour such as in $\textbf{Rel}$. 

### Effects

An  *effect* represents a process by which a system is destroyed or consumed.

>[!definition] Effect
>In a monoidal category, an *effect* or *costate* is the morphism $A \to I$, shown diagrammatically below:
>
>![[Pasted image 20250516163144.png|center|300]]
>
>We can interpret this as a history of events that has taken place. If the diagram has an effect, then it is interpreted to have undergone a measurement, with the given effect as a result. 
>
>In the above diagram, the state $a$ was prepared, then a process $f$ is performed producing two systems, the first of which is measured giving outcome $x$. This does not imply that $x$ is the *only* outcome of the measurement, but that we are only interested in the cases where outcome $x$ does occur. An effect can be thought of as a *postselection*, keep repeating the same experiment until a measurement has a specified outcome. 
>
>The overall history is a morphism $I \to A$, which is a state of $A$. The postselection interpretation dictates how to prepare this state, given the ability to perform its components.
>^effect-definition
>

>[!example] 
>To say more than general statements, we must look into our example categories:
>- In quantum theory, as described by $\textbf{Hilb}$, the morphisms $a$, $f$, and $x$ must be [[Basics#^7a8d4c|partial isometries]]. The [[The Postulates of Quantum Mechanics#^postulate-3|Born rule of quantum mechanics]] dictate that the probability for this history to take place is given by the square norm of its resulting state. So, in particular, the history described by this composite morphism is impossible exactly when the overall state is zero.
>- In non-deterministic classical physics, as described by $\textbf{Rel}$, there are no particular requirements on the morphisms $a$, $f$, and $x$, which may be arbitrary relations of the correct types. The overall composite relation then describes the amount of ways in which $A$ can be prepared as a result of its history. If the overall composite is empty, then this particular sequence of a state preparation, a dynamic step, and a measurement result cannot occur.
>- In deterministic classical physics, as described by $\textbf{Set}$, The [[Monoidal Categories#^monoidal-category-definition|monoidal unit object]] is [[Basics#^terminal-initial-definition|terminal]] in that category, meaning $\textbf{Set}(A, I)$ has only one single element for any object $A$. So, every object has a *unique* effect, and there is no non-trivial notion of "measurement".
>^effect-example

We may think of the wires in the graphical calculus to carry some sort of information flow. If the monoidal dagger category is [[Monoidal Categories#^well-pointed-categories|monoidally well-pointed]], two morphisms $A \xrightarrow{f, g} C$ are equal if and only if for all states $I \xrightarrow{a} A$ and $I \xrightarrow{c} C$ the two following scalars are equal:

![[Pasted image 20250519101018.png|center|300]]

So we could verify an equation by computing the "matrix entries" on both sides. In $\textbf{Rel}$ it is convenient to do this by decorating the wires with elements. For example, the morphism $I \to I$ given by:

![[Pasted image 20250519101420.png|center|300]]

Is non-empty if and only if there exists an element $b$ such that the following are also non-empty:

![[Pasted image 20250519110212.png|center|500]]

This allows us to draw the following diagram,

![[Pasted image 20250519110331.png|center|300]]

To show that if element $a$ is connected to $c$ by the composite morphism, then it must 'flow' through some element $b$ in the middle. 

However, in $\textbf{FHilb}$, this technique does not work because of interference.


## Braiding and Symmetry

In many processes, if $A$ and $B$ are systems, then $A \otimes B$ and $B \otimes A$ are considered to be essentially equivalent. However, they may not necessarily be equal. This leads us to introduce the notion of a braiding [[Basics#^natural-transformation-definition|natural isomorphism]] $$A \otimes B \xrightarrow{\sigma_{A, B}} B \otimes A.$$
This [[Basics#^natural-transformation-definition|natural isomorphism]] essentially just swaps the order of the tensor product, and hence the order of the systems. This notion extends to braided and symmetrical monoidal categories.

### Braided Monoidal Categories

>[!definition] Braided Monoidal Categories
>A *braded monoidal category* is a monoidal category equipped with a [[Basics#^natural-transformation-definition|natural isomorphism]] $$A \otimes B \xrightarrow{\sigma_{A, B}} B \otimes A,$$ that satisfies the following *hexagon equations*:
>
>![[Pasted image 20250519141919.png|center|500]]
>
>^braided-monoidal-category-definition

We include braiding in the graphical notation as such:

![[Pasted image 20250519142103.png|center|500]]

And the invertibility of the [[Basics#^natural-transformation-definition|natural isomorphism]] takes form:

![[Pasted image 20250519142133.png|center|500]]

This is very similar to the intuitive behavior of strings. The naturality of braiding and inverse braiding have the following representations:

![[Pasted image 20250520091537.png|center|500]]

And the hexagon equations are as follows:

![[Pasted image 20250520091600.png|center|500]]

Since the strands of a braiding cross over each other, we say that braided monoidal categories now have a notion of a third dimension. So while categories are linear, or one dimensional, and monoidal categories are planar, two dimensional, with planar isotopy, braided monoidal categories are spatial, three dimensional, with spatial isotopy. 

>[!theorem] Correctness of graphical calculus for braided monoidal categories
>A well-typed equation between morphisms in a braided monoidal category follows from the axioms if and only if it holds in the graphical language up to spatial isotopy.
>^braided-correctness

![[Pasted image 20250520092007.png|center|500]]

For example, these diagrams are clearly spatially isotopic. However, to prove from the axioms, we do the following:

![[Pasted image 20250520093808.png|center|500]]

![[Pasted image 20250520154335.png|center|500]]

We can also prove this result, known as the *Yang-Baxter equation*, which has an important role in the theory of knots, in the language of braided monoidal categories:

![[Pasted image 20250521094602.png|center|500]]

Where, in order, we use the hexagon equation, naturality, then the hexagon again.

For example in our example sets, there is a notion of swapping:

>[!definition]
>The monoidal categories $\textbf{Hilb}$, $\textbf{Set}$ and $\textbf{Rel}$ can be equipped with a canonical braiding:
>- In $\textbf{Hilb}$, $H \otimes K \xrightarrow{\sigma_{H, K}} K \otimes H$ is the unique linear map extending $a \otimes b \mapsto b \otimes a$ for all $a \in H$ and $b \in K$.
>- In $\textbf{Set}$, $A \times B \xrightarrow{\sigma_{A, B}} B \times A$ is defined by $(a, b) \mapsto (b, a)$ for all $a \in A$ and $b \in B$.
>- In $\textbf{Rel}$, $A \times B \xrightarrow{\sigma_{A, B}} B \times A$ is defined by $(a, b) \sim (b, a)$ for all $a \in A$ and $b \in B$.

Each of these categories has a stronger structure of *symmetric monoidal*.

### Symmetric Monoidal Categories

>[!definition] Symmetric Monoidal Categories
>A braided monoidal category is *symmetric* when $$\sigma_{B, A} \circ \sigma_{A, B} = \operatorname{id}_{A \otimes B}$$ for all objects $A$ and $B$, in which case we call $\sigma$ the *symmetry*.
>^symmetric-monoidal-categories-definition

Graphically, this condition has the following representation:

![[Pasted image 20250521095513.png|center|300]]

As such, the strings can intuitively pass through each other, and non-trivial knots cannot be formed.

In a *symmetric monoidal category*, $\sigma_{A, B} = \sigma_{B, A}^{-1}$:

![[Pasted image 20250521095616.png|center|300]]

Hence, a symmetric monoidal category does not distinguish between crossing over or crossing under, as strings can pass through each other. So we can draw:

![[Pasted image 20250521095846.png|center|150]]

>[!theorem] Correctness of graphical calculus for symmetric monoidal categories
>A well-typed equation between morphisms in a symmetric monoidal category follows from the axioms if and only if it holds in the graphical language up to graphical equivalence.
>^symmetric-monoidal-correctness

By 'graphical equivalence', we mean [[Monoidal Categories#^braided-correctness|spatial isotopy]] along with the previous properties of a symmetric monoidal category.

The notion of symmetric monoidal categories sees use in math and physics.

>[!definition] $\textbf{Rep(G)}$
>For a finite [[Basics#^groupoid-definition|group]] $\textbf{G}$, there is a symmetric monoidal category $\textbf{Rep(G)}$ of finite dimensional [[Basics#^group-representation-example|representations]] of $\textbf{G}$, in which:;
>- **Objects** are the finite-dimensional [[Basics#^group-representation-example|representations]] of $\textbf{G}$.
>- **Morphisms** are the [[Basics#^group-representation-example|intertwiners]] for the group action.
>- The **tensor product** is the [[Basics#^tensor-product-hilb-definition|tensor product]] of [[Basics#^group-representation-example|representations]].
>- The **unit object** is the trivial action of $\textbf{G}$ on the one-dimensional [[Basics#^vector-space-category-definition|vector space]].
>- The **symmetry** is inherited from [[Basics#^vector-space-category-definition|$\textbf{Vect}$]].
>^rep-g-definition

Another interesting symmetric monoidal category is inspired by the physics of bosons and fermions. These are quantum particles with the property that when two fermions exchange places, a phase of $-1$ is obtained. However, when two bosons, or one boson and one fermion exchange places, there is no extra phase. This has a categorical structure, described as follows:

