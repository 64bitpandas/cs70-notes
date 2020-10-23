# Countability

Injection: one-to-one $$|A| \le |B|$$ $$\forall x,y \in D, f(x) = f(y) \implies x = y$$

Surjection: onto $$|A| \ge |B|$$$$\forall y \in R, \exists x \in D, y = f(x)$$

Bijection: both injection and surjection $$|A| = |B|$$ \(Isomorphism Principle\)





Countability

A set S is countable if there is a bijection from S to the set of natural numbers $$\mathbb{N}$$or a subset of N

Bijection from A to B $$\implies$$bijection from B to A, so a bijection either to or from the natural numbers both imply that a set is countably finite

Common strategies for proving S is countable:

* Find a bijection from S to N or N to S \(must prove one to one and onto\)
* Find an injection from S to N, and an injection from N to S
* Enumeration: list all elements of S

Enumerability

Listing a set implies that it is countable.

* Output element of S
* Output next element of S

Every element $$x \in S$$must have a specific, finite position in the list.

Kind of like streams

Any infinite set that is countable is as large as the set of integers.

Example: enumerate all binary strings: $$B = \{0, 1\}^* = \{\emptyset, 0, 1, 00, 01, 10, 11, 000 \cdots \}$$   
This is enumerable because we can say that a string with $$n$$bits will be guaranteed to appear before position $$2^{n+1}$$

Example of non-enumerable set: rational numbers- can't write fractions in an order such that you can get to the next fraction in a finite number of steps



Pairs of natural numbers

A pair of natural numbers $$N \times N$$ has size $$|N| \times |N|$$so it is countably infinite. We can enumerate this: $$(0,0), (1,0), (0,1), (2,0) \cdots$$which guarantees that the pair $$(a,b)$$is in the first $$(\frac{(a+b+1)(a+b)}{2}$$elements in the list. \(triangle\)

![](../.gitbook/assets/image%20%2813%29.png)

Rational numbers

Rationals are countably infinite by writing them all in the form $$(p,q)$$for a rational number $$n=\frac{p}{q}$$. We determined that all pairs of natural numbers is countable so rational numbers are as well.



Diagonalization

Proof by contradiction: assume that a set S is countable \(even if it isn't\). Then, there must exist a listing that contains all elements in the list \(enumeration\).

We can construct an item that isn't in the set by taking the diagonals of digits in the set:

![](../.gitbook/assets/image%20%2815%29.png)

This can be used to prove that real numbers are not countable.

Formal steps:

* Assume that a set S can be enumerated.
* Consider an arbitrary list of all the elements of S.
* Use the diagonal from the list to construct a new element t.
* Show that t is not in the list, but that t is in S.
* This is a contradiction.

{% embed url="https://www.youtube.com/watch?v=elvOZm0d4H0" %}

Continuum hypothesis: there is no set with cardinality between the naturals and the reals. \(TODO what is cardinality?\)

Generalized continuum hypothesis: there is no infinite set whose cardinality is between the cardinality of an infinite set and its power set. \(The power set of the natural numbers is not countable.\)

