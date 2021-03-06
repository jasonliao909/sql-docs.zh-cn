---
title: LIKE 转义序列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 629ceaf666ae732d0838a216272c308dcb5b5658
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041709"
---
# <a name="like-escape-sequence"></a>LIKE 转义序列
ODBC 对 LIKE 子句使用转义序列。 此转义序列的语法如下所示：  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>备注  
 在 BNF 表示法中，语法如下：  
  
 *类似 ODBC-escape* ：： =  
  
 *Odbc-esc-发起程序*转义符 \*转义*符 ' *odbc-esc-终止符*  
  
 *转义*符：： =*字符*  
  
 *ODBC-esc-发起方*：： = {  
  
 *ODBC-esc-终止符*：： =}  
  
 若要确定驱动程序是否支持类似的转义序列，应用程序可以使用 SQL_LIKE_ESCAPE_CLAUSE 信息类型调用**SQLGetInfo** 。
