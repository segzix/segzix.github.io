---
title: "昇腾 NPU 上 AReaL 异步 RL 后训练性能剖析与优化"
date: 2026-09-30
summary: "异步训练 + 训推卡数配比 + 推测解码，单步耗时 1000s → 355s，吞吐最高 3.72×"
tags:
  - 系统
tech_stack:
  - AReaL
  - vLLM
  - 昇腾 NPU
  - MindStudio
  - GRPO
featured: true
status: "已完成"
---

移动九天 AI 实习项目（2026.03 — 2026.06）。

## 问题背景

NPU 集群上的企业 GRPO 知识库后训练 demo（Qwen3-8B，vLLM），同步模式下训练与推理串行执行，单步耗时约 1000 s。

## 方案

- **异步训练 / 资源配比**：基于 MindStudio 拆解 rollout 与权重同步耗时；采用异步训练 + A-3PO，并调整训推卡数配比
- **Rollout 优化**：异步后 rollout 等待仍占 49%–68%，引入推测解码，draft 模型随策略同步更新

## 结果

以同步训练为 baseline：

- 单步耗时 **1000 s → 355 s**，吞吐 **2.82×**
- 4/4 训推配比下吞吐达 **3.72×**
- A-3PO 再提升 **4.3%**
