---
title: Data File Auto Shrink 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Data File Auto Shrink event class
ms.assetid: ea02b01e-9f87-47ca-9117-afadc382fb45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b65f0200dd91c3813be405d9186543732eea6741
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62663156"
---
# <a name="data-file-auto-shrink-event-class"></a>Data File Auto Shrink 事件类
  **Data file 自动收缩**事件类指明数据文件已收缩。 如果通过显式 ALTER DATABASE 语句使数据文件收缩，则不会触发此事件。 
  **Data File Auto Shrink** 事件类包括在监视数据文件大小变化的跟踪中。  
  
 
  **Data File Auto Shrink** 事件类包括在跟踪中后，引发的开销量较低，除非数据文件频繁地收缩。  
  
## <a name="data-file-auto-shrink-event-class-data-columns"></a>Data File Auto Shrink 事件类的数据列  
  
|数据列名称|数据类型|说明|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|是|  
|**ClientProcessID**|**整形**|主机为运行该客户端应用程序的进程分配的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|是|  
|**DatabaseID**|**int**|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]如果在跟踪中捕获到**ServerName**数据列并且服务器可用，则将显示数据库的名称。 可使用 DB_ID 函数来确定数据库的值。|3|是|  
|**DatabaseName**|**nvarchar**|正在其中运行用户语句的数据库的名称。|35|是|  
|**Duration**|**bigint**|收缩文件的时间（毫秒）。|13|是|  
|**EndTime**|**datetime**|自动收缩的结束时间。|18|是|  
|**EventClass**|**int**|记录的事件类型 = 94。|27|否|  
|**EventSequence**|**int**|事件类在批处理中的顺序。|51|否|  
|**名字**|**nvarchar**|收缩的文件的逻辑名称。|36|是|  
|**HostName**|**nvarchar**|正在运行客户端的计算机的名称。 如果客户端提供主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|是|  
|**IntegerData**|**int**|文件减小的 8 KB 页数。|25|是|  
|**IsSystem**|**int**|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|是|  
|**LoginName**|**nvarchar**|用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。|11|是|  
|**LoginSid**|**图像**|登录用户的安全标识号 (SID)。 可以在**server_principals sys.databases**目录视图中找到此信息。 服务器中的每个登录名都具有唯一的 SID。|41|是|  
|**NTDomainName**|**nvarchar**|用户所属的 Windows 域。|7|是|  
|**ServerName**|**nvarchar**|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|否|  
|**SessionLoginName**|**nvarchar**|发起会话的用户的登录名。 例如，如果使用 Login1 连接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]并以 Login2 的身份执行语句，则**则 sessionloginname 将**将显示 Login1 和**LoginName**显示 Login2。 此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。|64|是|  
|**SPID**|**int**|发生该事件的会话的 ID。|12|是|  
|**StartTime**|**datetime**|该事件（如果存在）的启动时间。|14|是|  
  
## <a name="see-also"></a>另请参阅  
 [扩展事件](../extended-events/extended-events.md)   
 [sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
