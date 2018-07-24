---
title: 查看数据类型映射（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.reviewissues.f1
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbfaab44f1b7c40a912eec0c6c6cef8a6b00c51f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158908"
---
# <a name="review-data-type-mapping-sql-server-import-and-export-wizard"></a>查看数据类型映射（SQL Server 导入和导出向导）
  使用**查看数据类型映射**页后，可以查看有关该向导已执行，以使源数据与目标兼容的数据类型转换的详细的信息。 此信息包括可视提示，用于区分应成功的转换与可能导致错误或截断的转换。 对于每个转换，您都可以决定是否接受向导建议的转换，也可以指定如何处理发生的错误。  
  
 若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。 若要了解有关用于启动向导，选项以及已成功运行该向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。  
  
 用途[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]导入和导出向导，将数据从源复制到目标。 该向导还可以为您创建目标数据库和目标表。 但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。 有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。  
  
## <a name="options"></a>“常规”  
 **“查看数据类型映射”** 页由 **“表”** 列表、 **“数据类型映射”** 列表和错误处理选项组成。  
  
### <a name="table-list"></a>表列表  
 上部**查看数据类型问题**页面**表**列出了要从源传输到目标表的列表。 下表对列表中的列进行了说明。  
  
|“列”|Description|  
|------------|-----------------|  
|源图标|指示数据类型转换成功的可能性：<br /><br /> 绿色的选中标记图标指示向导认为此表的所有数据类型转换都将成功。<br /><br /> 黄色的警告图标指示您应检查向导将执行的单个转换。 若要检查这些转换，可以选择表，然后在 **“数据类型映射”** 列表中检查单个列的转换。<br /><br /> 红色错误图标指示向导不能可靠地执行对此表的某些转换。|  
|**数据源**|显示源表的名称。|  
|目标图标|指示目标是已经存在还是将由向导创建：<br /><br /> 表图标指示目标是一个现有表。<br /><br /> 阳光四射的表图标指示目标是一张新表，需要由向导创建。|  
|**目标**|显示目标表的名称。|  
  
 若要查看单个表的转换信息，请选择一个表，在此**表**网格。 所选表的转换信息显示在页面下半部分的 **“数据类型映射网格”** 的列中。  
  
### <a name="data-type-mapping-list"></a>数据类型映射列表  
 下端**查看数据类型问题**页面**数据类型映射**列表。 此网格提供有关在 **“表”** 列表中选择的表中的列的详细转换信息。 下表对列表中的列进行了说明。  
  
|“列”|Description|  
|------------|-----------------|  
|转换图标|指示数据类型转换成功的可能性：<br /><br /> 绿色的选中标记图标指示向导认为此列的数据类型转换会成功。<br /><br /> 黄色的警告图标指示您应检查向导将执行的转换。 若要查看转换，请双击该列以查看“列转换详细信息”  对话框。<br /><br /> 红色错误图标指示向导不能可靠地执行转换。|  
|**源列**|显示源列的名称。|  
|**源类型**|显示源列的数据类型。|  
|**目标列**|显示目标列的名称。|  
|**目标类型**|显示目标列的数据类型。|  
|**转换**|指定计划的转换是否应继续：<br /><br /> 选中复选框，可以使向导继续执行计划的转换。<br /><br /> 清除复选框，可以取消对数据类型的转换。|  
|**出错时**|指定向导处理错误的方式：<br /><br /> 使用**出错时 （全局）** 设置。<br /><br /> 失败时出现一个错误，并停止导入或导出过程。<br /><br /> 忽略错误。|  
|**截断时**|指定向导处理截断的方式：<br /><br /> 使用**截断时 （全局）** 设置。<br /><br /> 失败并报告错误并停止导入或导出过程<br /><br /> 忽略截断。|  
  
 若要查看有关特定数据列转换的详细信息，请双击列表中的任意行。 将打开 **“列转换详细信息”** 对话框，并显示列的更多详细转换信息。  
  
### <a name="error-handling-options"></a>错误处理选项  
 **出错时(全局)**  
 指定向导处理错误的方式：  
  
-   失败时出现一个错误，并停止导入或导出过程。  
  
-   忽略错误并继续导入或导出过程。  
  
 这些设置应用到在 **“数据类型映射”** 列表的 **“出错时”** 列中选择了 **“使用全局”** 的所有转换。  
  
 **截断时(全局)**  
 指定向导处理截断的方式：  
  
-   失败时出现一个错误，并停止导入或导出过程。  
  
-   忽略截断并继续导入或导出过程。  
  
 这些设置应用到在 **“数据类型映射”** 列表的 **“截断时”** 列中选择了 **“使用全局”** 的所有转换。  
  
  