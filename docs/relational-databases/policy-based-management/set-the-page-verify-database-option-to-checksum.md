---
title: 将 PAGE_VERIFY 数据库选项设置为 CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6d0491eb44eb2880927aef006ccc705230ab1940
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "68021656"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>将 PAGE_VERIFY 数据库选项设置为 CHECKSUM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  此规则检查 PAGE_VERIFY 数据库选项是否已设置为 CHECKSUM。 为 PAGE_VERIFY 数据库选项启用 CHECKSUM 后， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 会在向磁盘中写入页面时计算整个页面内容的校验并将该值存储在页头中。 从磁盘中读取页时，将重新计算校验和，并与存储在页头中的校验和值进行比较。 这有助于提供高级别的数据文件完整性。  
  
## <a name="best-practices-recommendations"></a>最佳做法建议  
 将 PAGE_VERIFY 数据库选项设置为 CHECKSUM。  
  
## <a name="for-more-information"></a>有关详细信息  
 [ALTER DATABASE SET 选项 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
