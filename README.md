# Name-Disambiguation-in-AMiner
homework2 report

一、所做的工作：

1. 复现乔子越、王寒雪同学的代码，得到0.46的分数，用户名为hamimelon2019。
并将聚类种类有DBSgan改成OPTICS，发现结果不理想，仅得到0.22的分数；
2. 发现乔王两位同学的模型有待改进之处。
1）常用名字存在大量的未消歧名字和文章。
根据训练完成的genename result，消歧效果差的前七八个名字集中表现为，中文名为两个字且名字为单个字母缩写的名字。举例来说其中s_liu和t_wang两个名字对应的论文篇数分别为1478篇和1357篇，qing_liu对应的论文为2388篇，一般来说，一名学者不可能达到这么高的论文产出，唐老师科研20年，论文200+篇，差不多一年10多篇，1478篇则需要147年，这其中肯定不是一位学者所写。
仔细分析，这几个名字的学者在在学科研究类别上有很大差异。
2）由此，应该重视venue和department两个特征。venue也许如两位同学所说，同样venue的人也许并不能归为一个人，但是同名字的学者，一位学科是药剂学，一位学科是计算机，这肯定是可以划分为两个人的。

3. 利用linux系统复现唐老师和同学们2018年KDD论文代码，得出与唐老师论文中相差不多的结果。100个名字，n_pubs平均值为271，n_clusters的平均值为10.66，precision、recall、f1的
average分别为0.76605、0.63292、0.69315，唐老师与同学们论文的这三个值分别为77.96、63.03、67.79，相差不大。
唐老师与同学们利用了TF-IDF、NLPK、WORD2VEC、RNN等模型进行数据预处理或训练，分别从特征学习和基于链接的图表示学习进行学习，特征信息的挖掘相对于乔子越、王寒雪两位同学的更加丰富。

二、问题与日后待改进之处

虽然发现乔王两位同学在venue和department特征信息处理不够的问题，但是由于受模型和工程能力低下所限，以及时间关系，很遗憾并未能做出相应改进，这有待与日后持续研究进步后改进。

唐老师和同学们的模型种类较多，需要日后加以理解吃透，并提高相应的编码工程能力。

参考文献：
1. Ziyue Qiao ; Yi Du ; Yanjie Fu ; Pengfei Wang ; Yuanchun Zhou
, "Unsupervised Author Disambiguation using Heterogeneous Graph Convolutional Network Embedding," 2019 IEEE International Conference on Big Data (Big Data), Los Angeles, CA, USA, 2019, pp. 910-919, doi: 10.1109/BigData47090.2019.9005458.
2.Yutao Zhang, Fanjin Zhang, Peiran Yao, and Jie Tang. 2018. Name Disambiguation in AMiner: Clustering, Maintenance, and Human in the Loop .
In KDD ’18: The 24th ACM SIGKDD International Conference on Knowledge
Discovery & Data Mining, August 19–23, 2018, London, United Kingdom. ACM,
New York, NY, USA, 10 pages. https://doi.org/10.1145/3219819.3219859


