# 介绍
Natural Language Processing and Chinese Computing (NLPCC) 大会 [1] 正在召开，今天是第一天，主要是 Advanced Disciplines Lectures (ADL) 的分享。NLPCC 会持续召开到 8 月 30 号，我也会持续更新每天的报告记录，供大家参考，由于时间紧迫等原因，一些内容只是给出提纲，具体内容以后有时间再详细阐述。  
今天有两个主题报告，即**神经机器翻译** (Neural Machine Translation, NMT) 的最新研究进展和 NLP 的**多任务学习** (Multi-task Learning, MTL)。

# NMT
今天上午来自微软亚洲研究院的副院长[刘铁岩](http://research.microsoft.com/users/tyliu)老师分享了 NMT 的最新研究进展 。该报告主要分为两大部分，第一部分概述了目前主流的 state-of-art 的 NMT 模型，第二部分介绍微软亚研的相关研究成果。

## 第一部分
总结说来，目前做 NMT 的 state-of-art 模型有三种：GNMT，ConvS2S 和 Transformer。
- GNMT

GNMT 是基于 RNNs 的模型，考虑了时间和空间两个因素。由于 RNNs 模型具有天然的序列特性，因此 GNMT 已经考虑了时间因素。为了加入空间因素，GNMT 在空间上堆砌了 8 层 RNNs。同时加入了 Residual connection 结构，并对数据和模型进行了并行训练。

- ConvS2S

ConvS2S 摒弃了 RNNs 太慢的缺点，只采用 CNNs 做编码和解码操作。比 GNMT 的结果稍微好一些。需要注意的是，CNNs 会丢失位置信息 (只考虑了窗口内的词序信息)，因此 ConvS2S 模型加入了 position embedding.
- Transformer

Transformer 摒弃了 RNNs 和 CNNs，只是基于 attention 机制做机器翻译，需要注意的是 attention 一点都没有考虑位置信息，因此加入了人工定义的位置函数。Transformer 的 paper 名字是 attention is all you need.
刘老师吐槽了 Transformer 模型两点：
- Paper 名字: Google 是互联网公司，因此必须聚焦到人们的关注点。
- Transformer 的 multi-head attention 类似于 CNNs 的 multi-channel filters, 因此也不是全部没有 CNNs 的影子。只是 Google 不承认而已。

总的来说，GNMT, ConvS2S 和 Transformer 都是遵循了 Encoder-Decoder 模型架构，因此遇到机器翻译类似问题时可以考虑一下这几个模型。

## 第二部分
这部分是刘老师研究组研究成果分享，主要包括 Dual learning,  Unsupervised NMT，推敲网络 (Deliberation net)，Non-autoregressive NMT 等内容。  
Dual learning 和 Unsupervised NMT 可以解决训练数据不充足的问题。Dual learning 是基于对称性提出的。分别包括 Dual supervised learning, Dual transfer learning, Dual inference, Model level 对偶等内容。Unsupervised NMT 构建了一个 latent space 完成 unsupervised 功能。  
当前 decoder 的 beam search 解码方式可能不是全局最优的，为了解决这个问题，从 AlphaGo 得到启发，设计 Value network。同时这个问题也可以利用推敲网络优化。  
同样对于 decoder 来说，decode 的时候是一个字一个字的解码出来的，速度慢，为了解决这个问题，提出了 Non-autoregressive NMT 的概念。  
最后，刘老师提出了几个观点：
- 对各种模型结构不感冒，由于 Universal approximation theorem 的存在，给定数据和任意深度模型，都能完成目标，因此刘老师觉得设计模型结构并各种拼机器调参的方式完全没有意义。
- Learning to teach。刘老师总结的机器学习三大件，即数据，模型空间和损失函数。与 Learning to learn (给定数据和模型空间，自己去学习如何优化) 不同的是，Learning to teach 使用另外一个模型 (i.e., 老师) 指导待训练模型 (i.e., 学生)，让二者共同去训练，达到 “因材施教，教学相长” 的目的。

注：刘老师会在 9 月或者 10 月出版新书 **《Distributed Machine Learning》**，主要讲述如何并行化训练机器学习模型。

# MTL
下午来自复旦大学的[邱锡鹏](http://nlp.fudan.edu.cn/xpqiu/)老师作了关于 Multi-task Learning 的报告。首先邱老师分享了深度学习在 NLP 中应用的基本概念，包括分布式表示等。然后介绍了 MTL 的概念，优势和几种模式。
## MTL 的概念是什么？
给定多个任务 (比如文本分类和 POS tagging)和各自的训练数据，MTL 能同时训练多个任务，并且比单独训练任务的结果还好。
## MTL 的优势在哪里？
- 隐式的数据增强
- 更好地表示学习
- 正则化
- 窃听 (Eavesdropping)
## MTL 有哪几种模式？
- 硬共享模式
- 软共享模式
- 共享私有模式
- 多级共享模式

目前基本上所有问题都可以归结为问答系统问题，比如，对于文本分类问题，归结为问答系统问题就是：这个文本属于哪一类？因此目前有几个平台是做这样的事情的，即
- DecaNLP [3]
- GLUE [4]

注：邱老师会在 9 月或者 10 月发布 FudanNLP 的升级版本 **FastNLP**。
