# Exponential Family Representations

A probability distribution belongs to the **exponential family** if it can be written in the form:

$$
p(x \mid \eta) = h(x) \exp \left( \eta^T T(x) - A(\eta) \right)
$$

Taking the logarithm of both sides:

$$
\log p(x \mid \eta) = \log h(x) + \eta^T T(x) - A(\eta)
$$

where:
- $\eta$ is the **natural parameter**,
- $T(x)$ is the **sufficient statistic**,
- $A(\eta)$ is the **log-partition function** (ensures normalization),
- $h(x)$ is the **base measure**.

Below, we derive the exponential family representation for the **Bernoulli**, **Poisson**, and **Gaussian** distributions.

---

## 1. Bernoulli Distribution

The Bernoulli distribution is:

$$
p(x \mid p) = p^x (1 - p)^{1-x}, \quad x \in \{0,1\}
$$

### **Step 1: Take the Log**
Taking the logarithm,

$$
\log p(x \mid p) = x \log p + (1 - x) \log (1 - p)
$$

Expanding the second term,

$$
\log p(x \mid p) = x \log p + \log (1 - p) - x \log (1 - p)
$$

$$
= x \log \frac{p}{1 - p} + \log (1 - p)
$$

### **Step 2: Identify Exponential Family Components**
Comparing with the log form:

$$
\log p(x \mid \eta) = \eta T(x) - A(\eta) + \log h(x)
$$

we recognize:
- **Natural Parameter:** $\eta = \log \frac{p}{1 - p}$ (log-odds)
- **Sufficient Statistic:** $T(x) = x$
- **Base Measure:** $h(x) = 1$
- **Log-Partition Function:** 

$$
A(\eta) = \log(1 + e^\eta)
$$

### **Final Form**
$$
p(x \mid \eta) = \exp \left( x\eta - \log(1 + e^\eta) \right)
$$

---

## 2. Poisson Distribution

The Poisson distribution is:

$$
p(x \mid \lambda) = \frac{\lambda^x e^{-\lambda}}{x!}, \quad x \in \mathbb{N}
$$

### **Step 1: Take the Log**
Taking the logarithm,

$$
\log p(x \mid \lambda) = x \log \lambda - \lambda - \log x!
$$

### **Step 2: Identify Exponential Family Components**
Comparing with the log form:

$$
\log p(x \mid \eta) = \eta T(x) - A(\eta) + \log h(x)
$$

we recognize:
- **Natural Parameter:** $\eta = \log \lambda$
- **Sufficient Statistic:** $T(x) = x$
- **Base Measure:** $h(x) = \frac{1}{x!}$
- **Log-Partition Function:** 

$$
A(\eta) = e^\eta
$$

### **Final Form**
$$
p(x \mid \eta) = \frac{1}{x!} \exp \left( x\eta - e^\eta \right)
$$

---

## 3. Gaussian Distribution

For a Gaussian $\mathcal{N}(\mu, \sigma^2)$, the density function is:

$$
p(x \mid \mu, \sigma^2) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp \left( -\frac{(x - \mu)^2}{2\sigma^2} \right)
$$

### **Step 1: Expand the Exponent**
Rewriting the quadratic term,

$$
(x - \mu)^2 = x^2 - 2\mu x + \mu^2
$$

$$
p(x \mid \mu, \sigma^2) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp \left( -\frac{x^2}{2\sigma^2} + \frac{2\mu x}{2\sigma^2} - \frac{\mu^2}{2\sigma^2} \right)
$$

Taking the logarithm,

$$
\log p(x \mid \mu, \sigma^2) = -\frac{x^2}{2\sigma^2} + \frac{\mu x}{\sigma^2} - \frac{\mu^2}{2\sigma^2} - \frac{1}{2} \log (2\pi \sigma^2)
$$

### **Step 2: Identify Exponential Family Components**
Comparing with the log form:

$$
\log p(x \mid \eta) = \eta^T T(x) - A(\eta) + \log h(x)
$$

we recognize:
- **Natural Parameters:**
  - $\eta_1 = \frac{\mu}{\sigma^2}$
  - $\eta_2 = -\frac{1}{2\sigma^2}$
- **Sufficient Statistics:** $T(x) = (x, x^2)$
- **Base Measure:** $h(x) = 1$
- **Log-Partition Function:**

$$
A(\eta_1, \eta_2) = -\frac{\eta_1^2}{4\eta_2} + \frac{1}{2} \log \left(-\frac{\pi}{\eta_2} \right)
$$

### **Final Form**
$$
p(x \mid \eta) = \exp \left( \eta_1 x + \eta_2 x^2 - A(\eta_1, \eta_2) \right)
$$

---

## **Conclusion**
For each distribution, we derived:

1. **Bernoulli**:
   - $\eta = \log \frac{p}{1 - p}$
   - $A(\eta) = \log(1 + e^\eta)$

2. **Poisson**:
   - $\eta = \log \lambda$
   - $A(\eta) = e^\eta$

3. **Gaussian**:
   - $\eta_1 = \frac{\mu}{\sigma^2}, \quad \eta_2 = -\frac{1}{2\sigma^2}$
   - $A(\eta_1, \eta_2) = -\frac{\eta_1^2}{4\eta_2} + \frac{1}{2} \log \left(-\frac{\pi}{\eta_2} \right)$

This demonstrates how the exponential family formulation provides a unified way to express these distributions using natural parameters and sufficient statistics.
