---
title: Type 属性（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ee1058299becb4a7a4234debc097516cb02dd41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937865"
---
# <a name="type-property-ado"></a>Type 属性 (ADO)
指示[参数](../../../ado/reference/ado-api/parameter-object.md)、[字段](../../../ado/reference/ado-api/field-object.md)或[属性](../../../ado/reference/ado-api/property-object-ado.md)对象的操作类型或数据类型。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回一个[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)值。  
  
## <a name="remarks"></a>备注  
 对于**参数**对象，**类型**属性是可读/写的。 对于附加到[记录](../../../ado/reference/ado-api/record-object-ado.md)的[字段](../../../ado/reference/ado-api/fields-collection-ado.md)集合的新**字段**对象，在指定了**字段**的[值](../../../ado/reference/ado-api/value-property-ado.md)属性并且数据提供程序已通过调用**Fields**集合的[Update](../../../ado/reference/ado-api/update-method.md)方法成功添加了新**字段**之后，**类型**为 read/write。  
  
 对于所有其他对象， **Type**属性为只读。  
  
## <a name="applies-to"></a>应用于  
  
||||  
|-|-|-|  
|[字段对象](../../../ado/reference/ado-api/field-object.md)|[Parameter 对象](../../../ado/reference/ado-api/parameter-object.md)|[属性对象 (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>另请参阅  
 [Type 属性示例（字段）（VB）](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Type 属性示例（属性）（VC + +）](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType 属性（ADO）](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type 属性（ADO 流）](../../../ado/reference/ado-api/type-property-ado-stream.md)
