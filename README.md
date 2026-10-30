# translate-consulting-cases-zh

将英文管理咨询案例整理成适合中文面试官使用的结构化面官稿，并检索经过核验的相关案例，帮助候选人继续练习。

> A Codex skill for turning English consulting cases into concise Chinese interviewer guides and recommending verified follow-up cases.

## 它解决什么问题

英文 casebook 的信息通常分散在题干、面官提示、图表、计算和参考答案中。直接逐句翻译容易丢失面试节奏，也容易把原文答案、补充解释和个人发挥混在一起。

这个 skill 会把案例重新组织为面试官可以直接使用的中文材料，同时严格保留原始事实、数据、单位和解题逻辑。

## 核心能力

- **结构化中文面官稿**：按照题干、澄清问题、分析框架、计算与图表、Brainstorm、结论等环节整理。
- **忠于原始案例**：不虚构缺失信息，不把通用框架冒充原案例答案。
- **明确区分信息层级**：分别标注“原文转译”“补充说明”和“延伸洞察”。
- **计算与图表复核**：以“公式 → 代入 → 结果 → 商业含义”的方式呈现，并检查单位、时间口径和舍入。
- **面官观察点**：总结候选人的优秀信号、常见问题和可继续追问的方向。
- **行业与方法论 Insight**：补充解决案例所需的行业背景，以及框架、计算、图表解读和总结表达方面的学习重点。
- **相关案例检索**：按照行业、问题类型、分析方法和难度推荐 3–5 个相关案例，并核验案例名称、来源、年份、页码和链接。
- **模拟面试模式**：隐藏答案，按照原案例节奏逐步释放信息和图表，结束后再进行复盘。

## 适用场景

- 将商学院 casebook 中的英文案例翻译为中文面官材料
- 准备咨询公司 case interview 或组织 mock interview
- 检查案例中的计算、图表与商业逻辑
- 为已完成的案例寻找同类、进阶或跨行业练习

它不适用于与 case interview 无关的普通商业翻译。

## 输出结构

完整模式通常包括：

1. 案例速览
2. 题干
3. 澄清问题（Clarification）
4. 分析框架（Framework）
5. 计算与图表（Calculation / Exhibits）
6. 头脑风暴（Brainstorm）
7. 结论（Conclusion）
8. 面官观察点
9. Insight
10. 相关案例推荐

如果原案例没有提供某个环节，skill 会明确标注“原文未提供”，而不是补造答案。

## 安装

将仓库克隆到 Codex 的 skills 目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/eric977-alt/translate-consulting-cases-zh.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/translate-consulting-cases-zh"
```

然后在 Codex 中显式调用：

```text
使用 $translate-consulting-cases-zh 处理这份英文 case，生成中文面官稿并推荐相关练习案例。
```

Codex 也可以根据 `SKILL.md` 中的名称和描述，在请求与该工作流匹配时自动选择该 skill。关于 skill 的结构和激活方式，可参考 [OpenAI Skills 官方文档](https://developers.openai.com/plugins/concepts/skills)。

## 使用示例

### 生成完整面官稿

```text
使用 $translate-consulting-cases-zh 处理我上传的 case。
保留原案例的面试顺序，计算部分逐步展开，最后推荐 3 个经过核验的相似案例。
```

### 只处理一个环节

```text
使用 $translate-consulting-cases-zh 重点整理这个案例的 framework 和 calculation。
请区分原文答案与补充说明。
```

### 进行模拟面试

```text
使用 $translate-consulting-cases-zh 以模拟面试模式带我完成这个 case。
先不要展示答案，只在我提出合适问题时提供原文中的信息。
```

### 寻找后续练习

```text
使用 $translate-consulting-cases-zh 为这个医疗健康行业的 M&A case 推荐进阶练习。
优先近五个学年的商学院官方 casebook，并核验标题、年份、页码和链接。
```

## 相关案例如何筛选

推荐不是简单的关键词匹配。skill 会综合判断：

- 行业与细分赛道
- 核心商业问题，如盈利、增长、市场进入、定价、M&A 或 PE 尽调
- 分析方法，如市场规模、盈亏平衡、单位经济、产能、估值或 NPV
- 被考察的能力、案例难度和面试形式

检索时优先使用商学院或咨询社团官方页面、官方 casebook 和咨询公司练习案例。无法核验的标题、年份或链接不会被编入推荐结果。

## 使用要求与限制

- 需要能够读取完整案例，包括图表、面官提示和参考答案；缺页或不可访问内容不会被猜测补全。
- 相关案例推荐需要当前环境具备网页检索能力。
- 扫描型 PDF 可能需要 OCR 或页面渲染能力才能完整读取。
- 行业补充信息与教学建议会明确标为“延伸洞察”，不会伪装成原案例内容。

## 仓库结构

```text
translate-consulting-cases-zh/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── related-case-search.md
```

- `README.md`：安装方法、使用示例与能力说明
- `SKILL.md`：核心工作流与输出要求
- `agents/openai.yaml`：Codex 中显示的名称、简介和默认调用示例
- `references/related-case-search.md`：相关案例的检索、核验和排序规则
