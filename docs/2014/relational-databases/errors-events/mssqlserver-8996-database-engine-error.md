---
title: MSSQLSERVER_8996 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8996 (Database Engine error)
ms.assetid: 4e655cdc-945a-4a18-95dd-75f050563d26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41f92430eecb0eb06fbca18bbb552a2e85ce6069
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62761831"
---
# <a name="mssqlserver_8996"></a>MSSQLSERVER_8996
    
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|8996|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP|  
|消息正文|对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）的 IAM 页 P_ID 控制着文件组 FG_ID1 中的页，这些页应该在文件组 FG_ID2 中。|  
  
## <a name="explanation"></a>说明  
 文件组 *FG_ID1* 中的索引分配映射 (IAM) 页 *P_ID* 错误地包括了文件组 *FG_ID2* 的区数。 IAM 页的所有区都应该在与 IAM 页本身相同的文件组中。  
  
## <a name="user-action"></a>用户操作  
  
### <a name="look-for-hardware-failure"></a>查找硬件故障  
 运行硬件诊断并更正任何问题。 也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。 修复日志中包含的所有与硬件相关的问题。  
  
 如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。 进行检查以确保系统未启用磁盘控制器上的写缓存。 如果怀疑写入缓存是问题起因，请与硬件供应商联系。  
  
 最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。 此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。  
  
### <a name="restore-from-backup"></a>从备份还原  
 如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。  
  
### <a name="run-dbcc-checkdb"></a>运行 DBCC CHECKDB  
 不适用。 无法修复此错误。 如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。  
  
  
