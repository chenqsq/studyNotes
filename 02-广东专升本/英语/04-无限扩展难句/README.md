# 第五章：定语从句——挂载在名词上的扩展插件 (Plugin System)

在第三、四章中，我们处理了单个主句的核心动词（时态与语态）。本章我们进入 L3 级长难句构造的第一个重磅模块：**定语从句（Attributive Clause / Relative Clause）**。

在中文里，无论修饰成分多长，我们都惯于放在名词前面（“一个昨天被我打碎的杯子”）。但在英文的底层架构中，遵循 **“核心前置，长修饰后置”** 的规则。当一个形容词短语过长，甚至本身就是一个完整的句子时，英文会把它挂载在目标名词的后面。

这个被修饰的名词叫 **“先行词（Antecedent）”**，而连接主句与从句的接口工具叫 **“关系词（Relativizer）”**。

```text
主句基类：I like the book. ──┐
                         ├── 挂载拼接 ──> I like the book [which was written by Lu Xun].
从句插件：The book was written by Lu Xun. ┘             └─────── 定语从句 (Plugin) ───────┘
```


## 一、 关系词的选择算法与分类矩阵

关系词在定语从句中承担着 **“双重身份”**：

- **连接器（Connector）**：负责把从句黏合到主句的先行词后面。
- **占位符（Placeholder）**：在从句内部充当一个具体的语法成分（主语、宾语、定语或状语）。

关系词分为 **关系代词** 和 **关系副词** 两大类：

```text
                              ┌── 关系代词 (在从句中作 主语/宾语/定语 ── 从句缺主或宾)
                              │    ├── who (指人，作主/宾)
                              │    ├── whom (指人，作宾)
                              │    ├── which (指物，作主/宾)
                              │    ├── that (指人/物，作主/宾)
                              │    ├── whose (指人/物，作定语/表示 "...的")
关系词决策树 (Relativizer Tree) ┤    └── as (指人/物/整个句子，作主/宾)
                              │
                              └── 关系副词 (在从句中作 状语 ── 从句主宾完整，仅缺时间/地点/原因)
                                   ├── when (指时间 = 在...时间, at/in/on which)
                                   ├── where (指地点 = 在...地点, in/at/on which)
                                   └── why (指原因 = 为...原因, for which)
```


## 二、 专升本/考研命题人必考的 4 大定语从句绝杀考点

### 考点 1：that 与 which 的互斥规则（强制约束）

在指代“物”时，`that` 和 `which` 很多时候可以互换，但在以下特殊规则下，**只能用 that** 或 **只能用 which**。

**1. 绝对只能用 `that` 的场景（只能用 that 强约束）**：

- **先行词为不定代词**：先行词是 `all, everything, nothing, anything, little, much, few, none` 时。  
  `All that glitters is not gold.`（发光的未必都是金子。）
- **先行词被最高级或序数词修饰**：先行词前有 `the most..., the first, the last` 等。  
  `This is the most interesting book that I have ever read.`
- **先行词被唯一性/特指限定词修饰**：先行词前有 `the only, the very, the same, the right` 等。  
  `He is the only person that can solve the problem.`
- **先行词既有人又有物**：  
  `They talked about the people and things that they remembered.`

**2. 绝对只能用 `which` 的场景（只能用 which 强约束）**：

- **紧跟在介词后面（介词 + 关系代词）**：介词后面指物时，严禁使用 `that`，只能用 `which`。  
  ❌ `This is the house in that I lived.`  
  ✅ `This is the house in which I lived.`
- **引导非限制性定语从句（有逗号隔离）**：逗号后面严禁使用 `that`，只能用 `which`（或指人用 `who/whom`）。  
  ❌ `He failed the exam, that made his father angry.`  
  ✅ `He failed the exam, which made his father angry.`

### 考点 2：关系副词 (where/when) vs 关系代词 (which/that) 的判别算法

这是 90% 考生最容易丢分的陷阱题。看到先行词是地点（如 `the factory`），很多考生想都不想就填 `where`。这是致命的误区！

**判定法则（算法执行流程）**：

> 看从句内部是否缺少主语或宾语：
> - 如果从句缺少主语或宾语 → 必须选 **关系代词 (which / that)**。
> - 如果从句主宾完整，只缺少地点、时间或原因状语 → 才能选 **关系副词 (where / when / why)**。

**测试用例对比**：

- **用例 A**：`This is the factory ________ he visited last year.`  
  从句分析：`he`（主语）+ `visited`（及物动词谓语）+ [缺失宾语]。  
  结论：从句缺宾语，必须填 `which / that`。

- **用例 B**：`This is the factory ________ his father works.`  
  从句分析：`his father`（主语）+ `works`（不及物动词谓语）。结构极其完整，不缺主宾，缺地点状语（在工厂里）。  
  结论：填 `where`（等价于 `in which`）。

### 考点 3：介词 + 关系代词（Preposition + Relative Pronoun）

当关系代词在从句中作介词的宾语时，介词可以提到关系代词的前面，构成 **介词 + which (物)** 或 **介词 + whom (人)**。

**1. 介词的选择规则（两个确定依据）**：

- **根据从句中动词的固定搭配确定**：  
  `This is the hero about whom we were talking.`（固定搭配：`talk about`）
- **根据先行词的默认介词搭配确定**：  
  `I will never forget the day on which I met her.`（先行词是 `the day`，具体某一天用介词 `on`）

**2. 高阶考点：名词/代词 + of + which / whom（表示部分与整体）**：

`There are 40 students in our class, most of whom come from Guangdong.`（我们班有40名学生，他们中的大多数来自广东。）

### 考点 4：whose 的变量属性拆解

`whose` 是唯一具有所有格/属性的关系代词，意为“……的”。它在从句中作定语，后面必须紧跟一个名词。

- **公式**：`先行词 + whose + 名词` ≡ `先行词 + of which / of whom + the + 名词`
- **示例**：`I live in a room whose window ( = the window of which) faces south.`（我住在一间窗户朝南的房间里。）


## 三、 真题长难句定语从句 AST 拆解实战

**真实真题演练句**：

> *"The research team conducted a series of experiments in the laboratory, the results of which clearly showed that the new drug, which was developed last year, is effective."*

**降维推演与语法树解构**：

1. **确定主句主干**：  
   `The research team`（主）+ `conducted`（谓）+ `a series of experiments`（宾）+ `in the laboratory`（地点状语）。  
   （研究团队在实验室进行了一系列实验。）

2. **定位第一个定语从句（介词+关系代词）**：  
   `, the results of which clearly showed that...`  
   关系词分析：`which` 指代前面的 `experiments`（实验）。`the results of which` 即“这些实验的结果”。修饰整套实验，引导非限制性定语从句。

3. **定位宾语从句（嵌套在第一个定语从句内部）**：  
   `showed` 后面跟了一个 `that` 引导的宾语从句：`that the new drug ... is effective.`（新药是有效的）。

4. **定位第二个定语从句（插入语式的非限制性定语从句）**：  
   在 `the new drug` 和 `is effective` 中间，插入了 `, which was developed last year,`。  
   关系词分析：`which` 指代 `the new drug`，作从句的主语（被动语态：去年被研发）。把它当作可折叠的代码块切除，主干恢复为：`the new drug is effective`。

```text
[句子主干]: 研究团队进行了实验 
               │
               └─► [定语从句 1]: 实验的结果清晰地显示 ...
                                      │
                                      └─► [宾语从句]: 新药是有效的
                                                            │
                                                            └─► [定语从句 2]: (这部新药是去年研发的)
```

**完整中文译文**：
> 研究团队在实验室里进行了一系列实验，这些实验的结果清晰地表明，去年研发的那种新药是有效的。


# 第六章：非谓语动词——核心 API 的降级与逻辑解耦 (Function Downgrading)

如果说“定语从句”是用一个完整的句子去修饰名词，那么 **非谓语动词（Non-finite Verbs）** 就是用更精炼的“动词变形”来替代整个从句。

非谓语动词是专升本与考研英语语法中分值最高、难度最大、最区分高低分的终极模块。


## 一、 底层设计逻辑：一山不容二虎（单线程铁律）

再次重申英语语法的核心底层铁律：

> **一个独立的句子中，有且只能有一个核心谓语动词。**

如果在句子里，你既不想用 `and`, `but`, `because` 等连词，也不想用定语从句，却还想表达另外的动作，你就必须把多余的动词 **“降级”为非谓语动词**。

非谓语动词脱去了“谓语”的身份，不再具备独立作谓语的权限，而是转码（Type-Casting）变成了名词、形容词或副词，挂载在句子的其他位置。


## 二、 三大降级形态的三维逻辑模型

非谓语动词共有三种形态。它们的核心区别在于**“时间时态”和“主被动逻辑”**：

```text
                    ┌── 1. 动词不定式 (To do) ──── 属性：将来 / 目的 / 偶发未完成 (面向未来)
                    │
非谓语动词三大形态 ─┼── 2. 现在分词 / 动名词 (Doing) ── 属性：主动 / 进行 / 持续名词化 (正在/主动)
                    │
                    └── 3. 过去分词 (Done) ───────── 属性：被动 / 完成 / 状态残留 (被动/完成)
```

**维度比对矩阵表**：

| 变形形态 | 语法属性转码 | 时间/时态维度 | 主被动逻辑 | 核心物理语义 |
| :--- | :--- | :--- | :--- | :--- |
| **不定式 (To do)** | 名词 / 形容词 / 副词 | 未发生 / 将来 | 主动 (被动为 to be done) | 表示目的、倾向、未发生的计划 |
| **现在分词 (Doing)** | 形容词 / 副词 | 正在进行 / 状态中 | 主动关系 (做动作) | 表示主动执行、伴随进行 |
| **动名词 (Doing)** | 名词 | 抽象概念 / 常规行为 | 主动 | 将动作名词化，作主语/宾语 |
| **过去分词 (Done)** | 形容词 / 副词 | 已经完成 | 被动关系 (承受动作) | 表示被动承受、完成的状态 |


## 三、 非谓语动词在句中的 4 大核心挂载接口

非谓语动词不能作谓语，但它可以作句子的主语、宾语、定语、状语和宾补。

### 接口 1：作定语（修饰名词，替代定语从句）

非谓语动词作定语时，单个词放在名词前，短语放在名词后。核心看它与被修饰名词之间是主动还是被动、将来还是完成。

- **To do 作定语（将来/未发生）**：  
  `I have a lot of homework to do tonight.`（我今晚有很多作业要做。—— 作业还没做，指向将来。）
- **Doing 作定语（主动/正在进行）**：  
  `The girl standing by the window is my sister.`（站在窗户边的那个女孩是我妹妹。—— 女孩“主动”站着，等价于定语从句 `who is standing...`）
- **Done 作定语（被动/已经完成）**：  
  `The window broken by the boy yesterday has been repaired.`（昨天被那个男孩打破的窗户已经被修好了。—— 窗户“被打破”，等价于定语从句 `which was broken...`）

### 接口 2：作状语（修饰全句，表示目的、原因、时间、条件、伴随）—— 专升本最高频！

当非谓语动词作状语放在句首或句末时，它的逻辑主语强制锁定为 **“全句的主语”**！

**判别算法（逻辑主语绑定法则）**：

1. 找出全句的核心主语。
2. 判断该主语与非谓语动词之间是主动 (Doing) 还是 被动 (Done)。
3. 如果表示目的，直接用 To do。

**示例印证**：

- **表示目的 → 选用 To do**：  
  `To pass the exam, he studied until midnight.`（为了通过考试，他学到了半夜。）
- **主语与动作是主动关系 → 选用 Doing**：  
  `Hearing the good news, the girl jumped with joy.`（听到好消息，女孩高兴地跳了起来。—— 逻辑主语 `the girl` “主动听到”消息，用 `Hearing`。）
- **主语与动作是被动关系 → 选用 Done**：  
  `Seen from the top of the mountain, the city looks beautiful.`（从山顶上看，这座城市看起来很美。—— 逻辑主语 `the city` 是“被看”，必须用过去分词 `Seen`！绝对不能用 `Seeing`！）

### 接口 3：作宾语（动词接 to do 还是 doing）

在及物动词后面，有些动词只能接 `to do` 作宾语，有些只能接 `doing`，而有些两者都能接，但语义完全不同。

**1. 强制只能接 `doing` 作宾语的高频动词（口诀顺口溜）**：

> 避免 (avoid) 错过 (miss) 习惯 (be used to)，  
> 介意 (mind) 完成 (finish) 延迟 (delay/postpone)。  
> 建议 (suggest/advise) 思考 (consider) 练习 (practice)，  
> 逃避 (escape) 抵抗 (resist) 享受 (enjoy)。

`He suggested going (不能用 to go) to Guangzhou by high-speed train.`

**2. 接 `to do` 与 `doing` 语义完全相反的考点动词**：

| 动词 (Verb) | 接 to do 的语义 (面向未来) | 接 doing 的语义 (面向过去/进行) |
| :--- | :--- | :--- |
| **remember** | 记得要去做某事（还没做） | 记得曾经做过某事（已经做了） |
| **forget** | 忘记要去做某事（还没做） | 忘记曾经做过某事（已经做了） |
| **stop** | 停下来去做另一件事 | 停止正在做的事 |
| **regret** | 很抱歉/遗憾要去做某事 | 后悔曾经做过某事 |
| **mean** | 打算/想要做某事 | 意味着做某事 |

### 接口 4：With 复合结构（With Absolute Construction）

`With + 名词 + 非谓语动词` 是一种高阶状语，用来表示伴随状态或原因。

- **公式**：`With + Noun (名词) + to do / doing / done`
- **判定逻辑**：
  - 名词与动词是主动 → `With + N. + doing`  
    `With winter coming`（主动）, it gets colder and colder.
  - 名词与动词是被动 → `With + N. + done`  
    `With all the work finished`（被动）, he left the office happily.
  - 名词与动词表示将来未做 → `With + N. + to do`  
    `With so many tasks to complete`（将来）, I cannot go on vacation.


## 四、 专升本/考研非谓语动词解题通用算法流程图

遇到非谓语动词选择题时，在脑海中运行以下四步推理算法，准确率可达 100%：

```text
[开始：面对非谓语动词空位]
          │
          ▼
[1. 检查句中有无谓语动词？]
    ├── 无 ──► [填谓语动词 (考虑时态/语态)]
    └── 有 ──► [确定使用非谓语动词]
          │
          ▼
[2. 寻找非谓语的逻辑主语]  
(作定语找被修饰名词 / 作状语找句首主语)
          │
          ▼
[3. 判断主被动与时间关系]
    ┌───────┼───────┐
    ▼       ▼       ▼
[表示将来/目的] [主动/进行] [被动/完成]
    │       │       │
    ▼       ▼       ▼
  To do    Doing   Done
```


## 五、 双剑合璧：真题长难句综合 AST 拆解

在真实专升本与考研真题中，“定语从句”与“非谓语动词”往往是交织在一起出现的。

**真实真题演练句**：

> *"Encouraged by the recent success, the scientists working in the lab decided to adopt a new method, which is believed to be more efficient, to solve the problem."*

**降维推演与语法树解构**：

1. **解析句首非谓语（作状语）**：  
   `Encouraged by the recent success,`  
   逻辑主语定位：全句主语是 `the scientists`。科学家被近期成功所“鼓舞”，是被动关系，所以用过去分词 `Encouraged` 作原因/伴随状语。

2. **解析核心主干**：  
   `the scientists ... decided to adopt a new method ...`  
   主语：`the scientists`  
   谓语：`decided`（决定）  
   宾语：`to adopt a new method`（不定式短语作 `decided` 的宾语，意为决定采用新方法）。

3. **解析后置非谓语（作定语）**：  
   在 `scientists` 后面挂载了 `working in the lab`。  
   逻辑判定：科学家“主动”在实验室工作，用现在分词 `working` 作后置定语，修饰 `scientists`（等价于定语从句 `who work in the lab`）。

4. **解析定语从句**：  
   `, which is believed to be more efficient,`  
   非限制性定语从句，`which` 指代 `a new method`，在从句中作主语，采用被动语态（被认为是更有效率的）。

5. **解析句末非谓语（作目的状语）**：  
   `to solve the problem.`  
   逻辑判定：不定式短语放在句末，说明采用新方法的“目的”是为了解决问题。

```text
[全句逻辑解构图]
受成功鼓舞 (Encouraged 状语) 
  └─► 在实验室工作的 (working 定语) 科学家 (主语) 
        └─► 决定采用 (decided 谓语) 
              └─► 新方法 (宾语)
                    ├─► 被认为是更有效的 (which... 定语从句)
                    └─► 为了解决问题 (to solve 目的状语)
```

**完整中文译文**：
> 受近期成功的鼓舞，在实验室工作的科学家们决定采用一种被认为更有效率的新方法来解决这个问题。


## 本章综合实战练习（代号：05-ADVANCED）

请拿出一张纸，结合“定语从句”与“非谓语动词”的语法规则，填写正确的括号内单词形态或关系词：

1. `The girl ____________ (sit) under the big tree is reading a novel ____________ was written by Mo Yan.`

2. `____________ (absorb) in his research, the professor didn't notice the time passing.`

3. `This is the very reason ____________ he gave us for his absence from the important meeting.`

4. `With all the problems ____________ (solve), the manager breathed a sigh of relief.`

5. `He made a promise ____________ he would spend more time with his family, ____________ made his wife very happy.`

**请提交你的答案，我们将为你运行全套语法编译检查，并输出详细的代码审查报告。**