---
layout: post-custom
title: "词汇本/术语表"
---

#### vocabulary
[vəˈkæbjəleri]
- n. （*某一语言的*）词汇；（*某个学科的*）术语；（*音乐、美术等领域的*）表现形式

#### Fault Tolerance
- n. 容错性

> 记忆方法：错误（被）吞了

##### tolerance
[tɑːlərəns]
- n. 容忍；忍耐力；耐药力

#### RAG
- Retrieval-Augmented Generation
  - n. 检索增强生成：在自然语言处理任务中，如问答和摘要生成等，通过检索相关的知识来辅助生成更准确、更符合上下文的结果。

> 记忆方法：
> - retry - 尝试
> - Aug - 八月是丰收的季节 （增强）

##### retrieve
- v. 找回；检索

#### agile
[ˈædʒ(ə)l]
- adj. 敏捷的；机灵的

> 记忆方法：敏捷模型的理念是 小步快跑（Sprint）、拥抱变化。轻文档、快速迭代，出bug会容易 **挨揍**。

#### OOM（面向对象方法）的特点

> 记忆方法：**EP-AI**，现在到AI这一集了。

##### abstraction
- n. 抽象
- 提取关键特征，忽略非本质的细节。
- **实现方式**：抽象类 / 接口 定义规范

##### inheritance
- n. 继承
- 子类可以继承父类的属性和方法
- **代码复用**：避免重复写代码
- **层次化设计**：继承关系可以建立层次结构（*但也不要过度使用*）

##### encapsulation
[ɪnˌkæpsjuˈleɪʃ(ə)n]
- n. 包装；封装
- 将数据（*属性*）和操作数据的方式（*方法*）封装到对象里，隐藏内部实现细节。
- **访问控制**、**降低耦合**

> 记忆方法：`en-`（使处于...境地） + `capsule`（胶囊） => 包装。

##### polymorphism
[ˌpɑːlɪˈmɔːrˌfɪzəm]
- n. 多态性；多形性
- 不同对象对同一接口（*方法*）有不同的实现
- **表现形式**：
  - 编译时多态：方法重写（Overload）———— 同一类中 方法名相同 但 参数不同
  - 运行时多态：方法重载（Override）———— 子类重新定义父类中 同名、同参数 的方法，实现不同功能。
- **提高代码拓展性**，支持开闭原则

> 记忆方法：怕你墨菲定律，所以不同对象对同一消息（方法调用）可能做出不同的响应（实现）。

#### 边缘计算的特性-CROSS
##### Consitency
- n. 一致性；稳定性

##### Realtime
- n. 实时；适时
- adj. 实时的；适时的

##### data Optimization
- n. 数据优化

##### Security
- n. 安全性

##### Smart
- adj. 敏捷的；明智的；智能的

#### metric
[ˈmetrɪk]
- adj. 格律诗的
- n. 度量；格律；衡量标准

#### matrix
[ˈmeɪtrɪks]
- n. 矩阵；线路网

#### 架构权衡分析法（ATAM）

> Architecture Tradeoff Analysis Method

由SAAS发展而来，主要针对的质量属性是：**性能**、**可用性**、**安全性**、**可修改性**

##### performance
- n. 性能；表现；表演；工作情况；

##### usability
- n. 可用性

##### security
- n. 安全性

##### modifiability / changeability
- n. 可修改性


#### persistence
- n. 持久化

#### scale
- n. 规模
- v. （*按比例*）放大或缩小

##### scaling
- n. 缩放比例

##### scalability
- n. 可伸缩性

#### maintainability
- n. 可维护性

#### Reliability
- n. 可靠性

> 记忆方法：`rely`是依赖，可靠是稳定的依赖。所以你可靠，我依赖。

#### portability
- n. 可移植性；轻便；可携带性

#### redundancy
- n. 冗余；裁员，解雇；

#### refactoring
- n. 重构

#### snapshot
- n. 快照

#### sharding
- n. 分片

#### pessimistic / optimistic
[ˌpesɪˈmɪstɪk] / [ˌɑːptɪˈmɪstɪk]
- adj. 悲观的 / 乐观的

#### latency
- n. 延迟

#### jitter
- n. 抖动，试时延抖动

#### immutable
- adj. 不可变的

#### feedback
- n. 反馈意见

#### feasible
[ˈfiːzəb(ə)l]
- adj. 可行的；办得到的；可能发生的

#### 数据库事务的属性 ———— ACID

> **ACID**指的是数据库事务的**原子性**、**一致性**、**隔离性**、**持久性**

##### atomic
- adj. 原子的
- 一个事务内的操作是要么全做，要么全不做，不能部分做。

##### consistency
- n. 一致性
- 事务的变化是从 一个一致性状态 到 另一个一致性状态

##### isolation
[ˌaɪsəˈleɪʃn]
- n. 隔离；孤立
- 正在执行的事务与其他事务是隔离的，不能相互影响

##### durability
- n. 持久性；耐用性
- 事务一经提交不可改变

#### SDK
- 软件开发工具包（Software Development Kit）

