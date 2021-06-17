# Weekly
Weekly progress and planning.

## 2021.6.9
### Progress 

#### 1. Lasso Ranker集成到工具，对SMACK生成Boogie语句进行转换，满足Lasso Ranker格式.

#### 2. 读LTL2BA论文([***Paper***](https://doi.org/10.1007/978-3-642-28756-5_8), [***Slides***](https://github.com/fengwz17/Paper-List/blob/master/6.9_notated.pdf))，相关知识，难点：

* Very weak Alternating Automata (VWAA)：注意到weak alternating automata表达能力与NBA是相同的，对于very weak且接受条件为co-Büchi的情况，其表达能力目前还不太情况..

* Alternating formula：本文针对性地对absolutely liveness做了优化（本文主要优化是用X\varphi替换\varphi），我们可以考虑对stable和fairness进行优化.

* VWAA to genaralized Büchi automata：没太理解清楚这个accepting transition的定义..

* Good for MDP?

### Planning

#### 1. 读rank-based与slice-based取补算法.

#### 2. Lasso Ranker.

#### 3. Spot调研:

* 如何调用自动机库.

* 如何在Spot中实现取补算法.
 
 ## 2021.6.16
### Progress 

#### 1. Lasso Ranker集成到工具，对SMACK生成Boogie语句进行转换，满足Lasso Ranker格式:

* 还没做完，但是知道了SMACK生成的Boogie语句处理四则运算等操作时全都是以函数调用形式实现的，后面需要调用相应接口函数继续处理assign语句.

#### 2. 读论文，学习rank-based与slice-based的Finitely ambiguity Büchi automata取补算法:

* 把握文章的主要脉络，要能脱稿讲清楚.
* 什么是FANBWs? 
* FANBWs accepting DAGs的separate levels. 
* Co-deterministic DAGs. 
* Nonaccepting co-deterministic DAGs的stable level. 
* Rank-based. 
* Slice-based.

### Planning

#### 1. 读文章Complementing Semi-deterministic Büchi Automata，主要学习NCSB算法:
* 类比slice-based取补的NCB算法.

#### 2. Spot中实现：

* 参看NCSB算法的实现. ([Seminator](https://github.com/mklokocka/seminator)).

#### 3. LassoRanker.
 
