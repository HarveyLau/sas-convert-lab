# sas-convert-lab 愿景

## 使命

在 VS Code + Copilot 内，构建一个可落地、开发者可控的框架，将 SAS
工程目录迁移到现代目标栈（首批支持 `python-pandas` 与 `python-bigquery`），且不依赖 SAS runtime。

## 问题定义

多数 SAS 迁移失败于“逐文件翻译”。数据作业本质是由血缘、隐式规则和业务约束
组成的工作流系统。可用的迁移框架应当：

- 以工程/目录为单位处理
- 在关键决策点让人参与
- 保留业务意图，而非仅转换语法

## 核心原则

1. **不依赖 SAS 运行时**
   - 仅做静态解析 + 语义提取
   - 不使用 `saspy`、不执行 SAS 引擎
2. **默认人机协同**
   - 每阶段主动提问
   - 未确认不进入下一阶段
3. **意图优先**
   - 以用户愿景和业务目标驱动转换
   - 记录假设、决策、偏差接受项
4. **全程可追踪**
   - 生成物可回溯到源代码上下文
   - 风险与置信度显式输出

## 生命周期

`Discover -> Analyze -> Plan -> Design -> Convert -> Validate`

### Discover
- 盘点源资产、include/macro 关系
- 发现快速风险与信息缺口

### Analyze
- 构建血缘与语义行为摘要
- 计算模块复杂度与迁移风险

### Plan
- 设计迁移波次、依赖和验收标准
- 明确时间与质量取舍

### Design
- 确定目标架构、模块契约、配置策略
- 转换前先收敛边界

### Convert
- 生成目标代码并建立可追踪映射
- 在转换前后执行意图对齐闸门

### Validate
- 校验代码结构、数据对账、意图一致性
- 输出可用于 go/no-go 的证据

## 多代理协作模型

- `sas-orchestrator`: 负责阶段编排与闸门控制
- `sas-discoverer`: 负责资产扫描与分类
- `sas-analyzer`: 负责语义与风险分析
- `sas-planner`: 负责波次规划与优先级
- `sas-designer`: 负责目标架构与契约
- `sas-converter`: 负责代码生成与映射追踪
- `sas-validator`: 负责验证与发布可行性评估

## 意图对齐闭环

每阶段必须输出：

- `questions_for_user`（3-5 个）
- `assumptions`
- `alignment_score`（1-5）

规则：

- `alignment_score >= 4`：用户确认后可继续
- `alignment_score < 4`：回环澄清并再评估

## 运行记忆工件

每次运行都保存：

- `vision_brief.json`
- `decision_log.json`
- `open_questions.json`

这些工件是 planner/designer/converter/validator 的必读输入。

## MVP 成功标准

- 用户可通过一次 orchestrator 指令启动流程。
- 框架在生成前能提出高价值问题。
- 输出包含可追踪映射与已知缺口。
- 验证报告可支持明确的发布决策。
