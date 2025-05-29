## Sparse Logistic Regression as Conditional Inference in an Ising MRF

Recall an Ising‐type Markov random field over binary variables \(x_i\in\{-1,+1\}\) has joint distribution
\[
P(x) \;=\; \frac{1}{Z}\,\exp\!\Bigl(\sum_{(i,j)\in E}\theta_{ij}\,x_i\,x_j\Bigr).
\]
Because it factors over edges, the **conditional** distribution of a single node given *all the others* is

\[
P\bigl(x_i=1 \mid x_{-i}\bigr)
\;=\;
\frac{P(x_i=1,x_{-i})}{P(x_i=1,x_{-i})+P(x_i=-1,x_{-i})}.
\]

### Proof: the Gibbs law becomes a logistic sigmoid

1.  **Write out the two numerators**  
    \[
    P(x_i=+1,x_{-i})
    \;\propto\;
    \exp\!\Bigl(\sum_{j\in N(i)}\theta_{ij}\,(+1)\,x_j \;+\;\sum_{(u,v)\neq(i,j)}\theta_{uv}\,x_u\,x_v\Bigr),
    \]
    \[
    P(x_i=-1,x_{-i})
    \;\propto\;
    \exp\!\Bigl(\sum_{j\in N(i)}\theta_{ij}\,(-1)\,x_j \;+\;\sum_{(u,v)\neq(i,j)}\theta_{uv}\,x_u\,x_v\Bigr).
    \]
    All terms not involving \(x_i\) cancel in the ratio.

2.  **Form the conditional ratio**  
    \[
    \frac{P(x_i=+1\mid x_{-i})}{P(x_i=-1\mid x_{-i})}
    \;=\;
    \frac{\exp\bigl(\sum_{j}\theta_{ij}\,x_j\bigr)}
         {\exp\bigl(-\sum_{j}\theta_{ij}\,x_j\bigr)}
    \;=\;
    \exp\!\Bigl(2\sum_{j\in N(i)}\theta_{ij}\,x_j\Bigr).
    \]

3.  **Convert to a sigmoid**  
    \[
    P(x_i=+1 \mid x_{-i})
    \;=\;
    \frac{1}{1 + \exp\!\bigl(-2\sum_{j}\theta_{ij}\,x_j\bigr)}
    \;=\;
    \sigma\!\Bigl(2\sum_{j\in N(i)}\theta_{ij}\,x_j\Bigr),
    \]
    where \(\displaystyle\sigma(z)=\frac{1}{1+e^{-z}}\) is the logistic sigmoid.

---

Hence, **learning** the \(\theta_{ij}\) in an Ising MRF reduces to \(n\) separate **sparse logistic‐regression** problems, one per node, with the neighbor‐states \(x_j\) as features and \(x_i\) as the binary label.
