---
title: 为数据处理扩展插件实现 Connection 类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fbd293c156f373de0cdad53b4419633ded15af8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164127"
---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>为数据处理扩展插件实现 Connection 类
  Connection 对象表示数据库连接或类似的资源，它是 **** 数据处理扩展插件的用户的起点[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。 它表示与数据库服务器的连接，尽管可以将任何具有类似行为的实体公开为 Connection****。  
  
 若要实现 Connection 对象，请创建一个实现 ** 并可选实现 ** 的类<xref:Microsoft.ReportingServices.DataProcessing.IDbConnection><xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>。  
  
 在实现中，您必须确保先创建和打开一个连接，然后才能执行命令。 确保您的实现要求客户端显式打开和关闭连接，而不是让实现为客户端隐式打开和关闭连接。 在获取连接时，将执行安全检查。 如果在 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 数据处理扩展插件中要求将某个现有连接用于其他类，则可以确保在使用数据源时始终执行安全检查。  
  
 所需连接的属性表示为一个连接字符串。 强烈建议 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 数据处理扩展插件使用由 OLE DB 定义的所熟悉的名称/值对系统支持 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> 属性。  
  
> [!NOTE]  
>  要获取的**连接**对象通常需要消耗大量资源，因此，你可能需要考虑建立池连接或其他技术来缓解这种情况。  
  
 
  <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 从 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 继承。 您必须将 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 接口作为连接类实现的一部分而实现。 借助于 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 接口，类可以实现本地化的扩展插件名称并处理存储在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置文件中的扩展插件特定的配置信息。  
  
 Connection 对象通过其 ** 的实现包含 ** 属性<xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A><xref:Microsoft.ReportingServices.Interfaces.IExtension>。 强烈建议 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件支持 <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> 属性，以便用户在用户界面（如报表管理器）中对于该扩展插件看到熟悉的本地化名称。  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>还使**连接**对象能够检索和处理存储在 rsreportserver.config 文件中的自定义配置数据。 有关处理自定义配置数据的详细信息，请参阅 <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> 方法。  
  
 对于实现 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 的类，当卸载其他数据处理扩展插件类时，不会从内存中卸载该类。 因此，可以使用 Extension 类存储跨连接状态信息或存储内存中可能缓存的数据****。 只要报表服务器正在运行，Extension 类就保持在内存中****。  
  
 可以通过实现 ** 来扩展 Connection 类，以便在 ** 中包含对于凭据的支持[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>。 当实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A> 接口的 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A>、<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> 属性时，就在报表设计器的“数据源”对话框中启用了“集成安全性”复选框以及“用户名”和“密码”文本框****************。 这使报表设计器能够针对支持身份验证的数据源存储和检索凭据。 将以安全的方式存储凭据，当以预览模式呈现报表时将使用这些凭据。  
  
> [!NOTE]  
>  隐式实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> 要求您实现 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 和 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 接口的成员。  
>   
>  有关示例 Connection 类实现，请参阅 **SQL Server Reporting Services Product Samples**[](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。  
  
## <a name="see-also"></a>另请参阅  
 [Reporting Services 扩展插件](../reporting-services-extensions.md)   
 [实现数据处理扩展插件](implementing-a-data-processing-extension.md)   
 [Reporting Services 扩展插件库](../reporting-services-extension-library.md)  
  
  
