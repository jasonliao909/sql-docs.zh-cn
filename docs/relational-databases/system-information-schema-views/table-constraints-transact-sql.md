---
title: TABLE_CONSTRAINTS （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLE_CONSTRAINTS
- TABLE_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.TABLE_CONSTRAINTS view
- TABLE_CONSTRAINTS view
ms.assetid: 687f3284-2849-4853-8a5c-fc936deceae0
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 05580f7687d61557325ae720ea8e638f9186a867
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078446"
---
# <a name="table_constraints-transact-sql"></a>TABLE_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  为当前数据库中的每个表约束返回一行。 该信息架构视图返回当前用户对其拥有权限的对象的相关信息。  
  
 若要从这些视图中检索信息，请指定 INFORMATION_SCHEMA 的完全限定名称 **。**_view_name_。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar （** 128 **）**|约束限定符。|  
|**CONSTRAINT_SCHEMA**|**nvarchar （** 128 **）**|包含该约束的架构的名称。<br /><br /> <strong> \* \*重要\*提示</strong>不要使用 INFORMATION_SCHEMA 视图来确定对象的架构。 查找对象架构的唯一可靠方法是查询 sys.databases 目录视图。|  
|**CONSTRAINT_NAME**|**sysname**|约束名称。|  
|**TABLE_CATALOG**|**nvarchar （** 128 **）**|表限定符。|  
|**TABLE_SCHEMA**|**nvarchar （** 128 **）**|包含该表的架构的名称。<br /><br /> <strong> \* \*重要\*提示</strong>不要使用 INFORMATION_SCHEMA 视图来确定对象的架构。 查找对象架构的唯一可靠方法是查询 sys.databases 目录视图。|  
|**TABLE_NAME**|**sysname**|表名。|  
|**CONSTRAINT_TYPE**|**varchar （** 11 **）**|约束的类型：<br /><br /> CHECK<br /><br /> UNIQUE<br /><br /> PRIMARY KEY<br /><br /> FOREIGN KEY|  
|**IS_DEFERRABLE**|**varchar （** 2 **）**|指定限制检查是否可延迟。 始终返回 NO。|  
|**INITIALLY_DEFERRED**|**varchar （** 2 **）**|指定是否首先延迟约束检查。 始终返回 NO。|  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;的系统视图 &#40;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [&#40;Transact-sql&#41;的信息架构视图](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. key_constraints &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys. check_constraints &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
