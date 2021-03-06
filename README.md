# Weekly

Weekly progress and planning.

## 2021.6.9

### Progress

#### 1. Lasso Ranker集成到工具，对SMACK生成Boogie语句进行转换，满足Lasso Ranker格式

#### 2. 读LTL2BA论文([***Paper***](https://doi.org/10.1007/978-3-642-28756-5_8), [***Slides***](https://github.com/fengwz17/Paper-List/blob/master/6.9_notated.pdf))，相关知识，难点

* Very weak Alternating Automata (VWAA)：注意到weak alternating automata表达能力与NBA是相同的，对于very weak且接受条件为co-Büchi的情况，其表达能力目前还不太情况..

* Alternating formula：本文针对性地对absolutely liveness做了优化（本文主要优化是用X\varphi替换\varphi），我们可以考虑对stable和fairness进行优化.

* VWAA to genaralized Büchi automata：没太理解清楚这个accepting transition的定义..

* Good for MDP?

### Planning

#### 1. 读rank-based与slice-based取补算法

#### 2. Lasso Ranker

#### 3. Spot调研

* 如何调用自动机库.

* 如何在Spot中实现取补算法.

## 2021.6.16

### Progress

#### 1. Lasso Ranker集成到工具，对SMACK生成Boogie语句进行转换，满足Lasso Ranker格式

* 还没做完，但是知道了SMACK生成的Boogie语句处理四则运算等操作时全都是以函数调用形式实现的，后面需要调用相应接口函数继续处理assign语句.

#### 2. 读论文，学习rank-based与slice-based的Finitely ambiguity Büchi automata取补算法

* 把握文章的主要脉络，要能脱稿讲清楚.
* 什么是FANBWs?
* FANBWs accepting DAGs的separate levels.
* Co-deterministic DAGs.
* Nonaccepting co-deterministic DAGs的stable level.
* Rank-based.
* Slice-based.

### Planning

#### 1. 读文章Complementing Semi-deterministic Büchi Automata，主要学习NCSB算法

* 类比slice-based取补的NCB算法.

#### 2. Spot中实现

* 参看NCSB算法的实现. ([Seminator](https://github.com/mklokocka/seminator)).

#### 3. LassoRanker

## 2021.6.23

### Progress

#### 1. 读论文[***TACAS'16***](https://doi.org/10.1007/978-3-662-49674-9_49)，学习semi-deterministic Büchi automata取补的NCSB算法，结合[Seminator](https://github.com/mklokocka/seminator)和spot代码理解

#### 2. 基于[Seminator](https://github.com/mklokocka/seminator)实现了对unambiguity Büchi automata取补的Slice-based算法的框架

* Reduced transition写的有问题，需要进行修改，在计算N'时保存map，并记录边的accepting信息，在计算C'的时候用前面记录的map替代原来自动机的transition.

### Planning

#### 实现Slice-based算法，进行实验

## 2021.6.30

### Progress

#### 1. 代码实现

* 基于seminator和spot提供的自动机库和接口等实现了GandALF文章中的NCB算法（一种对unambiguous \buchi automata取补的slice-based的算法）.
* 实现了李老师提出的一个对semi-deterministic automata取补的新算法.

#### 2. 实验结果

* 用150个ltl公式生成相应自动机跑了实验，输入unambiguous自动机，转为半确定自动机，分别用seminator中的取补算法和NCB算法，semi自动机取补新算法进行实验，实现的NCB算法结果正确，semi取补新算法有两个样例不对；
* 且目前实现的算法生成补自动机状态数普遍较大.

### Planning

#### 1. 找出semi取补新算法测试不对的问题，将其调试正确

#### 2. 实现上做一些优化，减小状态数

#### 3. 跑更多例子，记录运行时间和状态数，和spot，seminator中的算法进行比较

## 2021.8.6

### Progress

原来整个7月都没更新啊，不过也是因为7月初实现了两个算法之后就开始跑实验，然后去南京，回来就在写论文了，然后一直在写论文和跑实验，本质上没有什么特别新的东西...目前论文基本写完了，重新开始更新进展吧.

#### 1. 论文

* 第六章基本写完了（一个初稿），主要是对SDBA构造co-deterministic DAGs，再基于co-deterministic DAGs构造补自动机的NSBC算法，最后还有一个从SDBA转换到DRA的算法（Determinization）.

#### 2.实验

* 根据Andrea的结果来看效果一般，有一点优势，但不是“outstanding, overwhelming”...可能和benchmark的选取有关吧.

### planning

#### 1.论文

* 尽快写完投稿，如果实验效果没有特别好的话可能选一个理论一点的期刊投稿.

#### 2.硬件验证：开始学习一些硬件验证相关的内容

* RISC-V指令集，
* Chisel语言，
* 硬件形式化验证，
* LLVM IR编译器验证（？）

#### 3.读论文

* 读CAV文章，
* 读principal of program analysis...(已经退群了还要讲吗)

## 2021.10.19

### Progress

* TACAS投稿,
* 开始看NutShell源代码.

### planning

#### 1. 自动机

* 和Andrea完成TACAS artifact提交，
* 11月期刊投稿，
* 后面考虑优化COLA中确定化的算法，可能先主要让python jupyter能用.

#### 2. 硬件验证

* 看NutShell源码，
* 看chisel book第十二章，
* 看sail中生成SMT后端的代码和CAV文章.

## 2022.2.16

### Discussion

* 尝试pono后端使用不同求解器，发现出问题的地方；
* 整理pono：从编译到代码理解，是不是使用了抽象技术，加速了求解，但造成某些错误无法发现；
* 如何提升scalability：1）从Chisel到btor的转化是否丢失了某些结构信息；2）pono中从迁移系统到编码smt公式是否丢失了某些信息？如果额外编码上这些程序，或处理器设计带来的信息，看能不能加速求解（类比贺飞老师论文程序结构信息），如bool变量的赋值；
* 模型检测算法本身：bmc（处理器设计的结构信息encodeing进去加速，帮助求解），pono等能否继续优化，针对具体问题定制化算法

### Planning

* sail:发邮件
* Z3网页版
* pono，model checking算法深入了解
* 期刊文章

## 2022.4.2

### Progress

* Studying pono IC3IA source code

### Planning

* Try to improve pono IC3IA: combine IA with UF

## 4.6

### Todo

* 看pono-IC3IA代码
* 詹博华老师讨论班：能否在pono中类似avr实现启发式算法，unsat core最小化？
* 吴老师：读文章 1.在C中实现了一个reference model，然后生成smt 文件）； 2.ARM指令集一致性验证
* refine过程加UF：如何增加新谓词，add(a,b) = add(b,a), if a = b, add(a,c) = add(b,c)
* inductive_generalization：去掉一些clause中的literal，其中reduced unsat core考虑如何写代码

## 4.11

### Todo

* Minimal unsat core
* EUF
* ARM ISA-Formal paper
* 并行IC3：做block时如何并行？实现到word-level IC3

## 4.13

### Progress

* 需要看AVR thesis的第三章wIC3+EA技术
* Mufan: avr中reach_simulate.cpp部分fetch_failure_condition
* 关于pono中使用unsat core：还没有太清楚如何实现，看到ic3base.cpp中，IC3Base::rel_ind_check函数内有如下代码：

```
 // Use unsat core to get cheap generalization
 UnorderedTermSet core;
 solver_->get_unsat_assumptions(core);
 assert(core.size());
```

* 而ic3base.cpp的IC3Base::inductive_generalization部分有注释

```
TODO use unsat core reducer
```

* 需要考虑如何增加unsat core reducer，注意到ic3base.h有定义reducer_，但似乎没有使用，需要考虑如何利用reducer_：

```
smt::UnsatCoreReducer reducer_;
```

## 4.19

### tomasulo算法相关

* ROB继续看；
* 果壳中的具体实现；
* McMilan验证：Verfication of an Implementation of Tomasulo's Algorithm by Compositional Model Checking.

### model checking算法

* pono和avr算法；
* pono中怎么实现一些优化（工程）.

## 5.9

### PDR下近似？

* PROGRESS对blocked cubes会清空所有frames
* 如何对PDR做下近似，做类似PROGRESS过程中保留frames
* PDR的条件需要修改，类似有inv增长，每次都是下近似，可能从找错的角度会好一些
* 对偶版本PDR

## 5.23

### Progress

* 实现了一个简单版本的下近似算法。

### TODO

* 能否考虑提出一个方法对bit长度进行抽象，从32位到8位得到的counterexample也是32位情况下。

* unsat core和bitvector实现，bitvector：

  1) bit blasting, 直接split bitvector variables;

  2) 做抽象？

* 和PROGRESS找错对比，测试benchmark。

* under-approximation和over-approximation (IC3)如何结合。

* 如何做模型抽象。

## 5.30

### Progress

* bit-vector 算法实现中，暂时还有些问题，思考讨论了unsat-core部分的算法。

### TODO

* 实现bit-vector 算法，跑benchmark对比看实验效果。

## 6.10

### Progress

* 还在实现Li老师的generate算法，不知道为什么有问题，非常奇怪。
* 在看CAR算法和EveryThingAboutGeneralize文章。

### Plan

* 本周实现generalize算法。
* 尽量把文章重点部分看完。
* 跑一些实验。
* 思考或者实验对比今天讨论的Reach和IC3dual算法。

## 6.14

### TODO

* act实现。
* 深度优先实现。
* DualIC3尽量实现。

## 6.27

### Plan

* 整理前后向结合的算法，并实现。

* 调研QBF unsat core工具。
