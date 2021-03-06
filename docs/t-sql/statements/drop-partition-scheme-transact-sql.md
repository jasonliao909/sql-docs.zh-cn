---
title: DROP PARTITION SCHEME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP PARTITION SCHEME
- DROP_PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP PARTITION SCHEME statement
- deleting partition schemes
- dropping partition schemes
- removing partition schemes
- partition schemes [SQL Server], removing
ms.assetid: 6efbc87c-1c92-4e43-96a7-e0f30f1db185
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 709ba2af4cc06f1a1ff2314115f163032bd4227e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "68044026"
---
# <a name="drop-partition-scheme-transact-sql"></a>DROP PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从当前数据库中删除一个分区方案。 分区方案使用 [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) 创建，使用 [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md) 修改。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
DROP PARTITION SCHEME partition_scheme_name [ ; ]  
```  
  
## <a name="arguments"></a>参数  
 partition_scheme_name   
 要删除的分区方案的名称。  
  
## <a name="remarks"></a>备注  
 仅当不存在当前使用分区方案的表或索引时，才能删除分区方案。 如果存在使用分区方案的表或索引，DROP PARTITION SCHEME 将返回错误。 DROP PARTITION SCHEME 不删除文件组本身。  
  
## <a name="permissions"></a>权限  
 可以使用以下权限执行 DROP PARTITION SCHEME：  
  
-   ALTER ANY DATASPACE 权限。 默认情况下，此权限授予 **sysadmin** 固定服务器角色和 **db_owner** 及 **db_ddladmin** 固定数据库角色的成员。  
  
-   对创建分区方案时所在数据库的 CONTROL 或 ALTER 权限。  
  
-   对承载了创建分区方案时所在数据库的服务器的 CONTROL SERVER 或 ALTER ANY DATABASE 权限。  
  
## <a name="examples"></a>示例  
 以下示例从当前数据库中删除分区方案 `myRangePS1`：  
  
```  
DROP PARTITION SCHEME myRangePS1;  
```  
  
## <a name="see-also"></a>另请参阅  
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [ALTER PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [sys.partition_schemes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
