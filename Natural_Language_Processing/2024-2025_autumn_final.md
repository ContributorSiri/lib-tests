# NLP 2024 Final

- **Date**: 2024.12.3, 19:20 - 21:50.
- **Score**: $100$.
- **No cheatsheet is allowed.**

## Problem 1 True or False Questions ($20$)

Write **T** or **F** to each question. If your answer is **F**, please provide a brief explanation.

1. $\{a^nb^nc^n:n\in \mathbb{N}\}$ is not context-free.
2. Consider a HMM model of length $4$, containing nodes $q_{1:4}$ and $o_{1:4}$. Then the probability distribution 
$$p(Q,O)=p(q_1)p(q_2|q_1)p(q_3|q_2)p(q_4|q_3)p(o_1|q_1)p(o_2|o_1)p(o_3|o_2)p(o_4|o_3).$$
3. An uni-gram model gives a probability distribution $P$ over text such that
$$P(\text{we study NLP at THU})=P(\text{NLP study THU at we}).$$
4. Consider a RNN model, the input state and the hidden state all have dimension $1$ (i.e. they are scalars). Assume we do not have any activation layer. The computation formula is $h_t=Wh_{t-1}+b$. If $W>1$, we can say RNN can suffer from gradient vanishing when the sentence length is large.
5. BERT-like Transformers can generate deep contextualized word embeddings, but they cannot be directly used to do autoregressive language
modelling.
6. When the sentence length becomes large, the forward process of a Transformer will be time-consuming because the computation time of an attention block grows linear with the sentence length.
7. Suppose there are a mixture of two Gaussians $p=0.5\mathcal{N}(-10,1)+0.5\mathcal{N}(10,1)$. We need to find a Gaussian $q=\mathcal{N}(\mu,\sigma)$ that minimizes KL-divergence $\text{KL}(q||p)$. Then we should have $\mu=0$.
8. In T5 task-specific finetuning, all tasks (including classification or regression) are converted to a text-to-text format. In this way, we do not need to change model architecture for most tasks.
9. Both top-$k$ sampling ($k<|V|$), top-$P$ sampling ($P<1$), and tempreture sampling ($T<1$) will reduce the entropy of the probability distribution.
10. One downside of LoRA is it will introduce latency during applications.

## Problem 2 Question Answering ($10$)

1. What is byte pair encoding (BPE)? What is its core step?
2. What is in-context learning (ICL)? How can it help GPT-3 to learn downstream tasks?
3. Why naive RNN will face gradient exploding or vanishing problem?
4. What is tempreture sampling method? What is its utility in language generation?
5. What is positional embedding (PE)? Why do Transformer need it?

## Problem 3 Plot ($10$)

1. Plot an illustration of an one-layer transformer with masked LM objective. You don't need to draw residual connection, layer norm, or word embedding. The example sentence can be `We love cats .`
2. Plot an illustration of a RNN-LM, that generates the sentence `<s> We study NLP at THU . </s>`. Again, you don't need to draw word embedding.

## Problem 4 Thought Problem ($15$)

Consider a turn-by-turn chat-bot setting. Why decoder-only LM is more convenient or efficient (for both training or application) than encoder-decoder LM?

You should provide exactly 2 aspects.

## Problem 5 ($10$)

HMMs define joint distributions over sequences of labels and observations. However, in many structured prediction applications, we are only interested in the conditional distribution of $2$ labels given observations, $p(y|x)$. Conditional random fields (CRFs) permit this distribution to be modeled directly, using the following parametric form
$$p(y|x;w)=\dfrac{\exp\left\{w^T\sum\limits_{i=1}^Lf(x_i,y_i,y_{i-1})\right\}}{Z(x;w)},$$
where $y\in \Omega^{L+1},x\in \Sigma^L$, $\Omega$ is the **finite** label set, $\Sigma$ is the **finite** token set, $Z$ is the normalizing coefficient, $w\in \mathbb{R}^d$ is parameter vector, and $f:\Sigma\times\Omega\times\Omega\to \mathbb{R}^d$ is a $d$-dimensional feature vector mapping.

1. Given training data $\mathcal{D}=\{x^{(t)},y^{(t)}\}_{t=1}^n$. Please write down the training objective $J$ of the model, using conditional log-likelihood. ($3$ pts)
2. Assume now we have a CRF model, and an input sequence $x$. We hope to find $\hat y$ that maximizes $p(\hat y|x;w)$. Design an algorithm to find the optimal $\hat y$ in $\text{poly}(L,|\Omega|)$ time, and analyze the time complexity of your algorithm. ($4$ pts)
3. Can you combine CRF with neural network to improve the expressiveness? ($3$ pts)

_NOTE._ The third sub-question is regarded as a wrong question and the points are automatically given.

## Problem 6 ($10$)

> **RECAP**: The formula of a RNN block is
> $$h_t=\sigma(W_hx_t+U_hh_{t-1}+b_h);$$
> The formula of a GRU block is
> $$z_t=\sigma(W_zx_t+U_zh_{t-1}+b_z),$$
> $$r_t=\sigma(W_rx_t+U_rh_{t-1}+b_r),$$
> $$\tilde h_t=\tanh(W_hx_t+U_h(r_t\odot h_{t-1})+b_h),$$
> $$h_t=z_t\odot h_{t-1}+(1-z_t)\odot \tilde h_{t}.$$

In this problem, assume all the variables above are scalars, and $\sigma(\cdot),\tanh(\cdot)$ are replaced by an indicator function $\mathbf{1}[\cdot >0]$. Assume the initial hidden state $h_0=0$.

1. We want to design a model that can **memorize** the first position of $x$. Formally, we are given a sequence $x_1,x_2,\cdots,x_L$ ($L\ge 1$), such that $x_i=0$ for all $i\ge 2$, and $x_1\in \{0,1\}$. We want to design a model (RNN or GRU) such that $h_i=x_1$ for all $1\le i\le L$.       
    (i) Find $W_h,U_h$ such that the RNN model with $b_h=0$ can do this task.     
    (ii) Find $W_z,U_z,W_h,U_h$ such that the GRU model with $W_r=U_r=b_r=b_z=b_h=0$ can do this task.

2. Now we want a model such that, for each position $i$, if $x_i=1$, $h_i=1-h_{i-1}$; if $x_i=0$, $h_i=h_{i-1}$.    
    (i) Prove that RNN cannot achieve this task.    
    (ii) Find $W_z,U_z,W_h,U_h,b_r$ such that the GRU model with $W_r=U_r=b_z=b_h=0$ can do this task.

## Problem 7 Code Completion ($15$)

```python
import torch
import torch.nn as nn

class LayerNorm(nn.Module):

    def __init__(self, features, eps=1e-6):
        self.gamma = nn.Parameter(torch.ones(features))
        self.beta = nn.Parameter(torch.zeros(features))
        self.eps = eps

    def forward(self, x):
        # x.shape = (batch_size, features, )
        # TODO: compute mean and std
        mean = ...
        std = ...

        # TODO: use mean and std to compute normalized vector
        normalized = ...

        # TODO: use normalized to compute output
        output = ...

        return output

```

1. Fill in the blanks. ($12$ pts)
2. Briefly explain why `self.gamma` and `self.beta` are initialized with fixed vector instead of randomly initialized. ($3$ pts)

## Problem 8 Proof Problem ($10$)

RLHF formulates the alignment during-training process as a bandit learning problem with reward signals. Let $\mathcal{X}$ denotes the prompt set, which has a prior distribution $\mathcal{D}_x$, and $\mathcal{Y}$ denotes the response set. Language models can thus be viewed as a policy $\pi:\mathcal{X}\to \Delta (\mathcal{Y})$, i.e., mapping each prompt to a probability distribution on $\mathcal{Y}$. RLHF assumes that there exists a reward oracle $r:\mathcal{X}\times\mathcal{Y}\to \mathbb{R}$, and aims to train a policy to generate a response $y\in \mathcal{Y}$ with a high reward $r(x,y)$ given a prompt $x$. 

In practice, people often already have a base model $\pi_{\text{ref}}$ before they conduct RLHF. The objective of RLHF is
$$\arg\max_{\pi} \mathbb{E}_{x\sim \mathcal{D}_x,y\sim \pi(\cdot|x)}[r(x,y)-\beta \text{KL}(\pi(\cdot |x)||\pi_{\text{ref}}(\cdot|x))],$$
where $\beta\in \mathbb{R}_+$ is a hyperparameter. Assume $\pi_{\text{ref}}(y|x)>0$ for all $(x,y)$.

Given a human preference dataset $\mathcal{D}=\{x^{(t)},y_w^{(t)},y_l^{(t)}\}_{t=1}^n$, the reward function $r$ can be learned via parameter $\phi$ using a negative log-likelihood loss
$$\mathcal{L}_r(\phi)=-\dfrac{1}{n}\sum\limits_{i=1}^n \log \sigma(r_\phi(x^{(i)},y_w^{(i)})-r_{\phi}(x^{(i)},y_l^{(i)})).$$

1. Given a reward function $r$, solve the optimal policy $\pi^\star$. Then, show how we can use this result to train $\pi$ directly without training $r_\phi$. ($5$ pts)

2. Suppose
$$J(\theta)=\mathbb{E}_{x\sim \mathcal{D}_x,y\sim \pi_\theta(\cdot|x)}[r(x,y)-\beta \text{KL}(\pi_\theta(\cdot |x)||\pi_{\text{ref}}(\cdot|x))].$$
Prove that
$$\nabla_\theta J(\theta)=\dfrac{1}{2\beta}\mathbb{E}_{x\sim \mathcal{D}_x,y\sim \pi_\theta(\cdot|x)}\left[-\nabla_\theta \left(r(x,y)-\beta \log \dfrac{\pi_\theta(y|x)}{\pi_{\text{ref}}(y|x)}\right)^2\right].$$
($5$ pts)