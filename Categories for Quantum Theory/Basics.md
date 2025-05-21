
## Category Theory

This gives a brief introduction to category theory. We focus on the category $\textbf{Set}$ of sets and functions, and the category $\textbf{Rel}$ of sets and relations. 

### Categories

Categories consist of *objects* $A, B, C$ and *morphisms* $A \xrightarrow{f} B$ going between objects. We will often think of an object as a *system* and the morphisms as *processes* between that transforms one system into another. 

Categories can be formed from any reasonable construction of system and process. For example:
- Physical systems, and physical processes governing them;
- Data types in computer science, and algorithms manipulating them;
- Algebraic or geometric structures in mathematics, and structure-preserving functions;
- Logical propositions, and implications between them.

Category theory is quite different to other fields of mathematics. While it itself is an algebraic structure, akin to Groups, Rings, and Fields, we can use categories to understand and organize other mathematical objects. This happens by neglecting all the information about the structure of objects, and focusing entirely on the relationship between objects. This might seem limiting at first, but turns out to be a general language to describe many diverse structures.

>[!definition] A *category* $\textbf{C}$ consists of the following data:
>- A collection $\text{Ob}(\textbf{C})$ of objects;
>- For every pair of objects $A$ and $B$, a collection of *morphisms* $\textbf{C}(A, B)$ with $f \in \textbf{C}(A, B)$ written as $A \xrightarrow{f} B$;
>- For every pair of morphisms $A \xrightarrow{f} B$ and $B \xrightarrow{g} C$, a composite morphism $A \xrightarrow{g \circ f} C$;
>- For every object $A$ an identity morphism $A \xrightarrow{\text{Id}_A} A$
>  
>These must satisfy the following properties, for all objects $A$, $B$, $C$, $D$, and all morphisms $A \xrightarrow{f} B$, $B \xrightarrow{g} C$, $C \xrightarrow{h} D$:
>- Associativity, $$h \circ (g \circ f) = (h \circ g) \circ f$$ 
>- Identity, $$\text{Id}_B \circ f = f = f \circ \text{Id}_A$$
>  
>  Sometimes the notation $f: A \to B$ is used to represent a morphism $f \in \textbf{C}(A, B)$
>^category-definition

From this definition it can be observed that morphisms are far more important than objects, as objects can be represented with their identity morphism.


#### The Category $\textbf{Set}$

The most basic relationships between sets are given by functions.

>[!definition] 
>For sets $A$ and $B$, a *function* $A \xrightarrow{f} B$ comprises, for each $a \in A$, a choice of element $f(a) \in B$. We write $f: a \mapsto f(a)$ to denote this choice.
>
>Writing $\emptyset$ for the empty set, the data for the function $\emptyset \to A$ can be provided trivially, there is nothing for the 'for each' part of the definition to do. So there is exactly one function of this type for every set $A$. However, functions of the type $A \to \emptyset$ cannot be constructed unless $A = \emptyset$. In general there are $|B|^{|A|}$ functions of type $A \to B$ where $|\cdot|$ denotes the cardinality of a set.
>^set-definition

>[!definition] $\textbf{Set}$ and $\textbf{FSet}$
>In the [[Basics#^category-definition|category]] $\textbf{Set}$ of sets and functions:
>- **Objects** are the sets $A, B, C, \ldots$.
>- **Morphisms** are the functions $f, g, h, \ldots$.
>- **Composition** of $A \xrightarrow{f} B$ and $B \xrightarrow{g} C$ is the function $g \circ f: a \mapsto g(f(a))$. 
>- **The identity morphism** on $A$ is the function $\text{id}_A: a \mapsto a$. 
>We write $\textbf{FSet}$ for the restriction of $\textbf{Set}$ to finite sets.
>^set-cat-definition

We think of a function as a way that the elements of $A$ deterministically evolve into elements of $B$:
![[Pasted image 20250511162041.png|center|250]]

#### The Category $\textbf{Rel}$

Relations give a more general notion of processes between sets.

>[!definition]
>GIven sets $A$ and $B$, a *relation* $A \xrightarrow{R} B$ is a subset $R \subseteq A \times B$.
>
>If elements $a \in A$ and $b \in B$ satisfy $(a, b) \in R$, we often indicate this by writing $aRb$, or even $a \sim b$ when $R$ is clear. Since a subset can be made by giving its elements, we can define our relations by listing the related elements, in the form $a_1 R b_1$ and so on.
>
>We can think of a relation $A \xrightarrow{R} B$ dynamically also:
>
>![[Pasted image 20250511164008.png|center|250]]
>
>The difference with functions is that this picture indicates interpreting a relation as a nondeterministic classical process. This is because one element of $A$ can evolve into one of many possible element of $B$, so under this interpretation, we cannot predict perfectly how the system will evolve. Also, an element of $A$ can be related to *no* elements of $B$ at all. We interpret this to mean that for these elements of $A$, the dynamical process halts. 
>
>Because of this interpretation, the category of relations is important in studying nondeterministic classical computing.
>^relation-definition

Suppose we have a pair of relations, with the codomain of the first equal to the domain of the second:
![[Pasted image 20250511164329.png|center|500]]

Our interpretations of relations as dynamical processes give rise to a natural notion of composition: an element $a \in A$ is related to an element $c \in C$ if there is some $b \in B$ with $aRb$ and $bSc$. This gives rise to the following composite relation:
![[Pasted image 20250511164438.png|center|500]]

This definition of relational composition has the following algebraic form:
$$
S \circ R = \left\{\left(a, c\right) \mid \exists b \in B: aRb \text{ and } bSc\right\} \subseteq A \times B.
$$
We can write this differently as
$$
a(S \circ R)c \Leftrightarrow \bigvee_b (bSc \ \wedge \ aRb)
$$
where $\vee$ represents logical disjunction (OR) and $\wedge$ represents logical conjunction (AND). Comparing this with matrix multiplication, we see a strong similarity:
$$
(g \circ f)_{ik}=\sum_j f_{jk}g_{ij}
$$
This suggests yet another way to interpret a relation: as a matrix of truth values. For the example relation above, this gives the following matrix, where we write $0$ for false and $1$ for truth:
![[Pasted image 20250511165025.png|center|500]]

The composition of relations is then given by matrix multiplication, but replacing the conventional addition and multiplication with logical disjunction and conjunction, so that $1 + 1 = 1$. 

There is an interesting analogy between quantum dynamics and the theory of relations. First, a relation $A \xrightarrow{R} B$ tells us, for each $a \in A$ and $b \in B$, whether it is *possible* for $a$ to produce $b$, whereas a complex valued matrix $H \xrightarrow{f} K$ gives us the *amplitude* for $a$ to evolve to $b$. Second, relational composition tells us the *possibility* of evolving via an intermediate point through a sum-of-paths formula, whereas matrix multiplication tells us the *amplitude* for this to happen. 

This leads to the following category:

>[!definition] $\textbf{Rel}$ and $\textbf{FRel}$
>In the category $\textbf{Rel}$ of sets and relations:
>- **Objects** are the sets $A, B, C, ldots$.
>- **Morphisms** are the relations $R \subseteq A \times B$.
>- **Composition** of $A \xrightarrow{R} B$ and $B \xrightarrow{S} C$ is the relation $$\left\{ \left(a,c\right) \in A \times C \mid \exists b \in B: \left(a, b\right) \in R, \left(b,c\right) \in S \right\}.$$
>- **The identity morphism** on $A$ is the relation $\left\{ \left(a,b\right) \in A \times A \mid a \in A \right\}$.
>  
>We write $\textbf{FRel}$ for the restriction of $\textbf{Rel}$
>^rel-cat-definition

While $\textbf{Set}$ is a setting for classical physics, and $\textbf{Hilb}$ a setting for quantum physics, $\textbf{Rel}$ is somewhere in the middle. It seems like it should be a lot like $\textbf{Set}$, but in fact, it is much more similar to $\textbf{Hilb}$. This makes it an excellent test bed for investigating different aspects of quantum mechanics from a categorical perspective.

### Morphisms

It helps to draw diagrams of morphisms.
![[Pasted image 20250424141518.png | center]]

We say a diagram commutes when ever possible path from one object to another is the same. In this case, that means $g = j \circ i$ and $i \circ f = k \circ h$. It then follows that $g \circ f = j \circ k \circ h$

>[!definition] Domain, Codomain, Endomorphism, Operator
>For a morphism $A \xrightarrow{f} B$, its *domain* is the object $A$ and its codomain is the object $B$. If $A = B$ then we call $f$ an endomorphism or *operator* (from physics). We sometimes write $\text{dom}(f)=A$ and $\text{cod}(f)=B$.
>^domain-codomain-endomorphism-operator-definition

>[!definition] Isomorphism, Retraction
>A morphism $A \xrightarrow{f} B$ is an *isomorphism* when it has an *inverse* morphism $B \xrightarrow{f^{-1}} A$ satisfying $$\begin{aligned}&f^{-1} \circ f = \text{id}_A &f \circ f^{-1} = \text{id}_B \end{aligned}$$ We then say that $A$ and $B$ are isomorphic, or $A \simeq B$. If only the left or right equation holds, we say it is left-invertible or right-invertible. A right invertible morphism is also called a retraction.
>
>Furthermore, if a morphism has an inverse, then it is unique.
>^isomorphism-retraction-definition

As an example, in the case of the category of sets and the functions between them, the isomorphisms are the bijections of sets.

>[!definition] Skeletal Categories
>A category is *skeletal* when any two [[Basics#^isomorphism-retraction-definition|isomorphic]] objects are equal.
>^skeletal-definition

>[!definition] Groupoids and Groups
>A *groupoid* is a category where every morphism is an isomorphism. A *group* is a groupoid with one object.
>^groupoid-definition

>[!definition] Opposite Categories
>Given a category $\textbf{C}$, its *opposite* $\textbf{C}^\text{op}$ is a category with the same objects, but with $\textbf{C}^\text{op}(A, B)$ given by  $\textbf{C}(B, A)$. That is, the morphisms $A \to B$ in $\textbf{C}^\text{op}$ are the morphisms $B \to A$ in $\textbf{C}$.
>^opposite-category-definition

>[!definition] Product Category
>For categories $\textbf{C}$ and $\textbf{D}$, their *product* is a category $\textbf{C} \times \textbf{D}$, whose objects are pairs $(A, B)$ of objects $A \in \operatorname{Ob}(\textbf{C})$ and $B \in \operatorname{Ob}(\textbf{D})$, and whose morphisms are pairs $(A, B) \xrightarrow{f, g} (C, D)$ with $A \xrightarrow{f} C$ and $B \xrightarrow{g} D$
>^product-category-definition

>[!definition] Discrete Category
>A category is discrete when all morphisms are identities.
>^discrete-definition

>[!definition] Indiscrete Category
>A category is indiscrete when there is a unique morphism $A \to B$ for each two objects $A$ and $B$.
>^indiscrete-definition

### Graphical Notation

We use string diagrams for morphisms and their composites. We draw an object $A$ as:
![[Pasted image 20250510225115.png | center | 100]]

However, it is more apt to think of this as the morphism $A \xrightarrow{\text{id}_A} A$, as in category theory, morphisms are more important than the objects. A morphism $A \xrightarrow{f} B$ is drawn as a box taking an input from below and an output from the top:
![[Pasted image 20250510230102.png | center | 100]]
The composition of $A \xrightarrow{f} B$ and $B \xrightarrow{g} C$ is then drawn by connecting the output of $f$ into the input of $g$:
![[Pasted image 20250510230153.png | center | 100]]
 
The identity law and associativity law in [[Basics#^category-definition |the definition of categories]] are then shown as follows:
![[Pasted image 20250510230342.png | center | 600]]

To make the laws immediately obvious, we do not depict the identity morphisms at all and do not include the bracketing of composites. This notation is useful because the axioms are a consequence of the notation. This is because the axioms of a category are about stringing objects together in a sequence.

### Functors

There is an interesting notion of the morphisms between categories. These are functors.

>[!definition] Functor, Covariance, Contravariance
>Given categories $\textbf{C}$ and $\textbf{D}$, a functor $F: \textbf{C} \to \textbf{D}$ is defined by the following:
>- For each object $A \in \operatorname{Ob}(\textbf{C})$, an object $F(A) \in \operatorname{Ob}(\textbf{D})$. 
>- For each morphism $A \xrightarrow{f} B$ in $\textbf{C}$, a morphism $F(A) \xrightarrow{F(f)} F(B)$ in $\textbf{D}$.
>These must follow the following properties:
>- $F(g \circ f) = F(g) \circ F(f)$ for all morphisms $A \xrightarrow{f} B$ and $B \xrightarrow{g} C$ in  $\textbf{C}$.
>- $F(\text{id}_A) = \text{id}_{F(A)}$ for every object $A$ in $\textbf{C}$
>Functors are implicitly *covariant*. There are also *contravariant* versions that reverse the direction of morphisms: $F(g \circ f) = F(f) \circ F(g)$. We will only use this covariant direction, and model the contravariant version $\textbf{C} \to \textbf{D}$ as a covariant functor $\textbf{C}^\text{op} \to \textbf{D}$ where $\textbf{C}^\text{op}$ is an [[Basics#^opposite-category-definition|opposite category]].
>
>^functor-definition

A functor between [[Basics#^groupoid-definition|groups]] is also called a *group homomorphism*, which coincides with the usual notion.

We can further use functors to give a notion of equivalence in categories:

>[!definition] Equivalence
>A functor $F: \textbf{C} \to \textbf{D}$ is an *equivalence* when it is:
>- *full*, meaning that for the functions that take the morphisms $\textbf{C}(A, B) \to \textbf{D}(F(A), F(B))$ given by $f \mapsto F(f)$ are surjective for all $A, B \in \operatorname{Ob}(\textbf{C})$. That is, every morphism $\textbf{D}(F(A), F(B))$ has a corresponding morphism $\textbf{C}(A, B)$. 
>- *faithful*, meaning that for the functions that take the morphisms $\textbf{C}(A, B) \to \textbf{D}(F(A), F(B))$ given by $f \mapsto F(f)$ are injective for all $A, B \in \operatorname{Ob}(\textbf{C})$. That is, every morphism $\textbf{C}(A, B)$ has a corresponding morphism $\textbf{D}(F(A), F(B))$. 
>- *essentially surjective* on objects, meaning that for each object $B \in \operatorname{Ob}(\textbf{D})$ there is an object $A \in \operatorname{Ob}(\textbf{C})$ such that $B \simeq F(A)$ where $\simeq$ denotes [[Basics#^isomorphism-retraction-definition|isomorphism]].
>^equivalence-definition

If two categories are equivalent, then one is just as good as another when doing category theory. It might be much easier to work with one definition of a category than an equivalent one, which is why the notion of equivalence is important.

>[!definition] Subcategory
>A category $\textbf{C}$ is a *subcategory* of a category $\textbf{D}$ when every object of $\textbf{C}$ is an object of $\textbf{D}$, every morphism of $\textbf{C}$ is a morphism of $\textbf{D}$, and composition and identities in $\textbf{C}$ are the same as in $\textbf{D}$. 
>
>In other words, the inclusion $C \to D$ is a [[Basics#^equivalence-definition|faithful functor]].
>^subcategory-definition

>[!definition] Skeleton
>Every category has a skeleton, a smaller category with the same algebraic structure, that is equivalent to it.
>
>A *skeleton* of a category $\textbf{C}$ is a [[Basics#^subcategory-definition|subcategory]] $\textbf{S}$ such that every object in $\textbf{C}$ is [[Basics#^isomorphism-retraction-definition|isomorphic]] in $\textbf{C}$ to exactly one object in $\textbf{S}$.
>
>Intuitively, a skeleton is built by restricting the category $\textbf{C}$ to contain just one object from each isomorphism class. The definition says, in other words, that the inclusion functor $\textbf{S} \to \textbf{D}$ is an equivalence and that $\textbf{S}$ is [[Basics#^skeletal-definition|skeletal]].
>^skeleton-definition


### Natural Transformations

Just as a functor is a map between categories, a map between functors is a *natural transformation*.

>[!definition] Natural Transformation, Natural Isomorphism
>Given functors $F: \textbf{C} \to \textbf{D}$ and $G: \textbf{C} \to \textbf{D}$, a *natural transformation* $\zeta: F \Rightarrow G$ is assigns every object $A$ in $\textbf{C}$ a morphism $F(A) \xrightarrow{\zeta_A} G(A)$ in $\textbf{D}$, such that the following diagram commutes:
>![[Pasted image 20250511010506.png | center]]
>This means that $$\zeta_B \circ F(f) = G(f) \circ \zeta_A,$$
>or in other words, that transforming $F(A)$ to $G(A)$ and then applying $G(f)$ yields the same result as first applying $F(f)$ and then transforming $F(B)$ to $G(B)$.
>
>If every $\zeta_A$ is an [[Basics#^isomorphism-retraction-definition|isomorphism]] then $\zeta$ is called a *natural isomorphism* and $F$ and $G$ are *naturally isomorphic*. 
>^natural-transformation-definition

The notion of natural transformations and functors leads to the description of many important concepts in mathematics:

>[!example] Group Representation
>A *group representation* is a functor $\textbf{G} \to \textbf{Vect}$, where $\textbf{G}$ is a [[Basics#^groupoid-definition|group]]. An *intertwiner* is a natural transformation between such functors. 
>^group-representation-example

This notion then leads to another concept of equivalence:

>[!definition] Equivalence by Natural Isomorphism
>A functor $F: \textbf{C} \to \textbf{D}$ is an *equivalence* if and only if there exists a functor $G: \textbf{D} \to \textbf{C}$ and [[Basics#^natural-transformation-definition|natural isomorphisms]] $G \circ F \simeq \text{id}_\textbf{C}$ and $\text{id}_\textbf{D} \simeq F \circ G$.
>^equivalence-by-natural-transformation

A functor is an equivalence by the [[Basics#^equivalence-by-natural-transformation|above definition]] just when it is an equivalence by the [[Basics#^equivalence-definition|previous definition]], so we use the term 'equivalence' to refer to both themes. We should consider the differences between the two definitions. One is written on the internal structure of categories, on the objects and morphisms. The other is written on the external structure, given by functors and the natural transformations between them. 

### Limits

*Limits* are recipes for discovering *universal properties* in objects and morphisms, with great practical use in category theory.

>[!example] Disjoint Unions and Limits
>We consider the disjoint union $S+T$ of the sets $S$ and $T$. These sets some equipped with the functions $S \xrightarrow{i_S} S+T$ and $T \xrightarrow{i_T} S+T$ that show how sets are embedded in the disjoint union. These functions have a special property, a function $S + T \xrightarrow{f} U$ corresponds exactly to a pair of functions of types $S \xrightarrow{f_S} U$ and $T \xrightarrow{f_T} U$ such that $f \circ i_S = f_S$ and $f \circ i_T = f_T$. The concepts of *limits* and *colimits* generalize this observation.
>^disjoint-union-example

>[!definition] Product, Coproduct
>Given objects $A$ and $B$, a *product* is an object $A \times B$ with morphisms $A \times B \xrightarrow{p_A} A$ and $A \times B \xrightarrow{p_B} B$ such that any two morphisms $X \xrightarrow{f} A$ and $X \xrightarrow{g} B$ allow a **unique** morphism $\binom{f}{g}: X \to A \times B$ with $p_A \circ \binom{f}{g} = f$ and $p_B \circ \binom{f}{g} = g$. The following commutative diagram summarizes these relationships:
>
>![[Pasted image 20250511130400.png|center|600]]
>
>A *coproduct* is the dual notion, that reverses the direction of all arrows in this diagram. Given objects $A$ and $B$, a coproduct is an object $A+B$ equipped with morphisms $A \xrightarrow{i_A} A+B$ and $B \xrightarrow{i_B} A+B$, such that for any morphisms $A \xrightarrow{f} X$ and $B \xrightarrow{g} X$, there is a unique morphism $\begin{pmatrix}f & g \end{pmatrix}: A + B \to X$ such that $\begin{pmatrix}f & g \end{pmatrix} \circ i_A = f$ and $\begin{pmatrix}f & g \end{pmatrix} \circ i_B = g$.
>^product-coproduct-definition

>[!definition] Terminal Object, Initial Object
>An object $A$ is *terminal* if for every object $X$, there is exactly one morphism $X \to A$. It is initial if for every object $X$, there is exactly one morphism $A \to X$
>^terminal-initial-definition

A category may not have any of these structures, but if they exist they are unique up to isomorphism.

>[!definition] Cartesian Category
>A category is *Cartesian* when it has a terminal object and products of any pairs of objects.
>^cartesian-category-definition

These structures pop up everywhere.

>[!example]
>Products, coproducts, terminal objects and initial objects take the following forms in our main example categories:
>- In [[Basics#^set-cat-definition|$\textbf{Set}$]], products are given by the Cartesian product, and coproducts by the disjoint union, any 1-element set is a terminal object and the empty set is the initial object.
>- In [[Basics#^rel-cat-definition|$\textbf{Rel}$]], products and coproducts are both given by the disjoint union, and the empty set is both the terminal and initial object.

Given a pair of functions $S \xrightarrow{f, g} T$, it is interesting to ask on which elements of $S$ they take the same value. Category theory dictates that we should not talk about the elements, but use morphisms to get the same information using a universal property. This leads to the notion of an equalizer, a structure that *may or may not* exist in a category.

>[!definition] Equalizer
>For morphisms $A \xrightarrow{f, g} B$ their *equalizer* is a morphism $E \xrightarrow{e} A$ satisfying $f \circ e = g \circ e$, such that any morphism $E' \xrightarrow{e'} A$ satisfying $f \circ e' = g \circ e'$ allows a unique morphism $E' \xrightarrow{m} E$ with $e' = e \circ m$:
>
>![[Pasted image 20250511181135.png|center|500]]
>
>The *coequalizer* of $f$ and $g$ is their equalizer in the [[Basics#^opposite-category-definition|opposite category]].
>^equalizer-definition

>[!example] Equalizers in Example Categories
>- The categories $\textbf{Set}$, $\textbf{Vec}$ and $\textbf{Hilb}$ have equalizers for all pairs of parallel morphisms. An equalizer for $A \xrightarrow{f, g} B$ is the set $E = \{a \in A \mid f(a)=g(a)\}$, equipped with its embedding $E \xrightarrow{e} A$. That is, it is the largest subset of $A$ on which $f$ and $g$ agree.
>- The category $\textbf{Rel}$ does not have all equalizers. 
>>[!proof]
>>Consider the relation $R = \{(y, z) \in \mathbb{R}^2 \mid y < z \in \mathbb{R}\}: \mathbb{R} \to \mathbb{R}$. Suppose $E: X \to \mathbb{R}$  were an equalizer of $R$ and $\text{id}_\mathbb{R}$. Then $R \circ R = \text{id}_\mathbb{R} \circ R$, so there is a relation $M: \mathbb{R} \to X$ with $R = E \circ M$. Now $E \circ M \circ E = R \circ E = \text{id}_\mathbb{R} \circ E = E$, and since $S = \text{id}_X$ is the unique morphism satisfying $E \circ S = E$, we must have $M \circ E = \text{id}_X$. But then $xEy$ and $yMx$ for some $x \in X$ and $y \in \mathbb{R}$. It follows that $y(E \circ M)y$, that is, $y < y$, which is a contradiction
>
>^equalizer-example

A kernel is a special kind of equalizer:

>[!definition] Kernel
>A *kernel* of a morphism $A \xrightarrow{f} B$  is an equalizer of $f$ *and* the *zero* morphism $A \xrightarrow{0} B$
>^kernel-definition

A last instance of universal properties is the idea of split idempotents.

>[!definition] Idempotent, Splitting
>An endomorphism $A \xrightarrow{f} A$ is called *idempotent* when $f \circ f = f$. An idempotent $A \xrightarrow{f} A$ *splits* when there is an object $\hat{f}$ and morphisms $A \xrightarrow{p_f} \hat{f}$ and $\hat{f} \xrightarrow{i_f} A$ that satisfy $i_f \circ p_f = f$ and $p_f \circ i_f = \text{id}_\hat{f}$. 
>
>Given such a split idempotent, the injection $\hat{f} \xrightarrow{i_f} A$ gives an [[Basics#^equalizer-definition|equalizer]] of $f$ and $\text{id}_A$, and the projection $A \xrightarrow{p_f} \hat{f}$ gives a [[Basics#^equalizer-definition|coequalizer]] of $f$ and $\text{id}_f$.
>^idempotent-splitting-definition




## Hilbert Spaces

### Vector Spaces

We will take the terminology, concepts, and techniques in [[Nomenclature and Notation]] and [[Linear Algebra]], but in the lens of category theory.

>[!definition] Vector Space
>A *vector space* is a set $V$ with a chosen *zero* element $0 \in V$, an addition operation $+: V \to V$ and a scalar multiplication operation $\cdot : \mathbb{C} \times V \to V$. 
>^vector-space-category-definition

>[!definition] Linear Maps and Antilinear Maps
>A *linear map* is a function $f: V \to W$ between vector spaces, that satisfies $f(a+b)=f(a)+f(b)$ and $f(s \cdot a) = s \cdot f(a)$. An antilinear map is one that satisfies $f(s \cdot a) = s^* \cdot f(a)$ instead of the regular linear requirement, where $s^*$ denotes complex conjugation.
>^linear-antilinear-map-definition

Vector spaces and linear maps form the category $\textbf{Vect}$.

>[!definition] $\textbf{Vect}$ and $\textbf{FVect}$
>In the [[Basics#^category-definition|category]] $\textbf{Vect}$ of vector spaces and linear maps:
>- **Objects** are complex vector spaces.
>- **Morphisms** are linear functions.
>- **Composition** is the composition of functions
>- **Identity Morphisms** are the identity functions.
>  
>We write $\textbf{FVect}$ for the restriction of $\textbf{Vect}$ to those vector spaces isomorphic to $\mathbb{C}^n$ for some natural number $n$. These are also called *finite dimensional*. 
>
>Any morphism $f: V \to W$ in $\textbf{Vect}$ has a [[Basics#^kernel-definition|kernel]], $$\operatorname{ker}(f)=\{v \in V \mid f(v) = 0\}.$$ Hence, kernels in the categorical sense align with those in the sense of linear algebra. 
>^vect-definition

>[!definition] Direct Sum
>The *direct sum* of vector spaces $V$ and $W$ is the vector space $V \oplus W$, whose elements are pairs $(a, b)$ of elements $a \in V$ and $b \in W$, with entry-wise addition and scalar multiplication.
>^direct-sum-definition

Direct sums are both [[Basics#^product-coproduct-definition|products]] and [[Basics#^product-coproduct-definition|coproducts]] in the category $\textbf{Vect}$. Similarly, the zero dimensional space is both [[Basics#^terminal-initial-definition|terminal]] and [[Basics#^terminal-initial-definition|initial]] in $\textbf{Vect}$.

### Bases and Matrices

>[!definition] $\textbf{Mat}_\mathbb{C}$
>In the [[Basics#^skeletal-definition|skeletal category]] $\textbf{Mat}_\mathbb{C}$:
>- **Objects** are natural numbers $0, 1, 2, \ldots$.
>- **Morphisms** $m \to n$ are complex matrices with $m$ rows and $n$ columns.
>- **Composition** is given by matrix multiplication.
>- **Identities** $n \xrightarrow{\text{id}_n} n$ are given by $n$ by $n$ matrices with $1$ on the main diagonal, and $0$ elsewhere, as shown in [[Linear Algebra#^identity-example|Linear Algebra]].
>
 ^matc-definition

This theory of matrices is 'just as good' as the theory of finite-dimensional vector spaces, made precise by category theory.

>[!proof] There is an equivalence of categories $\textbf{Mat}_\mathbb{C} \to \textbf{FVect}$ that sends $n$ to $\mathbb{C}^n$ and a matrix to its associated linear map. 
>Because every finite dimensional complex vector space $H$ is isomorphic to $\mathbb{C}^{\operatorname{dim}(H)}$, the functor is [[Basics#^equivalence-definition|essentially surjective]] on objects. It is both full and faithful because there is an exact correspondence between matrices and linear maps for finite dimensional vector spaces, as given in [[Linear Algebra#^matrix-note|Linear Algebra]].

We can now talk about Hilbert Spaces.

### Hilbert Spaces

We gave a brief introduction of Hilbert Spaces in [[Linear Algebra#^ad6c5b|Linear Algebra]]. Here we try to make it more rigorous. Recall the [[Linear Algebra#^a74762|inner product]] and the [[Linear Algebra#^norm-definition|norm]]. The complex numbers carry a canonical inner product $$\langle s \vert t \rangle = s^*t.$$
The induced norm satisfies the triangle inequality $||a+b|| \leq ||a|| + ||b||$ by virtue of the [[Linear Algebra#^6a978f|Cauchy-Schwarz Inequality]], $$|\langle a \vert b \rangle|^2 \leq \langle a \vert a \rangle \cdot \langle b \vert b \rangle$$
Thanks to these properties, it makes sense to think of $||a-b||$ as the distance between vectors $a$ and $b$. 

A Hilbert Space is an inner product space in which it makes sense to add infinitely many vectors in certain cases.

>[!definition] Hilbert Space
>A *Hilbert space* is a vector space $H$ with an inner product that is *complete*, as in if a sequence of vectors $v_1, v_2, \ldots$ of vectors satisfies $\sum_{i=1}^\infty ||v_i|| < \infty$, then there is a vector $v$ such that $||v - \sum_{i=1}^n v_i||$ tends to zero as $n$ goes to infinity. 
>^hilbert-space-definition

Every finite-dimensional vector space with an inner product is necessarily complete. Any vector space with an inner product can be completed to a Hilbert space by formally adding the appropriate limit vectors. 

There is a notion of bounded linear maps between Hilbert spaces that make use of the inner product structure. The idea is that for each map there is some maximum amount by which the [[Linear Algebra#^norm-definition|norm]] of a vector can increase.

>[!definition] Bounded Linear Operator (blo)
>A linear map $f: H \to K$ between Hilbert spaces is *bounded* when there exists a number $r \in \mathbb{R}$ such that $||f(a)|| \leq r \cdot ||a||$ for all $a \in H$.
>^blo-definition

Every linear map between finite dimensional Hilbert spaces is bounded. Hilbert spaces and bounded linear maps form the category $\textbf{Hilb}$. This category will be the main example throughout these notes to model phenomena and quantum theory.

>[!definition] $\textbf{Hilb}$ and $\textbf{FHilb}$
>In the category $\textbf{Hilb}$ of Hilbert spaces and bounded linear maps:
>- **Objects** are the Hilbert spaces.
>- **Morphisms** are bounded linear maps.
>- **Composition** is composition of linear maps as ordinary functions.
>- **Identity Morphisms** are given by the identity linear maps.
>
>We write $\textbf{FHilb}$ for the restriction of $\textbf{Hilb}$ to finite dimensional Hilbert spaces.
>^hilb-definition

Since every linear map between Hilbert spaces is bounded, $\textbf{FHilb}$ is an equivalent category to $\textbf{FVect}$. In particular, inner products play no essential role. We will see later how to model inner products categorically, with the idea of *daggers*. 

Hilbert spaces have a more discerning notion of [[Linear Algebra#^basis-definition|basis]].

>[!definition]
>For a Hilbert space $H$, an *orthogonal basis* is a family of elements $\{e_i\}$ with the following properties:
>- They are *pairwise orthogonal*, as in $\langle e_i \vert e_j \rangle = \delta_{ij}$
>- Every element $a \in H$ can be written as an infinite linear combination of $e_i$; that is, there are coefficients $a_i \in \mathbb{C}$ for which $||a - \sum^n_{i=1}a_ie_i||$ tends to zero as $n$ goes to infinity.
>- It is *orthonormal* when additionally $\langle e_i \vert e_i \rangle = 1$.
>^hilb-basis-definition

Any orthogonal family of elements is linearly independent. For finite dimension Hilbert spaces, the notion of basis is still useful. Hence, once we fix ordered bases on finite dimensional Hilbert spaces, linear maps correspond to matrices, just as with vector spaces. For infinite dimension Hilbert spaces however, having a basis for the underlying vector space is rarely useful. 

If two vector spaces carry inner products, then we can give an inner product to the direct sum, leading to the direct sum of Hilbert spaces:

>[!definition] Direct Sum of Hilbert Spaces
>The *direct sum* of Hilbert spaces $H$ and $K$ is the vector space $H \oplus K$, made into a Hilbert space by the inner product $\langle (a_1, b_1) \vert (a_2, b_2) \rangle = \langle a_1 \vert a_2 \rangle + \langle b_1 \vert b_2 \rangle$.
>
>Direct sums provide both [[Basics#^product-coproduct-definition|products]] and [[Basics#^product-coproduct-definition|coproducts]] for the category [[Basics#^hilb-definition|$\textbf{Hilb}$]]. Hilbert spaces have the good property that any closed subspace can be complemented. That is, if the inclusion $U \hookrightarrow V$ is a morphism of $\textbf{Hilb}$ satisfying $||u||_U = ||u||_H$, then there exists another inclusion morphism $U^\perp \hookrightarrow V$ of $\textbf{Hilb}$ with $V = U \oplus U^\perp$. Explicitly, $U^\perp$ is the *orthogonal subspace* $\{a \in V \mid \forall b \in U: \langle a \vert b \rangle = 0\}$.
>^hilb-direct-sum-definition
>

### Adjoint Linear Maps

We take the idea of [[Linear Algebra#Adjoint and Hermitian Operators|adjoint linear maps]] further here by defining some extra terms.

>[!definition]
>A bounded linear map $H \xrightarrow{f} K$ between Hilbert spaces is an *isometry* when $f^\dagger \circ f = \text{id}_H$ and a *partial isometry* when $f^\dagger \circ f$ is a [[Linear Algebra#^2a48c0|projector]].

^7a8d4c

Recall the idea of *kets* and *bras* in Dirac Notation. The correspondence between these two, that $\ket{v} = \bra{v}^\dagger$, leads to the notion of a dual space.

>[!definition] Dual Space
>For a Hilbert space $H$, its *dual Hilbert Space* $H^*$ is the vector space $\textbf{Hilb}(H, \mathbb{C})$ consisting of all bounded linear maps from $H$ to $\mathbb{C}$.
>
>A Hilbert space is isomorphic to its dual in an anti-linear way: The map $H \to H^*$ given by $\ket{a} \mapsto \varphi_a = \bra{a}$ is an invertible anti-linear function. The inner product on $H^*$ is given by $\langle \varphi_a \vert \varphi_b \rangle_{H^*} = \langle a \vert b \rangle_H$, and makes the function $\ket{a} \mapsto \bra{a}$ bounded. 

### Tensor Product

We also give more rigorous definitions for the [[Linear Algebra#Tensor Products|tensor product]]. As previously mentioned, a tensor product is a way to make a new vector space out of two given ones. 

>[!definition] Bilinear Functions
>If $U$, $V$, and $W$ are vector spaces, a function $f: U \times V \to W$ is called *bilinear* when it is linear in each variable; that is, when the function $u \mapsto f(u, v)$ is linear for each $v \in V$ and the function $v \mapsto f(u, v)$ is linear for each $u \in U$.

>[!definition] Tensor Products
>The *tensor product of vector spaces* $U$ and $V$ is a vector space $U \otimes V$ together with the bilinear function $f: U \times V \to U \otimes V$ such that for every bilinear function $g: U \times V \to W$ there exists a unique linear function $h: U \otimes V \to W$ such that $g = h \circ f$. This is characterized by the following diagram:
>
>![[Pasted image 20250512165554.png|center|500]]
>
>Note that $U \times V$ is not a vector space, so it doesn't make sense to ask if $f$ or $g$ are linear. The function $f$ usually stays anonymous and is written as $f: (a, b) \mapsto a \otimes b$. It follows that arbitrary elements of $U \otimes V$ take the form $\sum_{i=1}^n s_ia_i \otimes b_i$ for $s_i \in \mathbb{C}$, $a_i \in U$ and $b_i \in V$. The tensor product also extends to linear maps. If $f_1: U_1 \to V_1$ and $f_2: U_2 \to V_2$ are linear maps, then there exists a unique linear map $f_1 \otimes f_2: U_1 \otimes V_1 \to U_2 \otimes V_2$ that satisfies  $(f_1 \otimes f_2)(a_1 \otimes a_2) = f_1(a_1) \otimes f_2(a_2)$ for $a_1 \in U_1$ and $a_2 \in U_2$. In this way, the tensor product becomes a functor $\otimes : \textbf{Vect} \times \textbf{Vect} \to \textbf{Vect}$.
>^tensor-product-functor-definition

>[!definition] Tensor Products of Hilbert Spaces
>The *tensor product of Hilbert spaces* $H$ and $K$ is the Hilbert space $H \otimes K$ built by taking the tensor product of the underlying vector spaces, and taking the inner product to be $\langle a_1 \otimes b_1 \vert a_2 \otimes b_2 \rangle = \langle a_1 \vert a_2 \rangle_H \cdot \langle b_1 \vert b_2 \rangle_K$, then completing it. If $H \xrightarrow{f} H'$ and $K \xrightarrow{g} K'$ are bounded linear maps, then so is the continuous extension of the tensor product of linear maps to a function that we again call $f \otimes g: H \otimes K \to H' \otimes K'$. This again gives a functor $\otimes : \textbf{Hilb} \times \textbf{Hilb} \to \textbf{Hilb}$.
>
>If $\{e_i\}$ is an orthonormal basis for the Hilbert space $H$, and $\{f_j\}$ an orthonormal basis for $K$, then $\{e_i \otimes f_j\}$ is an orthonormal basis for $H \otimes K$. So when $H$ and $K$ are finite-dimensional, there is no difference between their tensor products as vector spaces and as Hilbert spaces.
>^tensor-product-hilb-definition

## Quantum Information

Yeah this is a chapter in the book but this is covered in [[The Postulates of Quantum Mechanics]] and [[Density Operators]] sooooooooooooooooo
