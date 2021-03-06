---
title: 在 Active Directory 模式下管理大数据群集
description: 管理对大数据群集的访问
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9f9cca7e761b8f8ec3f5b87e9a195a0eb8b5da6d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "76259455"
---
# <a name="manage-big-data-cluster-access-in-active-directory-mode"></a>在 Active Directory 模式下管理大数据群集

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

本文介绍如何更新 clusterAdmins 和 clusterUsers 部署过程中提供的 Active Directory 组。

## <a name="two-overarching-roles-in-the-big-data-cluster"></a>大数据群集中的两个主要角色

可以在部署配置文件的“安全”部分中提供 Active Directory 组，这是大数据群集中授权的两个主要角色的一部分：

* `clusterAdmins`设置用户帐户 ：此参数采用一个 Active Directory 组。 此组的成员将获取整个群集的管理员权限。 它们具有 SQL Server 中的 sysadmin 权限、Hadoop 分布式文件系统 (HDFS) 和 Spark 中的超级用户权限，以及控制器中的管理员权限。

* `clusterUsers`设置用户帐户 ：这些 Active Directory 组是在群集中不具有管理员权限的普通用户。 它们有权登录到 SQL Server 主实例，但默认情况下，它们无权访问对象或数据。

在部署后向大数据群集授予其他 Active Directory 组权限的一种方法是，在部署过程中将其他用户和组添加到已命名的组。 

但是，管理员不一定总是能在 Active Directory 中更改组成员身份。 若要在不改变 Active Directory 内的组成员身份的情况下授予其他 Active Directory 组权限，请完成后续部分中的过程。

## <a name="grant-administrator-permissions-to-additional-active-directory-groups"></a>向其他 Active Directory 组授予管理员权限

>[!IMPORTANT]
>此过程不会授予对大数据群集中的 Hadoop 组件（例如 HDFS 和 Spark）的其他 Active Directory 组管理员访问权限。 这些组件只允许将一个 Active Directory 组作为超级用户组。 此限制意味着，即使在执行此步骤之后，在部署期间 `clusterAdmins` 中指定的组也将始终作为超级用户组。

按照本节中的过程操作后，可以授予管理员对控制器和 SQL Server 主实例的访问权限。

### <a name="create-a-login-for-the-active-directory-user-or-group-in-the-sql-server-master-instance"></a>为 SQL Server 主实例中的 Active Directory 用户或组创建登录名 

1. 使用你最喜欢的 SQL 客户端连接到主 SQL 终结点。 使用任何管理员登录名（例如，在部署期间提供的 `AZDATA_USERNAME`）。 或者，它可以是属于安全配置中作为 `clusterAdmins` 提供的 Active Directory 组的任何 Active Directory 帐户。

1. 若要为 Active Directory 用户或组创建登录名，请运行以下 TSQL 命令：

   ```sql
   CREATE LOGIN [<domain>\<principal>] FROM WINDOWS;
   ```

   如果要在 SQL Server 实例中授予管理员权限，还应授予以下权限：

   ```sql
   ALTER SERVER ROLE sysadmin ADD MEMBER [<domain>\<principal>];
   GO
   ```

### <a name="add-the-active-directory-user-or-group-to-the-roles-table-in-the-controller-database"></a>将 Active Directory 用户或组添加到控制器数据库的角色表中 

1. 通过运行以下命令获取控制器 SQL Server 凭据：

   a. 以 Kubernetes 管理员身份运行以下命令：

   ```bash
   kubectl get secret controller-sa-secret -n <cluster name> -o yaml | grep password
   ```

   b. Base64 解码机密：

   ```bash
   echo <password from kubectl command>  | base64 --decode && echo
   ```

1. 在单独的命令窗口中，公开控制器数据库服务器端口：

   ```bash
   kubectl port-forward controldb-0 1433:1433 --address 0.0.0.0 -n <cluster name>
   ```

1. 使用前面的连接将行插入到角色表中。 以大写字母形式键入 REALM 值。

   如果要授予管理员权限，请使用 \<角色名称> 中的 bdcAdmin 角色。 对于非管理员用户，请使用 bdcUser 角色。

   ```sql
   USE controller;
   GO

   INSERT INTO [controller].[auth].[roles] VALUES (N'<user or group name>@<REALM>', N'<role name>')
   GO
   ```

1. 登录到控制器终结点并运行以下命令，验证你添加的组的成员是否具有大数据群集管理员权限：

   ```bash
   azdata bdc config show
   ```

1. 对于非管理员用户，可以使用 `azdata login` 对 SQL 主实例或控制器进行身份验证，从而验证访问权限。

## <a name="next-steps"></a>后续步骤

- [SQL Server 2019 大数据群集的安全性概念](concept-security.md)
