---
title: SQL_VARIANT_PROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQL_VARIANT_PROPERTY_TSQL
- SQL_VARIANT_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SQL_VARIANT_PROPERTY function
- sql_variant data type
ms.assetid: 50e5c1d9-4e95-4ed0-9c92-435c872a399e
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 22b11ff1f9a6ed218b4c63c2f22bfb6e2d441703
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "74550199"
---
# <a name="sql_variant_property-transact-sql"></a>SQL_VARIANT_PROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回有关 sql_variant 值的基本数据类型和其他信息  。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
SQL_VARIANT_PROPERTY ( expression , property )  
```  
  
## <a name="arguments"></a>参数  
 *expression*  
 sql_variant 类型的表达式  。  
  
 *property*  
 包含将为其提供信息的 sql_variant 属性的名称  。 property 的数据类型为 varchar(128)，可以是下列任何值之一    ：  
  
|值|说明|返回的 sql_variant 基类型|  
|-----------|-----------------|----------------------------------------|  
|**BaseType**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型，例如：<br /><br /> **bigint**<br /><br /> **binary**<br /><br /> **char**<br /><br /> **date**<br /><br /> **datetime**<br /><br /> **datetime2**<br /><br /> **datetimeoffset**<br /><br /> **decimal**<br /><br /> **float**<br /><br /> **int**<br /><br /> **money**<br /><br /> **nchar**<br /><br /> **numeric**<br /><br /> **nvarchar**<br /><br /> **real**<br /><br /> **smalldatetime**<br /><br /> **smallint**<br /><br /> **smallmoney**<br /><br /> **time**<br /><br /> **tinyint**<br /><br /> **uniqueidentifier**<br /><br /> **varbinary**<br /><br /> **varchar**|**sysname**<br /><br /> NULL = 输入无效。|  
|**精度**|数值基本数据类型的位数：<br /><br /> datetime = 23 <br /><br />**datetime2** = 27<br /><br /> smalldatetime = 16 <br /><br /> float = 53 <br /><br /> real = 24 <br /><br /> decimal (p,s) 和 numeric (p,s) = p  <br /><br /> money = 19 <br /><br /> smallmoney = 10 <br /><br /> bigint = 19 <br /><br /> int = 10 <br /><br /> smallint = 5 <br /><br /> tinyint = 3 <br /><br /> bit = 1 <br /><br /> 所有其他类型 = 0|**int**<br /><br /> NULL = 输入无效。|  
|**缩放**|数值基本数据类型的小数点后的位数：<br /><br /> decimal (p,s) 和 numeric (p,s) = s  <br /><br /> money 和 smallmoney = 4  <br /><br /> datetime = 3 <br /><br />**datetime2** = 7<br /><br /> 所有其他类型 = 0|**int**<br /><br /> NULL = 输入无效。|  
|**TotalBytes**|同时容纳值的元数据和数据所需的字节数。 在检查 sql_variant 列中数据的最大一侧时，该信息很有用  。 如果该值大于 900，则索引创建会失败。|**int**<br /><br /> NULL = 输入无效。|  
|**排序规则**|代表特定 sql_variant 值的排序规则  。|**sysname**<br /><br /> NULL = 输入无效。|  
|**MaxLength**|最大数据类型长度（字节）。 例如，nvarchar(50) 的 MaxLength 是 100，int 的 MaxLength 是 4      。|**int**<br /><br /> NULL = 输入无效。|  
  
## <a name="return-types"></a>返回类型  
 **sql_variant**  
  
## <a name="examples"></a>示例  
### <a name="a-using-a-sql_variant-in-a-table"></a>A. 在表中使用 sql_variant  
 以下示例检索有关 `SQL_VARIANT_PROPERTY` 值 `colA` 的 `46279.1` 信息，其中，`colB` =`1689`，并假设 `tableA` 有类型为 `colA` 和 `sql_variant` 的 `colB`。  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]请注意，这三个值中的每一个都是 sql_variant  。  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sql_variant-as-a-variable"></a>B. 使用 sql_variant 作为变量   
 以下示例检索有关名为 `SQL_VARIANT_PROPERTY` 的变量的 @v1 信息。  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```  
  
## <a name="see-also"></a>另请参阅  
 [sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)  
  
  

