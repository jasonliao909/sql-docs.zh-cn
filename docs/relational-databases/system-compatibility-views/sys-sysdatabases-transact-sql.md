---
title: sys. sysdatabases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b0dab1ca5f21ced6a54192a4b0173ead68fd6f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089165"
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  实例[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的每个数据库在各占一行。 首[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次安装时， **sysdatabases**包含**master**、 **model**、 **msdb**和**tempdb**数据库的条目。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**路径名**|**sysname**|数据库名称|  
|**dbid**|**smallint**|数据库 ID|  
|**sid**|**varbinary （85）**|数据库创建者的系统 ID|  
|**众**|**smallint**|用于创建数据库时在内部锁定该数据库。|  
|**状态值**|**int**|状态位，其中一些可以通过使用[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)设置，如以下所示：<br /><br /> 1 = **autoclose** （ALTER DATABASE）<br /><br /> 4 = **select into/bulkcopy** （使用集恢复更改数据库）<br /><br /> 8 = **chkpt. 上的 trunc** （使用 SET RECOVERY 更改数据库）<br /><br /> 16 =**残缺页检测**（更改数据库）<br /><br /> 32 =**正在加载**<br /><br /> 64 =**预恢复**<br /><br /> 128 = 正在**恢复**<br /><br /> 256 =**未恢复**<br /><br /> 512 =**脱机**（更改数据库）<br /><br /> 1024 =**只读**（更改数据库）<br /><br /> 2048 =**仅供 dbo 使用**（使用 SET RESTRICTED_USER 更改数据库）<br /><br /> 4096 =**单用户**（更改数据库）<br /><br /> 32768 =**紧急模式**<br /><br /> 65536 =**校验和**（更改数据库）<br /><br /> 4194304 = 自动**收缩**（ALTER DATABASE）<br /><br /> 1073741824 =**干净关闭**<br /><br /> 可以同时打开多个位。|  
|**status2**|**int**|16384 = **ANSI null 默认值**（更改数据库）<br /><br /> 65536 = **concat null 生成 null** （ALTER DATABASE）<br /><br /> 131072 =**递归触发器**（更改数据库）<br /><br /> 1048576 =**本地游标的默认值**（更改数据库）<br /><br /> 8388608 =**带引号的标识符**（ALTER DATABASE）<br /><br /> 33554432 =**提交时关闭游标**（ALTER database）<br /><br /> 67108864 = **ANSI nulls** （ALTER DATABASE）<br /><br /> 268435456 = **ANSI 警告**（ALTER DATABASE）<br /><br /> 536870912 =**启用全文**（使用**sp_fulltext_database**设置）|  
|**crdate**|**datetime**|创建日期|  
|**保护**|**datetime**|保留供将来使用。|  
|**类别**|**int**|包含用于复制的信息位图：<br /><br /> 1 = 为快照或事务复制而发布。<br /><br /> 2 = 订阅快照或事务发布。<br /><br /> 4 = 为合并复制而发布。<br /><br /> 8 = 订阅合并发布。<br /><br /> 16 = 发布数据库。|  
|**cmptlevel**|**tinyint**|数据库的兼容级别。 有关详细信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)。|  
|**名字**|**nvarchar(260)**|数据库主文件的操作系统路径和名称。<br /><br /> **filename**对**dbcreator**、 **SYSADMIN**、具有 CREATE any database 权限的数据库所有者或具有以下权限之一的被授权者可见： ALTER any DATABASE，CREATE any database，VIEW any DEFINITION。 若要返回路径和文件名，请查询[sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md)兼容性视图或 " [sys. database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) " 视图。|  
|**版本**|**smallint**|用于创建数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代码的内部版本号。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>另请参阅  
 [ALTER DATABASE &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [将系统表映射到系统视图 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Transact-sql&#41;的兼容性视图 &#40;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
