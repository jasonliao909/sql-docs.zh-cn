---
title: 示例：检索二进制数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c39f508d20e194b0031baecf168851cd300031e1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62704847"
---
# <a name="example-retrieving-binary-data"></a>示例：检索二进制数据
  下面的查询返回在 `varbinary(max)` 类型列中存储的产品照片。 在此查询中指定了 `BINARY BASE64` 选项，以便以 base64 编码格式返回二进制数据。  
  
## <a name="example"></a>示例  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 结果如下：  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a>另请参阅  
 [将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md)  
  
  
