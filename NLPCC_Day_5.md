# 介绍
今天上午的分享主要包括三个部分: Invited Talk, Best Paper 和 Industrial Talk.
下午参加了方正和搜狗的两个 Workshop.

# 1. 上午
## Invited Talk
### Talk 1
Michigan State University 的 [**Joyce Chai**](https://www.egr.msu.edu/people/profile/jchai) 教授分享了 Keynote Topic: **Language Communication with Robots**.
报告的主要内容是与 Robot 对话，教给 Robot 一些动作，让它自己能学会。比如，让 Robot 学会如何把橘子放进榨汁机榨汁等。
这是一个交叉学科，包括 NLP 中的人机对话，CV 中的物体识别 (视频 demo 中用的 Yolo 算法)，认知学等。具体用到了 Graph matching (根据动态交互中不断修改节点之间的边连接), RL等方法。用到的数据集是 TACos. 最后讨论了如何将 Commonsense knowledge 考虑进去。
### Talk 2
阿里巴巴 [**Dr. Luo Si**](https://www.cs.purdue.edu/homes/lsi/) 介绍了 **AliNLP** 的技术优势，支撑了阿里巴巴很多业务。
并着重介绍了最近发表的Paper，主题分别是[商品描述压缩](https://mp.weixin.qq.com/s/C-Oh0bmpEon1Oeq5M6Q1GQ)，阅读理解和搜索。
- 商品描述压缩
[A Multi-task Learning Approach for Improving Product Title Compression with User Search Log Data](https://arxiv.org/pdf/1801.01725.pdf)
- 阅读理解
[Jiangnan at SemEval-2018 Task 11: Deep Neural Network with Attention Method for Machine Comprehension Task](http://aclweb.org/anthology/S18-1178)
- 搜索
SIGKDD 2017 [Cascade Ranking for Operational E-commerce Search](https://arxiv.org/pdf/1706.02093.pdf)

## Best Papers
第二部分是 Best Papers 分享，这次会议总共选出 4 篇英文和 1 篇中文。
### Paper 1
第一篇 Best Paper 分享是来自南开大学的 [**Hierarchical Attention Based Semi-supervised Network Representation Learning**](https://github.com/gaoisbest/NLPCC2018/blob/master/Best%20Paper%201_Hierarchical%20Attention%20Based%20Semi-supervised%20Network%20Representation%20Learning.pdf). 这是一篇做 Network embedding 的工作，Network 在社交网络，生物信息学等中是常用的数据结构。常用的 Network embedding 方法是 DeepWalk 和 node2vec 等。本篇 Paper 提出了 SHANE 模型，使用 hierarchical attention network 依次编码词和句子，即编码 Node 的 text 信息。然后将 text-based embeddings 和 structure-based embeddings 集成到一块。最后加入 Node 的 Label 信息。在 Link Prediction (也就是看任意两个 Nodes 之间有没有关系) 和 Node Classification 任务上表现优于其他方法。
### Paper 2
第二篇 Best Paper 分享是来自哈工大的[**基于对抗学习的讽刺识别研究**](https://github.com/gaoisbest/NLPCC2018/blob/master/Best%20Paper%202_%E5%9F%BA%E4%BA%8E%E5%AF%B9%E6%8A%97%E5%AD%A6%E4%B9%A0%E7%9A%84%E8%AE%BD%E5%88%BA%E8%AF%86%E5%88%AB%E7%A0%94%E7%A9%B6.pdf)，也是唯一一篇中文 Best Paper. 讽刺识别是情感分析的一个子任务。创新点：分类模型上将 CNNs 的池化层改为注意力层 ，使用对抗学习生成对抗样本。值得吐槽的是 Paper 原作者没来，问的几个问题都没回答好。

## Industrial Talk
## Talk 1
智能一点的 CEO **Dr.Hu** 介绍了为购物设计的智能客服 **ROBOTA** 系统。主要内容还是非常基础的 Pipeline 等方法。
## Talk 2
英语流利说的 CEO **Dr.Lin** 介绍了 **Human learning** 的概念，没有设计太多算法层面的知识。Dr.Lin 的代表作是关于文本摘要的：**A Class of Submodular Functions for Document Summarization**.

# 2. 下午

## 2.1 方正
方正 Workshop 包括 5 个分享，前两个是方正自己业务介绍和核心技术介绍，后三个分别是微软亚洲研究院的[周明](https://www.microsoft.com/en-us/research/people/mingzhou/)老师, 
北京大学的[万小军](http://59.108.48.5/lcwm/wanxj/)老师，抱歉最后一个老师的报告没听。
### 2.1.1 Applications and Exploration of NLP & CC technologies in the field of intelligent media, by Xiaojun Huang
方正业务介绍，主要是书籍，出版，报刊等业务，比较有吸引力的业务有**两点**：
- 根据公式搜索出原文
- 截取 pdf 中的公式粘贴到 word 中就可以自动变成可编辑的公式

### 2.1.2 Application and Innovation of CNDPLAB in the Field of Knowledge Service, by Haihua Xie
方正算法模型介绍，主要支撑方正业务，比如对书籍自动分类；用户 Query 解析搜索出符合条件的书籍；根据知识图谱找到相关书籍等。具体包括：
- 根据书的内容进行多标签分类
基于 Fasttext, CNNs 和 RNNs 的基于 char 和 word 的文本分类模型，最终结果是三个模型的集成结果。
- Query 的语义解析
比如用户输入 Query “莫言近三年的小说”，那么语义解析的结果就是：`{'label': 'novel', 'Year': '>=2015', author: 'moyan'}`，这样就可以转换成查询去数据库查找。

### 2.1.3 KB-QA: Recent Progress of Technologies and Application, by Ming Zhou
周明老师做了关于 KBQA 最新研究的报告。
- KBQA 的**整个流程**是：输入问题，首先做问题解析，得到问题的语义表达式，然后在知识库中查找。如果有多个候选，则还需要排序找出最佳候选
- KBQA 可以分为基于**语义解析 (Semantic parsing)** 的 KBQA 和基于**答案排序 (Answer Ranking)** 的 KBQA
  - 基于语义解析的 KBQA 就是把自然语言转换为逻辑表达式子，一般是 Lamda 算子表示。这个转换方法一般有两种，即
    - 基于语法的解析
      - 基于语法的解析使用指定的语法规则，生成语义解析树，通常有 CCG, SCFG 和 Lamda-DCS 语法。
    - 基于神经网络的解析
      - 基于神经网络的解析最基础的做法是 Seq2Seq 模型，今年的新工作 Semantic Parsing with Coarse-to-Fine Decoding 也是基于 Seq2Seq 框架，提出了 sketch decoding 概念，即一步 encode，多步 decode. 然后介绍了微软今年的新工作：Semantic Parsing with Multi-Gates and Syntax Constraints, 主题是基于表格的语义解析，这里基于表格而不是知识库，是因为有些数据是基于表格的，基于知识库的数据获取比较昂贵。
  - 基于答案排序的 KBQA 首先找到实体，在 KB 中找到实体的属性，如果有多个候选答案，根据多种特征做 ranking
    - 可以对 Question 进行 embedding, 候选答案进行 embedding，根据两个 embedding 的 distance 进行排序。通常基于答案排序的方法是优于基于语义解析的方法的
### 2.1.4 New Progress in Machine Writing, by Xiaojun Wan
NLG 可以分为：
- Text-to-Text Generation
- Data/Table-to-Text Generation
- Meaning/Syntax-to-Text Generation
- Image/Video-to-Text Generation
其中 Text-to-Text Generation 是最常见的，包括 Summarization/Compression, Paraphrasing/Simplification, Maching Translation 和 Dialogue Generation. 接下来，万老师着重介绍了最近发表的三个 Paper: Data2Text Generation (Li and Wan, 2018) 分 two-stage 做生成，即 stage 1: template generation, stage 2: slot filling with delayed copy network.
Pun Generation (You, Tan and Wan, 2018): conditional language model + Joint Beam Search + Associated words.
Images2Poem Generation (Liu, Wan&Guo, 2018): 从图像中做诗歌生成。具体参考 [pdf](https://github.com/gaoisbest/NLPCC2018/blob/master/Day5_Founder_workshop_wanxiaojun.pdf).

### 2.1.5 Semantic knowledge discovery system which is based on hybrid of knowledge organization system and deep learning, by Tan Sun


## 2.2 搜狗
搜狗的 Workshop 关注在人机对话，由清华大学的[黄民烈](http://coai.cs.tsinghua.edu.cn/hml/)老师，北京大学的[严睿](http://www.ruiyan.me)老师和微软亚洲研究院的[段楠](https://www.microsoft.com/en-us/research/people/nanduan/)老师做的分享。

### 2.2.1 Towards Building More Intelligent Chatbots, by Minlie HUANG
在以下三个角度剖析了 Chatbot 目前遇到的三个问题：
- Semantics: Content, Context, Scene
- Consistency: Personality, Personalization, Language Style, Emotion & Sentiment
- Instructiveness: Strategy, Behavior
也分别在以上三个角度讲诉了最近发表的一些 Paper，可以在黄老师官网上查看相关 Paper. 值得推荐的是，黄老师的主页上提供了很多**科研数据集**，大家可以免费下载调试模型。
### 2.2.2 人工智能在机对话系统中的技术现状与挑战, by Rui Yan
严睿老师首先定义了对话流程：用户输入，计算机结合上下文信息，知识库信息和语义逻辑信息返回输出。
对对话系统分类
- 按领域分类
  - 开放
  - 垂直
- 按回复生成方式分类
  - 检索式 (目前业界主流)
  - 生成式
  - 二者结合式
- 按场景分类
  - 单轮
  - 多轮
- 按方式分类
  - 被动
  - 主动
接着按照上面的方式列举了典型的 Paper，具体参考 [pdf](https://github.com/gaoisbest/NLPCC2018/blob/master/Day5_Sogou_workshop_yanrui.pdf).

### 2.2.3 Knowledge-enhanced NLP: Progress and Challenge, by Nan DUAN
段楠老师的分享主要关注知识增强的 NLP. 他把 Knowledge 分为 5 大类: 
- Pre-trained Word Embeddings
- Open Domain Knowledge
- Specific Domain Knowledge
- Commonsense Knowledge
- Pre-trained Task Embeddings
Pre-trained Word Embeddings 中介绍了 Word2Vec 和 ELMo, ULMFit 和 OPEN AI 的工作。然后介绍了最近的发展趋势：转向 multi-turn, complex-relation 和 specific task. 最后介绍了 Pre-trained Task Embeddings, 提到了十项全能的 decaNLP. 具体参考 [pdf](https://github.com/gaoisbest/NLPCC2018/blob/master/Day5_Sogou_workshop_duannan.pdf). 段楠老师和周明老师的新书《智能问答》也会将于近期出版。
