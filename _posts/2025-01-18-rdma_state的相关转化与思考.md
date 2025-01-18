---
title: rdma_state的相关转化与思考
categories:
  - coding
stars: 8
---

---


### 基本流程
[rdma state状态机，相关变量以及thread work](../_draws/rdma_state.svg)

### 心路历程
1. 最开始思考这个问题时，并没有考虑到需要新增加一个状态，认为和发送端一样维护两个状态，由listen thread和server thread分别来做各自的工作就可以了；如果需要进行定时的下发，是准备做一个flags数组来做这件事情的；
2. 后来发现新增一个flags数组极其没有美感，并且在理论架构层面总是缺少能涵盖所有情况的一种模型，因此重新进行思考，并且认为这种新增加一个状态的做法可以改变这种情况。因此摒弃了二状态机，并且采用了三状态机。

### 一些心得

- Q: check_flags需要由谁来做？
- A: 最开始打算由listen_thread来做，但发现并不可行。主要原因在于现在没有条件变量，wait/signal等唤醒机制，导致listen必须一直监听channel。如果由listen thread来做这件事情，将监听channel与下发wr事件绑定，可能会出现由于channel中一直没有新事件，因此wr难以下发的情况；
- A: 因此应该由server thread来做。即每次处理完就立刻下发新的wr，这样能保证队列中总有还没有使用的wr，并且server thread也不会因为监听信道而被阻塞住。
- Q: 为什么需要三个状态？
- A: 如果不需要每次下发一个Batch，可以做到每次server thread处理完一个wr的信息就立即下发新的wr；但是如果需要每次下发一个Batch，那么就需要专门用一个状态和对应的变量来记录下发的起始wr。