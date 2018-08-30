# 介绍
今天上午的分享主要包括三个部分: Invited Talk, Best Papers 和 Industrial Talk.
下午参加了方正和搜狗的两个 Workshop.

# 1. 上午
## Invited Talk
### Talk 1
来自 Michigan State University 的 **Joyce Chai** 教授分享了 Keynote Topic: **Language Communication with Robots**.
报告的主要内容是与 Robot 对话，教给 Robot 一些动作，让它自己能学会。比如，让 Robot 学会如何把橘子放进榨汁机榨汁等。
这是一个交叉学科，包括 NLP 中的人机对话，CV 中的物体识别 (视频 demo 中用的 Yolo 算法)，认知学等。具体用到了 Graph matching (根据动态交互中不断修改节点之间的边连接), RL等方法。用到的数据集是 TACos. 最后讨论了如何将 Commonsense knowledge 考虑进去。
### Talk 2
来自阿里巴巴 **Dr. Luo Si** 的分享，介绍了 **AliNLP** 的技术优势，支撑了阿里巴巴很多的业务。
并着重介绍了最近发表的Paper，主题分别是商品描述压缩，阅读理解和搜索。
- 商品描述压缩
[A Multi-task Learning Approach for Improving Product Title Compression with User Search Log Data](https://arxiv.org/pdf/1801.01725.pdf)
- 阅读理解
[Jiangnan at SemEval-2018 Task 11: Deep Neural Network with Attention Method for Machine Comprehension Task](http://aclweb.org/anthology/S18-1178)
- 搜索
SIGKDD 2017 [Cascade Ranking for Operational E-commerce Search](https://arxiv.org/pdf/1706.02093.pdf)

## Best Papers
第二部分是 Best Papers 分享，这次会议总共选出 4 篇英文和 1 篇 中文。
### Paper 1
第一篇 Best Paper 分享是来自南开大学的 **Hierarchical Attention Based Semi-supervised Network Representation Learning**. 这是一篇做 Network embedding 的工作，Network 在社交网络，生物信息学等中是常用的数据结构。常用的 Network embedding 方法是 DeepWalk 和 node2vec 等。本篇 Paper 提出了 SHANE 模型，使用 hierarchical attention network 依次编码词和句子，即编码 Node 的 text 信息。然后将 text-based embeddings 和 structure-based embeddings 集成到一块。最后加入 Node 的 Label 信息。在 Link Prediction (也就是看任意两个 Nodes 之间有没有关系) 和 Node Classification 任务上表现优于其他方法。
### Paper 2
第二篇 Best Paper 分享是来自哈工大的**基于对抗学习的讽刺识别研究**，也是唯一一篇中文 Best Paper. 讽刺识别是情感分析的一个子任务。创新点：分类模型上将 CNNs 的池化层改为注意力层 ，使用对抗学习生成对抗样本。值得吐槽的是 Paper 原作者没来，问的几个问题都没回答好。

## Industrial Talk
## Talk 1
来自智能一点的 CEO **Dr.Hu** 介绍了为购物设计的智能客服 **ROBOTA** 系统。
## Talk 2
来自英语流利说的 CEO **Dr.Lin** 介绍了 **Human learning** 的概念。Dr.Lin 的代表作是关于文本摘要的：A Class of Submodular Functions for Document Summarization.

# 2. 下午

## 2.1 方正
方正的 Workshop 包括 5 个分享，前两个是方正自己业务介绍和核心技术介绍，后三个分别是微软亚洲研究院的[周明](https://www.microsoft.com/en-us/research/people/mingzhou/), 
北京大学的[万小军](http://59.108.48.5/lcwm/wanxj/).
### 2.1.1 Applications and Exploration of NLP & CC technologies in the field of intelligent media, by Xiaojun Huang
方正业务介绍，主要是书籍，出版，报刊等业务，比较有吸引力的业务有两点：根据公式搜索出原文；拷贝 pdf 中的公式粘贴到 word 中就可以自动变成可编辑的公式。

### 2.1.2 Application and Innovation of CNDPLAB in the Field of Knowledge Service, by Haihua Xie
方正算法模型介绍，包括：
- 根据书的内容进行多标签分类

- Query 的语义解析
- 基于 KB 检索书
### 2.1.3 KB-QA: Recent Progress of Technologies and Application, by Ming Zhou
### 2.1.4 New Progress in Machine Writing, by Xiaojun Wan
### 2.1.5 Semantic knowledge discovery system which is based on hybrid of knowledge organization system and deep learning, by Tan Sun


## 2.2 搜狗
搜狗的 Workshop 关注在人机对话，由清华大学的黄民烈，北京大学的[严睿](http://www.ruiyan.me)老师和微软亚洲研究院的[段楠](https://www.microsoft.com/en-us/research/people/nanduan/)老师做的分享。

### 2.2.1 Towards Building More Intelligent Chatbots, by Minlie HUANG
在以下三个角度剖析了 Chatbot 目前遇到的三个问题：
- Semantics
- Consistency
- Instructiveness
也分别在以上三个角度讲诉了最近发表的一些 Paper，可以在黄老师官网上查看相关 Paper.
### 2.2.2 人工智能在机对话系统中的技术现状与挑战, by Rui Yan
### 2.2.3 Semantic Parsing for Search Engine & Conversational AI: Background, Methodology and Latest Progress, by Nan DUAN

- 《智能问答》一
