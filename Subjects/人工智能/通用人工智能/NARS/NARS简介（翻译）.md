# 智力逻辑模型——NARS简介



[*裴王*](http://www.cis.temple.edu/~pwang/)

 

[NARS](http://sites.google.com/site/narswang/)（非公理推理系统）是一个旨在构建通用智能系统的项目，即“思维机器”（也称为“[AGI](http://www.cis.temple.edu/~pwang/Writing/AGI-Intro.html)”），该机器遵循与人类大脑相同的原则，并可以解决各个领域的问题。

研究成果包括[智能理论](http://www.cis.temple.edu/~pwang/GTI-book/)、基于该理论[的智能形式模型](http://www.worldscientific.com/worldscibooks/10.1142/8665)和该模型的[计算机实现](http://www.cis.temple.edu/~pwang/demos.html)。

 

## 1. 主要设计决策

### 1.1. 目标：智力为原则

NARS的设计是基于这样一种信念，即[智能的本质是*适应环境*的原则*，同时在知识和资源不足的情况下工作*](http://www.cis.temple.edu/~pwang/Publication/AI_Definitions.pdf)。因此，智能系统应该依靠有限的处理能力，实时工作，对意外任务开放，并借鉴经验。

这个工作定义将“情报”解释为“[相对理性](http://www.worldscinet.com/ijmc/03/0301/S1793843011000686.html)”的一种形式，因为结论的有效性是根据目前系统的可用知识和资源来评估的，而不是根据客观现实或一些绝对标准。即使系统为给定问题提供了解决方案，系统仍然*没有足够的知识和资源*来解决这个问题，因为如果出现新证据或更多的处理时间，它可能会改变其解决方案。

这种智能的工作定义与我们对智能的总体理解一致，也赋予了人工智能领域一个适当的身份，因为这样定义，人工智能与计算机科学、认知心理学和其他相关领域明显不同。

### 1.2. 策略：一个多层推理系统

为了在计算机中实现这种形式的智能，NARS采取[*统一*的方法](http://www.cis.temple.edu/~pwang/Writing/AGI-Intro.html)，即系统依赖于单一的核心技术来执行各种认知功能和解决各种问题。这种方法的优点是简单和一致。系统在执行特定任务时，仍然可以使用其他技术作为插件工具来提高其性能。

NARS是在*推理系统的*框架下构建的，有*逻辑*部分和*控制*部分。前者由一种*形式*的知识表示*语言*、该语言的*语义理论*和一组*推理规则*组成；后者由*记忆*结构和*控制机制组成*。

推理框架的优点是与领域无关，并结合了单个推理步骤的合理性，以及以上下文敏感的方式在运行时将这些步骤链接在一起的灵活性。

为了使极其复杂的设计过程易于处理，NARS被设计成层，每个新层都扩展了语法规则和推理规则的集合，并在内存/控制机制中添加细节。

### 1.3. 技巧：一种非轴心推理系统

NARS与传统的推理系统有本质区别，主要是因为它假设知识和资源不足。*数学逻辑*来自数学中定理证明的研究，领域知识被公理总结，推理规则是保真，推理过程的资源成本被忽视，只要它是有限的。NARS的逻辑被称为“非公理逻辑”（NAL），因为它处理的知识（作为前提或结论）都不能被视为“公理”，就像固定的真值一样。相反，系统的信念是对系统经验的总结，并且总是可修改的。

在NARS中，“术语”命名了一个“概念”，代表系统体验中的循环模式，而“语句”表示一个术语替换为另一个术语。每个陈述在某种程度上都是“真实的”，表明该陈述从现有证据中获得的证据支持。推理规则指定如何从某些现有语句导出新语句。系统的存储和控制机制试图通过根据系统的经验和当前上下文动态分配资源，以最有效的方式使用系统的时空资源。这里简要概述了NARS的整体架构和工作周期。

NARS适应其经验，因此处于位置并体现。其信仰总结了系统的经验（而不是描述它本身的世界），其概念代表了经验中的模式（而不是表示世界上的对象）。其推理规则是*有效的*，因为每个结论都得到了前提提供的证据的支持（而不是因为它们从绝对真理中得出绝对真理）。系统是*理性*的，因为它的结论是系统在当前知识和资源限制下所能找到的最佳结果（而不是因为它们总是绝对正确或最佳的）。

 

## 2. 语言和逻辑

NARS的逻辑部分是*NAL*（非公理逻辑），它定义在形式语言*Narsese*上。NAL是多层渐进式设计。在每一层上，NAL和Narsese都被扩展为具有更高的表达力、更丰富的语义和更大的推理规则集，从而增加系统的智能。

为了为NAL奠定坚实的语义基础，首先介绍了遗传逻辑IL。这种逻辑使用*范畴语言*、*基于经验的语义*和一些*三段论推理规则*。它描述了如何将一个术语与另一个术语联系起来的*继承*系法（或其变体）形成语句，以及该关系如何从给定语句过渡到派生语句。由于IL拥有足够的知识和资源，它不是非轴心法的，而是通过指定其边界条件来帮助设计NAL。在每个层，语法规则和推理规则的扩展首先发生在IL中，然后在NAL中进一步扩展结果。

现将各层的主要内容简要总结如下：

- **[NAL-1:]**原子项和*继承*语句的推断，其中语句可能同时有肯定和否定的证据，并且需要考虑未来证据的影响。规则包括*扣除*、*绑架、归纳、修改、选择*等。
- **[NAL-2：]** 引入了继承系法的变体，包括*相似性*、*实例*和*属性*。新的推理规则包括*比较、类比*和*相似*。此外，术语可以表示由其唯一实例或属性定义的*集合*。
- **[NAL-3:]**复合项可以通过取现有项的*扩展*（实例）或*内涵（*属性）的*交集、联合*或*差*来导出。推理规则根据系统体验中的模式合成新术语。
- **[NAL-4:]**使用术语运算符乘*积*和*图像*，NAL被扩展为涵盖不能直接用作系词的术语之间的任意关系。这种关系的意义是由系统的经验决定的，而不是固定和内置的。
- **[NAL-5:]**当一个*语句*作为*术语时*，NAL可以对语句表示，也可以对此类“高阶语句”进行推断。在逻辑中添加两个高阶系词，即*蕴涵*和*等价*，以表达语句之间的派生关系。
- **[NAL-6:]** *可变术语*可以用作其他术语的符号。在推理规则中，变量项可以引入、统一或消除（即实例化）。利用变量项，系统可以对抽象符号进行假设推理，从而作为任意推理系统的元逻辑。
- **[NAL-7:]***事件*是具有时间属性的语句，针对另一个事件指定。在时间推理中，对前提中的逻辑信息和时间信息进行处理，以得出预测或解释。
- **[NAL-8 : ]** *操作*是系统通过执行主机系统中的某些程序，可以直接实现的事件。目标是系统希望实现的事件。通过程序推理，系统试图使用操作来实现目标。
- **[NAL-9 : ]** 当程序推理所涉及的操作是NARS的内部操作时，就形成了一个自我参照循环，赋予系统自我意识和自我控制的能力。其他相关话题包括情感和意识。

粗略地说，在上述NARS层次结构中，第1层在[术语逻辑](http://en.wikipedia.org/wiki/Term_logic)的框架下建立了最简单的非轴逻辑，从几种[非经典逻辑](http://en.wikipedia.org/wiki/Non-classical_logic)（包括[归纳逻辑](http://plato.stanford.edu/entries/logic-inductive/)、[概率逻辑](http://plato.stanford.edu/entries/logic-probability/)、[模糊逻辑](http://plato.stanford.edu/entries/logic-fuzzy/)、[相关性逻辑](http://plato.stanford.edu/entries/logic-relevance/)、[非单调逻辑](http://plato.stanford.edu/entries/logic-nonmonotonic/)等）[中](http://plato.stanford.edu/entries/logic-inductive/)汲取了教训。;第2-4层从[集合论中](http://plato.stanford.edu/entries/set-theory/)适应思想，以指定复合项;第5、6层分别介绍[命题逻辑](http://en.wikipedia.org/wiki/Propositional_logic)和[谓词逻辑](http://en.wikipedia.org/wiki/Predicate_logic)的某些功能;第7-9层借用[逻辑编程](http://en.wikipedia.org/wiki/Logic_programming)的思想,将推理框架扩展到过程知识和传感力学机制。然而，作为一个整体，NAL不属于任何上述逻辑系统。

NARS中的推理过程统一地执行许多认知功能，这些功能传统上被研究为具有不同机制的独立过程，如学习、感知、计划、预测、记忆、解决问题、决策等。

 

## 3. 控制和实施

### 3.1. 任务、信念和概念

在最简单的情况下，NARS在纳尔塞语中与环境通信。系统的体验由输入句子流组成，每个句子都是需要处理*的任务*。一项任务可以是需要吸收的知识，需要回答的问题，也可以是需要实现的目标。作为一个实时系统，NARS随时接受新任务，包含任何内容和时间请求。

任务通过在推理过程中与系统的*信念*相互作用来处理。信仰是从以前的经验中总结的知识。向前推理除了直接解决问题和目标外，还衍生出新的信念，后向推理衍生出新的问题和目标。

根据任务和信念中出现的术语，任务和信念被分组为概念。*概念*是由术语命名的实体，指与该术语直接相关的所有任务和信念。

### 3.2. 动态资源分配

在任何时候，在NARS中，通常有许多任务同时处理，优先级不同。在每个推理步骤中，根据优先级值选择所涉及的概念、任务和信念，这些因素总结了许多因素，并不时进行调整。系统根据过去的经验判断，在任务和信仰之间动态分配时空资源，以达到高预期的整体效率。

NARS根据目前可用的知识和资源，以逐案的方式解决每个问题，而不是遵循预先确定的算法。同样，NARS正在解决的问题没有固定的计算复杂性，但可能会因情况而异。

### 3.3. 计算机实现

NARS可以使用可用的计算机硬件和软件完全实现。

[NARS的](http://www.cis.temple.edu/~pwang/demos.html)几个[原型](http://www.cis.temple.edu/~pwang/demos.html)已经实现，NARS目前[是一个开源项目](http://code.google.com/p/open-nars/)，其中逻辑部分大部分是实现的，控制部分处于初步形式。目前的开发重点是逻辑的完成，特别是顶部（7-9）层。

还在考虑的话题包括控制部分的细化、广泛的测试、知识获取、系统增强或定制以及实际应用。

 

## 关于NARS的参考文献

简单介绍：

- [为了实现统一的人工智能](http://www.cis.temple.edu/~pwang/Publication/unifiedAI.pdf)，AAAI关于通过综合研究和系统实现人类级智能的秋季研讨会，第83-90页，华盛顿特区，2004年10月
- [从NARS到思维机器](http://www.cis.temple.edu/~pwang/Publication/roadmap.pdf)，人工智能进步，第75-93页，IOS出版社，阿姆斯特丹，2007年

综合描述：

- [刚性灵活性：智能逻辑](http://www.springer.com/west/home/computer/artificial?SGWID=4-147-22-173659733-0)，Springer，2006年
- [非公理逻辑：智能推理模型](http://www.worldscientific.com/worldscibooks/10.1142/8665)，世界科学，2013年

更多信息：

- [情报通论](http://www.cis.temple.edu/~pwang/GTI-book/)
- [关于NARS的出版物](http://www.cis.temple.edu/~pwang/papers.html)
- [NARS的演示](http://www.cis.temple.edu/~pwang/demos.html)
- [NARS作为一个开源项目](http://code.google.com/p/open-nars/)
- [NARS讨论小组](http://groups.google.com/group/open-nars)

-   http://groups.google.com/group/open-nars)