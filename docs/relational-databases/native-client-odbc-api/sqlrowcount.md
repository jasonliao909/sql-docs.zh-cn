---
title: SQLRowCount |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 676e2cc86a6b41a1bc778160611a9a967336390f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "73785689"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  当参数值的数组绑定到语句执行时，如果参数值的任意行在语句执行中生成错误条件，则**SQLRowCount**将返回 SQL_ERROR。 不通过函数的*RowCountPtr*参数返回值。  
  
 应用程序可以利用 SQL_ATTR_PARAMS_PROCESSED_PTR 语句属性捕获在错误发生之前已处理的参数个数。  
  
 此外，应用程序还可以使用由状态值构成的数组（通过使用 SQL_ATTR_PARAM_STATUS_PTR 语句属性进行绑定），来捕获生成错误的参数行的数组偏移量。 应用程序可以遍历状态数组以确定已处理的实际行数。  
  
 当执行[!INCLUDE[tsql](../../includes/tsql-md.md)]包含 output 子句的 INSERT、UPDATE、DELETE 或 MERGE 语句时，SQLRowCount 将不会返回受影响的行数，直到输出子句生成的结果集中的所有行都已被使用。 若要要使用这些行，请调用 SQLFetch 或 SQLFetchScroll。 SQLResultCols 将返回-1，直到使用完所有结果行为止。 在 SQLFetch 或 SQLFetchScroll 返回 SQL_NO_DATA 之后，应用程序必须调用 SQLRowCount 来确定受影响的行数，然后再调用 SQLMoreResults 以移到下一个结果。  
  
## <a name="see-also"></a>另请参阅  
 [SQLRowCount 函数](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API 实现细节](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
