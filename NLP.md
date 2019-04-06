## NLP

### TF-IDF
+ **IDF为什么用对数？**
	+ 涉及到信息论的知识，指IDF相当于一个权重，当该词越容易分辨，则相应权重也会特别大。
----

### word2vec
> 输入层+映射层+输出层
> 两种模型：skip-gram模型、CBOW模型

+ **损失函数**
	+ -log(P)，P为softmax函数

+ **skip-gram模型**
	+ 又称跳字模型，在n个word窗口内，由中心词预测n-1个背景词，要循环n-1遍。

+ **CBOW模型**
	+ 又称连续词袋模型，在n个word窗口内，由n-1个背景词预测中心词。输入层到映射层是将n-1个word的词向量相加。

+ **模型训练方法**
	+ 负采样
		+ 背景词是出现在中心词时间窗口内的词。噪声词是和中心词不同时出现在该时间窗口的词，噪声词由噪声词分布采样得到。噪声词分布可以是字典中的所有词的词频概率组成（一般是单字概率的3/4次方）。
	+ 层序softmax
		+ 原来的softmax中是从字典中选一个单词，而层序softmax的思路是将一次分类分解为多次分类，因此采用树的结构，而为什么采用Huffman树呢？是因为这样构建的话（根据词频构造），出现频率越高的词所经过的路径越短，从而使得所有单词的平均路径长度最短。
		+ Huffman树的节点含义：非叶子节点可以认为是神经网络中隐藏层参数（初始化长度为m的零向量），叶子节点为字典中的词向量（随机初始化），每个词具有唯一的编码。

+ **训练过程**
	+ 因为层序softmax的映射层到输出层是Huffman树，在训练过程中，对于CBOW来说，先将n-1个背景词向量相加然后作为映射层的输入，然后根据Huffman树计算每个非叶节点向量和输入向量的乘积再用sigmoid计算概率，依次递归下去直至叶节点，因为每个词都对应有唯一的一个编码，所以训练过程中的损失函数就是根据预测词的编码（分类的思想）累乘每次分叉时的概率，使得该概率值最大。

+ **为什么有了层序softmax后还要负采样的方法？**
	+ 虽然层序softmax可以提高模型的训练效率，但是如果训练样本中的中心词是一个**生僻词**，那么模型得到的Huffman编码就是一个很长的序列。
----

### Glove
+ 可以很好地表示词与词之间的类比关系;
+ 能够知道每个词的全局统计信息。
----

### Fasttext
+ Fasttest在word2vec基础上加入了n-gram的信息。解决oov问题。
+ 对于输入，也是将窗口内的word的词向量和n-gram的word的词向量相加。
----

### 为什么有了word2vec，还要Glove、ELMO等？
+ word2vec
	+ 学习到词之间的类比信息，适合局部间存在很强关联性的文本，但是缺乏词与词之间的共现信息。词义相近的词对贡献次数多，词义差得比较远的词对共现次数比较少，但是其实它们的区分度并不明显。
+ Glove
	+ 对word-pair共现进行建模，拟合不同word-pair的共现之间的差异。
	+ 相比于word2vec，Glove更容易并行化，速度更快。
+ ELMO
	+ 前两者学到某个词的词向量是固定的，不能很好处理一词多义。ELMO是基于整个语料训练的，而不是窗口，因而能更好地表达一个词。
+ Bert
	+ Bert中利用mask的方法有点像负采样，只不过Bert是基于整个语料做的，Bert主要是推翻了现有的对于某个任务必须特定的模型结构这一做法。
----
