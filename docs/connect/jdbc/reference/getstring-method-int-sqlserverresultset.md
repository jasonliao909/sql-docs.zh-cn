---
title: getString 方法 (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa493c4-fe07-449b-b4d0-384e1a1fce48
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3146c0874a6ba43d18f2fd4af2cca7533046c8b1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979504"
---
# <a name="getstring-method-int-sqlserverresultset"></a>getString 方法 (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索此 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象的当前行中指定列索引的值作为 Java 编程语言中的字符串  。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.lang.String getString(int columnIndex)  
```  
  
#### <a name="parameters"></a>parameters  
 columnIndex   
  
 指示列索引的 int  。  
  
## <a name="return-value"></a>返回值  
 一个字符串值  。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getString方法是由 java.sql.ResultSet 接口中的 getString 方法指定的。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的所有列都可作为字符串返回。 这意味着可以返回基于数字和基于字符的所有类型的字符串表示形式，以及二进制列的十六进制字符串表示形式，例如 binary、varbinary、varbinary(max)、image、timestamp 和 uniqueidentifier  。  
  
 位置敏感类型（例如 money、smallmoney, datetime、smalldatetime、float、real、decimal 和 numeric）将返回基础类型值的规范 toString() 格式。  
  
 用户定义类型将作为十六进制字符串值返回  。  
  
## <a name="see-also"></a>另请参阅  
 [getString 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
