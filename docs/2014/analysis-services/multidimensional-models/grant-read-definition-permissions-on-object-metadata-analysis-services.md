---
title: 授予对对象元数据的读取定义权限（Analysis Services） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e03e55451c2340b5f0773e2873127c3551a82aab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074899"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>授予对象元数据的读取定义权限 (Analysis Services)
  读取所选对象的对象定义或元数据的权限使得管理员能够授予查看对象信息的权限，而不用同时授予修改对象定义、修改对象结构或查看对象的实际数据的权限。 `Read Definition`可以在数据库、数据源、维度、挖掘结构和挖掘模型级别授予权限。 如果需要`Read Definition`多维数据集的权限，则必须为`Read Definition`数据库启用。请记住，权限是累加的。 例如，一个角色授予读取多维数据集的元数据的权限，同时，另一个角色向同一个用户授予读取维度元数据的权限。 两个不同角色的权限合并授予用户在该数据库内的读取多维数据集元数据和维度元数据的权限。  
  
> [!NOTE]  
>  读取数据库元数据的权限是使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 连接到 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]数据库时所需的最低权限。 可读取元数据的用户还可以使用 DISCOVER_XML_METADATA 架构行集来查询对象并查看其元数据。 有关详细信息，请参阅 [DISCOVER_XML_METADATA 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset)。  
  
## <a name="set-read-definition-permissions-on-a-database"></a>设置数据库的读取定义权限  
 授予读取数据库元数据的权限便同时授予了读取数据库中所有对象的元数据的权限。  
  
 建议你在为专用处理`Read Definition`设置角色时，包括数据库级别的权限。 `Read Definition`使非管理员能够在中[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]查看模型的对象层次结构，并导航到各个对象进行后续处理。  
  
1.  在[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到实例[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，在对象资源管理器中展开相应数据库的 "**角色**"，然后单击某个数据库角色（或创建一个新的数据库角色）。  
  
2.  在 "**常规**" 选项卡上`Read Definition` ，选择选项。  
  
3.  在“成员身份” **** 窗格中，输入使用此角色连接到 Analysis Services 的 Windows 用户和组帐户。  
  
4.  单击“确定” **** ，完成角色创建。  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>设置单个对象的读取定义权限  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，打开“数据库”**** 文件夹，选择一个数据库，在对象资源管理器中展开相应数据库的“角色”****，然后单击某个数据库角色（或创建新的数据库角色）。  
  
2.  在 "**常规**" 窗格中，清除的数据库`Read Definition`权限。 此步骤清除了权限继承，这样便可对单个对象设置权限。  
  
3.  选择要为其指定`Read Definition`属性的对象：  
  
    -   在 "**数据源**" 窗格中， `Read Definition`单击该数据源的复选框。 角色成员可查看数据源的连接字符串，包括服务器名称，还可能包括用户名称。 假如你想提供连接字符串信息，而不同时授予修改连接字符串或查看任何其它对象定义的权限，这时该权限可用。  
  
    -   在 "**维度**" 窗格中， `Read Definition`单击该维度对应的复选框。 有经验的分析人员和开发人员在没有能修改定义或查看其他对象（例如，其他维度、多维数据集对象或挖掘结构和模型）定义的权限的情况下，可能需要查看定义。  
  
    -   在 "挖掘结构" 窗格中， `Read Definition`单击数据挖掘结构或模型的复选框。 `Read Definition`浏览数据模型是必需的。 有关详细信息，请参阅[授予数据挖掘结构和模型的权限 (Analysis Services)](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)。  
  
4.  在“成员身份” **** 窗格中，输入使用此角色连接到 Analysis Services 的 Windows 用户和组帐户。  
  
5.  单击“确定” **** ，完成角色创建。  
  
## <a name="see-also"></a>另请参阅  
 [授予数据库权限 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [&#40;Analysis Services 授予进程权限&#41;](grant-process-permissions-analysis-services.md)  
  
  
