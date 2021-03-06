---
title: sys. database_automatic_tuning_options （Transact-sql） |Microsoft Docs
description: 了解如何在 SQL 数据库上查看自动优化选项
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 437dbbc4ea7deb32a9723febb443cc67941fdc5e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67940227"
---
# <a name="sysdatabase_automatic_tuning_options-transact-sql"></a>sys.databases\_自动\_tuning_options （transact-sql）
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  返回此数据库的自动优化选项。  

|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**路径名**|**nvarchar(128)**|自动优化选项的名称。 请参阅[ALTER DATABASE SET AUTOMATIC_TUNING &#40;transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)了解可用选项。|  
|**desired_state**|**smallint**|指示自动优化选项的所需操作模式，由用户显式设置。<br />0 = OFF<br />1 = ON|  
|**desired_state_desc**|**nvarchar （60）**|自动优化选项所需操作模式的文本说明。<br />OFF<br />ON|  
|**actual_state**|**smallint**|指示自动优化选项的操作模式。<br />0 = OFF<br />1 = ON|  
|**actual_state_desc**|**nvarchar （60）**|自动优化选项的实际操作模式的文本说明。<br />OFF<br />ON|  
|**在于**|**smallint**|指示实际和所需状态的不同原因。<br />2 = 已禁用<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar （60）**|实际和所需状态不同的原因的文本说明。<br />DISABLED = 选项已被系统禁用<br />QUERY_STORE_OFF = 查询存储已关闭<br />QUERY_STORE_READ_ONLY = 查询存储处于只读模式<br />NOT_SUPPORTED = 仅适用于[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>权限  
 需要 `VIEW DATABASE STATE` 权限。  
  
## <a name="see-also"></a>另请参阅  
 [自动优化](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [将数据库集 AUTOMATIC_TUNING &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys. database_query_store_options &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys. dm_db_tuning_recommendations &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
