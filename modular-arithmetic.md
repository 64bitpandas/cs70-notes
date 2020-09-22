# Modular Arithmetic

## What is Modular Arithmetic?

Modular arithmetic is "clock math" - that is, 

This is an important concept in many aspects of computer science, namely cryptography and error correction.

## Key Ideas

**If d divides x and d divides y, then d divides \(y-x\)**. $$d \mid x, d \mid y \implies d \mid (y-x)$$  
\(Reminder: $$a \mid b \iff (\exists q \in \mathbb{Z})(a = qb)$$\)

**Modular Equivalence:** If you're looking at a clock and it becomes 25:00, you know it's actually the same as 1:00. Even if they're technically not the same number, they can be treated the same way.

* More formally: **x is congruent to y modulo m:** $$x \equiv y \pmod{m}$$\*\*\*\*

**Important Notation Distinction:** $$x \pmod{m}$$ is the **class of numbers** that follow the mod rule $$m$$. It can be used to write equivalences \($$10 \equiv 21 \pmod{11}$$\). However, $$\mod(x, m)$$is just a number \(the remainder when dividing x by m\). $$\mod(x,m) = x - \lfloor{\frac{x}{y}}\rfloor \cdot y $$

**Greatest Common Denominator \(GCD Mod Corollary\):** Modular arithmetic can be used to identify an important property of the GCD, which is that $$GCD(x,y) = GCD(x \mod y, y)$$.

## Arithmetic

### Addition

Given that $$a \equiv b \pmod{m}$$, $$a+c \equiv b+c \pmod{m}$$.

![](.gitbook/assets/image%20%287%29.png)

### Multiplication

Multiplication works pretty much how you'd expect it to work. Formally defined, if $$a \equiv b \pmod{m}$$, then $$ka = kb \pmod{m}$$. Intuitively, this means that if you want to multiply a big number, you can take the mod of the big number before multiplying it, and that will be equivalent to multiplying before taking the mod.

As an example, let's try to figure out what day it is in 8 years. We know that there will be 2 leap years with 366 days each, and 6 normal years with 365 days each. We don't really feel like computing $$(365 \cdot 6) + (366 \cdot 2) \pmod{7}$$, so we can instead take the mod of 365 and 366 first. This yields the much simpler expression $$(1 \cdot 6) + (2 \cdot 2) \pmod{7} \equiv 1$$. Therefore, the day in 8 years will be one day after today.

### Division and Inverses

In normal number spaces, the **multiplicative inverse** of x is a y such that $$xy = 1$$. This concept still applies to modular arithmetic! 

If we have $$x \pmod{m}$$, then the multiplicative inverse is defined as a number y such that $$xy = 1 \pmod{m}$$. 

For example, let's take a look at $$4x = 5 \pmod{7}$$. We can multiply both sides by 2 in order to get $$8x = 10 \pmod{7}$$. At this point, we can use the $$\pmod{7}$$to reduce the 8 into a 1 and the 10 into a 3, resulting in $$x = 3 \pmod{7}$$.

There are some values where it's impossible to get an equivalence into the form $$1 \pmod{m}$$. This usually happens when there is a common factor \(like $$8x \equiv y \pmod{12}$$\). In other words, **if the greatest common divisor of x and m is 1, then x has a multiplicative inverse modulo m. \(x is relatively prime to y\).**

## Euclid's Algorithm

![](.gitbook/assets/image%20%284%29.png)

**Euclid's Algorithm** is a recursive procedure for calculating the greatest common denominator. Remember that $$GCD(x,y) = GCD(x \mod y, y)$$ by the GCD Mod Corollary. We can prove that this works using induction:

* Base Case: If y is 0, then any value for x is the GCD since everything can divide 0 to get 0.
* Inductive Case: Proof of the GCD Mod Corollary.

This is a rather efficient algorithm: at every iteration, the value of x and y decrease dramatically- at least by a factor of 2. This makes it $$\theta(\log_2(x))$$\(in other words, we need one division for each bit that is needed to represent $$x$$\).

### Using Euclid's Algorithm for Inverses

Great! We got the GCD. So what?

Remember that **if the GCD of x and m is 1, then there is an inverse of x.** In more concrete terms, we can state **Euclid's Extended GCD Theorem** as such:

$$
ax + by = gcd(x,y)
$$

In other words, the GCD can be written as a scalar multiple of x and y. Since we remember that the definition of the inverse is that $$ax + by = 1$$for some integers a and b, Euclid's Extended Theorem checks out for showing that the inverse exists if the GCD is 1.

