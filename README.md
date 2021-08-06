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

## 2021.6.23
### Progress

#### 1. 读论文[***TACAS'16***](https://doi.org/10.1007/978-3-662-49674-9_49)，学习semi-deterministic Büchi automata取补的NCSB算法，结合[Seminator](https://github.com/mklokocka/seminator)和spot代码理解.
#### 2. 基于[Seminator](https://github.com/mklokocka/seminator)实现了对unambiguity Büchi automata取补的Slice-based算法的框架.

* Reduced transition写的有问题，需要进行修改，在计算N'时保存map，并记录边的accepting信息，在计算C'的时候用前面记录的map替代原来自动机的transition.
### Planning

#### 实现Slice-based算法，进行实验.

## 2021.6.30
### Progress

#### 1. 代码实现：
* 基于seminator和spot提供的自动机库和接口等实现了GandALF文章中的NCB算法（一种对unambiguous \buchi automata取补的slice-based的算法）.
* 实现了李老师提出的一个对semi-deterministic automata取补的新算法.

#### 2. 实验结果:
* 用150个ltl公式生成相应自动机跑了实验，输入unambiguous自动机，转为半确定自动机，分别用seminator中的取补算法和NCB算法，semi自动机取补新算法进行实验，实现的NCB算法结果正确，semi取补新算法有两个样例不对；
* 且目前实现的算法生成补自动机状态数普遍较大.
   
### Planning
    
#### 1. 找出semi取补新算法测试不对的问题，将其调试正确；
#### 2. 实现上做一些优化，减小状态数;
#### 3. 跑更多例子，记录运行时间和状态数，和spot，seminator中的算法进行比较.
 
## 2021.8.6
### Progress
原来整个7月都没更新啊，不过也是因为7月初实现了两个算法之后就开始跑实验，然后去南京，回来就在写论文了，然后一直在写论文和跑实验，本质上没有什么特别新的东西...目前论文基本写完了，重新开始更新进展吧.

#### 1. 论文：
* 第六章基本写完了（一个初稿），主要是对SDBA构造co-deterministic DAGs，再基于co-deterministic DAGs构造补自动机的NSBC算法，最后还有一个从SDBA转换到DRA的算法（Determinization）.

#### 2.实验：
* 根据Andrea的结果来看效果一般，有一点优势，但不是“outstanding, overwhelming”...可能和benchmark的选取有关吧.

### planning
#### 1.论文
* 尽快写完投稿，如果实验效果没有特别好的话可能选一个理论一点的期刊投稿.
#### 2.硬件验证：开始学习一些硬件验证相关的内容：
* RISC-V指令集，
* Chisel语言，
* 硬件形式化验证，
* LLVM IR编译器验证（？）
#### 3.读论文
* 读CAV文章，
* 读principal of program analysis...(已经退群了还要讲吗)

