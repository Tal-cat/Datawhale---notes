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
