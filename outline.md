
• 我建议把这门课组织成一条清晰的历史与技术主线：

  > 证明检查器 → PCP 定理 → 近似困难性 → 并行重复与 Gap Amplification → UGC → 分析、几何与 SDP 后果 → 2-to-2 Games → 2026 年“完整 UGC 证明”的审
  > 查。

  课程暂名：

  # 《从 PCP 定理到 Unique Games：近似困难性的证明、算法与几何》

  默认每讲 90–120 分钟，面向有离散数学、算法和基础复杂性理论背景的读者。教材不会把 2026 年论文直接当作已确立事实，而是把它作为最后一讲的待验证重大
  宣称来分析。

  ## 总体结构

  ### 第一部分：PCP 与近似困难性的基础

  Lecture 1：为什么 PCP 和 UGC 重要

  核心问题：

  - 什么是 NP、NP-hardness、近似算法与 Gap Problem
  - 为什么“判定一个解是否存在”会转化成“判断一个解是否接近最优”
  - PCP、两证明者游戏、Label Cover、CSP 之间的关系
  - 整条研究路线的历史地图

  主要材料：

  - survey_Khot_UGC-survey.pdf
  - README 中关于 MIP、FGLSS、Feige–Lovász 的背景
  - 补充介绍未收录的 FGLSS 与 Khot 2002 原始 UGC 论文

  目标：读者能够理解后面所有论文试图解决的共同问题。

  ———

  Lecture 2：两证明者一轮游戏、Label Cover 与 PCP 的语言

  内容：

  - 2P1R 游戏的形式定义
  - completeness、soundness、value
  - Unique Game、一般 Label Cover、CSP 的统一表示
  - 从 PCP verifier 到约束图
  - FGLSS 范式：PCP 如何产生 Clique 等优化问题的困难性

  重点是建立以后反复使用的记号：

  [
  G=(V,E),\qquad \pi_{uv}:\Sigma_u\to\Sigma_v,
  ]

  以及

  [
  \operatorname{val}(G)=
  \max_{\ell:V\to\Sigma}
  \Pr_{(u,v)\in E}[\pi_{uv}(\ell(u))=\ell(v)].
  ]

  ———

  Lecture 3：PCP 定理的陈述与 Arora–Safra 路线

  内容：

  - PCP 定理的标准形式

  # [
  \mathrm{NP}

  \mathrm{PCP}[O(\log n),O(1)]
  ]

  - 证明系统的完备性与可靠性
  - 低次多项式编码、随机抽查与局部可验证性
  - Arora–Safra 证明的整体结构
  - 为什么递归编码能够把“全局正确性”变成“局部可检查性”

  主要材料：

  - 1998_Arora-Safra_PCP.pdf

  这里不追求逐行复现所有技术细节，而是严格解释证明中每一个模块的输入、输出和参数变化。

  ———

  Lecture 4：ALMSS 证明、代数化与 PCP 到不可近似性

  内容：

  - ALMSS 的代数化路线
  - 低次测试与多项式一致性
  - PCP composition
  - 从 PCP 定理到 Max-3SAT、Max-Clique 等不可近似性
  - Arora–Safra 与 ALMSS 两种证明的比较

  主要材料：

  - 1998_ALMSS_PCP-hardness.pdf

  本讲会明确区分：

  1. PCP 定理本身；
  2. PCP 到 Label Cover 的转换；
  3. Label Cover 到具体优化问题的归约。

  ———

  ### 第二部分：可靠性放大与最优不可近似性

  Lecture 5：Raz 并行重复定理

  内容：

  - 游戏的并行重复 (G^{\otimes k})
  - 为什么接受概率不是简单地独立相乘
  - Raz 定理的定性和定量形式
  - 依赖性、条件分布与信息论直觉
  - 并行重复在 PCP 归约中的作用

  主要材料：

  - 1995_Raz_parallel-repetition.pdf

  核心结论的教学版本是：

  若原游戏满足值小于 (1-\varepsilon)，则重复 (k) 次后接受概率会随 (k) 快速下降。

  ———

  Lecture 6：Dinur 的 Gap Amplification

  内容：

  - 约束图与 unsatisfiability gap
  - 图幂、局部检验与扩张图
  - Gap amplification 的一个循环步骤
  - 为什么重复 (O(\log n)) 次能够把很小的 gap 放大到常数
  - Dinur 的组合证明与早期代数 PCP 证明的关系

  主要材料：

  - 2006_Dinur_PCP-gap-amplification.pdf

  这是全课程中最适合完整讲解证明机制的一讲。教材可以给出一个简化版放大引理，再解释真实证明如何处理尺寸、度数和局部一致性问题。

  ———

  Lecture 7：Håstad 的最优不可近似性

  内容：

  - 3-bit PCP
  - 线性约束、非线性约束与 dictatorship test
  - Max-3SAT 的 (8/7) 阈值
  - Max-3LIN 的 (1/2+\varepsilon) 阈值
  - Clique 的 (n^{1-\varepsilon}) 困难性
  - “完备性接近 1、可靠性达到最优”意味着什么

  主要材料：

  - 2001_Hastad_optimal-inapproximability.pdf

  本讲也会解释为什么 Håstad 的结果把研究重点从一般 PCP 推向了更加结构化的 Unique Games。

  ———

  ### 第三部分：UGC 及其算法、分析和几何后果

  Lecture 8：Unique Games Conjecture 的提出与形式化

  内容：

  - Unique Constraint 的定义
  - UGC 的标准参数形式
  - UGC 与一般 PCP 的区别
  - 为什么 unique projection 是一个重要的结构限制
  - Khot 2002 论文的历史动机
  - UGC 作为近似算法中的“中间难题”

  主要材料：

  - survey_Khot_UGC-survey.pdf
  - README 中关于 Khot 2002 的说明

  需要特别强调 UGC 的逻辑形式：它不是“某个具体问题很难”，而是一个关于一整族 Unique Games 实例的复杂性猜想。

  ———

  Lecture 9：KKMO、噪声稳定性与 Max-Cut

  内容：

  - Max-Cut 与 Goemans–Williamson 算法
  - Gaussian noise stability
  - Majority is Stablest
  - 影响函数与布尔函数的噪声分析
  - UGC 如何推出 Goemans–Williamson 阈值的最优性

  主要材料：

  - 2004_KKMO_MaxCut.pdf

  核心结论：

  在 UGC 成立的前提下，Max-Cut 不存在优于 Goemans–Williamson 比率的多项式时间近似算法，除非允许任意小的误差。

  本讲会把“组合归约”和“高维分析”之间的对应关系讲清楚。

  ———

  Lecture 10：Khot–Vishnoi、积分间隙与负型度量

  内容：

  - Unique Games 与 SDP relaxation
  - 积分解与半正定规划
  - Khot–Vishnoi 实例
  - 负型度量
  - (\ell_1) 嵌入问题
  - UGC、近似算法和度量几何之间的联系

  主要材料：

  - 2005_Khot-Vishnoi_UGC-integrality-gap.pdf

  目标是让读者理解：UGC 的影响并不只限于复杂性理论，它还解释了许多 SDP 和度量嵌入算法为什么会出现不可突破的间隙。

  ———

  Lecture 11：Raghavendra 定理与“每个 CSP 的最优算法”

  内容：

  - CSP 的统一表示
  - Basic SDP / 基本半正定规划
  - integrality gap 的定义
  - SDP rounding
  - Raghavendra 的条件最优性框架
  - 在 UGC 下，为什么基本 SDP 的 integrality gap 等于 CSP 的最优近似阈值

  主要材料：

  - 2008_Raghavendra_every-CSP.pdf

  本讲会区分三个层次：

  1. 一个算法的近似保证；
  2. 某个 SDP relaxation 的积分间隙；
  3. 在 UGC 下的复杂性下界。

  ———

  Lecture 12：UGC 的算法反攻与分析型并行重复

  内容：

  - Arora–Barak–Steurer 的亚指数时间算法
  - threshold rank
  - small-set expansion
  - UGC 与 ETH 的关系
  - Dinur–Steurer 的分析型并行重复
  - 为什么并行重复既是硬度工具，也是算法分析工具

  主要材料：

  - 2010_Arora-Barak-Steurer_subexp-UG.pdf
  - 2014_Dinur-Steurer_parallel-repetition.pdf

  这一讲会呈现一个重要的张力：

  > UGC 若成立，许多问题在多项式时间内很难；但在亚指数时间内，实例的谱结构又可能被利用。

  ———

  ### 第四部分：2-to-2 Games 与 Grassmann 图

  Lecture 13：从 Unique Games 到 2-to-2 Games

  内容：

  - 2-to-1 与 2-to-2 约束的定义
  - 为什么 2-to-2 是 UGC 的“半个参数区间”
  - 2-to-2 约束如何拆成两个 Unique 约束
  - 3-LIN 到 2-to-2 Games 的归约思想
  - Grassmann 图和独立集问题
  - KMS 2017 的整体路线

  主要材料：

  - 2017_KMS_independent-sets-2to2.pdf
  - survey_Khot_2to2-exposition.pdf

  本讲会给出一个小规模的线性约束例子，帮助读者直观看到 3-LIN、2-to-2 和独立集之间的关系。

  ———

  Lecture 14：DKKMS 的 Subspace-vs-Subspace Agreement Test

  内容：

  - 子空间标签
  - Subspace-vs-Subspace agreement test
  - 局部一致性与全局一致性
  - 2-to-1 Games 与 Grassmann 图扩张之间的归约
  - “非扩张集结构假设”的精确定义
  - KMS 2017 与 DKKMS 2018 的分工

  主要材料：

  - 2018_DKKMS_towards-2to1.pdf
  - survey_Khot_2to2-exposition.pdf

  这一讲的重点不是记住所有 Grassmann 图参数，而是理解证明的逻辑形状：

  [
  \text{2-to-1/2-to-2 Games}
  \Longleftarrow
  \text{Grassmann 图中的扩张性质}.
  ]

  ———

  Lecture 15：Grassmann 图扩张与 Shortcode 图视角

  内容分两部分。

  第一部分：KMS 2018

  - Grassmann 图上的伪随机集
  - near-perfect expansion
  - 小集合扩张与伪随机性
  - 组合结构、谱方法和分析工具
  - 2-to-2 Games Conjecture 的收官逻辑

  第二部分：Barak–Kothari–Steurer 2019

  - Shortcode 图
  - Small-Set Expansion
  - 与 Grassmann 图假设的等价或对应关系
  - 为什么 shortcode 视角可能更适合继续研究完整 UGC

  主要材料：

  - 2018_KMS_Grassmann-near-perfect-expansion.pdf
  - 2019_Barak-Kothari-Steurer_shortcode.pdf
  - survey_Khot_2to2-exposition.pdf

  这是全课程技术密度最高的一讲。教材中会提供“主线证明图”和“技术附录”，避免让读者被长篇组合论证淹没。

  ———

  ### 第五部分：2026 年的完整 UGC 宣称与课程总结

  Lecture 16：从 2-to-2 到完整 UGC：如何审查一份重大证明宣称

  内容：

  - 2026_OpenAI_Unique-Games-Theorem.pdf 的正式主张
  - 它与经典 UGC 表述的逐项比较
  - 完备性、可靠性、归约复杂度和字母表大小
  - 从 2-to-2 Games 到完整 Unique Games 之间真正缺失的技术环节
  - 如何检查一个复杂性理论证明：
      - 参数是否闭合
      - 归约是否保持完备性
      - 可靠性是否真的下降
      - 多项式时间界是否成立
      - 是否出现循环使用待证明结论
      - 形式化代码究竟验证了哪些内容

  - 如果主张成立，它对 Max-Cut、Vertex Cover、Min-UnCut 等问题意味着什么
  - 如果主张不成立，最可能出现的逻辑断点在哪里

  主要材料：

  - 2026_OpenAI_Unique-Games-Theorem.pdf
  - 前面全部经典论文
  - 两篇综述作为交叉索引

  这一讲明确区分三种陈述：

  1. 已经被社区广泛验证的定理；
  2. 有完整论文但尚未被充分复核的结果；
  3. 仅由作者或机构单方面发布、仍待独立检查的证明宣称。

  因此不会在教材中写成“UGC 已被证明”，而会准确写成：

  > 该论文宣称给出了完整 UGC 的证明；截至课程编写时，其正确性仍需独立复核。

  ## 每讲统一的教材模板

  为了让教材既严密又适合自学，我建议每一讲固定采用以下结构：

  1. 本讲问题：先说明为什么需要这个概念。
  2. 直观图景：用小例子解释游戏、图、约束或测试。
  3. 形式定义：统一记号和参数。
  4. 核心定理：给出精确数学表述。
  5. 证明路线：说明每个引理负责什么。
  6. 完整证明或证明骨架：对核心基础定理展开，对特别长的论文给出严格路线图。
  7. ** worked example**：手算一个小实例。
  8. 常见误解：例如把 soundness 当成独立概率相乘。
  9. 练习题：基础题、证明题、论文阅读题各若干。
  10. 进一步阅读：标注主论文、综述和选读材料。

  ## 预计的 TeX 文件结构

  最终版本可以采用 ctexbook，结构大致如下：

  main.tex
  ├── preamble.tex
  ├── macros.tex
  ├── frontmatter/
  │   ├── notation.tex
  │   └── roadmap.tex
  ├── lectures/
  │   ├── lecture01.tex
  │   ├── lecture02.tex
  │   ├── ...
  │   └── lecture16.tex
  ├── appendices/
  │   ├── complexity.tex
  │   ├── probability.tex
  │   ├── Fourier.tex
  │   ├── SDP.tex
  │   └── Grassmann.tex
  └── references.bib

  每讲使用统一的 definition、theorem、lemma、example、exercise 和 warning 环境。关于 2026 年论文的内容会使用单独的“状态说明”框，明确标记哪些是已知
  定理、哪些是条件结果、哪些是尚未独立验证的宣称。

  这版大纲的核心取舍是：前 12 讲让读者真正掌握 PCP、UGC、分析和 SDP 的共同语言，后 4 讲再进入 2-to-2 和 Grassmann 图。这样最后一讲讨论 2026 年宣称
  时，读者已经有足够工具判断它究竟填补了哪一个缺口，而不会只是把“证明 UGC”当成一句口号。