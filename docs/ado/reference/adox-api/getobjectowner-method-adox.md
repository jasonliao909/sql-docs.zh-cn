---
title: GetObjectOwner 方法（ADOX） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff85491cf7ca30e3f95526aa7043f321a65cccc5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966277"
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner 方法 (ADOX)
返回[目录](../../../ado/reference/adox-api/catalog-object-adox.md)中对象的所有者。  
  
## <a name="syntax"></a>语法  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>返回值  
 返回一个**字符串**值，该值指定拥有对象的[用户](../../../ado/reference/adox-api/user-object-adox.md)或[组](../../../ado/reference/adox-api/group-object-adox.md)的[名称](../../../ado/reference/adox-api/name-property-adox.md)。  
  
#### <a name="parameters"></a>parameters  
 *ObjectName*  
 一个**字符串**值，该值指定要为其返回所有者的对象的名称。  
  
 *ObjectType*  
 一个**长整型**值，可以是[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)常量之一，用于指定要为其获取所有者的对象的类型。  
  
 *ObjectTypeId*  
 可选。 一个**变量**值，指定 OLE DB 规范未定义的提供程序对象类型的 GUID。 如果*ObjectType*设置为**adPermObjProviderSpecific**，则此参数是必需的;否则，不使用此方法。  
  
## <a name="remarks"></a>备注  
 如果提供程序不支持返回对象所有者，则会发生错误。  
  
## <a name="applies-to"></a>应用于  
 [目录对象 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>另请参阅  
 [GetObjectOwner 和 SetObjectOwner 方法示例（VB）](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner 方法](../../../ado/reference/adox-api/setobjectowner-method.md)
