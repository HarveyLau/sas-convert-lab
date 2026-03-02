# sas-convert-lab

一个以人为中心（human-in-the-loop）的多代理框架，用于在 VS Code +
GitHub Copilot 中，将 SAS 工程目录迁移到目标数据技术栈。

## 解决什么问题

- 以工程目录为单位迁移 SAS 数据作业，而不是逐文件生硬翻译。
- 支持迭代式迁移目标栈：
  - `python-pandas`
  - `python-bigquery`
  - 可扩展到 `pyspark` 等
- 每个阶段都强制提问与对齐，确保开发者持续掌控迁移方向。
- 仅使用静态分析 + LLM 语义提取（不依赖 SAS runtime，不使用 `saspy`）。

## 端到端流程

`Discover -> Analyze -> Plan -> Design -> Convert -> Validate`

每个阶段都必须包含：

1. `questions_for_user`（3-5 个高价值问题）
2. `assumptions`（必须被用户确认或修正）
3. `alignment_score`（1-5）

若 `alignment_score < 4`，编排代理必须回环澄清后再继续。

## 人机协同原则

- 先提问，再生成。
- 转换前先复述开发者愿景。
- 关键决策落地为机器可读工件。
- 偏差与风险必须显式暴露。

## 仓库结构

```text
.github/agents/
  sas-orchestrator.agent.md
  sas-discoverer.agent.md
  sas-analyzer.agent.md
  sas-planner.agent.md
  sas-designer.agent.md
  sas-converter.agent.md
  sas-validator.agent.md
schemas/
templates/
  python-pandas/mapping.yaml
  python-bigquery/mapping.yaml
docs/
  vision.md
  customer-demo-playbook.md
  stage-question-pack.md
examples/sample-run/artifacts/run-001/
```

## 工件契约

每次运行在 `artifacts/{runId}/` 下输出：

- `vision_brief.json`
- `decision_log.json`
- `open_questions.json`
- `discovery.json`
- `analysis.json`
- `migration_plan.json`
- `design_spec.json`
- `conversion_manifest.json`
- `validation_report.json`

字段约束见 `schemas/`。

## 中文文档入口

- 框架愿景（中文）：`docs/vision.zh-CN.md`
- 客户演示手册（中文）：`docs/customer-demo-playbook.zh-CN.md`
- 分阶段提问模板（中文）：`docs/stage-question-pack.zh-CN.md`

## 快速开始（VS Code + Copilot）

1. 在 VS Code 中打开本仓库。
2. 打开 Copilot Chat，选择 `@sas-orchestrator`。
3. 发送：
   - `@sas-orchestrator Convert this SAS project to python-bigquery`
4. 按阶段回答问题并确认假设。
5. 每个阶段审核通过后再进入下一阶段。

## 分阶段直接调用

- `@sas-discoverer Scan current SAS project and build source inventory`
- `@sas-analyzer Build lineage and migration risk report`
- `@sas-planner Propose phased migration backlog`
- `@sas-designer Produce target architecture and module contracts`
- `@sas-converter Generate conversion manifest and code skeleton`
- `@sas-validator Run code+data parity validation checklist`

## 约束

- 不执行 SAS。
- 不使用 `saspy`。
- 不允许隐式假设跨阶段传播。
- 未经用户确认不允许阶段跳转。

## MVP 非目标

- 无人工参与的一键全自动迁移。
- 对所有重宏项目一次性达到完美语义等价。
- 在迁移过程中执行 SAS 程序。
