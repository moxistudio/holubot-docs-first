# HoluBot（葫芦宝）

**36% 的 AI Agent 技能存在安全缺陷。**  
HoluBot 是一个放在 Agent 前面的治理与调度层：先审计、先审批、再执行。

HoluBot 不是另一个“大而全 Agent 框架”，而是一个轻量控制面（Control Plane），负责路由、信任分级、记忆治理和可审计执行。

![HoluBot 架构图](docs/architecture.svg)

## 快速开始

当前仓库处于 **文档先行开源阶段**。

- 查看脱敏白皮书：[`docs/WHITEPAPER_ZH.md`](docs/WHITEPAPER_ZH.md)
- 查看 `agent.yaml` 规范和最小示例：[`examples/`](examples/)
- 可运行版本即将发布，欢迎 Star 关注进展。

## 核心价值

- 治理优先：审批拦截、审计日志、信任等级
- 成本友好：前台轻模型，复杂任务才下发后端
- 后端可插拔：通过适配层接入不同 Agent Runtime

## 当前状态

- 阶段：早期公开预览（文档 + 规范 + 示例）
- 当前范围：架构说明、治理原则、Agent 合约、路线图产物

## 许可证

[MIT](LICENSE)
