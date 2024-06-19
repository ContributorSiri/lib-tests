# DL FINAL
# Total points: 88 points
# Total time: 120 min

# 1. T/F Questions (30*1 pt=30pts, wrong answer will lead to -1pt)
1. This course has 3 TAs
2. In high dimension(e.g.1000), dict embedding is better than Gumbel softmax.
3. Skip connection is a common technique in neural network design, e.g. ResNet, DenseNet, Transformers.
4. Flamingo, gpt-4v, llava are LLMs that support interleaved images.
5. There's no safety issue to use generative models as the things they generated are fake.
6. In normalizing flow, the term log p($z_0$) can be ignored in training since it is a constant.
7. AF has fast training speed and low inference speed, in contrast, IAF has fast inference speed and high traing speed.
8. In GAN training, we should first train the discriminator to make it converge, then train the generator.
9. Intuitively, methods like Adam, ADaGrad are making the learning rate different and disentangled in different dimension.
10. Intuitively, large $\beta$ in $\beta-VAE$ make the latent space disentangled. 
11. Since we need bijection in normalizing flows, we can't use ReLU as activation function.
12. Although Nestrov Momentum have no convergence gurantee, it's commonly used in real training.
13. When training a CNN with batchnorm, it's equivalent to use batchsize 32 for one step and use batchsize 1 for 32 steps while accumulating the gradient.
14. SGD and GD have equal mean and variance in training.
15. In evaluation, batchnorm normalizes the input by the mean and variance of a batch.
16. LoRA makes it possible to do fine-tuning with limited GPU memory.
17. When batchsize is 1, batchnorm and layernorm are equivalent.
18. The likelihood is tractable in both normalizing flow and diffusion models.
19. When doing inpainting with VAE, we can just randomly mask out pixels and do generation.
20. EBM is hard to scale-up because the restriction of the model structure.
21. Gibbs Sampling is a special case of the MH algorithm, where the acceptance rate is always 1.
22. We want to fit a multimodal distribution by normal distribution and using KL loss function, but this results in collapsing to one mode. Change the loss function to JSD can fix this problem.

(I can only remember this much... QWQ)
# 2. Short Response Questions(2pts+(4+2)pts+2pts=10pts)

1. After training a VQ-VAE, can we sample the latent $z$ from a uniform distribution and do generation? If not, what should we do?

2. 
(1) Suppose we have a dataset with labels $\{x_i,y_i\}$, show how can we use these data to train a conditioned VAE and GAN.

(2) Suppose we have another dataset without labels, show the training process now for VAE and GAN using both the labels and unlabeled data.

3. Suppose you trained a LLM and put it weight on the internet. Somebody just downloaded it and do small modification, saying it's his model. How can you show the plagiarization? (Hint: small modification means adding small Guassian to the weights, or do neuron permutation that don't affect the result. We can assume that he didn't do any training on the model.)

# 3. Back Propagation of Attention (2pts+4pts+3pts=9pts)

Suppose $x_i(1\le i \le n)$ are inputs of d-dimension and the q-k-v vectors are calculated by $q_i = W_Q x_i$, $k_i = W_K x_i$, $v_i = W_V x_i$. The attention weight is $\alpha_{ij}=\frac{\exp(q_i^Tk_j)}{\sum_t{q_i^Tk_t}}$, and $y_j=\sum \alpha_{ij} v_j$. Let $L$ be a scalar loss function.

1. Compute $\frac {\partial L}{\partial v_i}$ and $\frac {\partial L}{\partial \alpha_{ij}}$, given $\frac {\partial L}{\partial y_j}$
1. Compute $\frac {\partial L}{\partial q_i}$ and $\frac {\partial L}{\partial k_i}$, given $\frac {\partial L}{\partial \alpha_{ij}}$
1. Compute $\frac {\partial L}{\partial W_Q}$, $\frac {\partial L}{\partial W_V}$ and $\frac {\partial L}{\partial W_K}$, given $\frac {\partial L}{\partial q_i},\frac {\partial L}{\partial k_i},\frac {\partial L}{\partial v_i}$

# 4. The State-Space Model(2pts+2pts+2pts+3pts=9pts)

Let a state-space model defined as $h_t=Ah_{t-1}+Bx_t, y_t=Ch_t$, where $x_t$ are **scalar** inputs, and $B$ be $d\times 1$ matrix, $A$ is a $d\times d$ matrix, $C$ is a $1\times d$ matrix. For simplicity $h_{-1}$=**0**.

1. Compute $y_T$ respect to $A,B,C,\{x_t\}$
2. To reduce to computational complexity to calculate the power of $A$, we want a new parameter $h_t=Dh_{t-1}+\tilde{B}x_t, y_t=\tilde{C}h_t$ where $D$ is a diag. matrix. If $A$ can be diagnolized as $V^{-1}DV$, show that there exist $\tilde{B},\tilde{C}$ such that the new model is equivalent to the previous one.
3. Show that this model can do the copy task: make $y_{t+k} = x_t$, where $k$ is small compared to $d$,(for simplicity, let k=3). structure and each update should remain linear time.
4. Show that this model can do the restrict copy task: The input sequence is $(x_0,x_1,x_2,x_3,x_4,4,...,4,x_T=5,x_{T+1}=5,x_{T+2}=5,x_{T+3}=5,x_{T+4}=5)$. $T$ is unknown to the model. The task is to make $ y_{T+i}=x_i(i=0,1,2,3,4) $ Show the design of the model, you can do small modification, but should remain the structure and each update should remain linear time.

# 5. Mutual Information and VAE/GAN (3pts+1pts+2pts+2pts+2pts=10pts)

The mutual information is defined as
$$I(X,Z)=\sum_{x,z} p(X=x,Z=z)\frac{\log p(X=x,Z=z)}{\log [p(X=x)p(Z=z)]}$$
(It's just the definition on the exam paper, but later it will use the mutual information of continuious case.)

1. Consider a VAE, where $p_{data}$ is the data distribution and $z$ is the latent variable. Let $E(z|x)$ be the encoder distribution. Prove: If $x \sim p_{data}$, $z \sim E(z|x)$, then $$I(X,Z)\le \mathbb{E}_{x\sim p_{data}} KL(E(z|x)||R(z))$$, where $R$ denote the standard normal distribution.

2. Suppose we are doing Lagrange form on training. Deduce the training objective. (comment: I don't fully understand this question, so it may be wrong)

3. Consider a GAN, prove that the optimal discriminator will output possiblity $D_{\phi}^*(x) = \frac{p_{data}(x)}{p_{data}(x)+p_{\theta}(x)}$.

4. Prove that when the discriminator is too strong, the generator will face the issue of gradient vanishing. You can assume that $D_{\phi}(x)=\sigma(D_{\phi}'(x))$, where $\sigma$ is the sigmoid function, and $D_{\phi}'(x)$ << 0.
The generator loss is $\mathbb{E}_{z\sim N(0,1)} \log D_{\phi}(G_{\theta}(z))$

5. To deal with the issue above, we want to make the discriminator don't achieve 100% accuracy(say 70%). Use mutual information to modify the training objective, and explain your loss function and training procedure.

# 6.Discrete Diffusion(2pts+2pts+2pts+4pts=10pts)

Consider a diffusion model on discrete space $\{1,2,...,K\}$, at each time step, the forward process can be defined as a matrix $Q_t$, where $q(x_{t}|x_{t-1}) = Cat(x_t; x_{t-1}Q_t)$, here $x_0$ is represented by a one-hot vector.

1. Calculate $q(x_T|x_0)$
2. Calculate $q(x_{T-1}|x_T,x_0)$
3. Design a set of $Q_i$ that makes the input more and more noisy (e.g. $\mathcal{H}(q(x_0))<\mathcal{H}(q(x_1|x_0))<...<\mathcal{H}(q(x_T|x_0))$), and calculate $q(x_T|x_0)$ correspond to your construction.
4. Briefly discuss how this model can be used to train on sentences with small length. You should show the training procedure and the loss function.

# 7."Fill in the middle"(2pts+2pts+2pts+2pts+2pts=10pts)

Suppose you have a pretrained BERT model, and say the probability distribution of it is $p^{BERT}$. You are given a sentence with middle part missing, say $x_1...x_l???x_r...x_n$ and you want to reconstruct it.

1. The vanilla approach is just set all the middle words to be the mask token and sample from the model. However, this might be problematic. Explain why and show a failure case.

2. You want to do Metropolis-Hasting Algorithm. Design a proposal distribution, and show the process of using this alogrithm to do the filling task.

3. Calculate the acceptance rate of your algorithm, your answer should be as simple as possible.

4. Can you think of other approaches to do this task? Show the method together with the training procedure.

5. If the length of the missing part is unknown, can the above approaches still work? If yes, explain how it can work; if not, show how to modify to make it work.

