---
title: sys. filetable （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- filetables
- filetables_TSQL
- sys.filetables
- sys.filetables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetables catalog view
ms.assetid: a740be59-cd52-4707-9ad2-5203669a63ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 791bba2f5ec1830e343acff24fd55628a3f13d2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133999"
---
# <a name="sysfiletables-transact-sql"></a>sys.filetables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的每个 FileTable 返回一行。 有关 FileTable 的详细信息，请参阅 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)。    
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**object_id**||对象标识号。 在数据库中是唯一的。<br /><br /> 有关详细信息，请[&#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。|  
|**is_enabled**|**bit**|1 = FileTable 处于“已启用”状态。|  
|**directory_name**|**varchar （255）**|FileTable 的根目录名称。|  
|**filename_collation_id**||为 FileTable 定义的排序规则标识符|  
|**filename_collation_name**||为 FileTable 定义的排序规则名称。|  
  
## <a name="see-also"></a>另请参阅  
 [管理 Filetable](../../relational-databases/blob/manage-filetables.md)   
 [FileTables (SQL Server)](../../relational-databases/blob/filetables-sql-server.md)  
  
  
