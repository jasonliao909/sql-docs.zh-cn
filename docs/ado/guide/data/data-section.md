---
title: Data 部分 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data section [ADO]
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6aebf318652e604c5f5ad4c30ef389fdfd9e78c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925643"
---
# <a name="data-section"></a>数据部分
Data 节定义行集的数据以及任何挂起的更新、插入或删除。 数据节可以包含零行或多行。 它只能包含一个行集中的数据，该行由架构定义。 另外，如上所述，可以省略没有任何数据的列。 如果在 data 节中使用了某个特性或子元素，并且该构造未在 schema 节中定义，则它将以无提示方式忽略。  
  
## <a name="string"></a>String  
 文本数据中的保留 XML 字符必须替换为相应的字符实体。 例如，在公司名称 "Joe，车库" 中，单引号必须替换为实体。 实际行如下所示：  
  
```  
<z:row CompanyName="Joe's Garage"/>  
```  
  
 以下字符在 XML 中保留，必须替换为字符实体： {"，"、&、\<>}。  
  
## <a name="binary"></a>Binary  
 二进制数据是 bin。十六进制编码（即，一个字节映射到两个字符，每个字节1个字符）。  
  
## <a name="datetime"></a>DateTime  
 XML 数据类型不直接支持 variant VT_DATE 格式。 数据和时间组件的日期的正确格式为 Yyyy-mm-ddthh： mm： ss。  
  
 有关 XML 指定的日期格式的详细信息，请参阅[W3C XML 数据规范](https://go.microsoft.com/fwlink/?LinkId=5692)。  
  
 如果 XML 数据规范定义了两个等效数据类型（例如，i4 = = int），则 ADO 将写出友好名称，但同时读入这两种数据类型。  
  
## <a name="managing-pending-changes"></a>管理挂起的更改  
 记录集可以在即时或批更新模式下打开。 当使用客户端游标在批处理更新模式下打开时，在调用 UpdateBatch 方法之前，对记录集所做的所有更改都处于挂起状态。 保存记录集后，还会保存挂起的更改。 在 XML 中，它们使用 urn：架构-microsoft-com：行集中定义的 "update" 元素来表示。 此外，如果可以更新行集，则必须在该行的定义中将可更新属性设置为 true。 例如，若要定义货主表包含挂起的更改，行定义将如下所示。  
  
```  
<s:ElementType name="row" content="eltOnly" updatable="true">  
  <s:attribute type="ShipperID"/>  
  <s:attribute type="CompanyName"/>  
  <s:attribute type="Phone"/>  
  <s:extends type="rs:rowbase"/>  
</s:ElementType>  
```  
  
 这会告诉永久性提供程序显示数据，以便 ADO 可以构造可更新的记录集对象。  
  
 下面的示例数据显示了在持久文件中的插入、更改和删除的外观。  
  
```  
<rs:data>  
  <z:row ShipperID="2" CompanyName="United Package"   
    Phone="(503) 555-3199"/>  
<rs:update>  
  <rs:original>  
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>  
  </rs:original>  
  <z:row Phone="(503) 552-7134"/>  
</rs:update>  
<rs:insert>  
  <z:row ShipperID="12" CompanyName="Lightning Shipping"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="13" CompanyName="Thunder Overnight"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="14" CompanyName="Blue Angel Air Delivery"   
    Phone="(505) 111-2222"/>  
</rs:insert>  
<rs:delete>  
  <z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/>  
</rs:delete>  
</rs:data>  
```  
  
 更新始终包含整个原始行数据，后跟已更改的行数据。 已更改的行可能包含所有列，或者只包含实际更改的那些列。 在上面的示例中，货主2的行未发生更改，并且只有 Phone 列已更改发货方3的值，因此在已更改的行中只包含一个列。 货主12、13和14的插入行在一个 rs： insert 标记下一起分批分批。 请注意，删除的行也可以一起分批显示，但在前面的示例中未显示这种情况。  
  
## <a name="see-also"></a>另请参阅  
 [以 XML 格式保留记录](../../../ado/guide/data/persisting-records-in-xml-format.md)
