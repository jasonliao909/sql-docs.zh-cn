---
title: sp_check_for_sync_trigger （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe8cf327ff3db175c57382201ca3918a86770433
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "72251243"
---
# <a name="sp_check_for_sync_trigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  确定是否正在用于立即更新订阅的复制触发器的上下文中调用用户定义的触发器或存储过程。 该存储过程在发布服务器的发布数据库中或在订阅服务器的订阅数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>参数  
 [**@tabid =** ]'*tabid*'  
 正对检查即时更新触发器的表的对象 ID。 *tabid*的值为**int** ，无默认值。  
  
 [**@trigger_op =** ]"*trigger_output_parameters*" 输出  
 指定输出参数是否返回正在调用它的触发器的类型。 *trigger_output_parameters*为**char （10）** ，可以是下列值之一。  
  
|值|说明|  
|-----------|-----------------|  
|**插件**|INSERT 触发器|  
|**Upd**|UPDATE 触发器|  
|**Del**|DELETE 触发器|  
|NULL（默认值）||  
  
`[ @fonpublisher = ] fonpublisher`指定执行存储过程的位置。 *fonpublisher*的值为**bit**，默认值为0。 如果为 0，则在订阅服务器上执行；如果为 1，则在发布服务器上执行。  
  
## <a name="return-code-values"></a>返回代码值  
 0 指示在即时更新触发器的上下文中未调用此存储过程。 1指示正在即时更新触发器的上下文中调用该触发器，它是* \@trigger_op*中返回的触发器的类型。  
  
## <a name="remarks"></a>备注  
 **sp_check_for_sync_trigger**用于快照复制和事务复制。  
  
 **sp_check_for_sync_trigger**用于在复制和用户定义的触发器之间进行协调。 此存储过程确定它是否正在复制触发器的上下文中被调用。 例如，可以在用户定义的触发器体中调用过程**sp_check_for_sync_trigger** 。 如果**sp_check_for_sync_trigger**返回**0**，则用户定义的触发器将继续进行处理。 如果**sp_check_for_sync_trigger**返回**1**，则用户定义的触发器将退出。 这将确保当复制触发器更新表时不会激发用户定义触发器。  
  
## <a name="example"></a>示例  
 以下示例说明了可在订阅服务器表的触发器中使用的代码。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>示例  
 还可以将代码添加到发布服务器上的表中的触发器;此代码类似，但对**sp_check_for_sync_trigger**的调用包含附加参数。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>权限  
 在[sys.databases](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)系统视图中具有 SELECT 权限的任何用户都可以执行**sp_check_for_sync_trigger**存储过程。  
  
## <a name="see-also"></a>另请参阅  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
