---
title: 停用 Istio
description: 本节介绍如何在一个集群，命名空间或工作负载中停用 Istio。
keywords:
  - rancher 2.0中文文档
  - rancher 2.x 中文文档
  - rancher中文
  - rancher 2.0中文
  - rancher2
  - rancher教程
  - rancher中国
  - rancher 2.0
  - rancher2.0 中文教程
  - 集群管理员指南
  - 集群访问控制
  - 告警
  - Istio
  - 停用 Istio
---

本节介绍如何在一个集群，命名空间或工作负载中停用 Istio。

## 在集群中停用 Istio

停用 Istio 需执行以下步骤：

1. 从**全局**视图中，导航到要停用 Istio 的集群。
1. 单击 **工具 > Istio。**
1. 单击 **停用**，然后再次单击红色按钮以确认停用操作。

**结果：** 集群的 `system` 项目中的 `cluster-istio` 应用被删除。Istio Sidecar 无法部署在集群中的任何工作负载上。

## 在命名空间中停用 Istio

1. 在 Rancher UI 中，进入到您要停用 Istio 的命名空间所属的项目中。
1. 在 **工作负载** 标签页上，您将看到命名空间及其中部署的工作负载的列表。找到要停用的命名空间，然后单击 **省略号（...）>停用 Istio 自动注入**。

**结果：** 在该命名空间中部署工作负载时，它们将不会带有 Istio sidecar。

## 从工作负载中删除 Istio Sidecar

在命名空间中停用 Istio，然后重新部署其中的工作负载。它们将不会带有 Istio sidecar。
