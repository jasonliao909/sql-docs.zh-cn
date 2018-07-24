---
title: 创建 CHECK 约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- table constraints [SQL Server]
- attaching check constraints
- columns [SQL Server], constraints
- constraints [SQL Server], check
- CHECK constraints, attaching
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e355da0fcc4e94386ca19e2ff5c6ace928216953
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37262333"
---
# <a name="create-check-constraints"></a>创建 CHECK 约束
  您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在表中创建 CHECK 约束以便指定在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的一列或多列中可接受的数据值。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [Security](#Security)  
  
-   **使用以下工具创建新的 CHECK 约束：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要具有表的 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-create-a-new-check-constraint"></a>创建新的 CHECK 约束  
  
1.  在“对象资源管理器”中，展开要为其添加 CHECK 约束的表，右键单击“约束”，然后单击“新建约束”。  
  
2.  在 “CHECK 约束”对话框中，单击“表达式”字段，然后单击省略号 **(…)**。  
  
3.  在 **“CHECK 约束表达式”** 对话框中，键入 CHECK 约束的 SQL 表达式。 例如，若要将 `SellEndDate` 表的 `Product` 列中的条目限制为大于等于 `SellStartDate` 列中的日期的值，或者为 NULL 值，则键入：  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     或者，如果要求 `zip` 列中的项为 5 位数，请键入：  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  确保将任何非数字约束值包含在单引号 (') 中。  
  
4.  单击“确定” 。  
  
5.  在“标识”类别中，您可以更改 CHECK 约束的名称并且为该约束添加说明（扩展属性）。  
  
6.  在 **“表设计器”** 类别中，您可以设置何时强制约束。  
  
    |**若要：**|**在以下字段中选择“是”：**|  
    |-------------|---------------------------------------------|  
    |对在创建约束前存在的数据测试约束|**在创建或启用时检查现有数据**|  
    |在此表上发生复制操作时强制约束|**强制用于复制**|  
    |在此表中插入或更新行时强制约束|**强制用于 INSERT 和 UPDATE**|  
  
7.  单击 **“关闭”**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-create-a-new-check-constraint"></a>创建新的 CHECK 约束  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。  
  
###  <a name="TsqlExample"></a>  