# AI Writing Skills

从真实的协作写作、原文讲解与修订中，积累可复用的 Agent Skills。**核心目标：让读者跟着有依据的故事线索，真正理解知识是如何形成的，而不只是接收结论。**

## 设计原则

- **故事驱动的知识解释**：从真实困惑切入，沿着合理猜测、关键发现、机制和证据推进；不为了戏剧效果虚构困难或事实。
- **知识连续**：明确本篇与已有知识的关系，不制造错误的技术演进叙事。
- **先理解再成稿**：重要原理通过最小例子、数值验证或代码先被作者理解。
- **图文分工**：每张图必须回答一个明确问题，技术准确性优先于装饰。
- **以真实反馈迭代**：将创作中的理解缺口转化为测试案例和规则，而非堆积个人随想。

## 当前 Skills

- [`technical-explainer`](skills/technical-explainer/SKILL.md) **v0.6.0（故事驱动）**：兼容已有名称和路径；现可用于技术文章/知识随笔创作、已有论文或文章的故事式解读、修订与审稿；负责全文结构和插图教学目标。方法详见 [story-driven-explanation.md](skills/technical-explainer/references/story-driven-explanation.md)。
- [`technical-diagram`](skills/technical-diagram/SKILL.md)：技术原理图设计、生图、技术审图、作者确认与版本来源追溯。

## 目录结构

```text
skills/
  technical-explainer/
    SKILL.md
    references/
      writing-checklist.md
      rnn-case-study.md
      story-driven-explanation.md
    assets/
      article-outline.md
  technical-diagram/
    SKILL.md
    references/
      acceptance-and-provenance.md

evals/
  technical-explainer.md
  technical-diagram.md
CHANGELOG.md
```

## 未来候选能力（未实现）

只有当真实项目中反复出现独立、可测试的任务时才拆分，例如：`health-education-writing`、`platform-adaptation`、`fact-checking`。技术配图已基于真实 LLM 图文审查案例独立为 `technical-diagram`。

## 使用说明

本仓库遵循 [Agent Skills](https://agentskills.io/specification) 的 `SKILL.md` 格式。将相应 Skill 目录配置到支持 Agent Skills 的工具中，或明确让 AI 读取相应文件。**仅创建 GitHub 仓库不会让所有 ChatGPT 会话自动加载这些规范**；具体接入方式取决于所用的客户端/插件。

## 改进流程

1. 记录真实任务及输出中出现的缺陷（包括文章创作与别人的文章解读）。
2. 先将缺陷写成可检验的测试案例。
3. 修改最相关的 Skill 或 reference，而不是到处复制规则。
4. 在原测试案例和一个新的任务上验证。
5. 更新 `CHANGELOG.md`，再合并到主分支。

## 如何使用故事驱动能力

- **写文章**：“帮我写/修改一篇关于 X 的文章，用真实问题驱动理解。”→ 用 CREATE 模式，从读者的困惑、探索、关键转折、机制、验证来组织，不照搬固定的五个章节；如要配图，仍需先完整正文经作者批准。
- **讲解别人文章**：“帮我看一下这篇论文/文章讲了什么，并讲给我听。”→ 用 EXPLAIN 模式，先读取和核查原文，再按读者理解路径讲解；标注作者实证、解释者类比与个人推论。**单纯讲解无需进入博客配图和发布门禁。**
- **短解释/固定格式**：保持短回答或用户指定的表格清单，故事只是思路，不强制长篇结构。
- **现有项目兼容**：保留 `technical-explainer` 标识及路径，不新建功能重复的 Skill；`personal-blog/AGENTS.md` 继续引用它。
