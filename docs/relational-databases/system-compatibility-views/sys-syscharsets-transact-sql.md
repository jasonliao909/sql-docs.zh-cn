---
title: sys. syscharsets （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscharsets
- syscharsets
- sys.syscharsets_TSQL
- syscharsets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscharsets system table
- sys.syscharsets compatibility view
ms.assetid: f16d987c-bd19-4668-9ef7-785b8fb9ff5b
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4332159765791addfdfcc32a9d19d29836f2460c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053541"
---
# <a name="syssyscharsets-transact-sql"></a>sys.syscharsets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  每个字符集都占一行，其中还包含定义以供 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]使用的排序顺序。 其中一个排序顺序在**sysconfigures**中标记为默认的排序顺序。 此排序顺序是实际使用的唯一排序顺序。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|type |**smallint**|此行表示的实体的类型：<br /><br /> 1001 = 字符集。<br /><br /> 2001 = 排序顺序。|  
|**识别**|**tinyint**|字符集或排序顺序的唯一 ID。 请注意，排序顺序和字符集不能共享相同的 ID 号。 从 1 至 240 的 ID 范围是保留给[!INCLUDE[ssDE](../../includes/ssde-md.md)]使用的。|  
|**csid**|**tinyint**|如果行表示字符集，则不使用此字段。 如果行表示排序顺序，则此字段为排序顺序据以生成的字符集的 ID。 假设此表中存在具有此 ID 的字符集行。|  
|**状态值**|**smallint**|内部系统状态信息位。|  
|**路径名**|**sysname**|字符集或排序顺序的唯一名称。 此字段必须只包含字母 A-Z 或 a-z、数字 0 - 9 以及下划线 (_)，并且必须以字母开始。|  
|**2008**|**nvarchar(255)**|字符集或排序顺序功能的说明（可选）。|  
|**binarydefinition**|**varbinary （6000）**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**定义**|**图像**|字符集或排序顺序的内部定义。 此字段中的数据结构取决于类型。|  
  
## <a name="see-also"></a>另请参阅  
 [将系统表映射到系统视图 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Transact-sql&#41;的兼容性视图 &#40;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
