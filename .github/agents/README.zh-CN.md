# Copilot Agents（中文说明）

本目录包含用于 SAS 迁移的 GitHub Copilot 自定义代理定义。

## 推荐入口

- `@sas-orchestrator`

## 阶段顺序

1. `@sas-discoverer`
2. `@sas-analyzer`
3. `@sas-planner`
4. `@sas-designer`
5. `@sas-converter`
6. `@sas-validator`

每个阶段都必须先提问、收敛假设并计算 `alignment_score`，确认后再推进。
