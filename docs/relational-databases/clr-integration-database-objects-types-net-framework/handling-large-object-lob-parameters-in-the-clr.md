---
title: 在 CLR 中处理大型对象（LOB）参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: 64b890f7b4dd801a43c85f0375987c6ff5f5cd1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081330"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>在 CLR 中处理大型对象 (LOB) 参数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用**SqlBytes**和**SqlChars**分别传递大型对象（LOB）二进制类型（**varbinary （max）**）和 LOB 字符类型（**nvarchar （max）**）参数。 这些类型允许以流方式将 LOB 值从数据库传送到公共语言运行时 (CLR) 例程，而不是将整个值复制到托管空间中。 **SqlBinary**和**SqlString**只能用于小型二进制和字符串值。  
  
## <a name="see-also"></a>另请参阅  
 [.NET Framework 中的 SQL Server 数据类型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
