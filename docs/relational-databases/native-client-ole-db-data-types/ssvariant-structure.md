---
title: SSVARIANT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2298bbbfcdb4c0245d9b932152c21f39d7e884f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "73770744"
---
# <a name="ssvariant-structure"></a>SSVARIANT 结构
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  在 sqlncli.msi 中定义的**SSVARIANT**结构与[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB 访问接口中的 DBTYPE_SQLVARIANT 值相对应。  
  
 **SSVARIANT**是一个对比联合。 根据 vt 成员的值，使用者可以确定要读取的成员。 vt 值与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型相对应。 因此，SSVARIANT 结构可以具有任何 SQL Server 类型****。 有关标准 OLE DB 类型的数据结构的详细信息，请参阅[类型指示器](https://go.microsoft.com/fwlink/?LinkId=122171)。  
  
## <a name="remarks"></a>备注  
 如果 DataTypeCompat==80，几个 SSVARIANT 子类型都将成为字符串****。 例如，以下 vt 值将在 SSVARIANT 中显示为 VT_SS_WVARSTRING****：  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 如果 DateTypeCompat == 0，这些类型将按它们原来的形式显示。  
  
 有关 SSPROP_INIT_DATATYPECOMPATIBILITY 的详细信息，请参阅将[连接字符串关键字用于 SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。  
  
 Sqlncli.msi 文件包含可简化在**SSVARIANT**结构中取消引用成员类型的变体访问宏。 例如 V_SS_DATETIMEOFFSET，您可以按如下方式使用它：  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 有关**SSVARIANT**结构的每个成员的一组完整的 access 宏，请参阅 sqlncli.msi 文件。  
  
 下表介绍了 SSVARIANT 结构的成员****：  
  
|成员|OLE DB 类型指示器|OLE DB C 数据类型|vt 值|注释|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||指定 SSVARIANT 结构中包含的值类型****。|  
|bTinyIntVal|DBTYPE_UI1|**位**|**VT_SS_UI1**|支持**tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|sShortIntVal|DBTYPE_I2|**短暂**|**VT_SS_I2**|支持**smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|lIntVal|DBTYPE_I4|**漫长**|**VT_SS_I4**|支持**int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|支持**bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|支持**real** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|支持**float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|支持**money**和**smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|支持**位**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|rgbGuidVal|DBTYPE_GUID|**GUID.EMPTY**|**VT_SS_GUID**|支持**uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|支持**数值**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|dDateVal|DBTYPE_DATE|**为 DBDATE**|**VT_SS_DATE**|支持**date** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|支持**smalldatetime**、 **datetime**和**datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|支持**时间**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。<br /><br /> 包括以下成员：<br /><br /> *tTime2Val* （**DBTIME2**）<br /><br /> *bScale* （**BYTE**）指定*tTime2Val*值的小数位数。|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|支持**datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。<br /><br /> 包括以下成员：<br /><br /> *tsDataTimeVal* （DBTIMESTAMP）<br /><br /> *bScale* （**BYTE**）指定*tsDataTimeVal*值的小数位数。|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|支持**datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。<br /><br /> 包括以下成员：<br /><br /> *tsoDateTimeOffsetVal* （**DBTIMESTAMPOFFSET**）<br /><br /> *bScale* （**BYTE**）指定*tsoDateTimeOffsetVal*值的小数位数。|  
|NCharVal|没有对应的 OLE DB 类型指示器。|**结构 _NCharVal**|**VT_SS_WVARSTRING，**<br /><br /> **VT_SS_WSTRING**|支持**nchar**和**nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。<br /><br /> 包括以下成员：<br /><br /> *sActualLength* （**SHORT**）指定*pwchNCharVal*指向的字符串的实际长度。 不包括尾零。<br /><br /> *sMaxLength* （**SHORT**）指定*pwchNCharVal*指向的字符串的最大长度。<br /><br /> *pwchNCharVal* （**WCHAR** \*）指向字符串的指针。<br /><br /> 未使用的成员： *rgbReserved*、 *dwReserved*和*pwchReserved*。|  
|CharVal|没有对应的 OLE DB 类型指示器。|**结构 _CharVal**|**VT_SS_STRING，**<br /><br /> **VT_SS_VARSTRING**|支持**char**和**varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。<br /><br /> 包括以下成员：<br /><br /> *sActualLength* （**SHORT**）指定*pchCharVal*指向的字符串的实际长度。 不包括尾零。<br /><br /> *sMaxLength* （**SHORT**）指定*pchCharVal*指向的字符串的最大长度。<br /><br /> *pchCharVal* （**CHAR** \*）指向字符串的指针。<br /><br /> 不使用的成员：<br /><br /> *rgbReserved*、 *dwReserved*和*pwchReserved*。|  
|BinaryVal|没有对应的 OLE DB 类型指示器。|**结构 _BinaryVal**|**VT_SS_VARBINARY，**<br /><br /> **VT_SS_BINARY**|支持**binary**和**varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。<br /><br /> 包括以下成员：<br /><br /> *sActualLength* （**SHORT**）指定*prgbBinaryVal*指向的数据的实际长度。<br /><br /> *sMaxLength* （**SHORT**）指定*prgbBinaryVal*指向的数据的最大长度。<br /><br /> *prgbBinaryVal* （**BYTE** \*）指向二进制数据的指针。<br /><br /> 未使用的成员： *dwReserved*。|  
|UnknownType|不使用|不使用|不使用|不使用|  
|BLOBType|不使用|不使用|不使用|不使用|  
  
## <a name="see-also"></a>另请参阅  
 [数据类型 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
