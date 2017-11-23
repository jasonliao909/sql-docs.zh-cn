---
title: "sp_dsninfo (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords: sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4882ce3dd87c60f4fceaeb2b770c8879fadf3b78
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="spdsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从与当前服务器关联的分发服务器中返回 ODBC 或 OLE DB 数据源信息。 此存储过程在分发服务器上的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>参数  
 [  **@dsn =**] *dsn*  
 ODBC DSN 或 OLE DB 链接服务器的名称。 *dsn*是**varchar （128)**，无默认值。  
  
 [  **@infotype =**] *info_type*  
 是要返回类型。 如果*info_type*未指定或如果指定 NULL，则返回所有信息类型。 *info_type*是**varchar （128)**，默认值为 NULL，并且可以为这些值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**DBMS_NAME**|指定数据源供应商名称。|  
|**DBMS_VERSION**|指定数据源版本。|  
|**DATABASE_NAME**|指定数据库名。|  
|**SQL_SUBSCRIBER**|指定数据源可以是订阅服务器。|  
  
 [  **@login =**] *登录*  
 数据源的登录名。 如果数据源包括登录名，则指定 NULL 或忽略该参数。 *登录名*是**varchar （128)**，默认值为 NULL。  
  
 [  **@password =**] *密码*  
 登录名的密码。 如果数据源包括登录名，则指定 NULL 或忽略该参数。 *密码*是**varchar （128)**，默认值为 NULL。  
  
 [  **@dso_type=**] *dso_type*  
 为数据源类型。 *dso_type*是**int**，并且可以为这些值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**1** （默认值）|ODBC 数据源|  
|**3**|OLE DB 数据源|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**信息类型**|**nvarchar(64)**|信息类型，如 DBMS_NAME、DBMS_VERSION、DATABASE_NAME 和 SQL_SUBSCRIBER。|  
|**值**|**nvarchar(512)**|关联的信息类型的值。|  
  
## <a name="remarks"></a>注释  
 **sp_dsninfo**在所有类型的复制中使用。  
  
 **sp_dsninfo**检索显示是否可以执行复制或查询中使用数据库的 ODBC 或 OLE DB 数据源信息。  
  
## <a name="permissions"></a>Permissions  
 只有的成员**sysadmin**固定的服务器角色可以执行**sp_dsninfo**。  
  
## <a name="see-also"></a>另请参阅  
 [sp_enumdsn &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  