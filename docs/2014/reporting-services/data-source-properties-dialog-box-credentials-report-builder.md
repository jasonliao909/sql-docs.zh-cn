---
title: "\"数据源属性\" 对话框-\"凭据（报表生成器） |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5dd4d113c92e0a2d094aa02d49010a5dd477c6ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109444"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a>“数据源属性”对话框 -&gt;“凭据”（报表生成器）
  在 **“数据源属性”** 对话框中选择 **“凭据”** 可以显示和修改用于连接到报表中的嵌入数据源的凭据。 您所提供的凭据用于访问数据源以便预览报表。 有关凭据的详细信息，请参阅 [在报表生成器中指定凭据](../../2014/reporting-services/specify-credentials-in-report-builder.md)。  
  
## <a name="options"></a>选项  
 **使用 Windows 身份验证(集成安全性)**  
 选择此选项可以使用 Windows 身份验证。  
  
 **使用此用户名和密码**  
 选择此选项可以提供特定用户名和密码。 对于嵌入数据源，在将报表服务器项目发布到目标服务器时，用户名和密码将保存为数据库的存储凭据。 如果要将用户名和密码用作 Windows 凭据，则可以在目标服务器上更改已发布共享数据源的属性。 有关详细信息，请参阅 [](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)联机丛书[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中 文档中的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [创建、删除或修改共享数据源（报表管理器）](https://go.microsoft.com/fwlink/?linkid=121312)。  
  
 **用户名**  
 键入用于登录数据源的用户名。  
  
 **权限**  
 键入用于登录数据源的密码。  
  
 **提示输入凭据**  
 选择此选项可以在报表运行时提示输入凭据。  
  
 **输入提示字符串**  
 键入用于指示用户提供数据源登录凭据的语句。  
  
 **无凭据**  
 选择此选项可指定不向数据源提供任何凭据。 仅当数据源不接受凭据，或者要通过其他方式传递凭据时，才使用此选项。  
  
 对于某些数据扩展插件，必须在报表服务器上配置无人参与的执行帐户。  
  
 有关详细信息，请参阅 [](report-data/add-data-from-external-data-sources-ssrs.md)联机丛书[中 ](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) 文档中的[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]从外部数据源中添加数据(SSRS)和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [配置无人参与的执行帐户（SSRS 配置管理器）](https://go.microsoft.com/fwlink/?linkid=121312)中相应数据源类型的主题。  
  
## <a name="see-also"></a>另请参阅  
 [报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 ["数据源属性" 对话框-"常规" &#40;报表生成器&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md)   
 [添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
