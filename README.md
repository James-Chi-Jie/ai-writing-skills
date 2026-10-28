# AI Writing Skills

从真实的协作写作、解释与修订中，积累可复用的 Agent Skills。

## 设计原则

- **问题驱动**：从读者的具体困惑开始，而不是先堆定义。
- **知识连续**：明确本篇与已有知识的关系，不制造错误的技术演进叙事。
- **先理解再成稿**：重要原理通过最小例子、数值验证或代码先被作者理解。
- **图文分工**：每张图必须回答一个明确问题，技术准确性优先于装饰。
- **以真实反馈迭代**：将创作中的理解缺口转化为测试案例和规则，而非堆积个人随想。

## 当前 Skills

- [`technical-explainer`](skills/technical-explainer/SKILL.md)：问题驱动的技术解释与图文写作；负责文章结构与插图教学目标。
- [`technical-diagram`](skills/technical-diagram/SKILL.md)：技术原理图设计、生图、技术审图、作者确认与版本来源追溯。

## 目录结构

```text
skills/
  technical-explainer/
    SKILL.md
    references/
      writing-checklist.md
      rnn-case-study.md
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

1. 记录真实任务及输出中出现的缺陷。
2. 先将缺陷写成可检验的测试案例。
3. 修改最相关的 Skill 或 reference，而不是到处复制规则。
4. 在原测试案例和一个新的任务上验证。
5. 更新 `CHANGELOG.md`，再合并到主分支。
