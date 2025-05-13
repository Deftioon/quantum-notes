We interpret objects of categories as systems and the morphisms as the processes in between them. A monoidal category has additional structure allowing us to consider processes that occur in *parallel*, as well as sequentially. One could interpret this in the following ways:
- letting independent physical systems evolve simultaneously;
- running computer algorithms in parallel;
- taking products or sums of algebraic or geometric structures;
- using separate proofs of $P$ and $Q$ to construct a proof of the conjunction ($P$ and $Q$).

## Monoidal Structure

It is perhaps surprising that a non-trivial theory can be developed from such simple intuition. But, in fact, some interesting general issues quickly arise. For example, let $A$, $B$, and $C$ be processes, and write $\otimes$ for parallel composition. One might say that $(A \otimes B) \otimes C$ should be equal to $A \otimes (B \otimes C)$, as they are different ways to express the same arrangement of systems. 

However, this is too strong and might not be the case. For example, if $A$, $B$, and $C$ are [[Basics#^hilbert-space-definition|Hilbert spaces]], and $\otimes$ is the usual [[Basics#^tensor-product-functor-definition|tensor product]], then these two composite Hilbert spaces are not *exactly equal*, they are only *isomorphic*. 

Now we have a new problem, what equations should these isomorphisms satisfy? The theory of monoidal categories is formulated to deal with these issues.

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



