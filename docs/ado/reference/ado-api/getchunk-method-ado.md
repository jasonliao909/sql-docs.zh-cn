---
title: GetChunk 方法（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43c5fef08d22364b9842c58fc82d46ba4bfa00bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918567"
---
# <a name="getchunk-method-ado"></a>GetChunk 方法 (ADO)
返回大文本或二进制数据[字段](../../../ado/reference/ado-api/field-object.md)对象的全部或部分内容。  
  
## <a name="syntax"></a>语法  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>返回值  
 返回**Variant**。  
  
#### <a name="parameters"></a>parameters  
 *大小*  
 一个**长整型**表达式，它等于要检索的字节数或字符数。  
  
## <a name="remarks"></a>备注  
 使用**Field**对象上的**GetChunk**方法检索其长整型或字符数据的部分或全部。 在系统内存有限的情况下，可以使用**GetChunk**方法在部分中（而不是在整个中）操作长值。  
  
 **GetChunk**调用返回的数据将分配给*变量*。 如果*Size*大于剩余数据，则**GetChunk**方法仅返回不含空格的空白*变量*的剩余数据。 如果该字段为空，则**GetChunk**方法返回 null 值。  
  
 每个后续的**GetChunk**调用都从上一个**GetChunk**调用停止的位置检索数据。 但是，如果您要从一个字段中检索数据，然后设置或读取当前记录中另一个字段的值，则 ADO 假设您已经完成了从第一个字段中检索数据的操作。 如果再次对第一个字段调用**GetChunk**方法，则 ADO 会将调用解释为新的**GetChunk**操作，并从数据的开头开始读取。 访问不是第一个**记录集**对象的克隆的其他[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象中的字段将不会中断**GetChunk**操作。  
  
 如果**字段**对象的[Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)属性中的**adFldLong**位设置为**True**，则可以对该字段使用**GetChunk**方法。  
  
 如果对**字段**对象使用**GetChunk**方法时没有当前记录，则会发生错误3021（无当前记录）。  
  
> [!NOTE]
>  **GetChunk**方法不对[Record](../../../ado/reference/ado-api/record-object-ado.md)对象的**字段**对象进行操作。 它不执行任何操作，并将生成运行时错误。  
  
## <a name="applies-to"></a>应用于  
 [字段对象](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>另请参阅  
 [AppendChunk 和 GetChunk 方法示例（VB）](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk 和 GetChunk 方法示例（VC + +）](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [AppendChunk 方法（ADO）](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Attributes 属性 (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
