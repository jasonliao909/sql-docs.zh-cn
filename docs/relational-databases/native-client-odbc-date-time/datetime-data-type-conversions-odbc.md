---
title: datetime 数据类型转换（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c5d601f53492b72efbcf730200fbd431f2649b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "73783918"
---
# <a name="datetime-data-type-conversions-odbc"></a>datetime 数据类型转换 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  以下转换或者已由 ODBC 定义，或者是 ODBC 的一致扩展。 每个访问接口提供的转换由该访问接口所服务的社区决定，因此，各个访问接口之间通常不一致。 方括号中的值是可选的。  
  
-   日期时间字符串的格式为 'yyyy-mm-dd[ hh:mm:ss[.9999999][ 加/减 hh:mm]]'  
  
-   时间字符串的格式为 'hh:mm:ss[.9999999]'  
  
-   日期字符串的格式为 'yyyy-mm-dd'  
  
 从字符串转换允许更灵活处理空格和字段宽度。 有关详细信息，请参阅[针对 ODBC 日期和时间改进的数据类型支持](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)中的 "数据格式：字符串和文字" 部分。  
  
 下面是一般的转换规则：  
  
-   如果未提供时间但接收方可存储时间，则将时间设置为零。  
  
-   如果不存在日期但接收方可以存储日期，则使用当前日期。  
  
-   如果客户端正在使用的数据类型中不存在时区，但服务器可以存储时区，则在客户端时区中存储日期。 请注意，此行为与服务器行为不同。  
  
-   如果服务器类型中不存在时区，但客户端类型具有时区，则先将时间转换为 UTC，再将其存储到服务器。  
  
-   如果存在时间但接收方无法存储时间，则忽略时间部分。  
  
-   如果存在日期但接收方无法存储日期，则忽略日期部分。  
  
-   如果在从 C 转换到 SQL 时截断了秒或秒的小数部分，则生成带有 SQLSTATE 22008 的诊断记录和消息“日期时间字段溢出”。  
  
-   如果在从 SQL 转换到 C 时截断了秒或秒的小数部分，则生成带有 SQLSTATE 01S07 的诊断记录和消息“截断小数部分”。  
  
## <a name="in-this-section"></a>本节内容  
 [由 C 转换为 SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
 列出了在从 C 类型转换到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/时间类型时要考虑的问题。  
  
 [由 SQL 转换为 C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
 列出了在从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/时间类型转换到 C 类型时要考虑的问题。  
  
## <a name="see-also"></a>另请参阅  
 [ODBC&#41;&#40;的日期和时间改进](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
