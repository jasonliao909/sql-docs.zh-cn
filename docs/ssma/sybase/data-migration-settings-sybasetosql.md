---
title: 数据迁移设置（SybaseToSQL） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9fcf6142a0df913c33782b4c65e8e95d4fcf91ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029385"
---
# <a name="data-migration-settings-sybasetosql"></a>数据迁移设置 (SybaseToSQL)
  
## <a name="data-migration-settings"></a>数据迁移设置  
**数据迁移设置**允许用户编写自定义查询以进行数据迁移。  
  
-   当 "**扩展数据迁移选项**" 设置为 "**显示**" 时，此选项卡可用，在项目设置中设置为 "**隐藏**" 时，此选项卡处于隐藏状态。 有关项目迁移设置的详细信息，请参阅[项目设置（迁移）](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924) 。  
  
-   自定义 SQL 语句的分析将在表节点的 "**数据迁移设置**" 选项卡中实现。  
  
-   以下是**数据迁移设置**即中可用的两个复选框：  
  
    1.  截断 SQL Server 表  
  
    2.  使用自定义选择  
  
1.  **截断表 SQL Server：**  
     使用此选项，用户可以清楚地查看目标数据库上已迁移的数据。  
  
    -   默认情况下，此文本框处于选中状态。  
  
    -   如果未选中此文本框，则迁移的数据将添加到目标数据库中的现有数据。  
  
2.  **使用自定义选择：**  
     此选项允许用户修改**select**语句（**select**语句允许用户选择要在目标数据库上显示的数据）。  
  
    1.  默认情况下，此 textbox 处于未选中状态。  
  
    2.  如果选中此文本框，则允许用户修改显示的**select**语句。  
  
即提供了两个按钮：  
  
-   **应用：** 单击 "**应用**" 以应用已更改的设置。  
  
-   **取消：** 单击 "**取消**" 以还原在进行更改之前显示的设置。  
  
## <a name="see-also"></a>另请参阅  
[将 Sybase 数据迁移到 SQL Server/SQL Azure](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)  
  
