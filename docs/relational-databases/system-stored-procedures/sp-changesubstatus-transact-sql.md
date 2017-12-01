---
title: "sp_changesubstatus (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
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
- sp_changesubstatus
- sp_changesubstatus_TSQL
helpviewer_keywords: sp_changesubstatus
ms.assetid: 9370e47a-d128-4f15-9224-1c3642770c39
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9fb31421c8f9398e259b41f652d13a5ff8d565b5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="spchangesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更改现有订阅服务器的状态。 在发布服务器的发布数据库上执行此存储的过程。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_changesubstatus [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
        , [ @status = ] 'status'  
    [ , [ @previous_status = ] 'previous_status' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @distribution_jobid = ] distribution_jobid ]  
    [ , [ @from_auto_sync = ] from_auto_sync ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @offloadagent= ] remote_agent_activation ]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] dts_package_location ]  
    [ , [ @skipobjectactivation = ] skipobjectactivation  
  [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>参数  
 [  **@publication=**] *发布*  
 发布的名称。 *发布*是**sysname**，默认值为 **%** 。 如果*发布*未指定，则所有发布会受到都影响。  
  
 [  **@article=**] *文章*  
 项目的名称。 该名称对发布必须是唯一的。 *文章*是**sysname**，默认值为 **%** 。 如果*文章*未指定，则会影响所有项目。  
  
 [  **@subscriber=**] *订阅服务器*  
 要更改其状态的订阅服务器的名称。 *订阅服务器*是**sysname**，默认值为 **%** 。 如果*订阅服务器*未指定，则状态将用于所有订阅服务器更改为指定的文章。  
  
 [  **@status =**] *状态*  
 是中的订阅状态**syssubscriptions**表。 *状态*是**sysname**，无默认值，并且可为这些值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**活动**|订阅服务器已被同步并且正在接收数据。|  
|**非活动状态**|存在订阅服务器项，但没有订阅。|  
|**订阅**|订阅服务器正在请求数据，但尚未同步。|  
  
 [  **@previous_status=**] *previous_status*  
 订阅的以前的状态。 *previous_status*是**sysname**，默认值为 NULL。 此参数使你可以更改任何当前具有该状态，因此并组功能允许一组特定的订阅的订阅 (例如，设置所有活动订阅回**订阅**)。  
  
 [  **@destination_db=**] *destination_db*  
 目标数据库的名称。 *destination_db*是**sysname**，默认值为 **%** 。  
  
 [  **@frequency_type=**] *frequency_type*  
 安排分发任务所使用的频率。 *frequency_type*是**int**，默认值为 NULL。  
  
 [  **@frequency_interval=**] *frequency_interval*  
 是要应用于通过设置的频率的值*frequency_type*。 *frequency_interval*是**int**，默认值为 NULL。  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 分发任务的日期。 使用此参数时*frequency_type*设置为 32 （每月相对）。 *frequency_relative_interval*是**int**，并且可以为这些值之一。  
  
|值|说明|  
|-----------|-----------------|  
|**1**|第一个|  
|**2**|第二个|  
|**4**|第三个|  
|**8**|第四个|  
|**16**|上一次|  
|NULL（默认值）||  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 是由重复因素*frequency_type*。 *frequency_recurrence_factor*是**int**，默认值为 NULL。  
  
 [  **@frequency_subday=**] *frequency_subday*  
 在定义周期内重新调度的频率（分钟）。 *frequency_subday*是**int**，并且可以为这些值之一。  
  
|值|说明|  
|-----------|-----------------|  
|**1**|一次|  
|**2**|第二个|  
|**4**|Minute|  
|**8**|Hour|  
|NULL（默认值）||  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 是的间隔*frequency_subday*。 *frequency_subday_interval*是**int**，默认值为 NULL。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 第一次安排分发任务的时间，格式为 HHMMSS。 *active_start_time_of_day*是**int**，默认值为 NULL。  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 停止安排分发任务的时间，格式为 HHMMSS。 *active_end_time_of_day*是**int**，默认值为 NULL。  
  
 [  **@active_start_date=**] *active_start_date*  
 第一次安排分发任务的日期，格式为 YYYYMMDD。 *active_start_date*是**int**，默认值为 NULL。  
  
 [  **@active_end_date=**] *active_end_date*  
 停止安排分发任务的日期，格式为 YYYYMMDD。 *active_end_date*是**int**，默认值为 NULL。  
  
 [  **@optional_command_line=**] *optional_command_line*  
 可选的命令提示符。 *optional_command_line*是**nvarchar （4000)**，默认值为 NULL。  
  
 [  **@distribution_jobid=**] *distribution_jobid*  
 将订阅状态从非活动设置为活动时，订阅的分发服务器上分发代理的作业 ID。 在其他情况下，不定义该参数。 如果对此存储过程的单个调用中涉及多个分发代理，则不定义结果。 *distribution_jobid*是**binary （16)**，默认值为 NULL。  
  
 [  **@from_auto_sync=**] *from_auto_sync*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@offloadagent=** ] *remote_agent_activation*  
 > [!NOTE]  
>  已不推荐使用远程代理激活，也不再支持该功能。 支持此参数只是为了让脚本能够向后兼容。 设置*remote_agent_activation*到以外的其他值**0**生成错误。  
  
 [  **@offloadserver=** ] *remote_agent_server_name*  
 > [!NOTE]  
>  已不推荐使用远程代理激活，也不再支持该功能。 支持此参数只是为了让脚本能够向后兼容。 设置*remote_agent_server_name*为任何非 NULL 值生成一个错误。  
  
 [  **@dts_package_name** =] *dts_package_name*  
 指定 Data Transformation Services (DTS) 包的名称。 *dts_package_name*是**sysname**，默认值为 NULL。 例如，对于名为包**DTSPub_Package**会指定`@dts_package_name = N'DTSPub_Package'`。  
  
 [  **@dts_package_password** =] *dts_package_password*  
 指定包上的密码。 *dts_package_password*是**sysname**默认值为 NULL，它指定密码属性是保持不变。  
  
> [!NOTE]  
>  DTS 包必须具有密码。  
  
 [  **@dts_package_location** =] *dts_package_location*  
 指定包位置。 *dts_package_location*是**int**，默认值为**0**。 如果**0**，包位置为分发服务器。 如果**1**，包位置为订阅服务器。 包的位置可以是**分发服务器**或**订阅服务器**。  
  
 [  **@skipobjectactivation** =] *skipobjectactivation*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@distribution_job_name=** ] *distribution_job_name*  
 分发作业的名称。 *distribution_job_name*是**sysname**，默认值为 NULL。  
  
 [  **@publisher** =] *发布服务器*  
 指定一个非[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]发布服务器。 *发布服务器*是**sysname**，默认值为 NULL。  
  
> [!NOTE]  
>  *发布服务器*上更改项目属性时不应使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]发布服务器。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>注释  
 **sp_changesubstatus**快照复制和事务复制中使用。  
  
 **sp_changesubstatus**中的订阅服务器的状态更改**syssubscriptions**具有已更改状态表。 如果需要，则会更新中的文章状态**sysarticles**表，以指示活动或非活动。 如果需要，它复制中设置标志打开或关闭**sysobjects**复制的表的表。  
  
## <a name="permissions"></a>Permissions  
 只有的成员**sysadmin**固定服务器角色、 **db_owner**固定的数据库角色或订阅的创建者可以执行**sp_changesubstatus**。  
  
## <a name="see-also"></a>另请参阅  
 [sp_addsubscription &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  