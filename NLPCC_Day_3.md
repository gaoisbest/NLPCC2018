# 介绍

今天 ADL 也是有两个主题报告的，包括上午的搜索场景下的**用户行为建模** (Search User Behavior Modeling) 和下午的知识图谱的语义：从理论到实战 (Semantics of Knowledge Graph: From Science to Pratice).  
下午同时有腾讯 **Lingo Lab** Workshop 分享，因此舍弃了知识图谱方面的报告。

# 用户行为建模
今天上午来自清华大学的[刘奕群](http://www.tsinghua.edu.cn/publish/cs/4616/2013/20131122152918302181212/20131122152918302181212_.html)老师给大家分享了搜索场景下的用户行为建模 (Search User Behavior Modeling).  
昨天聂老师分享的 Neural IR，主要是从模型的角度考虑的，这个模型是基于纯文本的模型，没有考虑其他因素，比如用户行为等。  
在搜索场景中，搜索的目标是为了让用户点击，因此如何考虑用户行为因素加大用户点击率是搜索的目标，也是张老师报告的主要内容。  
张老师还列举了 Facebook 前一段时间分析用户点赞数据刻画用户性格的例子，对用户行为建模影响政治选举等例子阐述社交网络中的用户行为建模作用。  
报告分为两个部分，即**同质化环境** (Homogeneous environment) 下的用户行为建模和**异质化环境** (Heterogeneous environment) 下的用户行为建模。

## 第一部分
同质化环境，指的是搜索结果中只有文本的情况。
首先基于搜索行为 (Querying Behavior) 数据，在搜索文本长度，使用设备 (如手机，平板，台式电脑) 等不同方面分析了数据并图形展示，发现查询频次和查询长度是服从幂律分布 (Power low distribution) 的。  
在点击/检验行为 (Clicking/Examination Behavior) 部分中，提出了位置偏差 (Position bias), 级联假设 (Cascade assumption), 回访行为 (Revisiting behavior), 从 skimming (略读) 到 reading (精读) 的 two-stage examination.  
在构建点击模型 (Click Models) 部分中，介绍了 Cascade model, Dependent click model (DCM) 和 User Browsing Model (UBM) 模型. 其中，UBM是应用最广的模型。

## 第二部分
异质化环境，指的是搜索结果中包含文本，图像等的情况。这部分刘老师分享了最新的工作，基于图像搜索结果的用户行为分析。Google 的图像搜索是按行排列的，Bing 的图像搜索是按列排列的，不管怎样，二者都是网格展示图像搜索结果的。研究结果表明，第一行第二列的图像是最显著的 (Saliency)，也就是用户会最先看这个位置的图片。


# 腾讯 Lingo Lab Workshop
分为 5 个主题，包括机器翻译和对话系统等，即 
- Tencent Machine Translation Systems: Introduction and Application, by Mingxuan Wang
- Knowledge Engine is Everywhere in Tencent QQ Browser, by Yancheng He
- End-to-end Task-oriented Dialog Systems, by Wanxiang Che
- Joint Models for Goal-Driven Dialog, by Xiaojie Wang
- Toward Diverse Text Generation with Inverse Reinforcement Learning, by Xipeng Qiu
下面一一介绍不同的主题。

## 主题一: Tencent Machine Translation Systems: Introduction and Application
Wang 博士首先概述了 ConvS2S 和 Transformer 等模型，然后简单介绍了他们自己发表在 COLING 2018 的 Paper: Neural Machine Translation with Decoding-History Enhanced Attention [3]. 着重介绍了工业界实践中遇到的一些问题：
- 加入知识
- 不流畅度检测 (Disfluency Detection)
- OCR

### 问题1: 加入知识
这部分考虑了三个问题，即：
- Vocabulary Constrained
  - Limited Vocabulary
    - 限制只在某些词中 decode. (Jean, 2018)
  - Lexically Constrained Decoding
  - Copy Network
- Incorporate Word Reordering
- Data augmentation
  - Language model
  - Back Translation
  - Dual learning
  - Joint Training

## 问题 3: OCR
这里指的是把图片中的文字抠出来，翻译后再粘回去。遇到的问题是先把小块字识别出来，组合在一起整块翻译。在扣字的时候需要进行背景还原等操作。
机器翻译在腾讯中的落地应用是[翻译君]( fanyi.qq.com.

## 主题二: Knowledge Engine is Everywhere in Tencent QQ Browser
这个主题分享主要是业务介绍。介绍了知识图谱在推荐系统和搜索中的应用场景。
在推荐系统中，He 举了两个例子，即王宝强离婚和韩信的例子。由王宝强链接到离婚事件，进而可以推荐李小璐出轨等其他事件；如果用户喜欢韩信，就可以根据韩信在知识图谱的关联边，给用户推荐关联的信息。
最后，He 推荐了他们组在文本匹配方面的新 Paper：MIX: Multi-Channel Information Crossing for Text Matching，并进行了总结：NLP 算法模型红利正在消失，结合知识的 NLP 会更好！

## 主题三：End-to-end Task-oriented Dialog Systems
Che 老师的报告首先介绍了 Task-oriented 对话系统的 Pipeline 模型，即 NLU-DM-NLG, 其中 NLU 部分包括 Domain identification, User intent detection 和 Slot filling. DM 部分包括 Dialog state tracking 和 Dialog policy, 其中可能会调用 API 或者查询数据库。DM 模型也演变到使用 Reinforcement Learning 去做。  
然后介绍了 End-to-end 方式的几个模型，如：
- End-to-end Trainable System (Wen et al., 2016)
- Latent Intention Dialogue Models (Wen et al., 2017)
- KB-Info Bots (Dhingra et al., 2017)
- End-to-End with Belief Tracking (Liu et al., 2017)
- Sequicity (Lei et al., 2018)
- Mem2Seq(Madotto et al., 2018)

最后 Che 老师介绍了自己最近的工作: Sequence to sequence for Dialogue system with  dialogue state representation. 大体思路是用向量表示所有可能的值，一个向量代表数据库中的一个 column, 具体参考 [pdf](https://github.com/gaoisbest/NLPCC2018/blob/master/Day3_Tencent_workshop_chewangxiang.pdf).

## 主题四：Joint Models for Goal-Driven Dialog
Wang 老师说这个主题与主题三有些“撞车”，也是 Task-oriented 对话系统，主要是联合学习方面的知识。比如将 Pipeline 的 NLU 和 DM 一块联合训练，或者 Pipeline 全部组建联合训练等。这个报告没仔细听。

## 主题五：Toward Diverse Text Generation with Inverse Reinforcement Learning
Qiu 老师首先总结 NLP 的任务分为两类：**理解**和**生成**。报告题目是基于逆强化学习的文本生成。所谓逆强化学习，指的是把 Reward 逆向学出来。
通常有三种文本生成方法：
- Maximum Likelihood Estimation
- GAN
- Inverse RL
Variational AutoEncoder 基于 MLE 的，用分布而不是向量表示文档。直接用 GAN 生成文本是行不通的，因为在 Generator 中的梯度断了，不能反向传播。解决办法有: 
- Gumbel-softmax GAN
- SeqGAN
  - 用 Policy Gradient 做 Reward
- RankGAN
  - 用 Ranker 代替 Discriminator, 不用 0 或者 1 这么强的约束了

然后介绍了基于 GAN 方法的两个问题：Reward Sparsity 和 Mode Collapse.最后介绍了自己的工作: Toward Diverse Text Generation with Inverse Reinforcement Learning. 结果表明 SeqGAN 只能生成训练集中存在的句子，而 Inverse RL 方法可以生成训练集中不存在的句子。具体参考 [pdf](https://github.com/gaoisbest/NLPCC2018/blob/master/Day3_Tencent_workshop_qiuxipeng.pdf).
