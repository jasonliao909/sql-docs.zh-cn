---
title: IDBProperties （OLE DB） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b6dada26e15fc83d890b270ad553eb051bb08fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62692181"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  OLE DB 标准规范允许提供程序为 `DBPROPINFO::vValues` 指定 VT_EMPTY。 但是， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]在调用`IDBProperties::GetPropertyInfo` `DBPROPSET_ROWSETALL`以检索行集属性时，Native Client OLE DB 始终返回 VT_EMPTY。  
  
## <a name="see-also"></a>另请参阅  
 [接口 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
