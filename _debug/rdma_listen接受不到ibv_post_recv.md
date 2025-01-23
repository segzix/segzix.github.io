
#### 日志文件

ibv_post_send方

```
[INFO] [Thread main ] (rdma/rdma_comm.c:282:init_comm_qp_context) Local address: LID 0x0002, QPN 0x00033d, PSN 0x000000, GID fe80000000000000:98f2b3ffffe153c2

[INFO] [Thread main ] (src/main.c:72:generate_random_string) generate string: pkDHTxmMR18N2l9

[INFO] [Thread listen] (rdma/rdma_listen.c:40:post_recv) Post recv wr successfully

[INFO] [Thread client] (rdma/rdma_client.c:85:rdma_client) Send outqueue[0] msg <pkDHTxmMR18N2l9> successfully

[INFO] [Thread main ] (src/main.c:72:generate_random_string) generate string: k88EmLgN7cCCTt9

[INFO] [Thread main ] (src/main.c:72:generate_random_string) generate string: rWksb1fEBw397vi

[INFO] [Thread client] (rdma/rdma_client.c:85:rdma_client) Send outqueue[1] msg <k88EmLgN7cCCTt9> successfully

[INFO] [Thread client] (rdma/rdma_client.c:85:rdma_client) Send outqueue[2] msg <rWksb1fEBw397vi> successfully

[INFO] [Thread main ] (src/main.c:72:generate_random_string) generate string: 5Ug1YHC3UAVUAoB
```

ibv_post_recv方

```
[INFO] [Thread main ] (rdma/rdma_comm.c:282:init_comm_qp_context) Local address: LID 0x0001, QPN 0x000354, PSN 0x000000, GID fe80000000000000:98f2b3ffffe16912

[INFO] [Thread listen] (rdma/rdma_listen.c:40:post_recv) Post recv wr successfully

[INFO] [Thread main ] (src/main.c:72:generate_random_string) generate string: pkDHTxmMR18N2l9

[INFO] [Thread client] (rdma/rdma_client.c:85:rdma_client) Send outqueue[0] msg <pkDHTxmMR18N2l9> successfully
```