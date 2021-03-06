---
title: sys. dm_os_threads （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ef8eeeaaf59934d6c3307641b6c93f110ab5738f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982542"
---
# <a name="sysdm_os_threads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程中运行的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 操作系统线程的列表。  
  
> [!NOTE]  
>  若要从[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]调用此，请使用名称**dm_pdw_nodes_os_threads**。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|thread_address|**varbinary(8)**|线程的内存地址（主键）。|  
|started_by_sqlservr|**bit**|指示线程发起方。<br /><br /> 1 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动了线程。<br /><br /> 0 = 其他组件启动了线程，例如，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的扩展存储过程。|  
|os_thread_id|**int**|操作系统分配的线程 ID。|  
|status|**int**|内部状态标志。|  
|instruction_address|**varbinary(8)**|当前执行的指令的地址。|  
|creation_time|**datetime**|该线程的创建时间。|  
|kernel_time|**bigint**|该线程占用的内核时间。|  
|usermode_time|**bigint**|该线程占用的用户时间。|  
|stack_base_address|**varbinary(8)**|该线程的最高堆栈地址在内存中的位置。|  
|stack_end_address|**varbinary(8)**|该线程的最低堆栈地址在内存中的位置。|  
|stack_bytes_committed|**int**|在堆栈中提交的字节数。|  
|stack_bytes_used|**int**|线程目前使用的字节数。|  
|affinity|**bigint**|该线程运行时使用的 CPU 掩码。 这取决于**ALTER SERVER CONFIGURATION SET PROCESS 地缘**语句配置的值。 在软关联的情况下，可能与计划程序不同。|  
|优先度|**int**|该线程的优先级值。|  
|Locale|**int**|线程的缓存区域设置 LCID。|  
|令牌|**varbinary(8)**|线程的缓存模拟令牌句柄。|  
|is_impersonating|**int**|指示该线程是否使用 Win32 模拟。<br /><br /> 1 = 该线程使用与进程默认的安全凭据不同的安全凭据。 这表明线程正在模拟创建该进程的实体以外的其他实体。|  
|is_waiting_on_loader_lock|**int**|指示线程是否正在等待加载程序锁的操作系统状态。|  
|fiber_data|**varbinary(8)**|线程当前运行的 Win32 纤程。 只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置了轻型池时，这才适用。|  
|thread_handle|**varbinary(8)**|仅限内部使用。|  
|event_handle|**varbinary(8)**|仅限内部使用。|  
|scheduler_address|**varbinary(8)**|与该线程关联的计划程序的内存地址。 有关详细信息，请参阅[sys.databases&#41;dm_os_schedulers &#40;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)。|  
|worker_address|**varbinary(8)**|绑定到该线程的工作线程的内存地址。 有关详细信息，请参阅[sys.databases&#41;dm_os_workers &#40;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)。|  
|fiber_context_address|**varbinary(8)**|内部纤程上下文地址。 只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置了轻型池时，这才适用。|  
|self_address|**varbinary(8)**|内部一致性指针。|  
|processor_group|**smallint**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 处理器组 ID。|  
|pdw_node_id|**int**|**适用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分发所在的节点的标识符。|  
  
## <a name="permissions"></a>权限

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要权限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高级层上，需要`VIEW DATABASE STATE`具有数据库中的权限。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   

## <a name="notes-on-linux-version"></a>Linux 版本上的说明

由于 SQL 引擎在 Linux 中的工作原理，某些信息与 Linux 诊断数据不匹配。 例如， `os_thread_id`与工具（如`ps`）`top`或 procfs （/proc/`pid`）的结果不匹配。  这是由于平台抽象层（SQLPAL）、SQL Server 组件和操作系统之间的一层。

## <a name="examples"></a>示例  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在启动时将启动线程，然后将工作与这些线程进行关联。 但是，外部组件（如扩展存储过程）可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程中启动线程。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法控制这些线程。 sys. dm_os_threads 可以提供有关使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]进程中的资源的恶意线程的信息。  
  
 下面的查询用于查找正在运行非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动的线程的工作以及执行的时间。  
  
> [!NOTE]
>  为清晰起见，下面的查询在 `*` 语句中使用星号 (`SELECT`)。 应避免使用星号 (*)，尤其是对目录视图、动态管理视图和系统表值函数。 将来的[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]升级和版本可能会添加列并将列的顺序更改为这些视图和函数。 这些更改可能会中断需要特定顺序和列数的应用程序。  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>另请参阅  
  [sys. dm_os_workers &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [&#40;Transact-sql 的与操作系统相关的动态管理视图 SQL Server&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


