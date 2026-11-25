---
title: "LLM 推理跨实例 KV Cache 复用与快照恢复"
date: 2026-05-31
summary: "基于 RDMA 异步传输与 userfaultfd 按需恢复，Prefill 开销降低约 65%，重启后首次命中 64s → 0.94s"
tags:
  - 系统
tech_stack:
  - RDMA
  - C/C++
  - userfaultfd
  - iSCSI
  - vLLM
featured: true
status: "已完成"
---

摩尔线程实习项目（2026.08 — 2026.12）。

## 问题背景

企业 70B 模型长上下文推理场景（4 节点 × 4×H100）中，相同前缀在不同副本间重复 Prefill；服务重启后 KV Cache 全部失效，导致 TTFT 过长。

## 方案

- **RDMA 异步传输**：使用 RDMA Recv/Send 与 CQ 流水线，引入多线程流控机制，实现多机间 KV Cache 复用
- **快照与恢复**：采用后台快照机制，通过 iSCSI 协议将 KV 存储至远程 LUN；重启后仅加载索引，经 userfaultfd 按需取回数据

## 结果

- Prefill 开销降低约 **65%**
- KV 传输耗时仅为重算的 **1/13**
- 重启后首次命中耗时 **64 s → 0.94 s**
