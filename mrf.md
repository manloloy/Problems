# Sparse Logistic Regression as Conditional Inference in an Ising MRF

An Ising‐type Markov Random Field over binary variables \(x_i\in\{-1,+1\}\) has joint distribution:

$$
P(x)
\;=\;
\frac{1}{Z}\,\exp\!\Bigl(\sum_{(i,j)\in E}\theta_{ij}\,x_i\,x_j\Bigr),
$$

where \(Z\) is the partition function.

The **conditional** distribution of a single node given all others is

$$
P\bigl(x_i=+1 \mid x_{-i}\bigr)
\;=\;
\frac{P(x_i=+1,x_{-i})}
     {P(x_i=+1,x_{-i}) + P(x_i=-1,x_{-i})}.
$$

## Proof: Gibbs law ⇒ logistic sigmoid

1. **Unnormalized probabilities**  
   Partition‐function factors and any terms not involving \(x_i\) cancel in ratios.  

$$
     P(x_i=+1,\;x_{-i})
     \;\propto\;
     \exp\!\Bigl(\sum_{j\in N(i)}\theta_{ij}\,(+1)\,x_j\Bigr),
$$  

$$
     P(x_i=-1,\;x_{-i})
     \;\propto\;
     \exp\!\Bigl(\sum_{j\in N(i)}\theta_{ij}\,(-1)\,x_j\Bigr).
$$

3. **Odds ratio**  

$$
     \frac{P(x_i=+1 \mid x_{-i})}
          {P(x_i=-1 \mid x_{-i})}
     \;=\;
     \frac{\exp\bigl(\sum_{j}\theta_{ij}\,x_j\bigr)}
          {\exp\bigl(-\sum_{j}\theta_{ij}\,x_j\bigr)}
     \;=\;
     \exp\!\Bigl(2\,\sum_{j\in N(i)}\theta_{ij}\,x_j\Bigr).
$$

4. **Convert odds to probability**  

$$
     P(x_i=+1 \mid x_{-i})
     =
     \frac{1}{1 + \exp\bigl(-2\sum_{j}\theta_{ij}\,x_j\bigr)}
     =
     \sigma\!\Bigl(2\sum_{j\in N(i)}\theta_{ij}\,x_j\Bigr),
$$  
   
   where $\displaystyle\sigma(z)=\frac{1}{1+e^{-z}}$ is the logistic sigmoid.

---

 
Estimating the edge‐parameters $\{\theta_{ij}\}$ of an Ising MRF reduces to fitting, for each node $i$, a **sparse logistic regression** of $x_i$ on its neighbors $\{x_j: j\in N(i)\}$.
