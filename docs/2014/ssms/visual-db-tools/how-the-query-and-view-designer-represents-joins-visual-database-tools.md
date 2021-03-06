---
title: 查询和视图设计器如何表示联接（Visual Database Tools） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abd8dd7c3c23a13b1cdff7a2d6f76fb99375a641
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63155255"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a>查询和视图设计器如何表示联接 (Visual Database Tools)
  如果对表进行了联接， [查询和视图设计器](visual-database-tools.md) 将在[“关系图”](diagram-pane-visual-database-tools.md) 窗格中以图形方式表示联接，并在 [SQL 窗格](sql-pane-visual-database-tools.md)中使用 SQL 语法表示联接。  
  
## <a name="diagram-pane"></a>“关系图”窗格  
 在“关系图”窗格中，查询和视图设计器在联接所涉及的数据列之间显示一条联接线。 查询和视图设计器为每个联接条件显示一条联接线。 例如，下图阐释两个联接的表之间的联接线：  
  
 ![联接线显示两个表之间的关系](../../database-engine/media//dv3wbig.gif "联接线显示两个表之间的关系")  
  
 如果用多个联接条件联接表，则查询和视图设计器将显示多条联接线，如下例所示：  
  
 ![使用多个联接条件联接的表](../../database-engine/media//dv3w9n1.gif "使用多个联接条件联接的表")  
  
 如果没有显示联接的数据列（例如，表示表或表结构对象的矩形已最小化，或者联接涉及表达式），则查询和视图设计器会将联接线放到表示表或表结构对象的矩形的标题栏中。  
  
 联接线中间的图标形状指示表或表结构对象的联接方式。 如果联接子句使用等号 (=) 以外的运算符，则该运算符将出现在联接线图标中。 下表列出了在联接线上显示的图标。  
  
|**联接线图标**|**说明**|  
|------------------------|---------------------|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbih.gif "可视化数据库工具图标")|内部联接（用等号创建）。|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbii.gif "可视化数据库工具图标")|基于“大于”运算符的内部联接。|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbij.gif "可视化数据库工具图标")|外部联接，其中包括左侧表示的表中的所有行，即使它们在相关表中没有匹配行。|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbik.gif "可视化数据库工具图标")|外部联接，其中包括右侧表示的表中的所有行，即使它们在相关表中没有匹配行。|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbil.gif "可视化数据库工具图标")|完全外部联接，其中包括两个表中的所有行，即使它们在相关表中没有匹配行。|  
  
 联接线末端的符号指示联接类型。 下表列出联接类型和在联接线末端显示的图标。  
  
|**联接线末端的图标**|**联接类型**|  
|-----------------------------------|----------------------|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbim.gif "可视化数据库工具图标")|一对一联接。|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbin.gif "可视化数据库工具图标")|一对多联接。|  
|![Visual Database Tools 图标](../../database-engine/media//dv3wbio.gif "可视化数据库工具图标")|查询和视图设计器无法确定联接类型。 这种情况最常发生在手动创建联接时。|  
  
## <a name="sql-pane"></a>SQL 窗格  
 在 SQL 语句中，可以采用许多方式表达联接。 确切的语法取决于所使用的数据库以及定义联接的方式。  
  
 联接表的语法选项包括：  
  
-   **From 子句的联接限定符**。   关键字 INNER 和 OUTER 指定联接类型。 此语法是 ANSI 92 SQL 的标准语法。  
  
     例如，如果基于每个表中的 `publishers` 列联接 `pub_info` 和 `pub_id` 表，所得到的 SQL 语句可能类似于以下形式：  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     如果创建外部联接，将显示关键字 LEFT OUTER 或 RIGHT OUTER 来代替关键字 INNER。  
  
-   **WHERE 子句比较两个表中的列**。   如果数据库不支持 JOIN 语法（或用户自己输入该语法），将显示 WHERE 子句。 如果联接是在 WHERE 子句中创建的，则两个表名都出现在 FROM 子句中。  
  
     例如，下面的语句联接 `publishers` 和 `pub_info` 表。  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [利用联接查询 &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)   
 [“联接”对话框 (Visual Database Tools)](join-dialog-box-visual-database-tools.md)  
  
  
