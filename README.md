# Datawhale-Machine-Learning-notes    
2024.5 

![1359141715867507_ pic](https://github.com/Tal-cat/Datawhale-Machine-Learning-notes/assets/60603537/b526c28c-8345-4241-9c8e-f58f97bf5c6b)

第一章 绪论    
1. 主要是概念的各种介绍，大致清楚，以下值得记录。
2. 经典定义：利用经验改善系统自身的性能。【1997】
3. 目前主要研究：智能数据分析的理论和方法。   
4. 没有免费的午餐定理（No Free Lunch Theorem, NFL）：在f均匀分布时，任何2个算法的期望都相同。
5. 但是！并不意味着选择算法无用，因为在特定情境（数据）下，f并非均匀分布，因此机器学习有一番用武之地。
6. 发展历史：推理期→知识期→学习期【符号主义（表示能力强导致复杂，成也萧何败萧何，程野不是唱二人转那个么？）→连接主义→统计学习→连接主义（算力提升）】。

第二章 模型评估与选择   
1. 基础评估：accuracy, specificity, recall/precision, F1-score (Fβ-score), PR, ROC, AUC-ROC。曲线完全包裹代表性能更好。    
2. 模型训练方法：（1）留出法hold-out：最简单。（2）Cross-validation: 常用，5-fold, 10-fold。特殊一点是留一法。（3）自助法Bootstraping:感觉强化学习用的多些，放回的抽样，可能改变数据分布。
3. 调参及训练过程：其实在书上画了个图。data分成training set和test set, training set分成实际training set和validation set。用实际training set调参，根据validation set表现确定hyperparameters。然后才是真正的训练：用大的training set训练然后test set评估。
4. ROC曲线画法：将threshold分别设置为每个样本的数值，然后计算画图。
5. 代价曲线cost curve:多个线段交集下的面积，下次画一个。
6. 比较检验：假设检验，交叉验证t检验，McNemar检验，Friedman检验，Nemenyi后续检验。其中Friedman检验的图很实用，下次画一个。
7.泛化误差：偏差+方差+噪声。偏差反映拟合能力，方差反应数据变化的影响。噪声反应问题难度。    
8. 偏差-方差窘境。

第三章 线性模型    
3,2 线性回归【数学部分南瓜书很详细，不赘述】     
1. 针对离线属性，如果存在“序”，可转化为连续值【如大中小对应1,0.5,0】；不存在“序”时转换为k维向量，避免将无序属性连续化，引入序【如篮球足球对应（1,0）和（0,1）】。
2. 可解释性好，w大小代表贡献度。   
3. 使用最小二乘法最小化MSE，即：找到一条直线，使得样本到直线的距离最小。
4. 求解最小参数argmin的过程称为参数估计。
5. 多元线性回归时，满秩有唯一解，不满秩时有多个解，就像3个x只有2个公式一样，此时根据偏好（如需要某个数最小）或加入正则化限制，以获取答案。   
6. 广义线性模型：y=g^(-1)(w^Tx+b)。期中g(.)称之为联系函数。

3.3 对数几率回归（大名鼎鼎的Logistic Regression/逻辑回归【被批判，不是】）    
1. 用于分类任务，将不连续且不可微的[0,1]二分类转化为单调+任意阶可导的函数。
2. 属于Sigmoid函数的一种。
3. 命名由来：ln(y/1-y)=e^(w^Tx+b)，其中y/1-y反应相对可能性，称为几率（odds）。log+odds→取名logit→形容词化logistic→被【错误翻译成了逻辑啊啊啊啊】。
4. 优点：（1）；无需实现预测数据分布（2）可得到近似概率；（3）现有许多optimization方法。    
5. MLE思想：max(P(真是+)P(预测是+)+P(真是-)P(预测是-))。
6. LR的MLE高阶连续可导，但是不用MSE，原因有二：（1）多元时MSE计算，w=(x^Tx)^(-1)x^Ty，(x^Tx)^(-1)不一定存在；（2）GD为迭代算法，方便计算机实现。
7. MLE求解使用GD（一阶导数）或者Newton Method（二阶导数）。注意GD常用，Newton计算麻烦且不一定都能用二阶。

3.4 线性判别分析（LDA）    
1. 线性方法，不严格时也叫做”Fisher“判别分析。但是严格来说，LDA假设了各类样本的协方差矩阵相同且满秩。
2. 思想：给定训练集，投影到直线，同类聚集，不同类远离。新样本投影后根据位置进行分类。属于监督（需要label）降维技术。
3. 计算：不同类距离最大，同类距离最小。综合上就是：最大化广义瑞利商【不同类距离/同类距离】。
4. w=S_w^(-1)(u_0-u_1)。计算是通常对S_w进行奇异值分解，S_w=UsigmaV^T, S_w^(-1)=Vsigma^(-1)U^T。    
5. 具体计算挺好玩，笔记在书上，建议参考周志华老师课程。 
6. 多分类LDA和二分类类似。W的闭式解S_w^(-1)S_b的d'个非零广义特征值所对应的特征向量组成的矩阵，d‘<=N-1。   
