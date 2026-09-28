# Research Method Engineering

个人的科研代码 skills。
这是一个用于 Codex 的科研代码与方法改进 skill，名称为 `research-method-engineering`。

## 能做什么

- 管理科研代码修改时的 Git 分支；
- 区分方法性改动和工程性改动；
- 从概率建模、目标函数、可微性和反向传播角度分析方法；
- 在需要时规划近两年、CCF-A 和高水平 CCF-B 论文检索；
- 设计 baseline、消融、复现和失败恢复流程；
- 根据实验结果判断继续迭代、回退或删除本地失败分支。

## 目录

```text
SKILL.md                         技能入口和路由规则
agents/openai.yaml               Codex 界面元数据和自动调用策略
references/workflow-routing.md   请求分类和工作流程
references/git-branch-policy.md  Git 分支、未提交改动和失败分支规则
references/mathematical-method-analysis.md
                                 数学与方法分析规则
references/literature-search.md  文献检索和公平比较规则
references/experiment-reproducibility.md
                                 实验、消融和复现规则
references/failure-recovery.md   失败判断、回退和迭代规则
```

## 默认分支命名

```text
<类型>/<功能短名>__from_<父分支短名>
```

功能短名和父分支短名均限制为 1～3 个词，例如：

```text
feature/adaptive-loss__from_main
feature/temp-schedule__from_adaptive-loss
experiment/hard-negatives__from_adaptive-loss
```

## 安装

将本仓库根目录作为 skill 目录复制到 Codex skills 目录：

```bash
cp -R /path/to/Personal_research_skills ~/.codex/skills/research-method-engineering
```

也可以直接使用本仓库目录进行开发，修改后重新复制到 `~/.codex/skills/research-method-engineering`。

## 使用

自动调用开启。也可以显式调用：

```text
$research-method-engineering 请分析当前模型的损失函数改进方案，并按 Git 规则实现和验证。
```

## 设计边界

- 非 Git 项目跳过分支规则；
- 工作区存在混合未提交改动时先询问；
- 用户已创建匹配分支时直接使用；
- 只自动删除本地、未合并、未推送且被用户明确判断为失败的分支；
- 失败实验的日志、checkpoint、配置和结果文件应保留。
# Personal_research_skills
个人的科研代码 skills
