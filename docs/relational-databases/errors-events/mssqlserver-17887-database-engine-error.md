---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: caf58e486706913fbaa8016e142f6aefc8bded3b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "68137205"
---
# <a name="mssqlserver_17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|17887|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|SRV_IO_COMP_LISTENER_NONYIELDING|  
|消息正文|节点 %ld 上的 IO 完成侦听器(0x%lx)工作线程 0x%p 似乎无法完成。 CPU 近似使用时间: 内核 %I64d 毫秒，用户 %I64d 毫秒，间隔: %I64d。|  
  
## <a name="explanation"></a>说明  
指示当为某一网络读/写事件执行 I/O 完成例程时，指定节点上的 I/O 完成端口侦听器可能出现了问题。 当 I/O 完成端口侦听器从执行 I/O 完成例程返回时，此错误将消失。  
  
## <a name="user-action"></a>用户操作  
请与 Microsoft 客户支持服务部门 (CSS) 联系。  
  
