# Research Method Engineering

`research-method-engineering` 是面向人工智能科研代码和方法改进的 Codex skill，包括但不限于计算机视觉、自然语言处理、多模态、生成模型、强化学习、图学习、推荐系统和时间序列等方向。

## 能做什么

- 判断任务是方法研究、方法实现、工程适配，还是实验评估与失败恢复；
- 从数据与监督、表征与预训练、模型结构、目标与奖励、优化与训练、推理与部署、泛化与评估等方面寻找改进空间；
- 根据问题选择从直觉和经验入手，或直接进行数学分析，再通过可复现实验检验假设；
- 管理科研方法改动对应的 Git 分支，并保留已有工作与失败实验记录；
- 在需要时检索相关论文，设计 baseline、消融与公平比较。

数学推导是判断方案的工具，而非所有研究任务的固定起点。对于损失、概率模型、梯度估计或约束等问题，会重点检查目标与反向传播；对于数据、训练动态或推理现象，可以先依据错误分析和领域经验提出假设，必要时再形式化，并通过实验验证。

## 目录

```text
SKILL.md                                  入口、工作模式与按需读取规则
agents/openai.yaml                        Codex 界面配置
references/workflow-routing.md            AI 任务分类与项目侦察
references/git-branch-policy.md           Git 分支与未提交改动规则
references/ai-method-design-space.md      AI 方法优化维度
references/ai-method-reasoning.md         直觉、经验与数学推理的选择
references/literature-search.md           AI 文献检索与公平比较
references/experiment-reproducibility.md  实验与复现
references/failure-recovery.md            失败诊断与迭代
```

## 分支约定

方法性改动默认采用 `<类型>/<功能短名>__from_<父分支短名>`；短名为 1～3 个词，例如：

```text
feature/adaptive-loss__from_main
experiment/hard-negatives__from_adaptive-loss
```

用户已创建与任务匹配的分支时直接使用。非 Git 项目跳过分支规则；混合未提交改动先询问；只自动删除本地、未合并、未推送且被用户明确判断为失败的分支。路径、多 GPU、数据集接口等工程适配通常在当前分支完成。

## 安装

在仓库根目录执行以下命令，将 skill 文件同步到 Codex 的 skills 目录；已废弃的旧参考文件会从安装目录移除，仓库的 `.git/` 不会被复制：

```bash
skill_dir="${CODEX_HOME:-$HOME/.codex}/skills/research-method-engineering"
mkdir -p "$skill_dir"
rsync -a --delete --exclude='.git/' --exclude='README.md' ./ "$skill_dir/"
```

## 使用

技能默认允许自动调用，也可显式调用：

```text
$research-method-engineering 请分析当前视觉模型的性能瓶颈，提出有依据的改进方案和最小消融实验。
```
