# Weekly
Weekly progress and planning.

## 2021.6.9
### Progress 

1) Lasso Ranker集成到工具，对SMACK生成Boogie语句进行转换，满足Lasso Ranker格式.

2) 读LTL2BA论文([***Paper***](https://doi.org/10.1007/978-3-642-28756-5_8), [***Slides***](https://github.com/fengwz17/Paper-List/blob/master/6.9_notated.pdf))，相关知识，难点：

* Very weak Alternating Automata (VWAA)：注意到weak alternating automata表达能力与NBA是相同的，对于very weak且接受条件为co-Büchi的情况，其表达能力目前还不太情况..

* Alternating formula：本文针对性地对absolutely liveness做了优化（本文主要优化是用X\varphi替换\varphi），我们可以考虑对stable和fairness进行优化.

* VWAA to genaralized Büchi automata：没太理解清楚这个accepting transition的定义..

* Good for MDP?

### Planning

1) 读rank-based与slice-based取补算法.

2) Lasso Ranker.

3) Spot调研.

* 如何调用自动机库.

* 如何在Spot中实现取补算法.
 
