---
title: 书签 C 数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86488da93470a61a54638e9c60e6e1795a9da4dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125746"
---
# <a name="bookmark-c-data-type"></a>书签 C 数据类型
书签 C 数据类型允许应用程序检索书签。 书签 C 类型仅用于检索长度可变的书签值;不应将它们转换为其他数据类型。 应用程序通过**SQLBulkOperations** （操作为 SQL_ADD）、 **SQLFetch**、 **SQLFetchScroll**或**SQLGetData**，从结果集的列0检索书签。 有关详细信息，请参阅[书签](../../../odbc/reference/develop-app/bookmarks-odbc.md)。  
  
 下表列出了书签 C 数据类型的*CType*值、实现了书签 c 数据类型的 ODBC c 数据类型，以及 SQL 中此数据类型的定义。高.  
  
> [!NOTE]
>  SQL_C_BOOKMARK 的数据类型已弃用。 ODBC *2.x*应用程序不应使用 SQL_C_BOOKMARK。 仅当 ODBC 2.x 驱动程序需要使用 ODBC 2.x*应用程序时*，才需要支持*SQL_C_BOOKMARK。* 当应用程序*与 ODBC 2.x 驱动程序一起*使用时，驱动程序管理器会将 SQL_C_VARBOOKMARK 映射到 SQL_C_BOOKMARK。  
  
|C 类型标识符|ODBC C typedef|C 类型|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />（已弃用）|书签|无符号长整型|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|
