---
title: getNClob 方法 (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 10dfa251-9408-469e-ae2a-1acf3917cf47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63dbc19502ef0d22362008c67a17448bfa48d7f1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981524"
---
# <a name="getnclob-method-int"></a>getNClob 方法 (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索指定 JDBC NCLOB  参数作为 Java 编程语言中的 NClob 对象的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.NClob getNClob(int parameterIndex)  
```  
  
#### <a name="parameters"></a>parameters  
 parameterIndex   
  
 指示参数索引的 int  。  
  
## <a name="return-value"></a>返回值  
 NClob 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getNClob 方法是由 java.sql.CallableStatement 接口中的 getNClob 方法指定的。  
  
 此方法仅支持检索 NCHAR  、NVARCHAR  、NTEXT  和 XML  参数。 在其他数据类型参数上调用这些方法会引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [getNClob 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
