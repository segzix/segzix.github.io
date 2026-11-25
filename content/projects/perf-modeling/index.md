---
title: "GPU 单卡与多卡集群性能建模与分析"
date: 2025-06-01
summary: "基于 Roofline 与 α-β 模型，为 LLM 训推部署建立统一性能评估基线"
tags:
  - 系统
tech_stack:
  - CUDA
  - PTX
  - torch_npu
  - HCCL
featured: true
status: "已完成"
---

为单卡算力/访存与多卡通信开销建立统一性能评估基线，用于 LLM 推理与训练的部署决策。

## 方案

- 基于 CUDA/PTX 微基准与 Roofline 模型，评估单卡计算、访存及 LLM 算子性能
- 开发 HCCL All-Reduce 基准，建立 HCCS + RoCE 分层 α-β 模型，分析消息规模与梯度分桶开销

## 结果

- LLM 算子预测误差 5%–9%
- 梯度 Bucket 调优范围收敛至 64–128 MiB
- 形成 16 卡性能评估方案
