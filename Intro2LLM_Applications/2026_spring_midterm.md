# Intro to LLM Applications Midterm Examination

**Duration:** 70 minutes  
**Total Marks:** 100  
**Instructions:** All short answer questions should be answered briefly. Results without proper explanations may not receive full credit.

---

## Question 1: Basic Machine Learning [20 marks]

(a) Contrast Stochastic Gradient Descent (SGD) with Batch Gradient Descent (GD), including their main differences and the advantages of SGD. [10 marks]

(b) Explain the role of momentum in optimization, and why it helps optimization. [10 marks]

---

## Question 2: Moment Generating Functions [15 marks]

(a) Derive the moment generating function $M_X(t)$ for $X \sim \text{Bernoulli}(p)$. [5 marks]

(b) Prove that for independent random variables $X$ and $Y$, the MGF of $Z = X + Y$ satisfies $M_Z(t) = M_X(t) \cdot M_Y(t)$. [5 marks]

(c) Using (a) and (b), derive the MGF of $Y \sim \text{Binomial}(n, p)$. [5 marks]

---

## Question 3: Maximum Likelihood Estimation [20 marks]

(a) For $X_1, \ldots, X_n \stackrel{\text{i.i.d.}}{\sim} \text{Uniform}(0, a)$, prove that $\hat{a}_{\text{MLE}} = \max(X_1, \ldots, X_n)$. [5 marks]

(b) Compute the bias of $\hat{a}_{\text{MLE}}$. [7 marks]

(c) Compute the mean squared error of $\hat{a}_{\text{MLE}}$. [8 marks]

---

## Question 4: N-gram Language Modeling [30 marks]

Consider the corpus with sentence boundary tokens:

```text
<s> I like maths <e>
<s> I like physics <e>
<s> You like physics <e>
```

(a) Write down the maximum log-likelihood objective for the bigram model. [6 marks]

(b) Calculate all distinct bigram probabilities appearing in the corpus. [8 marks]

(c) Describe how to estimate trigram probabilities (explicit calculation is not needed), and determine whether trigram MLL achieves higher objective than bigram MLL and explain why or why not. [8 marks]

(d) Calculate $P(\text{You like maths})$ under the trigram model. [4 marks]

(e) Explain why the result of (d) is not desired in language models and propose a technique to address it. [4 marks]

---

## Question 5: Multi-layer Perceptrons [15 marks]
Consider a MLP with $\sigma(z) = \mathbb{I}[z > 0]$ activation, three input channels and one output channel. 

(a) Prove that a single-layer perceptron can represent the 3-input majority function $\text{MAJ}(x_1, x_2, x_3) = \mathbb{I}[x_1 + x_2 + x_3 \geq 2]$. You need to provide explicit weights and verify your results on each possible input. [5 marks]

(b) Prove that a two-layer perceptron architecture can represent $\text{XOR}_3(x_1, x_2, x_3) = x_1 \oplus x_2 \oplus x_3$. [10 marks]

You need to provide explicit weights and verify the results on each possible input.

---
