# Part 1

## Context-free Grammar

Motivation: represent a language by a set of relatively simple rules.

Given $G$ as a CFG. The language of $G$, denoted by $L(G)$, is the set of strings derivable by $G$ from the start symbol.

Thm: every regular language is context-free. 

$S\to aSb|\epsilon$ can't be expressed by a regular expression.

$L=\{a^nb^nc^n|n>0\}$ is not context-free.

A CFG is in CNF if it is $\epsilon$-free and if in addition Chomsky normal form each production is either of the form $A\to BC$ or $A\to a$.

Thm: every context-free language can be converted into a CNF.

Parsing: given a CFG $G$, syntactic parsing refers to mapping from a sentence to its parse tree. 

CKY parsing: dynamic programming

Limitation: Ambiguity -> Probabilistic CFG, learn with a corpus where each sentence is associated with a parse tree (treebank).

Train neural model to assign a score $s(i,j,l)$ to each span-label pair. $s_{\text{best}}(i,j)=\max_{l} s(i,j,l)+\max_{i<k<j} s_{\text{best}}(i,k)+s_{\text{best}}(k,j)$.

Synchrnous CFG: generate pairs of related strings instead of single strings, use in machine translation.

## Latent semantic analysis

Term-document matrix: $A_{ij}$ is the number of times term $i$ appears in document $j$, sparse -> hope $W_{ij}\approx\max(lv(w_i)lv(d_j)^T,0)$ -> SVD

TF-IDF normalization:
$$
tf = \frac{\text{\# of times word i appears in doc j}}{\text{\# of words in doc j}}\\
idf = \log\left(\frac{\text{\# of docs + 1}}{\text{\# of docs containing word i + 1}}\right) + 1
$$

Pointwise mutual information: for word $w$ and context $c$, $PMI(w,c)=\frac{P(w,c)}{P(w)P(c)}$

## Hidden Markov Model

Motivation: model the joint distribution of observed and hidden variables. Hidden variables: pos tag; observed variables: words.

Following the topological order, we can generate the whole sequence given hidden-hidden transition probabiities $A$ and all hidden-emission probability $B$.

Joint probability: $P(O)=\sum_{Q}P(O,Q)$

Forward algorithm: $p(o_{:t},q_t=j)=p(o_t|q_t=j)\sum_i p(q_t=j|q_{t-1}=i)p(o_{:t-1},q_{t-1}=i)$ -> DP -> $p(o)=\sum_i \alpha_T(i)$

Backward algorithm: $p(o_{t+1:T}|q_t=i)=\sum_j p(o_{t+2:T}|q_{t+1}=j)p(o_{t+1}|q_{t+1}=j)p(q_{t+1}=j|q_t=i)$ -> DP

Hence $p(o,q_t=i)=p(o_{:t},q_t=i)p(o_{t+1:T}|q_t=i)$, $p(o,q_t=i,q_{t+1}=j)=p(o_{:t},q_t=i)p(o_{t+2:T}|q_{t+1}=j)p(o_{t+1}|q_{t+1}=j)p(q_{t+1}=j|q_t=i)$

Viterbi algorithm: given $q$, infer $o$; store $\max_{q_{:t-1}}p(o_{:t},q_{:t-1},q_t=j)$ and backtrack by
$$
\max_{q_{:t-1}}p(o_{:t},q_{:t-1},q_t=j)=\max_i\left(\max_{q_{:t-2}}p(o_{:t-1},q_{:t-2},q_{t-1}=i)\right)p(o_t|q_t=j)p(q_t=j|q_{t-1}=i)
$$

Supervised training: learn $A$ and $B$ from labeled data.

Unsupervised training: EM algorithm, maximize $\log P(O|\theta)=\log\sum_Q P(O,Q|\theta)=\sum_Q q(Q)\log P(O,Q|\theta)+KL(q(Q)||p(Q|O,\theta))+H(q(Q))$. Denote $q(Q)=p(Q|O,\theta_k)$, if $\theta_k$ is close to $\theta$, then $KL(q(Q)||p(Q|O,\theta))$ can be ignored.

Rewrte the formula above, $\sum_Q q(Q)\log P(O,Q|\theta)=\sum_Q p(Q|O,\theta_k)\log P(O,Q|\theta)=\sum_{t,i,j}p(q_{t-1}=i,q_t=j|O,\theta_k)\log p(q_t=j|q_{t-1}=i)+\sum_{t,j}p(q_t=j|O,\theta_k)\log p(o_t|q_t=j)$

## N-gram Language Model

Trigram $k$-smoothing: $P(w_t|w_{t-2}w_{t-1})=\frac{c(w_{t-2}w_{t-1}w_t)+k}{c(w_{t-2}w_{t-1})+k|V|}$

Linear interpolation: $P(w_t|w_{t-2}w_{t-1})=\lambda_1P(w_t|w_{t-2}w_{t-1})+\lambda_2P(w_t|w_{t-1})+\lambda_3P(w_t)$, $\lambda_1+\lambda_2+\lambda_3=1$, optimize $\lambda$ on dev set or tune using EM.

Backoff: if $c(w_{t-2}w_{t-1}w_t)=0$, use $\alpha(w_{t-2}w_{t-1})P(w_t|w_{t-1})$ instead.

## Word2Vec

Learn input embedding matrix $W$ and output embedding matrix $U$.

Skip-gram: learn context words given center word, $p_\theta(out|in)=softmax(U_{out}^TW_{in})$

CBOW: learn center word given context words, $p_\theta(in|out)=\frac{\exp(u_{x_t}\frac{1}{2s}\sum_j w_{t+j})}{Z}$

Negative sampling to approximate softmax

# Part 2

## NN LM

feed forward NN LM: embed($w_{i-2}$) + embed($w_{i-1}$) -> hidden layer -> linear + softmax

Class-based LM: cluster words into $\sqrt{V}$ clusters, decompose prediction into two steps

Limitation of FNNLM: encode very limited context

RNNLM: $h_t=\tanh(W_{hh}h_{t-1}+W_{xh}x_t+h_o)$, $o_t=softmax(W_{ho}h_t+b_o)$

BPTT: gradient exploding and vanishing ($W_{hh}$ is the bottleneck) -> gradient clipping for exploding

RNN: parallel across sentences, pad, truncate or mask to deal with variable sentence length -> Bucketing: group sentences with similar length to better utilize GPU

GRU: reference to the slides, $h_t=(1-z_t)\odot h_{t-1}+z_t\odot \tilde{h}_t$, avoid gradient vanishing

Extensive Architecture Search for LSTMs: basic LSTMs are quite good

Bi-directional RNN: for encoding, not for AR-LM. Two ways to get a sentence encoding from bi-RNN: add a special token to the input / max-pooling or mean-pooling of hidden states

## Seq2Seq

bi-RNN encoder + uni-RNN decoder for output: average encoder's hidden vectors for the input of the decoder RNN / use attention mechanism

Attention mechanism: for each encoder hidden state, compute alignment score $\hat{a}_i=(h_i^{\text{enc}})^T W_a h^{\text{dec}}$, then softmax to get $a_i$, pass $\sum_i a_i h_i^{\text{enc}}$ to the decoder

Beam search for decoding

BLEU: brevity penalty defined as $\min\{1,\exp(-\frac{r}{c})\}$, where $r$ is the reference length and $c$ is the predicted length. BLEU defined as brevity-penalty $\times\left(\prod_{i=1}^4 p_i\right)^{1/4}$, where $p_i$ is the precision of $i$-gram

Back translation: given $(X,Y)$ and a good amount of $Y$, train a model from $Y$ to $X$, then use this model to generate $X'$ from $Y$, train a model from $X'$ to $Y$. (use sampling and noise can improve performance)

FastText: feed-forward net for classification, average pretrain embedding of $n$-grams feature to form hidden variable -> linear -> softmax, performs close to RNNs and CNNs on simple tasks

CNN for text classification: easier to train

RNN build on parse trees, useful when high-quality trees are available

Tree LSTM

Benchmark: GLUE, SuperGLUE

ELMo (Embeddings from Language Models): multi-layer bi-LSTM, objective: predict next word in both directions, extract output-layer features from the model

Subword tokenization: BPE(Byte Pair Encoding): merge most frequent pair of characters

## BERT

self-supervised learning: masked language model / next sentence prediction (predict whether two sentences are consecutive)

ELECTRA: corrupts input by replacing some tokens using a small MLM, then train a discriminator to distinguish the original and corrupted input

Longformer: use slide window attention -> 2 heads using dilated attention, other heads using local attention, wider receptive field with same amount of computation

## Research Topic

Top-$k$ sampling: provide a quality-diversity trade-off

MLE problem: teacher forcing and exposure bias (error accumulation during generation) -> language GANs (not direct since discrete output)

Gumbel-softmax reparameterization: draw sample $z$ from a categorical distribution with $\pi$ by

$$
z=\text{one-hot}(\text{argmax}_i(g_i+\log\pi_i))
$$

where $g_i$ is i.i.d. Gumbel(0,1). Generate $y=\text{softmax}((g+\log\pi)/\tau)$, return equals $y_{\text{hard}}-y_{\text{soft}}.\text{detach}()+y_{\text{soft}}$. Generating process: $\arg\max_\theta\mathbb{E}_{y\sim p_\theta(y|x)}[R(x,y)]$, using policy gradient.

However, language GAN can't tune temprature $\tau$ for changing the trade-off between quality and diversity.

Next token prediction with MLE: $\arg\min_\theta\mathbb{E}_{W\sim P_D} -\log P_M(W)=\arg\min_\theta KL(P_D||P_M)$, $P_M$ will try to cover $P_D$.

Is exposure bias a problem? Consider feed a LM with 3 kinds of prefix: ground truth, generated by the model, and random. We find model can recover from errors

Popular sampling algorithm: top-$k$ sampling, nucleus (top-$p$) sampling, temperature sampling. Human evaluation shows they are almost same -> both satisfy order perserved, reduce entropy, slope perserved

We claim sampling algorithms that satisfy the above properties are at least as good as the three algorithms, e.g. Max-entropy sampling, ramdom top-$k$ sampling (one anomaly: random mask sampling)

The repetition problem for beam-search in open-ended generation. Tackling bad behaviors in the following ways: 
1. biased decoding $p_i=\frac{\exp(x_i/(T\cdot I(i\in g)))}{\sum_j \exp(x_j/(T\cdot I(j\in g)))}$, where $I(c)=\theta$ if $c$ is True else 1 
2. Unlikelihood training: $L=-\alpha\sum_{c\in C_{prev}}\log (1-p_\theta(c|x_{<t}))-\log p_\theta(x_t|x_{<t})$
3. MMI criterion: $\hat{T}=\arg\max_T\{\log p(T|S)-\log p(T)\}$, penalize uninformative response
4. Negative training: assign $y_{neg}$ for most frequent samples, $L=-\log p_\theta(y_{pos}|x_{pos})+\log p_\theta(y_{neg}|x_{neg})$

## Transformer

Pretrain encoder-decoder -> BART, T5 (text-to-text)

Decoder only: convenient and efficient

Rotary position embedding: $PE_{(pos,2i)}=\sin(pos/10000^{2i/d})$, $PE_{(pos,2i+1)}=\cos(pos/10000^{2i/d})$ for absolute PE. Motivation: want dot product between $m$ and $n$ be a function of $m-n$. -> $f_{\{q,k\}}(x_m,m)=R^d_{\Theta,m}W_{\{q,k\}}x_m$

Scaling Laws: clear patterns when increase model/data size (model size > data requirements > serial steps)

In context learning: more shot increase performance on SuperGLUE

Before GPT, few shot learning means adapt to a new task demonstrated with a few examples via gradient update (Meta-learning phase on a wide set of tasks)

MAML: for each task compute $\theta_i=\theta-\alpha\nabla_\theta L_{\tau_i}(f_\theta)$, then update $\theta=\theta-\beta\nabla_\theta L_{\tau_i}(f_{\theta_i})$

CoT: Let's think step by step.

CoT with self-consistency: sample multiple paths, then take majority vote -> ToT: prompt LLM propose multiple next steps, then judge which is more promising (by provide a value by LLM)

Bias in ICL: majority and recency bias -> use a linear transformation to correct the bias ($\hat{q}=\text{softmax}(W\hat{p}+b)$), give null as input, set $W=\text{diag}(\text{prediction}_{\text{null}}^{-1}),b=0$ for balancing the output for null (useful for few shot)

Rethinking ICL: replace label in few-shot demonstration with random labels, performance is still good

1. Models with more than one layer have a sudden improvement in in-context learning.
2. Induction attention head: heads increase the likelihood of $[B]$ given $[A][B]...[A]$ for repetition -> form suddenly for models with more than one layer
3. From the fact above, we can infer that ICL is in fact a repetition problem

Instruction tuning: FLAN (Finetuned Language Net), use a prompt to guide the model to generate the desired output, inference on unseen task

## RLHF

Advantage: train a good discriminator easier than a good generator, teach model "what not to say" by giving low reward

Pratical: label rank reponses eaiser than coming up with a better response, LLM can generate good sample when sample enough times

Trivial method: prompting, best-of-$N$ (choose the best response from $N$ samples using a reward model)

$$
\max_\theta\mathbb{E}_{y\sim p_\theta(y|x)}[r_\phi(x,y)]-\beta\text{KL}(\pi_\theta||\pi_{\text{ref}})=\max_\theta\mathbb{E}_{y\sim p_\theta(y|x)}[r_\phi(x,y)-\beta\log\frac{p_\theta(y|x)}{p_{\text{ref}}(y|x)}]
$$

regard $r_\phi(x,y)-\beta\log\frac{p_\theta(y|x)}{p_{\text{ref}}(y|x)}$ as reward, then use PPO. Regard a 6B model trained on human labels as gold label for synthetic comparison

PPO: $L_{\text{PPO}}=\mathbb{E}_{\tau\sim\pi_{\theta_{\text{old}}}}\left[\min\left(\frac{\pi_\theta(a_t|s_t)}{\pi_{\theta_{\text{old}}}(a_t|s_t)}A(a_t|s_t),\text{clip}(\frac{\pi_\theta(a_t|s_t)}{\pi_{\theta_{\text{old}}}(a_t|s_t)},1-\epsilon,1+\epsilon) A(s_t,a_t)\right)\right]$, where $A(s_t,a_t)$ is the advantage function. However, hard to tune hyperparameters

DPO: $L_{\text{DPO}}=\mathbb{E}_{(x,y_w,y_l)\sim D}\left[\log\sigma(\beta\log\frac{\pi_\theta(y_w|x)}{\pi_{\text{ref}}(y_w|x)}-\beta\frac{\pi_\theta(y_l|x)}{\pi_{\text{ref}}(y_l|x)})\right]$

RLAIF: use LLM provide feedback

Parameter-efficient tuning:
1. Adapter: add some adapter modules in each transformer layer $d_{\text{model}}\to m\to d_{\text{model}}$
2. BitFit: only train bias-term and task-specific classification layer
3. LoRA: no latency

Discrete prompt optimization: random initialize prompt, iteratively pick a position and find $V_{\text{cand}}=\text{top-k}_{w\in V}[w\cdot\nabla\log p(y|x_{\text{prompt}})]$

## Detection

GROVER: generate fake news, train GPT2-like news-generation LM. Transfer from model $M$ to $N$ is poor

GLTR: check probability of next token

DetectGPT: check local probability distribution around $x$ by apply a LM to add noise to text $\tilde{x}$, then compute $d(x,p_\theta,q)=\log p_\theta(x)-\mathbb{E}_{\tilde{x}\sim q(\tilde{x}|x)}[\log p_\theta(\tilde{x})]$

Rewrite a fraction or add a few typos can degrade DetectGPT

Fast-Detect GPT: see paper

Watermarked generation: at each time, pseudo-randomly partition(seeded by the previous token) the vocabulary into a green list and a red list, add small bias to the logits of green-list tokens

Threats: reverse-engineer (using $|V|^{1+h}$ tokens to get watermark), paraphrase

Semantic Watermark algorithm: map sentences to semantic embeddings(S-BERT), partition semantic space via LSH, sampling with rejection

Model stealing: use embedding model and distill

Watermark embedding against model stealing: inject $e_t$ by $e_p=\frac{(1-Q(S))e_o+Q(S)e_t}{||(1-Q(S))e_o+Q(S)e_t||}$, $Q(S)$ is the number of trigger tokens in $S$

Verification: check whether trigger tokens are closer to $e_t$.

If stealer know the watermark approach, stealer can do random permutation / orthogonal linear transformation ()

Membership inference attack: means determine whether a text is used to train a given model

Min-$K\%$ prob: take $K\%$ of the tokens with the lowest probability, if the average log likelihood is high, the text is likely in the pretraining data