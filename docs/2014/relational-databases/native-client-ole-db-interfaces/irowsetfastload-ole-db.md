---
title: IRowsetFastLoad （OLE DB） |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35cee52e9a85989123bcb10d998d37ce86a28601
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63209815"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  `IRowsetFastLoad`接口公开对基于内存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的大容量复制操作的支持。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者使用接口将数据快速添加到现有[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]表中。  
  
 如果将会话的 SSPROP_ENABLEFASTLOAD 设置为 VARIANT_TRUE，则无法读取后续从该会话返回的行集中的数据。 将 SSPROP_ENABLEFASTLOAD 设置为 VARIANT_TRUE 时，在会话上创建的所有行集将属于 IRowsetFastLoad 类型。 IRowsetFastLoad 行集不支持行集提取功能，因此无法读取这些行集中的数据。  
  
## <a name="in-this-section"></a>本节内容  
  
|方法|说明|  
|------------|-----------------|  
|[IRowsetFastLoad：： Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|标记一批插入的行的末尾并将这些行写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。|  
|[IRowsetFastLoad：： InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|将行添加到大容量复制行集中。|  
  
## <a name="see-also"></a>另请参阅  
 [接口 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [使用 IRowsetFastLoad &#40;的批量复制数据 OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM &#40;OLE DB&#41;将 BLOB 数据发送到 SQL SERVER](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
