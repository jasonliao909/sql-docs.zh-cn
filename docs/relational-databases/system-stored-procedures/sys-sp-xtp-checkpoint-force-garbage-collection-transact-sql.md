---
title: "sys.sp_xtp_checkpoint_force_garbage_collection (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection_TSQL
- sys.sp_xtp_checkpoint_force_garbage_collection
dev_langs: TSQL
helpviewer_keywords: sys.sp_xtp_checkpoint_force_garbage_collection
ms.assetid: 82b35b2b-edbd-44ac-9fc8-80695f2fd1df
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80b82684ab06f2ba9e748808a2286b38cee9d044
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysspxtpcheckpointforcegarbagecollection-transact-sql"></a>sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  为合并操作中使用的源文件标上日志序列号 (LSN)，此序号之后的文件将不再需要，可对其进行垃圾收集。 此外，它将关联 LSN 小于日志截断点的文件移至文件流垃圾收集。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 
## <a name="syntax"></a>语法  
  
```  
sys.sp_xtp_checkpoint_force_garbage_collection [[ @dbname=database_name]  
```  
  
## <a name="arguments"></a>参数  
 *database_name*  
 要对其运行垃圾收集的数据库。 默认为当前数据库。  
  
## <a name="return-code-values"></a>返回代码值  
 0 表示成功。 非零表示失败。  
  
## <a name="result-set"></a>结果集  
 返回的行包含以下信息：  
  
|列|Description|  
|------------|-----------------|  
|num_collected_items|指示已移至文件流垃圾收集的文件数。 这些文件的日志序列号 (LSN) 小于日志截断点的 LSN|  
|num_marked_for_collection_items|指示已使用日志结尾 LSN 的日志块 ID 更新其 LSN 的数据/差异文件数。|  
|last_collected_xact_seqno|返回上一个对应的 LSN，之前的文件已移至文件流垃圾收集。|  
  
## <a name="permissions"></a>Permissions  
 需要数据库所有者权限。  
  
## <a name="sample"></a>示例  
  
```  
exec [sys].[sp_xtp_checkpoint_force_garbage_collection] hkdb1  
```  
  
## <a name="see-also"></a>另请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [内存中 OLTP（内存中优化）](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  