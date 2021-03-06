---
title: 将 DB2 数据库迁移到 SQL Server （DB2ToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 79cc961148add0bf2096a716b669199360a565b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68084647"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>将 DB2 数据库迁移到 SQL Server （DB2ToSQL）
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DB2 的迁移助手（SSMA）是一个全面的环境，可帮助你快速将 DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库迁移到或 AZURE SQL DB。 通过使用 SSMA for DB2，你可以查看数据库对象和数据、评估要迁移的数据库、将数据库对象[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]迁移到或 AZURE sql 数据库，以及将数据[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]迁移到或 azure sql 数据库。 请注意，不能迁移 SYS 和 SYSTEM DB2 架构。  
  
## <a name="recommended-migration-process"></a>建议的迁移过程  
若要成功地将对象和数据从 DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库迁移到或 AZURE SQL 数据库，请使用以下过程：  
  
1.  [新的 SSMA 项目](https://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0)。  
  
    创建项目后，可以设置项目转换、迁移和类型映射选项。 有关项目设置的信息，请参阅 DB2ToSQL&#41;和相关部分的[项目设置 &#40;转换&#41; &#40;](../../ssma/db2/project-settings-conversion-db2tosql.md) 。 有关如何自定义数据类型映射的信息，请参阅[映射 DB2 和 SQL Server 数据类型 &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)。  
  
2.  [连接到 DB2 数据库](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844)。  
  
3.  [正在连接到 SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e)。  
  
4.  [将 DB2 架构映射到 SQL Server 架构](https://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a)。  
  
5.  还可以选择[评估报表](https://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de)来评估用于转换的数据库对象，并估计转换时间。  
  
6.  [转换 DB2 架构](https://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0)。  
  
7.  [将转换后的数据库对象加载到 SQL Server 中](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3)。  
  
    可以通过以下方式之一执行此操作：  
  
    -   保存并在中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]运行脚本。  
  
    -   同步数据库对象。  
  
8.  将[DB2 数据迁移到 SQL Server](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b)。  
  
9. 如有必要，请更新数据库应用程序。  
  
## <a name="see-also"></a>另请参阅  
[安装 SSMA for DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[SSMA for DB2 &#40;DB2ToSQL&#41;的入门](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
