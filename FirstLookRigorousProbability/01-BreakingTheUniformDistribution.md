# Proof: The Vitali Set is Not Measurable

## **Definitions**
Define an equivalence relation on $[0,1]$:

$$
x \sim y \iff x - y \in \mathbb{Q}
$$

This partitions $[0,1]$ into **disjoint equivalence classes**.

Define the **Vitali set** $V$ as a choice of exactly one representative from each equivalence class:

$$
V \subset [0,1], \quad \forall x \in [0,1], \exists! v \in V \text{ such that } x \sim v
$$

## **Proof (by Contradiction)**

1. **Assume $V$ is Lebesgue measurable.**  
   Define $V_q = V + q$ for each $q \in \mathbb{Q} \cap [-1,1]$:

$$
   V_q = \{ v + q \mid v \in V \}.
$$

2. **The sets $\{V_q\}$ form a countable partition of $[0,1]$.**  
   Since rationals are dense, we cover $[0,1]$ with **disjoint translates** of $V$:

$$
   \bigcup_{q \in Q} V_q = [0,1], \quad Q = \mathbb{Q} \cap [-1,1]
$$

3. **By translation invariance of Lebesgue measure, $m(V_q) = m(V)$.**  
   If $m(V)$ exists, then:

$$
   \sum_{q \in Q} m(V) = m([0,1]) = 1
$$

4. **Contradiction: The sum is either $0$ or $\infty$.**  
   - If $m(V) = 0$, then $m([0,1]) = 0$
   - If $m(V) > 0$, then $\sum m(V) = \infty$ (since $Q$ is countable)
   - Both contradict $m([0,1]) = 1$

5. **Conclusion:** $V$ is not measurable.

$$
\Rightarrow V \text{ is not Lebesgue measurable}.
$$
