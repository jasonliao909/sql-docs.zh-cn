---
title: SQLError 映射 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f24a305c2f22ef4cfacbbe4bcbcf498eab648f1c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064468"
---
# <a name="sqlerror-mapping"></a>SQLError 映射
当应用程序*通过 ODBC 1.x*驱动程序调用**SQLError**时，调用  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 映射到  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 根据需要，将*HandleType*参数设置为值 SQL_HANDLE_ENV、SQL_HANDLE_DBC 或 SQL_HANDLE_STMT，并根据需要将*HANDLE*参数设置为*henv*、 *hdbc*或*hstmt*中的值。 *RecNumber*参数由驱动程序管理器决定。
