---
title: sys. dm_filestream_file_io_requests （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_filestream_file_io_requests
- dm_filestream_file_io_requests
- sys.dm_filestream_file_io_requests_TSQL
- dm_filestream_file_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_requests catalog view
ms.assetid: d41e39a5-14d5-4f3d-a2e3-a822b454c1ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4fb51b33655756d9c3c65dfcb5de3bae380ee9a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67951038"
---
# <a name="sysdm_filestream_file_io_requests-transact-sql"></a>sys.dm_filestream_file_io_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  显示命名空间所有者 (NSO) 在给定时刻正处理的 I/O 请求的列表。  
  
|列|类型|说明|  
|------------|----------|-----------------|  
|**request_context_address**|**varbinary(8)**|显示包含来自驱动程序的 I/O 请求的 NSO 内存块的内部地址。 不可为 null。|  
|**current_spid**|**smallint**|显示当前 SQL Server 的连接的系统进程 id （SPID）。 不可为 null。|  
|**request_type**|**nvarchar （60）**|显示 I/O 请求包 (IRP) 类型。 可能的请求类型为 REQ_PRE_CREATE、REQ_POST_CREATE、REQ_RESOLVE_VOLUME、REQ_GET_VOLUME_INFO、REQ_GET_LOGICAL_NAME、REQ_GET_PHYSICAL_NAME、REQ_PRE_CLEANUP、 REQ_POST_CLEANUP、REQ_CLOSE、REQ_FSCTL、REQ_QUERY_INFO、REQ_SET_INFO、 REQ_ENUM_DIRECTORY、REQ_QUERY_SECURITY 和 REQ_SET_SECURITY。 不可为 Null。|  
|**request_state**|**nvarchar （60）**|显示 NSO 中 I/O 请求的状态。 可能的值为 REQ_STATE_RECEIVED、REQ_STATE_INITIALIZED、REQ_STATE_ENQUEUED、 REQ_STATE_PROCESSING、REQ_STATE_FORMATTING_RESPONSE、REQ_STATE_SENDING_RESPONSE、REQ_STATE_COMPLETING 和 REQ_STATE_COMPLETED。 不可为 null。|  
|request_id |**int**|显示驱动程序分配给此请求的唯一请求 ID。 不可为 null。|  
|**irp_id**|**int**|显示唯一 IRP ID。 该值用于标识与给定 IRP 相关的所有 I/O 请求。 不可为 null。|  
|**handle_id**|**int**|指示命名空间句柄 ID。 这是 NSO 特定的标识符，并且在实例之间是唯一的。 不可为 null。|  
|**client_thread_id**|**varbinary(8)**|显示发出请求的客户端应用程序的线程 ID。<br /><br /> ** \*警告\* \* **仅当客户端应用程序在与 SQL Server 相同的计算机上运行时，这才有意义。 当客户端应用程序远程运行时， **client_thread_id**显示代表远程客户端工作的某个系统进程的线程 id。<br /><br /> 可以为 Null。|  
|**client_process_id**|**varbinary(8)**|如果客户端应用程序在 SQL Server 所在的同一台计算机上运行，则显示客户端应用程序的进程 ID。 对于远程客户端，这将显示代表客户端应用程序工作的系统进程 ID。 可以为 Null。|  
|**handle_context_address**|**varbinary(8)**|显示与客户端的句柄关联的内部 NSO 结构的地址。 可以为 Null。|  
|**filestream_transaction_id**|**varbinary(128)**|显示与给定句柄相关联的事务的 ID 以及与该句柄相关联的所有请求。 它是**get_filestream_transaction_context**函数返回的值。 可以为 Null。|  
  
## <a name="permissions"></a>权限  
 要求具有服务器的 VIEW SERVER STATE 权限。  
  
## <a name="see-also"></a>另请参阅  
 [Filestream 和 FileTable 动态管理视图 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
