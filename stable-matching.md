# Stable Matching

The **stable matching problem** deals with how to match one group to another group while trying to maximize everyone's 'happiness'. 

It works best when 



### Some Definitions

In order to more concretely set up the stable matching problem, let's define some terms formally:

A **pairing** is a set of job-candidate pairs that uniquely \(disjointly\) matches each job to each candidate. For example, {\(Esports, Joe\), \(Steakhouse, Donald\)} is a valid pairing if we're trying to match Joe and Donald to two possible jobs.

Note that 'job' and 'candidate' can be replaced with any two arbitrary groups, as long as one group doesn't contain any items from the other group!

A **rogue couple** is a single pair where neither person in the pair wants to be with the other person. If a pairing is **stable**, it cannot contain any rogue couples.

**x-optimal matching** is a stable pairing that favors the choices of group x over the other group. This group is **whichever group chooses**- In the example above, the pairing would be **job optimal**, and **candidate pessimal.**

### The Propose and Reject Algorithm

1. On the first day, each job sends an offer to their favorite candidate.
2. Each candidate has their own set of preferences, though, so if they get multiple job offers they'll reject all but their favorite one.
3. The candidate will then say to their favorite offer, "I like it, but please wait until tomorrow so I can see if I get a better offer."
4. Repeat until each job gets exactly one candidate.

#### Important notes about this algorithm:

* **It is guaranteed to terminate.**
* **Every day, it gets better for candidates.** This is because candidates can choose their best offer, so as more offers keep rolling in they get more \(and better\) choices.

### Proofs of the Algorithm

Insert proof of existence

Insert proof of stability

#### Optimality

Theorem: Job Propose, Candidate Reject produces a job-optimal pairing.

* Proof by contradiction: assume that there's a job j that doesn't get an optimal candidate c.
* Let t be the first day job j gets rejected by its optimal candidate g.
* On that day, there was another job offer j\* that c preferred.
* Therefore, j\* likes c at least as much as the optimal candidate. **This creates a rogue couple.** 
* By the Well Ordering Principle, this is the first day that job j was rejected

**Pessimality**

Theorem: Job Propose, Candidate Reject produces a candidate-pessimal pairing:

* Let T be a pairing where \(j, c\) is a pair.
* Let S be a stable pairing that is worse for c than T is. So \(j, c\*\) is a pair.
* Since j prefers c to c\*, \(j, c\*\) is a rogue couple for S which is a **contradiction.** Therefore, T is the worst possible pairing for c.

### An Example

Let's say that three people, A,B,C, applied to jobs 1,2,3. Their preferences are \(in order from most to least favored\):

CANDIDATES                 JOBS  
A \|\| 1 2 3                         1 \|\| C A B  
B \|\| 1 2 3                         2 \|\| A B C  
C \|\| 2 1 3                         3 \|\| A C B

On day 1, Job 1 will send an offer to candidate C, and jobs 2 and 3 will send an offer to candidate A. Since A got multiple offers, they will reject Job 3.  
**Day 1: \(1,A\), \(2, C\)**

On day 2, Job 1 will send an offer to candidate However, C still prefers Job 1, so they will reject 3.  
**Day 2: \(1**

