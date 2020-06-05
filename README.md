# Name-Disambiguation-in-AMiner

homework2 report 2.0 （6.5.2020）

一、比赛信息：
1. 比赛用户名：hamimelon2019 
2. 分数：0.466060323749797，提高了0.11% 
3. 名次：暂列第三

二、本周所做的新工作：

*完成顺利的工作：
1. 与上周第一版相比，为了改进特征提取效果，增加了一批停用词，对org、conf、word和venue等进行提纯，得到了performance的稍许提升。

   根据语料生成的四个txt文件分析判断，这些停用词不是学科等核心词，对作者的定点定位、消歧没有帮助，所以去除，从实际效果看，推断得到了证实。
   
   增加的停用词有：
   
       stop = [from];
       
       stop1 = ['Dept','state',
                 'research','world','Sciences','high','traditional','null','people','general','national','2007','european',
                 'life','key']
                 


*尝试但未成功的工作：   

2. 加入venue特征提取，但没有成功。
出现语料不足的bug，需要接下来再努力检查调试代码直至成功。

3. 把语料放入Name Disambiguation in AMiner: Clustering, Maintenance, and Human in the Loop .In KDD ’18 中 尝试实现，processing这一步成功，但是第二步出现bug。
需要接下来继续检查调试代码。

三、心得
1. 特征提取精准选取特征映射信息比高超的工具技术更为关键重要。当然，对各种技术掌握也有利于更好的精准提取特征信息。
2. 超参数调试，有领域基础知识更好，随机试效果不好效率低。

四、接下来，应该：
1. 在NLP理论技术和工程代码双方面继续学习思考，学会修改、改造模型，提升模型performance；
2. 从模仿到创造。

五、求教与致谢

时间能力所限，所得有限。
感谢老师们教授批阅：）有任何未尽和不对之处，敬请不吝指正。
再次感谢。
   
   



————————————————————————————————

homework2 report 1.0 （5.29.2020）

比赛用户名：hamimelon2019 
分数：0.464947673582703

一、所做的工作：
1. 复现乔子越、王寒雪同学的代码，调超参数，在比赛中得到0.464947673582703的分数；
并将聚类种类由DBSCAN改成OPTICS，发现结果不理想，仅得到0.22的分数。

2. 发现乔王两位同学的模型有待改进之处。

1）常用名字存在大量的未消歧名字。

从训练完成的genename result文件来分析，消歧效果差的前七八个名字问题集中表现为：中文名为两个字且名字为单个字母缩写的名字。
举例来说其中s_liu和t_wang两个名字对应的论文篇数分别为1478篇和1357篇，qing_liu对应的论文为2388篇。一般来说，一位学者在学术生涯中不可能达到这么高的论文产出。比如唐老师科研20年，论文200+篇，差不多一年10多篇，这样算来，一位学者发表1478篇论文则需要147年，所以可以推断s_liu名字下所属的论文肯定不是一位学者所写。
继续沿此思路仔细分析，这几个名字的学者在在学科研究类别上有很大差异，证实了我们的猜测。

2）经过继续分析，我们认为应该重视venue和department两个特征。

venue的特征意义是否显著，也许如两位同学所说，同样venue或department的人也许并不能归为一个人，但是同名字的学者，不同的venue和department，则很有可能不是同一人，比如一位学科是药剂学，一位学科是计算机，这肯定是可以划分为两个人的。
如果把university与venue和department相结合，也许结果会更显著。

3. 利用linux系统复现唐老师和同学们2018年KDD论文代码，得出与唐老师论文中相差不多的f1结果。 

100个名字，n_pubs平均值为271，n_clusters的平均值为10.66，precision、recall、f1的average分别为0.76605、0.63292、0.69315，唐老师与同学们论文的这三个值分别为77.96、63.03、67.79，相差不大。
唐老师与同学们利用了TF-IDF、NLPK、Word2Vec、RNN等等模型进行数据预处理或训练，分别从特征学习和基于链接的图表示学习进行学习。

二、本次作业过程中显现出的问题与日后待改进之处

虽然发现乔王两位同学在venue和department特征信息处理方面有改善的空间，但是由于受NLP模型掌握应用和工程能力低下所限，以及时间关系，很遗憾并未能做出相应改进，这有待与日后持续研究进步后改进。

唐老师和同学们的模型种类较多，需要日后加以理解吃透，并提高相应的编码工程能力。

感谢。


参考文献：
1. Ziyue Qiao ; Yi Du ; Yanjie Fu ; Pengfei Wang ; Yuanchun Zhou, "Unsupervised Author Disambiguation using Heterogeneous Graph Convolutional Network Embedding," 2019 IEEE International Conference on Big Data (Big Data), Los Angeles, CA, USA, 2019, pp. 910-919, doi: 10.1109/BigData47090.2019.9005458.

2. Yutao Zhang, Fanjin Zhang, Peiran Yao, and Jie Tang. 2018. Name Disambiguation in AMiner: Clustering, Maintenance, and Human in the Loop .In KDD ’18: The 24th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, August 19–23, 2018, London, United Kingdom. ACM, New York, NY, USA, 10 pages. https://doi.org/10.1145/3219819.3219859


