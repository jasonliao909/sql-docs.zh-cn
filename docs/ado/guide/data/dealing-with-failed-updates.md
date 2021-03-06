---
title: 处理失败的更新 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d442a9c397ad184658f9101343e139697c9b3756
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925638"
---
# <a name="dealing-with-failed-updates"></a>处理失败的更新
如果更新结束时出现错误，则解决这些错误的方式取决于错误的性质和严重性以及应用程序的逻辑。 但是，如果数据库与其他用户共享，则典型的错误是，其他人在执行此操作之前会修改该字段。 这种类型的错误被称为冲突。 ADO 检测到这种情况并报告错误。  
  
## <a name="remarks"></a>备注  
 如果存在更新错误，将在错误处理例程中捕获这些错误。 筛选包含 adFilterConflictingRecords 常量的记录集，以便仅显示冲突的行。 在此示例中，错误解决策略只是打印作者的名字和姓氏（au_fname 和 au_lname）。  
  
 提醒用户发生更新冲突的代码如下所示：  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>另请参阅  
 [批处理模式](../../../ado/guide/data/batch-mode.md)
