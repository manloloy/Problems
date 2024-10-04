# A collection of problems we are discussing

## Problem 1
In a specified 24-hour period, a student wakes up at time T1 and goes to sleep at some later time T2. The
student always goes to sleep after he wakes up. Students do not stay up after midnight! The outcomes of
the random experiment are the pairs (T1, T2).
1. Find the sample space and sketch it on the x-y plane.
2. Consider the event A: “student is awake at 9 am.” Specify the set A and sketch it on the on the x-y
plane.
3. Consider the even B: “Student is asleep more than he is awake.” Specify the set B and sketch it on
the on the x-y plane.
4. Sketch the region corresponding to the event Ac \ B and describe the corresponding event in words.


## Problem 2
For $A_1, A_2, \dots, A_n \in \mathcal{F}$, show that

$$
P\left( \bigcup_{i=1}^{n} A_i \right) \leq \sum_{i=1}^{n} P(A_i)
$$

## Probelem 3
Let $A_1, A_2, \dots, A_n$ be events where $n \geq 2$, and prove that

$$
P\left( \bigcup_{i=1}^{n} A_i \right) = \sum_{i=1}^{n} P(A_i) - \sum_{1 \leq i < j \leq n} P(A_i \cap A_j) + \sum_{1 \leq i < j < k \leq n} P(A_i \cap A_j \cap A_k) - \cdots + (-1)^{n+1} P(A_1 \cap A_2 \cap \cdots \cap A_n)
$$

## Problem 4
Given the following context tree
```
        Root
        /  \
      0     1
    B(3/4)  /  \
           0 (01)  1 (11)
        B(1/3)   B(1/4)
```


- Root → 0: Bernoulli(3/4) means that after observing a 0, the next bit has a 3/4 chance of being 1.
- Suffix 01: Bernoulli(1/3) means that after observing the sequence 01, the next bit has a 1/3 chance of being 1.
- Suffix 11: Bernoulli(1/4) means that after observing 11, the next bit has a 1/4 chance of being 1.

The extended tree is shown below.
```
            Root
        /         \
      0            1
    /   \         /  \
  0 (00) 1 (10) 0 (01)  1 (11)
  B(3/4) B(3/4) B(1/3)  B(1/4)
```

Write out the Transition Matrix and solve the Statrionary probabilities P(0) and P(1)


## Problem 5a
If $X$ is geometric, show that $P(X = n + k \mid X > n) = P(X = k)$ for $k, n \geq 1$. 

Why do you think that this is called the "lack of memory" property? Does any other distribution on the positive integers have this property?

## Problem 5b
Show that the exponential variable also has the "lack of memory" property. This is similar to problem 5

## Problem 5c
Show that if a random variable has the "lack of memory" property, then it must be a geometric random variable or an exponential random variable

## Problem 6
TODO: Fill in with Cauchy Random Variable Experiment and discussion

## Problem 7
- Let $\( P \sim U(0,1) \)$ be a random variable.
- Let $\( x_1, x_2, \dots, x_n \)$ be random variables such that, conditioned on $\( P = p \)$, they are independent and identically distributed (iid) Bernoulli random variables with parameter \( p \).
  - That is, conditioned on $\( P = p \)$, we have:
    $$\[
    x_i | P = p \sim \text{Bernoulli}(p) \quad \text{for } i = 1, 2, \dots, n.
    \]$$
1. What is the distribution of $\( x_1, x_2, \dots, x_n \)$ conditioned on $\( P = p \)$?
2. What is $\( \mathbb{E}[P | x_1, x_2, \dots, x_n] \)$?

**Note:** Without conditioning on \( P \), the \( x_1, x_2, \dots, x_n \) are exchangeable, but not independent.




