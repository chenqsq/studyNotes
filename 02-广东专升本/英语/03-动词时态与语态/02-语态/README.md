# 第四章：动词语态——反向数据流与受体视角（Reverse Data Flow）

上一章我们打通了动词的“时态”（时间 + 状态），现在我们把最后一个关于动词的核心模块——**语态（Voice）**拼上。

在英语中，句子的数据流向只有两种模式：

- **主动语态（Active Voice）**：主语是动作的发出者（发力点）。  
  逻辑：`A (主语) ──[执行动作]──> B (宾语)`  
  代码：`User.click(Button);`（用户点击了按钮。）

- **被动语态（Passive Voice）**：主语是动作的承受者（受体）。  
  逻辑：`B (主语) ──[被执行动作]──> by A (被A)`  
  代码：`Button.onClicked(by User);`（按钮被用户点击了。）

在广东省专升本考试中，被动语态是单选题、翻译题和阅读理解极高频的考点。尤其是在学术或科技类阅读中，为了体现客观性，大量句子都会采用被动语态。


## 一、 被动语态的底层底层公式

很多零基础考生一看到被动语态就头晕，是因为觉得变形态太复杂。其实，所有的被动语态，底层公式只有一个：

> **被动语态万能公式：`be + 过去分词 (done)`**

在这个公式中，存在明确的分工解耦：

- **`be` 动词**：负责承载时态（时间/状态）和主语的单复数。它会根据时间改变成 `am/is/are`, `was/were`, `been`, `being` 等形态。
- **过去分词 (done)**：负责承载被动语义。它永远保持过去分词形态，固定不变。


## 二、 八大高频时态与被动语态的组合矩阵

当上一步学过的“8 大时态”遇上“被动语态（be + done）”时，`be` 动词会发生融合变形。你不需要死记硬背，看一下它们的叠加推导过程：

> 以“现在完成时”为例推导被动语态：
> - 现在完成时公式：`have/has + V-pp`
> - 被动语态公式：`be + done`
> - **叠加融合结果**：`have/has + been + done`

以下是专升本必须掌握的 **8 大时态被动语态汇总表**：

| 时态名称 | 主动语态结构 | 被动语态公式 (`be + done`) | 真实考场示例 |
| :--- | :--- | :--- | :--- |
| **一般现在时** | `do / does` | `am / is / are + done` | `English is spoken around the world.` |
| **一般过去时** | `did` | `was / were + done` | `The computer was repaired yesterday.` |
| **一般将来时** | `will do` | `will be + done` | `A new bridge will be built next year.` |
| **现在进行时** | `am/is/are + doing` | `am / is / are + being + done` | `The document is being printed now.` |
| **过去进行时** | `was/were + doing` | `was / were + being + done` | `The system was being tested at 10:00.` |
| **现在完成时** | `have/has + done` | `have / has + been + done` | `The bug has been fixed by the developer.` |
| **过去完成时** | `had + done` | `had + been + done` | `The work had been finished before he came.` |
| **含情态动词** | `can/must/should + V` | `情态动词 + be + done` | `This task must be completed today.` |

> **内存优化秘籍**：看到句子里有 `being + done`，必定是**进行时的被动**（正在被做）；看到有 `been + done`，必定是**完成时的被动**（已经被做）。


## 三、 专升本/考研命题人必考的 4 大被动语态陷阱

如果你只记住了公式，去考场依然会踩坑。命题人极度喜欢利用“中文习惯”和“特殊语法规则”来设计陷阱。

### 陷阱 1：不及物动词绝对没有被动语态（Intransitive Prohibition）

第一章和第二章我们反复强调：**只有及物动词（vt.）后面才能跟宾语（动作受体）**。而不及物动词（vi.）本身就不能接宾语，因此它**绝对不可能**被改写为被动语态！

中文里我们常说“事故被发生了”、“变化被产生了”，但在英文里这是严重的 `Syntax Error`。

**考场高频死穴词（绝对不能加 `be + done`）**：
- `happen` (发生) / `occur` (发生) / `take place` (发生)
- `appear` (出现) / `disappear` (消失)
- `rise` (上升) / `break out` (爆发)

> **错例排查**：
> - ❌ **错误 Syntax Error**：`An accident was happened yesterday.`
> - ✅ **正确 Code**：`An accident happened yesterday.`
> - ❌ **错误 Syntax Error**：`The sun is risen in the east.`
> - ✅ **正确 Code**：`The sun rises in the east.`

### 陷阱 2：感官/使役动词被动语态中 `to` 的强行还原

上一章我们学过：在主动语态中，使役动词（`make, let, have`）和感官动词（`see, hear, watch, notice`）作谓语时，后面的宾补必须省略 `to`（用裸不定式）。

**但是！** 一旦改写为被动语态，原本被省去的 `to` 必须像弹簧一样**强行弹回还原**！

- **主动语态（省略 `to`）**：
  - `Active: The boss made him work (省略 to) 12 hours a day.`（老板让他每天工作12小时。）
- **被动语态（`to` 还原！）**：
  - `Passive: He was made to work (还原 to!) 12 hours a day by the boss.`（他被迫每天工作12小时。）

> **口诀**：主动省 `to`，被动还原 `to`。广东省专升本单选题极其喜欢在 `was made _____` 后面放 `do` 和 `to do` 两个选项让你选。

### 陷阱 3：主动形式表被动意义（Active Form with Passive Meaning）

有些情况下，句子在结构上用的是主动形态，但在逻辑语义上表达的却是被动含义。这是专升本的高阶扣分点。

1. **描述主语内在属性/特征的动词 + 副词**：  
   当说明某个事物“吃起来、用起来、卖起来”怎么样时，动词用主动形式，后面跟副词（如 `well`, `smoothly`, `easily`）。
   - `The book sells well.`（这本书卖得很好。—— 不用 `is sold well`）
   - `This pen writes smoothly.`（这支笔写起来很顺畅。—— 不用 `is written`）
   - `The cloth washes easily.`（这布料很好洗。）

2. **感官系动词 + 形容词（第二章知识点）**：
   - `The food smells delicious.`（食物闻起来很香。—— 不用 `is smelled`）

3. **`need / require / want + doing`**：  
   在表示“某物需要被处理”时：`need doing` 结构等价于 `need to be done`。
   - `My phone needs charging.` ≡ `My phone needs to be charged.`（我的手机需要充电了。）

### 陷阱 4：双宾语结构的被动改写与介词还原

当句型四（S + V + IO + DO，主谓双宾）改写为被动语态时，有两个宾语可以提作主语。如果把“物（直接宾语）”提到句首作主语，人（间接宾语）前面**必须还原介词 `to` 或 `for`**。

- **主动语态**：
  - `Active: She gave me (人) a present (物).`
- **被动改写 A（人作主语）**：
  - `Passive A: I was given a present.`
- **被动改写 B（物作主语，介词 `to` 必须还原）**：
  - `Passive B: A present was given to me.`（不能漏掉 `to`!）


## 四、 真题长难句被动语态 AST 拆解实战

在真实阅读和翻译中，被动语态常与从句、介词短语嵌套在一起。

**真实真题演练句**：

> *"New artificial intelligence algorithms have been widely applied in medical diagnosis, but some ethical concerns are still being discussed by experts."*

**降维推演与结构拆解**：

1. **扫描连词，切分句子**：  
   看到了并列连词 `but`，说明这句话由两个独立的子句构成。

2. **拆解前半句**：
   - 主语：`New artificial intelligence algorithms`（新的 AI 算法，复数/物）
   - 谓语：`have been widely applied`
     - 语法剖析：`have been + applied`，这是**现在完成时的被动语态**（已经被广泛应用），中间插了一个副词 `widely` 进行修饰。
   - 地点状语：`in medical diagnosis`（在医疗诊断中）。

3. **拆解后半句**：
   - 主语：`some ethical concerns`（一些伦理担忧，复数/物）
   - 谓语：`are still being discussed`
     - 语法剖析：`are being + discussed`，这是**现在进行时的被动语态**（此时此刻依然正在被讨论），中间插了一个副词 `still`。
   - 动作发出者：`by experts`（被专家们）。

```text
[句子解构图]
前半句: AI算法 (主) ──[已经被广泛应用 (现在完成时被动)]──> 医疗诊断中
   │ (but 转折)
后半句: 伦理担忧 (主) ──[依然正在被讨论 (现在进行时被动)]──> 被专家们
```

**完整中文译文**：
> 新的人工智能算法已经被广泛应用于医疗诊断中，但一些伦理担忧目前依然在被专家们讨论。


## 本章实战练习（代号：04-VOICE）

请拿出一张纸，结合括号内提供的动词以及句中的时态与语态逻辑，填写正确的动词形态：

1. `Great changes ____________ (take place) in my hometown over the past five years.`

2. `The young boy was seen ____________ (enter) the internet bar by his teacher yesterday.`

3. `A new primary school ____________ (build) in this village next month.`

4. `Look! The broken roads ____________ (repair) by the workers.`

5. `This kind of soft cloth ____________ (wash) easily and sells well.`

**请提交你的答案，我们将为你运行代码语法检查并校验语态逻辑链。**