---
title: 执行语句（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1517e17a7b0ecaf9137e3af21e076dacc2fd98f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68207066"
---
# <a name="executing-statements-odbc"></a>执行语句 (ODBC)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序提供了在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]数据库中执行 SQL 语句的多种方法：  
  
-   直接执行  
  
-   准备好的执行  
  
 直接执行涉及构建包含[!INCLUDE[tsql](../../../includes/tsql-md.md)]语句的字符串，并使用**SQLExecDirect**函数提交它以执行执行。 准备好的执行即生成一个包含 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句的字符串，然后分两个阶段执行。 第一个阶段使用[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)函数分析和编译中的语句的执行计划[!INCLUDE[ssDE](../../../includes/ssde-md.md)]。 第二个阶段使用**SQLExecute**函数执行之前准备好的执行计划。 这节省了每次执行的分析和编译开销。 应用程序通常使用准备好的执行来重复执行相同的参数化 SQL 语句。  
  
 直接执行和准备好的执行都可以执行单个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句或批处理 SQL 语句，也可以调用存储过程。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [直接执行](direct-execution.md)  
  
-   [准备好的执行](prepared-execution.md)  
  
-   [过程](procedures.md)  
  
-   [语句的批处理](batches-of-statements.md)  
  
-   [ISO 选项的作用](effects-of-iso-options.md)  
  
## <a name="see-also"></a>另请参阅  
 [&#40;ODBC&#41;执行查询](../executing-queries-odbc.md)  
  
  
