---
title: SQLServerClob 构造函数 (SQLServerConnection, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7a539ef893788be9e0200b9f412f8c3ed7652b26
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971800"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>SQLServerClob 构造函数 (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  在给定 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverclob-class.md) 对象和数据字符串时，初始化 [SQLServerClob](../../../connect/jdbc/reference/sqlserverconnection-class.md) 类的新实例。  
  
> [!NOTE]  
>  JDBC 驱动程序 2.0 版已不推荐使用此方法， 而是使用 [SQLServerConnection](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) 类的 [createClob](../../../connect/jdbc/reference/sqlserverconnection-class.md) 方法。  
  
## <a name="syntax"></a>语法  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>parameters  
 连接   
  
 SQLServerConnection 对象。  
  
 data   
  
 CLOB 数据。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerClob 构造函数](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [SQLServerClob 成员](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 类](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
