---
title: 生成脚本向导支持的对象
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c14ea09d45c59def95f078eb87e72e2a70925892
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253762"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>生成脚本向导支持的对象
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  “生成和发布脚本向导”支持 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]所支持的对象的一个子集。  
  
## <a name="supported-objects"></a>支持的对象  
 下表列出“生成和发布脚本向导”支持的可发布对象。  
  
||||||  
|-|-|-|-|-|  
|应用程序角色|数据库角色|架构|用户定义聚合|视图*|  
|Assembly|DEFAULT 约束|存储过程*|用户定义数据类型|XML 架构集合|  
|CHECK 约束|全文目录|同义词|用户定义函数||  
|CLR（公共语言运行时）存储过程*|索引|表|用户定义表||  
|CLR 用户定义函数|规则|用户**|用户定义类型||  
  
 *已发布但未加密。  
  
 **数据库中存在的任何非系统用户将作为角色发布。  
  
  
