---
title: "Todo2"
date: 2022-06-19T15:13:49+08:00
---

# Project2 RaftKV

这一节需要我们实现 Raft，TinyKV Raft 这部分很多都是抄 Etcd 的 Raft 模块。你可以注意到连测试用例都很像。所以这一节我拿到手就会做啊，首先去 Etcd clone 一份源码。我抄的是 Etcd 3.5.1 版本，也就是目前最新版。

TinyKV 中的 Raft 和 6.824 中的 Raft 有很大的不同。这里将整个 Raft 设计为一个状态机，从一端输入消息，从另一端输出消息，整一个过程是线性的，你**不需要考虑并发**的情况，这能极大降低心智负担。

在这一节实验中，大家一定可以参考 [https://www.codedump.info/post/20180922-etcd-raft/](https://www.codedump.info/post/20180922-etcd-raft/)  这个网站，会有很大的帮助。

这里我将 Project2 中 3 个实验合在一起讲，同时有些内容是在 Project3 中才会遇到，如果在这里你不懂，可以先直接跳过。

在 Part A 实验中，我们需要实现三个模块。分别是 RawNode，Raft 和 RaftLog。三个模块分别对应 `rawnode.go`，`raft.go `和 `log.go` 三个文件。三个模块的结构图如下所示： 
