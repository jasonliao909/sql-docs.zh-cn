---
title: “执行 SQL Server 代理作业”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 33f037f4d82cbf5bbdebde01a5c4492128ecc8ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206026"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a>“执行 SQL Server 代理作业”任务（维护计划）
  使用 "**执行 SQL Server 代理作业任务**" 对话框可以执行维护计划中的 Microsoft SQL Server 代理作业。 如果所选连接上没有 SQL Server 代理作业，此选项将不可用。  
  
 此任务将使用 **.sp_start_job** 语句。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **连接**  
 选择执行此任务时使用的服务器连接。  
  
 **新建**  
 创建一个新的服务器连接，在执行此任务时使用。 下面对 **“新建连接”** 对话框进行了介绍。  
  
 **可用的 SQL 代理作业**  
 选择要执行的作业。 该网格提供用于标识作业的 **“作业名称”** 和 **“说明”** 。  
  
 **查看 T-sql**  
 根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。  
  
> [!NOTE]  
>  当受影响的对象很多时，可能需要相当长的时间才可显示。  
  
## <a name="new-connection-dialog-box"></a>“新建连接”对话框  
 **连接名称**  
 输入新连接的名称。  
  
 **选择或输入服务器名称**  
 选择执行此任务时所要连接的服务器。  
  
 **“刷新”**  
 刷新可用服务器的列表。  
  
 **输入用于登录到服务器的信息**  
 指定如何对服务器进行身份验证。  
  
 **使用 Windows 集成安全性**  
 使用 Microsoft Windows 身份验证连接[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]到的实例。  
  
 **使用特定的用户名和密码**  
 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。 此选项不可用。  
  
 **用户名**  
 提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。 此选项不可用。  
  
 **权限**  
 提供一个在进行身份验证时要使用的密码。 此选项不可用。  
  
## <a name="see-also"></a>另请参阅  
 [sp_add_job &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)   
 [创建作业](../../ssms/agent/create-a-job.md)   
 [sp_start_job &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
