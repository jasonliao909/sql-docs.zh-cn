---
title: DefinedSize 属性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4bfb0db701801f1853009594b9d6d24aeb41c629
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933214"
---
# <a name="definedsize-property"></a>DefinedSize 属性
指示[Field](../../../ado/reference/ado-api/field-object.md)对象的数据容量。  
  
## <a name="return-value"></a>返回值  
 返回一个**长整型**值，该值反映字段的定义大小，该字段依赖于 field 对象的数据类型;有关详细信息，请参阅[类型](../../../ado/reference/ado-api/type-property-ado.md)。 对于使用固定长度的数据类型的字段，返回值为数据类型的大小（以字节为单位）。 对于使用可变长度数据类型的字段，这是以下项之一：  
  
1.  字段的长度（对于**adVarChar**和**adVarWChar**）或以字节表示的最大长度（对于**adVarBinary**，和**adVarNumeric**）。 例如， **adVarChar （5）** 字段的最大长度为5。  
  
2.  数据类型的最大长度（对于**adChar**和**adWChar**）或以字节表示的最大长度（对于**adBinary**和**adNumeric**）。  
  
3.  ~ 0 （位值，值不为 0; 所有位均设置为1），前提是该字段和数据类型都没有定义的最大长度。  
  
4.  对于没有长度的数据类型，此值设置为 ~ 0 （位，值不为 0; 所有位均设置为1）。  
  
## <a name="remarks"></a>备注  
 使用**DefinedSize**属性可确定**Field**对象的数据容量。  
  
 **DefinedSize**和[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)属性不同。 例如，假设某个**字段**对象的类型为**adVarChar** ， **DefinedSize**属性值为50，其中包含单个字符。 它返回的**ActualSize**属性值是单个字符的长度（以字节为单位）。  
  
## <a name="applies-to"></a>应用于  
 [字段对象](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>另请参阅  
 [ActualSize 和 DefinedSize 属性示例（VB）](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize 和 DefinedSize 属性示例（VC + +）](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [ActualSize 属性 (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
