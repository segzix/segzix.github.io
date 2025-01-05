---
title: "tcp-connect连接"
categories:
  - debug
tags:
---
### 超时的定义
分两种情况：
1)connect时对方还没有进入listen状态，此时会立刻返回错误，超时的的定义没有任何作用
2)connect时对方已经进入了listen状态，此时由于listen可能不会及时的返回信息，内核会先将这次连接挂起，在超时定义的时间范围内如果尽量及时返回，不然就报错