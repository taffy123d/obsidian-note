# 1
- 智能是 <u style="color:red">知识与智力</u> 的总和
- 人工智能是用人工的方法在 <u style="color:red">机器（计算机）</u> 上实现的智能；或者说是人们使 <u style="color:red">机器</u> 具有类似于人的智能。
- 人工智能学科是一门研究如何构造 <u style="color:red">智能机器（智能计算机）或智能系统</u>，使它能模拟、延伸、扩展人类智能的学科
- 面向特定任务（比如下围棋）的人工智能称为 <u style="color:red">专用人工智能</u>。
- 世界上第一台电子计算机是 <u style="color:red">阿塔纳索夫－贝瑞计算机（ABC）</u>，为人工智能的研究奠定了物质基础。
- <u style="color:red">分布式人工智能系统</u> 以鲁棒性作为控制系统质量的标准，并具有互操作性，即不同的异构系统在快速变化的环境中，具有交换信息和协同工作的能力。

---
<div style="page-break-after: always;"></div>

# 2
- 知识表示是对知识的一种描述，或者说是一组约定，一种让<u style="color:red">计算机</u>可以接受的用于描述知识的<u style="color:red">数据结构</u>。
- 命题是一个<u style="color:red">非真即假</u>的陈述句。
- 如果谓词公式$P$对个体域$D$上的任何一个解释都取得真值$T$，称$P$在$D$上是<u style="color:red">永真的</u>。
- 设$P$与$Q$是两个谓词公式，$D$是它们共同的个体域，若对$D$上任何一个解释，$P$与$Q$都有相同的真值，则称公式$P$和$Q$在$D$上<u style="color:red">等价的</u>。
- 对于谓词公式$P$与$Q$，如果$P \to Q$永真，则称公式$P$<u style="color:red">永真蕴含</u>，且称$Q$为$P$的<u style="color:red">逻辑结论</u>，称$P$为$Q$的<u style="color:red">前提</u>。
- 产生式通常用于表示事实、规则以及它们的<u style="color:red">不确定性度量</u>，适合于表示<u style="color:red">事实性知识</u>和<u style="color:red">规则性知识</u>。

---
<div style="page-break-after: always;"></div>

# 3 

**简答**
1. 知识的特性
2. 产生式与谓词逻辑中蕴含式的区别
3. 框架表示法的特点
   
---
<div style="page-break-after: always;"></div>

# 4

- 从<font color="red"><u>初始证据</u></font>出发，按某种策略不断运用知识库中的已知知识，逐步推出结论的过程称为<font color="red"><u>推理</u></font>。
- <font color="red"><u>非单调推理</u></font>是在推理过程中由于新知识的加入，不仅没有加强已推出的结论，反而要否定它，使推理退回到前面的某一步，重新开始。
- 自然演绎推理是从一组已知为真的事实出发，运用<font color="red"><u>经典逻辑的推理规则</u></font>推出结论的过程。
- 子句是任何文字的<font color="red"><u>析取式</u></font>。任何文字本身也都是子句。
- 对于谓词逻辑，归结式是其亲本子句的<font color="red"><u>逻辑结论</u></font>。
- 应用归结原理证明定理的过程称为<font color="red"><u>归结反演</u></font>。

---
<div style="page-break-after: always;"></div>

# 5

- 不确定性匹配算法是用来计算匹配<font color="red"><u>双方相似程度</u></font>的算法。
- 静态强度$CF(H, E)$为<font color="red"><u>知识的强度</u></font>，即当$E$所对应的证据为真时对$H$的影响程度。
- 设D是变量$x$所有可能取值的集合，且D中的元素是互斥的，在任一时刻$x$都取且只能取D中的某一个元素为值，则称D为$x$的<font color="red"><u>样本空间</u></font>。
- 集合是<font color="red"><u>论域</u></font>中具有某种相同属性的确定的、可以彼此区别的<font color="red"><u>元素的全体</u></font>，常用A，B等表示。
- 模糊逻辑给集合中<font color="red"><u>每一个元素</u></font>赋予一个介于0和1之间的实数，描述其属于一个集合的强度，该实数称为元素属于一个集合的<font color="red"><u>隶属度</u></font>。

---
<div style="page-break-after: always;"></div>

# 6
- <u style="color:red;">启发式搜索</u>考虑特定问题领域可应用的知识，动态地确定调用操作算子的步骤，优先选择较适合的操作算子，尽量减少不必要的搜索，以求尽快地到达结束状态。
- <u style="color:red;">状态空间</u>是利用状态变量和操作符号，表示系统或问题的有关知识的符号体系。
- <u style="color:red;">NPS（new path states）</u>表包含了等待搜索的状态，其后裔状态还未被搜索到，即未被生成扩展。
- 在具体求解中，能够利用与该问题有关的信息来简化搜索过程，称此类信息为<u style="color:red;">启发信息</u>。
- 当一个搜索算法在最短路径存在时能保证找到它，就称该算法是<u style="color:red;">可采纳的</u>。

---
<div style="page-break-after: always;"></div>

# 7

### 简答题：
1.简述搜索的主要过程1
2.简述图搜索算法的回溯思想
3.简述启发信息的分类
4.简述A算法和A*算法的区别
***p137 5.1  修道士和野人问题 试写出A*搜索树***

---
<div style="page-break-after: always;"></div>

# 8

- 智能优化方法通常包括<u style="color:red;">进化计算</u>和<u style="color:red;">群智能</u>等两大类方法，是一种典型的<u style="color:red;">元启发式</u>随机优化方法。
- 遗传算法是一类借鉴生物界<u style="color:red;">自然选择</u>和<u style="color:red;">自然遗传</u>机制的随机搜索算法。
- 在遗传算法中，将所有妨碍适应度值高的个体产生，从而影响遗传算法正常工作的问题统称为<u style="color:red;">欺骗问题</u>。
- 选择操作也称为<u style="color:red;">复制</u>操作，即从当前群体中按照<u style="color:red;">一定概率</u>选出优良的个体，使它们有机会作为父代繁殖下一代子孙。
- 双种群遗传算法建立两个<u style="color:red;">遗传算法群体</u>，分别独立地运行复制、交叉、变异操作，同时当每一代运行结束以后，选择两个种群中的<u style="color:red;">随机个体</u>及<u style="color:red;">最优个体</u>分别交换。

---
<div style="page-break-after: always;"></div>

# 9
- <u style="color:red;">词法分析</u>的定义为：从句子中切分出单词，找出词汇的各个词素，并确定其词义。
- <u style="color:red;">语义分析</u>是将句法成分与应用领域中的目标表示相关联。
- 先分析原文内容，产生原文的句法结构，再转换成译文的句法结构，最后再生成译文的翻译系统是<u style="color:red;">规则式翻译系统</u>。
- 提升高频部分，使信号的频谱变得平坦，保持在低频到高频的整个频带中，能用同样的信噪比求频谱，便于频谱分析或声道参数分析的数据预处理方式叫<u style="color:red;">预加重</u>。
- 隐马尔科夫模型中的“隐”指的是马尔科夫模型的状态集合<u style="color:red;">观测不到</u>。

---
<div style="page-break-after: always;"></div>

# 10

- 人工神经网络模拟<u style="color:red;">人脑神经系统</u>的结构和功能，运用大量简单处理单元经广泛连接而组成的人工网络系统。
- 任一时刻只有一个神经元调整状态，而其它神经元的状态保持不变的神经网络工作方式是<u style="color:red;">异步（串行）方式</u>。
- 神经网络方法是一种<u style="color:red;">隐式的</u>知识表示方法和推理方法。
- BP学习算法的<u style="color:red;">反向传播</u>实现流程为从输出层方向计算到第一个隐层，按连接权值修正公式向<u style="color:red;">减小误差</u>方向调整网络的各个连接权值。
- <u style="color:red;">随机神经网络</u>中，神经元状态为1是随机的，服从一定的概率分布。
- Boltzmann机是<u style="color:red;">离散Hopfield神经网络</u>的一种变型，通过对网络加以扰动，使其以概率的形式表达。

---
<div style="page-break-after: always;"></div>

# 11

- 7、CNN（卷积神经网络）是一个多层的神经网络，每层由多个二维平面组成，而每个平面由多个<u style="color:red;">独立神经元</u>组成。
- 8、通过卷积获得了特征之后，如果直接利用这些特征训练分类器，计算量是非常大的，因此，要对不同位置的特征进行聚合统计,称为<u style="color:red;">池化</u>。
- 9、胶囊网络的核心思想：胶囊里封装的检测特征的相关信息是以<u style="color:red;">向量</u>的形式存在的，胶囊的输入是一个<u style="color:red;">向量</u>，是用一组神经元来表示多个特征。
- 10、生成对抗网络中，两个网络相互对抗的过程，就是各自网络参数不断调整的过程，即<u style="color:red;">学习过程</u>。

---
<div style="page-break-after: always;"></div>

# 12

### 简答题
1. 简述BP算法的计算机实现流程
2. 简述神经网络方法求解优化问题的一般步骤
3. 简述卷积神经网络的关键技术
***P255 【8.8】 【8.9】***

---
<div style="page-break-after: always;"></div>

### 群体智能

- 群体智能是由简单个体组成的群落与环境以及<u style="color:red;">个体之间</u>的<u style="color:red;">互动行为</u>。
- 粒子通过跟踪两个“极值”来更新自己。第一个就是粒子本身所找到的最优解，这个解称为<u style="color:red;">个体极值</u>。另一个是整个种群目前找到的最优解，这个解称为<u style="color:red;">全局极值</u>。
- 若 \( \varphi_1 = 0,\ \varphi_2 > 0 \) 且 \( g \neq i \)，则称该算法为<u style="color:red;">PSO无私模型</u>。
- 信息素规则是越靠近食物播撒的信息素<u style="color:red;">越多</u>，越离开食物播撒的信息素<u style="color:red;">越少</u>。
- <u style="color:red;">蚂蚁圈系统</u>利用的是全局信息 \( Q/L_k \)，即蚂蚁完成一个循环后，更新所有路径上的信息。

---
<div style="page-break-after: always;"></div>

### 专家系统
- 专家系统是一种智能的<u style="color:red;">计算机程序</u>，它运用<u style="color:red;">知识</u>和<u style="color:red;">推理</u>来解决只有专家才能解决的复杂问题。
- 机器学习使计算机能模拟<u style="color:red;">人的学习行为</u>，自动地通过学习来获取知识和技能，不断改善性能，实现自我完善。
- 一个学习系统一般应该由<u style="color:red;">环境、学习、知识库、执行与评价</u>等四个基本部分组成。
- 知识发现和数据挖掘的目的是从数据集中<u style="color:red;">抽取和精化</u>一般规律或模式。
- KAS系统是由PROSPECTOR系统抽去原有的地质勘探知识而形成的，适用于开发<u style="color:red;">解释型</u>专家系统。

---
<div style="page-break-after: always;"></div>
