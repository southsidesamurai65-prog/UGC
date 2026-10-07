# PCP / UGC 这条线：经典论文合集

本目录收集了 **Probabilistically Checkable Proofs（PCP 定理）→ Unique Games Conjecture（UGC）→ 2-to-2 Games → 2026 年 AI 宣称证明 UGC** 这一整条研究脉络中最核心的论文。
所有 PDF 放在 `papers/` 下，文件名格式为 `年份_作者_主题.pdf`。

> 说明：PCP 定理的论文块（Arora–Safra、ALMSS、Raz、Håstad）多为 1990s 的会议/期刊版，ACM/IEEE 原文有付费墙；这里尽量选用作者主页、ECCC、arXiv 等**开放获取**版本。个别经典（Feige–Lovász 1992、Khot STOC 2002）没有合法开放 PDF，仅在文末「未能收录」中列出引用。

---

## 一、发展史时间线

### 前史：交互式证明与「证明检查」的诞生（1990–1991）
- **Babai–Fortnow–Lund** 证明 MIP = NEXP，两证明者交互证明的威力远超 NP。
- **Feige–Lovász (STOC'92)** 把 **two-prover one-round games（2P1R）** 与 PCP / 近似难度联系起来，证明 MIP(2,1) = NEXPTIME，并首次把「游戏的近似值」当作困难性来源。这是整条线的游戏视角起点。
- **FGLSS (Feige–Goldwasser–Lovász–Safra–Szegedy, 1991/1996)** 给出 PCP 与最大团（Clique）近似难度之间的等价，确立了「PCP ⇒ 不可近似性」这一核心范式。

### 1992：PCP 定理
- **Arora–Safra** 与 **Arora–Lund–Motwani–Sudan–Szegedy（ALMSS）** 在同一年（FOCS'92）独立证明：
  \[
  \mathrm{NP} = \mathrm{PCP}\!\left[O(\log n),\, O(1)\right].
  \]
  即：NP 中的每个语言都有一个概率可验证证明，验证者只读常数个比特、用对数级随机比特，完备性为 1、可靠性为常数。
- 直接推论：**Max-3SAT、Max-Clique 等一大类优化问题存在常数因子近似难度**（除非 P = NP）。这就是「PCP 定理 = 近似困难性的基石」。

### 1995：并行重复定理
- **Raz, "A Parallel Repetition Theorem"**：证明 two-prover game 并行重复 k 次后，接受概率指数衰减。这给 label cover / 2P1R 提供了强可靠性归约，成为之后几乎所有 hardness 结果里那个「outer verifier」的核心部件。

### 1997/2001：Håstad 的最优不可近似性
- **Håstad** 给出 3-bit PCP（对每个声称的赋值读 3 个比特），得到 **Max-3SAT 的 8/7、Max-3LIN 的 1/2+ε、Clique 的 n^{1-ε}** 等一整套紧的不可近似性，其中很多结论此后二十年都无人能再改进（只能改常数）。

### 2002：UGC 被提出
- **Khot, "On the power of unique 2-prover 1-round games" (STOC'02)** 提出 **Unique Games Conjecture**：对任意 ε, δ > 0，存在足够大的字母表大小 k，使得区分「≥1−ε 可满足的 unique game」与「≤δ 可满足」是 NP-hard 的。
- 动机正是 above 的「many-to-one projection 屏障」：Håstad 之后的 hardness 卡在 2-query 上，UGC 提供了一种新的 outer verifier。
- 从这天起，**大量基本问题的紧近似阈值都被证明「在 UGC 下成立」**：Max-Cut、Vertex Cover、Sparsest Cut、Min-2SAT-Deletion、Coloring 等。UGC 于是成为近似算法领域最重要的猜想。

### 2004–2008：UGC 的黄金时代
- **Khot–Kindler–Mossel–O'Donnell (FOCS'04)**：用「噪声稳定性 / Majority is Stablest」证明 **UGC ⇒ Max-Cut 的最优阈值 GW ≈ 0.878**，第一次让人看到 UGC 能推出没它根本证不出的结果。
- **Khot–Vishnoi (FOCS'05)**：构造 UGC 的 integrality gap，并证明**负类型度量不能嵌入 ℓ₁**，推翻了 Goemans–Linial 猜想，是 UGC 与度量几何的经典交汇。
- **Dinur (STOC'06)**：给出 PCP 定理的**纯组合证明**（gap amplification / 图幂放大），不需要代数化技术。这是 PCP 定理的「第二生命」，也是后来 2-to-2 证明里 gap amplification 思想的源头。
- **Raghavendra (STOC'08)**：证明**在 UGC 下，每个 CSP 的最优近似比都等于一个自然 SDP（基本 SDP）的 integrality gap**。这基本「终结」了 CSP 近似算法的理论：UGC 若真，泛型 SDP 就是最优。

### 2010–2014：算法反攻与 UGC 的边界
- **Arora–Barak–Steurer (FOCS'10)**：给出 unique games 与 small-set expansion 的**亚指数时间算法**（exp(kn^ε)）。这说明 UGC 若成立，任何 hardness 归约必须有 exp(k n^{O(ε)}) 级别的膨胀；也把 UGC 与 ETH 联系起来。
- **Dinur–Steurer (STOC'14)**：用分析方法（而非组合的 Raz 方法）给出并行重复定理的另一个证明，成为后续 2-to-2 分析的关键工具。

### 2016–2019：2-to-2 Games Conjecture 被证明 —— UGC 的「一半」
2-to-2 是 UGC 的「宽松版」：每个约束的答案不是唯一对应，而是**一对二**（给定一端赋值，另一端恰有两个可行值）。把每个 2-to-2 约束拆成两个 unique 约束，就能得到 **「1/2-可满足情形的 UGC」**。因此 2-to-2 被证明 = 证明了 UGC 的半个参数区间。
- **Khot–Minzer–Safra (STOC'17)**：把 3-Lin 归约到 2-to-2 games，并指出只需证明 **Grassmann 图**上的一个组合假设（非扩张集的结构刻画），就能得到 independent set / Vertex Cover 的 √2 硬度。这是整条证明线的起点。
- **DKKMS：Dinur–Khot–Kindler–Minzer–Safra (STOC'18)**：给出 subspace-vs-subspace agreement test，把 2-to-1 / 2-to-2 猜想归约到 Grassmann 图上的「扩张假设」。
- **Khot–Minzer–Safra (FOCS'18)**：**证明上述扩张假设**（伪随机集在 Grassmann 图中近完美扩张），补上最后一块拼图，宣告（不完全完备性版本的）2-to-2 Games Conjecture 成立。论文后来发表于 Annals of Mathematics (2023)。
- **Barak–Kothari–Steurer (ITCS'19)**：用 **shortcode 图**重新表述，建立与原假设的等价并给出更清晰的证明路线。

### 2026：AI 宣称证明 UGC
- **OpenAI (2026-09-23)** 在 `openai/math` 仓库发布 *"The Unique Games Theorem"*，宣称**证明完整的 UGC**，并给出确定性多项式时间归约（3SAT 完备性任意接近 1、可靠性任意小），部分结果附 Lean 形式化。其余结论涉及 Max-Cut、Vertex Cover、Min-UnCut、directed FVST 的紧阈值。
- ⚠️ **重要提醒**：截至本合集整理时，这是 OpenAI 单方面发布的结果，**尚未经过独立审稿 / 社区复核**（仓库自述未完成 Lean 检查、审阅状态为 unchecked）。请把它当作「一个待验证的重大宣称」而非既成事实。它已收录在本目录，方便对照原始经典工作阅读。

---

## 二、收录论文一览（`papers/`）

### 奠基：PCP 定理与其后果
| 文件 | 引用 | 要点 |
|---|---|---|
| `1998_Arora-Safra_PCP.pdf` | Arora, Safra. *Probabilistic Checking of Proofs: A New Characterization of NP.* FOCS'92 / JACM 45(1):70–122, 1998. | PCP 定理的原始证明之一；引入递归编码 + 低次测试。证明 NP = PCP[log, O(1)]。 |
| `1998_ALMSS_PCP-hardness.pdf` | Arora, Lund, Motwani, Sudan, Szegedy. *Proof Verification and the Hardness of Approximation Problems.* FOCS'92 / JACM 45(3):501–555, 1998. | 另一条独立证明 PCP 定理的路线（代数化 + 递归编码），并直接给出 Max-3SAT 等的不可近似性。 |
| `1995_Raz_parallel-repetition.pdf` | Raz. *A Parallel Repetition Theorem.* STOC'95 / SICOMP 27(3):763–803, 1998. | 2P1R 游戏并行重复的可靠性指数衰减；后续 hardness 归约的通用 outer verifier。 |
| `2001_Hastad_optimal-inapproximability.pdf` | Håstad. *Some Optimal Inapproximability Results.* STOC'97 / JACM 48(4):798–859, 2001. | 3-bit PCP；Max-3SAT 8/7、Max-3LIN、Clique n^{1−ε} 等最优阈值。 |

### PCP 定理的「第二生命」与组合化
| 文件 | 引用 | 要点 |
|---|---|---|
| `2006_Dinur_PCP-gap-amplification.pdf` | Dinur. *The PCP Theorem by Gap Amplification.* STOC'06 / JACM 54(3):12, 2007. (ECCC TR05-046) | 纯组合证明：图幂放大 unsat 值，每次翻倍，log n 次后得到常数 gap。近代 PCP / gap amplification 的模板。 |
| `2014_Dinur-Steurer_parallel-repetition.pdf` | Dinur, Steurer. *Analytical Approach to Parallel Repetition.* STOC'14. | 用分析方法（和 Fourier / 扩张）重证并行重复，直接服务 2-to-2 的分析框架。 |

### UGC：提出、推论与算法
| 文件 | 引用 | 要点 |
|---|---|---|
| `2004_KKMO_MaxCut.pdf` | Khot, Kindler, Mossel, O'Donnell. *Optimal Inapproximability Results for MAX-CUT and Other 2-Variable CSPs?* FOCS'04 / SICOMP 37(1):319–357, 2007. (ECCC TR05-098) | 「Majority is Stablest」；UGC ⇒ Max-Cut 的 GW 阈值最优，UGC 首个标志性推论。 |
| `2005_Khot-Vishnoi_UGC-integrality-gap.pdf` | Khot, Vishnoi. *The Unique Games Conjecture, Integrality Gap for Cut Problems and Embeddability of Negative Type Metrics into ℓ₁.* FOCS'05. (arXiv:1305.4581) | UGC 的 integrality gap；负类型度量不可嵌入 ℓ₁，推翻 Goemans–Linial 猜想。 |
| `2008_Raghavendra_every-CSP.pdf` | Raghavendra. *Optimal Algorithms and Inapproximability Results for Every CSP?* STOC'08. | UGC ⇒ 每个 CSP 的最优近似 = 基本 SDP 的 integrality gap；CSP 近似理论的统一框架。 |
| `2010_Arora-Barak-Steurer_subexp-UG.pdf` | Arora, Barak, Steurer. *Subexponential Algorithms for Unique Games and Related Problems.* FOCS'10 / JACM 62(5):42, 2015. | UGC 与亚指数算法 / ETH 的张力；threshold-rank 图分解。算法阵营的代表。 |

### 2-to-2 Games：证明 UGC 的「一半」
| 文件 | 引用 | 要点 |
|---|---|---|
| `2017_KMS_independent-sets-2to2.pdf` | Khot, Minzer, Safra. *On Independent Sets, 2-to-2 Games, and Grassmann Graphs.* STOC'17. (Theory of Computing 21(10), 2025) | 系列开篇：3-Lin → 2-to-2 归约 + Grassmann 图组合假设；推出 Vertex Cover √2 硬度。 |
| `2018_DKKMS_towards-2to1.pdf` | Dinur, Khot, Kindler, Minzer, Safra. *Towards a Proof of the 2-to-1 Games Conjecture.* STOC'18. (Theory of Computing 21(11), 2025) | 第二篇：subspace-vs-subspace agreement，把猜想归约到 Grassmann 扩张假设。 |
| `2018_KMS_Grassmann-near-perfect-expansion.pdf` | Khot, Minzer, Safra. *Pseudorandom Sets in Grassmann Graph Have Near-Perfect Expansion.* FOCS'18 / Annals of Mathematics 198(1), 2023. (ECCC TR18-006) | **收官之作**：证明 Grassmann 扩张假设，完成 2-to-2 Games Conjecture。 |
| `2019_Barak-Kothari-Steurer_shortcode.pdf` | Barak, Kothari, Steurer. *Small-Set Expansion in Shortcode Graph and the 2-to-2 Conjecture.* ITCS'19. (arXiv:1804.08662) | 用 shortcode 图重述并等价化该假设，给出更可推广（可能通向完整 UGC）的视角。 |

### 综述
| 文件 | 引用 | 要点 |
|---|---|---|
| `survey_Khot_UGC-survey.pdf` | Khot. *On the Unique Games Conjecture.* CCC'10（综述）. | 作者本人对 UGC 及其与算法、Fourier 分析、几何联系的权威综述。 |
| `survey_Khot_2to2-exposition.pdf` | Khot. *On the Proof of the 2-to-2 Games Conjecture.* (2019 exposition). | 2-to-2 证明的高层导读，串起 KMS/DKKMS/BKS 四篇论文。 |

### 2026 AI 宣称
| 文件 | 引用 | 要点 |
|---|---|---|
| `2026_OpenAI_Unique-Games-Theorem.pdf` | OpenAI. *The Unique Games Theorem.* 2026-09-23. 仓库 <https://github.com/openai/math>（family 102）。 | **宣称**证明完整 UGC 与相关最优近似阈值。单方面发布，未经独立验证。 |

---

## 三、未能收录的经典（有付费墙 / 无合法开放 PDF）

以下三篇极为重要，但公开渠道找不到合法开放 PDF，故仅列引用：

1. **U. Feige, L. Lovász.** *Two-prover one-round proof systems: their power and their problems.* STOC 1992, pp. 733–744. DOI: `10.1145/129712.129783`. — 2P1R 游戏与 PCP 视角的起点。
2. **S. Khot.** *On the power of unique 2-prover 1-round games.* STOC 2002, pp. 767–775. DOI: `10.1145/509907.510017`. — **UGC 的原始论文**（其摘要与背景可在 Khot 的综述 `survey_Khot_UGC-survey.pdf` 中看到）。
3. **U. Feige, S. Goldwasser, L. Lovász, S. Safra, M. Szegedy.** *Interactive proofs and the hardness of approximating cliques.* JACM 43(2):268–292, 1996.（FGLSS）— PCP ⇒ Clique 近似难度。

---

## 四、推荐阅读顺序

**入门**：`survey_Khot_UGC-survey.pdf` → `2006_Dinur_PCP-gap-amplification.pdf`
**理解 PCP 定理**：`1998_Arora-Safra_PCP.pdf` 与 `1998_ALMSS_PCP-hardness.pdf`（二选一精读）→ `1995_Raz_parallel-repetition.pdf` → `2001_Hastad_optimal-inapproximability.pdf`
**理解 UGC 及其威力**：`2004_KKMO_MaxCut.pdf` → `2005_Khot-Vishnoi_UGC-integrality-gap.pdf` → `2008_Raghavendra_every-CSP.pdf` → `2010_Arora-Barak-Steurer_subexp-UG.pdf`
**2-to-2 史诗**：`survey_Khot_2to2-exposition.pdf` → `2017_KMS_independent-sets-2to2.pdf` → `2018_DKKMS_towards-2to1.pdf` → `2018_KMS_Grassmann-near-perfect-expansion.pdf` → `2019_Barak-Kothari-Steurer_shortcode.pdf`
**2026**：先读上面的经典，再对照 `2026_OpenAI_Unique-Games-Theorem.pdf`，自行判断。

---

## 五、来源说明

PDF 取自作者主页、ECCC、arXiv、Theory of Computing、以及 `openai/math` 仓库等开放渠道，仅用于个人学习研究。引用信息以论文本身为准；各篇的会议/期刊年份可能因版本（会议版 vs 期刊版 vs arXiv 版）不同而略有差异。

> 一句题外话：把 UGC 从「猜想」变成「定理」的，从来不只是某一次灵光。2-to-2 花了 2016–2019 四年、多篇论文互相咬合才拼出来。AI 在 2026 年给出的这份证明若最终被验证，它站立的也是这条线上无数人的肩膀——PCP 定理本身，就是人类智慧非常漂亮的结晶。
