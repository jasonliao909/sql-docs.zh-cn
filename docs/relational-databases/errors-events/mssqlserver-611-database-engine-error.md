---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c54c9e2f5e0e3d0a640935d80f22537a96876903
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "67903914"
---
# <a name="mssqlserver_611"></a>MSSQLSERVER_611
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|611|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|VAR_SIZE_TOO_BIG|  
|消息正文|无法插入或更新行，因为总可变列大小(包括系统开销)比限值多出 %d 个字节。|  
  
## <a name="explanation"></a>说明  
最大可变列大小超过架构所允许的大小。 当可变列超过启用 vardecimal 存储格式时的固定列大小限制，或可变列大小超过 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 对压缩数据记录所允许的限制时，将返回错误 611。  
  
## <a name="user-action"></a>用户操作  
减小记录的大小。  
  
