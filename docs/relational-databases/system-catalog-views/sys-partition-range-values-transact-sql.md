---
title: sys. partition_range_values （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.partition_range_values
- partition_range_values_TSQL
- partition_range_values
- sys.partition_range_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_range_values catalog view
ms.assetid: 9aee483e-61f3-4613-bec6-f084161f45ac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c071a09f7b70499b8d869f4763448572b20cfcd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102216"
---
# <a name="syspartition_range_values-transact-sql"></a>sys.partition_range_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  类型为 R 的分区函数的每个范围边界值都在表中占一行。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|该范围边界值的分区函数的 ID。|  
|**boundary_id**|**int**|边界值元组的 ID（从 1 开始的序号），最左边界以值为 1 的 ID 开始。|  
|**parameter_id**|**int**|该值所对应的函数参数的 ID。 此列中的值与任何特定**function_id**的**sys.databases partition_parameters**目录视图的**parameter_id**列中的值相对应。|  
|**负值**|**sql_variant**|实际的边界值。|  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;分区函数目录视图](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. partition_functions &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys. partition_parameters &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
