---
title: 表值参数的描述符字段
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 070029c5f1bf8445a699abacf61e6e988dbdbe2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "75246511"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>表值参数构成列的描述符字段
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  本部分中描述的表值参数描述符字段是通过将[SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)和[SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)与实现参数描述符（IPD）的句柄结合使用来进行操作的。  
  
## <a name="remarks"></a>备注  
 SQL_DESC_AUTO_UNIQUE_VALUE 用于表值参数以及其他功能。  
  
|属性名称|类型|说明|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE 指示该列是标识列。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可使用此信息来优化性能，但不要求应用程序为标识列设置该设置。|  
||||

 以下属性将添加到应用程序参数描述符 (APD) 和实现参数描述符 (IPD) 中的所有参数类型：  
  
|属性名称|类型|说明|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE 指示该列是计算列。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可使用此信息来优化性能，但不要求应用程序为计算列设置该设置。<br /><br /> 对于非表值参数列的绑定，将忽略此属性。|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE 指示表值参数列参与唯一键。 这可能导致查询性能提高。 对于非表值参数列的绑定，将忽略此属性。|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|指示表值参数列的排序顺序。 这可能导致查询性能提高。 对于非表值参数列的绑定，将忽略此属性。 下面列出了可能的值： <br />**SQL_SS_ASCENDING_ORDER**<br />**SQL_SS_DESCENDING_ORDER**<br />**SQL_SS_ORDER_UNSPECIFIED**<br /><br /> 除**SQL_SS_ASCENDING_ORDER**和**SQL_SS_DESCENDING_ORDER**以外的值还会生成**SQLSTATE HY024**和消息 "属性值无效" 的错误，并将其视为**SQL_SS_ORDER_UNSPECIFIED**，这是此属性的默认值。|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|指示表值参数列在列集中的序号，它定义表值参数的整体排序顺序。 这可能导致查询性能提高。 对于非表值参数列的绑定，将忽略此属性。 排序序号从 1 开始。 默认值 0 指示表值参数列未进行列排序。|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|指示表值参数中的所有行是否都将具有此列的默认值。 对于表值参数，无法逐行选择默认值。 值 SQL_FALSE 指示行将具有非默认值。 这是默认值。 值 SQL_TRUE 指示此列的所有行都将具有默认值。<br /><br /> 如果设置为 SQL_TRUE，则不会将任何数据发送到服务器。<br /><br /> 如果服务器处理不需要相应列值，则此字段还可以用于标识列或计算列。|  
||||

 这些属性仅对表值参数列有效。 对于其他参数，将忽略它们。  
  
 如果为表值参数列设置了 SQL_CA_SS_COL_HAS_DEFAULT_VALUE，则该列的 SQL_DESC_DATA_PTR 必须为 Null 指针。 否则，SQLExecute 或 SQLExecDirect 将返回 SQL_ERROR。 将使用 SQLSTATE = 07S01 生成诊断记录，并使用消息 " \<参数 p>，列\<c>" 的默认参数使用无效，其中\<p> 是参数序号， \<c> 为列序号。  
  
## <a name="see-also"></a>另请参阅  
 [ODBC&#41;&#40;表值参数](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
