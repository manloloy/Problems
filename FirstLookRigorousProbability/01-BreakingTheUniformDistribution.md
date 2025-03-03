# Proof: The Vitali Set is Not Measurable

## **Definitions**
Define an equivalence relation on $[0,1]$:

$$
x \sim y \iff x - y \in \mathbb{Q}
$$

This partitions $[0,1]$ into **disjoint equivalence classes**.

Define the **Vitali set** $V$ as a choice of exactly one representative from each equivalence class:

$$
V \subset [0,1], \quad \forall x \in [0,1], \exists! v \in V \text{ such that } x \sim v.
$$

## **Proof (by Contradiction)**

1. **Assume $V$ is measurable with probability measure $P(V)$.**  
   Define translated copies:

$$
V_q = V + q = \{ v + q \mid v \in V \}, \quad q \in Q = \mathbb{Q} \cap [-1,1].
$$

2. **The sets $\{V_q\}$ form a countable partition of $[0,1]$.**  
   Since rationals are dense, we cover $[0,1]$ with **disjoint translates** of $V$:

$$
\bigcup_{q \in Q} V_q = [0,1].
$$

3. **By translation invariance, $P(V_q) = P(V)$.**  
   Since probability measure is translation-invariant:

$$
\sum_{q \in Q} P(V) = P([0,1]) = 1.
$$

4. **Contradiction: The sum is either $0$ or $\infty$.**  
   - If $P(V) = 0$, then $P([0,1]) = 0$.
   - If $P(V) > 0$, then $\sum_{q \in Q} P(V) = \infty$ (since $Q$ is countable).
   - Both contradict $P([0,1]) = 1$.

5. **Conclusion:** $V$ is not measurable.

$$
\Rightarrow V \text{ is not measurable}.
$$


