---
title: sys. dm_database_encryption_keys （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2c66fbc1cdf98d45a7440d2def9cb3fd1be5635a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68255750"
---
# <a name="sysdm_database_encryption_keys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回与数据库加密状态以及相关联数据库加密密钥有关的信息。 有关数据库加密的详细信息，请参阅[透明数据加密 (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)。  
 
|列名|数据类型|说明|  
|-----------------|---------------|-----------------|  
|database_id|**int**|数据库 ID。|  
|encryption_state|**int**|指示数据库是加密的还是未加密的。<br /><br /> 0 = 不存在数据库加密密钥，未加密<br /><br /> 1 = 未加密<br /><br /> 2 = 正在进行加密<br /><br /> 3 = 已加密<br /><br /> 4 = 正在更改密钥<br /><br /> 5 = 正在进行解密<br /><br /> 6 = 正在进行保护更改（正在更改对数据库加密密钥进行加密的证书或非对称密钥）。|  
|create_date|**datetime**|显示加密密钥的创建日期（UTC）。|  
|regenerate_date|**datetime**|显示重新生成加密密钥的日期（UTC）。|  
|modify_date|**datetime**|显示加密密钥的修改日期（UTC）。|  
|set_date|**datetime**|显示加密密钥应用于数据库的日期（UTC）。|  
|opened_date|**datetime**|显示上次打开数据库密钥的时间（UTC）。|  
|key_algorithm|**nvarchar （32）**|显示用于密钥的算法。|  
|key_length|**int**|显示密钥的长度。|  
|encryptor_thumbprint|**varbinary （20）**|显示加密程序的指纹。|  
|encryptor_type|**nvarchar （32）**|**适用范围**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]到[当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)）。<br /><br /> 描述加密程序。|  
|percent_complete|**实际上**|数据库加密状态更改的完成百分比。 如果未发生状态更改，则为 0。|
|encryption_state_desc|**nvarchar （32）**|**适用于**：[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 及更高版本。<br><br> 指示数据库是否已加密或未加密的字符串。<br><br>无<br><br>未加密<br><br>过<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**适用于**：[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 及更高版本。<br><br>指示加密扫描的当前状态。 <br><br>0 = 未启动任何扫描，TDE 未启用<br><br>1 = 正在进行扫描。<br><br>2 = 正在进行扫描，但已挂起，用户可以继续。<br><br>3 = 扫描已成功完成，TDE 已启用并且加密已完成。<br><br>4 = 由于某种原因，扫描已中止，需要手动干预。 请联系 Microsoft 支持部门以获得更多帮助。|
|encryption_scan_state_desc|**nvarchar （32）**|**适用于**：[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 及更高版本。<br><br>指示加密扫描当前状态的字符串。<br><br> 无<br><br>RUNNING<br><br>SUSPENDED<br><br>完成<br><br>ABORTED|
|encryption_scan_modify_date|**datetime**|**适用于**：[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 及更高版本。<br><br> 显示上次修改加密扫描状态的日期（UTC）。|
  
## <a name="permissions"></a>权限

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要权限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高级层上，需要`VIEW DATABASE STATE`具有数据库中的权限。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   

## <a name="see-also"></a>另请参阅  

 [与安全性相关的动态管理视图和函数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [透明数据加密 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL Server 加密](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server 和数据库加密密钥（数据库引擎）](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE SET 选项 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [&#40;Transact-sql&#41;创建数据库加密密钥](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-sql&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
