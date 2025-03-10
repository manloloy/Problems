# Proof of the Multivariate Normal PDF

## 1. Introduction

Let $X \in \mathbb{R}^n$ be a random vector with a multivariate normal distribution, denoted as

$$
X \sim \mathcal{N}(m, K),
$$

where:
- $m \in \mathbb{R}^n$ is the mean vector,
- $K \in \mathbb{R}^{n \times n}$ is the covariance matrix, which is symmetric and positive definite.

Our goal is to prove that the PDF of $X$ is given by

$$
f_X(x) = \frac{1}{(2\pi)^{n/2} \sqrt{\det(K)}}
\exp \left( -\frac{1}{2} (x - m)^T K^{-1} (x - m) \right).
$$

## 2. The Univariate Normal Case

Recall that for a univariate normal random variable $X \sim \mathcal{N}(\mu,\sigma^2)$, the PDF is

$$
f_X(x) = \frac{1}{\sqrt{2\pi\sigma^2}}
\exp \left( -\frac{(x-\mu)^2}{2\sigma^2} \right).
$$

This simple case will serve as the foundation for the multivariate generalization.

## 3. Independent Normal Variables

If $X = \begin{bmatrix} X_1 \\ X_2 \\ \vdots \\ X_n \end{bmatrix}$ is a vector of **independent** normal random variables with

$$
X_i \sim \mathcal{N}(\mu_i, \sigma_i^2),
$$

the joint PDF is the product of the individual densities:

$$
f_X(x) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi\sigma_i^2}} \exp \left( -\frac{(x_i-\mu_i)^2}{2\sigma_i^2} \right).
$$

Writing this in vector form, with a diagonal covariance matrix $K = \text{diag}(\sigma_1^2, \sigma_2^2, \dots, \sigma_n^2)
$, we have

$$
f_X(x) = \frac{1}{(2\pi)^{n/2} \sqrt{\det(K)}}
\exp \left( -\frac{1}{2} \sum_{i=1}^{n} \frac{(x_i-\mu_i)^2}{\sigma_i^2} \right).
$$

Notice that

$$
(x-m)^T K^{-1} (x-m) = \sum_{i=1}^{n} \frac{(x_i-\mu_i)^2}{\sigma_i^2},
$$

so the joint PDF becomes

$$
f_X(x) = \frac{1}{(2\pi)^{n/2} \sqrt{\det(K)}}
\exp \left( -\frac{1}{2} (x-m)^T K^{-1} (x-m) \right).
$$

This derivation holds when $K$ is diagonal (i.e., the $X_i$ are independent).

## 4. Whitening Transformation for the General Case

For a general multivariate normal vector $X \sim \mathcal{N}(m, K)$, the covariance matrix $K$ is not necessarily diagonal. 
However, since $K$ is symmetric and positive definite, it can be decomposed using its eigenvalue decomposition:

$$
K = Q \Lambda Q^T,
$$

where:
- $Q$ is an orthogonal matrix whose columns are the eigenvectors of $K$, i.e., $Q^T Q = I$,
- $\Lambda$ is a diagonal matrix with the eigenvalues $\lambda_1,\lambda_2,\dots,\lambda_n$ on the diagonal.

### 4.1 Define the Whitening Transformation

We define the whitened variable $Z$ as

$$
Z = \Lambda^{-1/2} Q^T (X-m).
$$

**Mean of $Z$:**

Since $\mathbb{E}[X] = m$, it follows that

$$
\mathbb{E}[Z] = \Lambda^{-1/2} Q^T (\mathbb{E}[X]-m) = 0.
$$

**Covariance of $Z$:**

The covariance is computed as

$$
\begin{aligned}
\text{Cov}(Z) &= \Lambda^{-1/2} Q^T \text{Cov}(X) Q \Lambda^{-1/2} \\
&= \Lambda^{-1/2} Q^T K Q \Lambda^{-1/2} \\
&= \Lambda^{-1/2} Q^T (Q \Lambda Q^T) Q \Lambda^{-1/2} \\
&= \Lambda^{-1/2} \Lambda \Lambda^{-1/2} \\
&= I.
\end{aligned}
$$

Thus, $Z \sim \mathcal{N}(0, I)$, meaning that $Z$ is a standard multivariate normal vector with **independent** components.

### 4.2 The PDF of $Z$

Since the components of $Z$ are independent standard normals, its joint PDF is

$$
f_Z(z) = \frac{1}{(2\pi)^{n/2}} \exp \left( -\frac{1}{2} z^T z \right).
$$

## 5. Change of Variables: From $Z$ to $X$

Recall that

$$
Z = \Lambda^{-1/2} Q^T (X-m).
$$

This linear transformation can be inverted to express $X$ in terms of $Z$:

$$
X = Q \Lambda^{1/2} Z + m.
$$

### 5.1 Jacobian of the Transformation

The transformation $X = Q \Lambda^{1/2} Z + m$ is linear, and its Jacobian determinant is given by the absolute value of the determinant of the transformation matrix:

$$
\det(Q \Lambda^{1/2}) = \det(Q) \det(\Lambda^{1/2}).
$$

Since $Q$ is an orthogonal matrix, $\det(Q) = \pm 1$ and we have

$$
|\det(Q \Lambda^{1/2})| = |\det(\Lambda^{1/2})| = \sqrt{\det(\Lambda)} = \sqrt{\det(K)}.
$$

### 5.2 Applying the Change of Variables Formula

The change of variables formula for densities tells us that

$$
f_X(x) = f_Z(z) \left| \det \left( \frac{\partial z}{\partial x} \right) \right|,
$$

where the Jacobian $\left| \det \left( \frac{\partial z}{\partial x} \right) \right|$ is the reciprocal of the Jacobian for the transformation from $Z$ to $X$, i.e.,

$$
\left| \det \left( \frac{\partial z}{\partial x} \right) \right| = \frac{1}{\sqrt{\det(K)}}.
$$

Thus, substituting $z = \Lambda^{-1/2} Q^T (x-m)$ into the PDF of $Z$, we have

$$
\begin{aligned}
f_X(x) &= f_Z\left(\Lambda^{-1/2} Q^T (x-m)\right) \frac{1}{\sqrt{\det(K)}} \\
&= \frac{1}{(2\pi)^{n/2}} \exp \left( -\frac{1}{2} (\Lambda^{-1/2} Q^T (x-m))^T (\Lambda^{-1/2} Q^T (x-m)) \right)
\frac{1}{\sqrt{\det(K)}}.
\end{aligned}
$$

Notice that

$$
(\Lambda^{-1/2} Q^T (x-m))^T (\Lambda^{-1/2} Q^T (x-m)) = (x-m)^T Q \Lambda^{-1} Q^T (x-m).
$$

Since $K^{-1} = Q \Lambda^{-1} Q^T$, the above expression simplifies to

$$
(x-m)^T K^{-1} (x-m).
$$

Therefore, the PDF for $X$ becomes

$$
f_X(x) = \frac{1}{(2\pi)^{n/2} \sqrt{\det(K)}}
\exp \left( -\frac{1}{2} (x-m)^T K^{-1} (x-m) \right).
$$



