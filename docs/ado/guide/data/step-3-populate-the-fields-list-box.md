---
title: 步骤3：填充 "字段" 列表框 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d7f351b90030e755dde8ad13905ef4533eff08e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924051"
---
# <a name="step-3-populate-the-fields-list-box"></a>步骤 3：填充字段列表框
若要填充 "字段" 列表框，请将以下代码插入到的 Click `lstMain`事件处理程序中：  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 此代码将分别声明并实例化本地记录和`rec`记录`rs`集对象。  
  
 与中`lstMain`所选资源相对应的行成为的当前行`grs`。 然后，"详细信息" 列表框`rec`将被清除，并以的`grs`当前行作为源打开。  
  
 如果资源是由[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)指定的集合记录，则会在记录的子级`rs`上打开本地记录集。然后`lstDetails` ，将用的行中的值填充`rs`。  
  
 如果资源是简单记录， `recFields`则调用。 有关的详细信息`recFields`，请参阅下一步。  
  
 如果资源是结构化文档，则不实现任何代码。  
  
## <a name="see-also"></a>另请参阅  
 [Internet 发布方案](../../../ado/guide/data/internet-publishing-scenario.md)   
 [步骤2：初始化主列表框](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [步骤 4：填充详细信息文本框](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
