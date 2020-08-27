---
title: 添加项目成员
---

如果您需要给用户提供访问某个集群内特定项目和项目资源的权限，您需要将该用户添加到项目成员列表中。在 Rancher 中，项目和项目成员存在多对多的映射关系，也就是说，一个用户可以是多个项目的成员，与此同时，一个项目也可以有多个项目成员。本文主要介绍在新建的项目和已有的项目中添加成员的操作步骤。如果您需要将同一个集群的全部项目的权限开放给一个用户，请参考[添加集群成员](/docs/rancher2/cluster-admin/cluster-access/cluster-members/_index)。

## 新建项目时添加成员

我们建议用户在创建项目的时候添加项目成员。关于如何创建项目，请参考[集群管理员指南](/docs/rancher2/cluster-admin/projects-and-namespaces/_index)。若您想先创建项目，再添加项目成员，请参考下文的操作指导。

## 在已有项目中添加成员

完成项目创建以后，您可以将其他用户添加到项目成员名单里面，这样他们就有访问项目内容和项目资源的权限了。

1. 访问 Rancher UI **全局** 页面，单击项目名称，跳转到需要添加成员的项目。

2. 从项目的主菜单中选择**成员**，然后单击**添加成员**。

3. 在搜索框中输入您想要添加的成员名称。

   如果外部认证已经配置好了：

   - Rancher 会返回外部认证中含有您输入的用户名称的账户。

   - 您可以通过 UI 中的下拉菜单添加组，下拉菜单中显示的是组而不是用户，下拉菜单中仅会显示当前登录用户所在的组。

   > **说明：** 如果您以本地用户的方式登录 Rancher，搜索结果中不会显示外部用户。

4. 分配用户或用户组的项目角色。

   [什么是项目角色？](/docs/rancher2/admin-settings/rbac/cluster-project-roles/_index)

   > **说明：**
   >
   > - 被分配到 `Owner` 或 `Member` 角色的用户自动继承 `namespace creation` 角色。然而，这个角色是一个[Kubernetes ClusterRole](https://kubernetes.io/docs/reference/access-authn-authz/rbac/#role-and-clusterrole)，这意味它的作用范围会延伸到集群中的所有项目。因此，如果用户在一个项目中分配到了 `Owner` 或 `Member` 角色，而在同一个集群中的另一个项目中即使只分配到了 `Read Only` 权限，该用户还是可以在这个项目中创建命名空间。
   >
   > - 对于`自定义`角色，您可以修改可分配的单个角色的列表。
   >
   >   - 向这个列表中添加角色的详细步骤请参考[添加自定义角色](/docs/rancher2/admin-settings/rbac/default-custom-roles/_index)。
   >   - 将角色从这个列表中删除的详细步骤请参考[锁定/解锁角色](/docs/rancher2/admin-settings/rbac/locked-roles/_index)。

**结果：** 用户分配到了指定的角色，成为了指定项目的成员。

- 需要修改项目用户名单时，您可以选择用户，单击**删除**，把用户从项目成员中移除。这个操作会取消用户访问该项目的权限，而不是删除用户本身。
- 需要调整用户在项目内的角色时，您需要先将用户从成员名单中删除，再重新将用户和新角色添加到项目中。