---
title: Web 服务任务编辑器（"常规" 页） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6f993f1f2386782bf8225f22b285b9385e2f8e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054543"
---
# <a name="web-service-task-editor-general-page"></a>Web 服务任务编辑器（“常规”页）
  使用“Web 服务任务编辑器”**** 对话框的“常规”**** 页，可以指定 HTTP 连接管理器，指定 Web 服务任务所使用的 Web 服务描述语言 (WSDL) 文件的位置，对 Web 服务任务进行说明，以及下载 WSDL 文件。  
  
 有关此任务的详细信息，请参阅 [Web 服务任务](control-flow/web-service-task.md)。  
  
## <a name="options"></a>选项  
 **HTTPConnection**  
 在列表中选择一个文件连接管理器，或单击“\<新建连接…>”，新建一个连接管理器****。  
  
> [!IMPORTANT]  
>  HTTP 连接管理器仅支持匿名身份验证和基本身份验证， 而不支持 Windows 身份验证。  
  
 **相关主题：**  [Http 连接管理器](connection-manager/http-connection-manager.md)、 [http 连接管理器编辑器 &#40;Server 页面&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 键入计算机本地上 WSDL 文件的完全限定路径，或单击浏览按钮 (…) 并定位到该文件****。  
  
 如果您已经将该 WSDL 文件手动下载到计算机，请选择此文件。 但是，如果尚未下载该 WSDL 文件，请执行以下步骤：  
  
-   创建文件扩展名为“.wsdl”的空文件。  
  
-   为 **WSDLFile** 选项选择此空文件。  
  
-   将**OverwriteWSDLFile**的值设置为`True` ，以允许使用实际的 WSDL 文件覆盖空文件。  
  
-   单击 **“下载 WSDL”** 下载实际 WSDL 文件，并覆盖空文件。  
  
    > [!NOTE]  
    >  在“WSDLFile”**** 框中提供现有本地文件的名称后，才会启用“下载 WSDL”**** 选项。  
  
 **OverwriteWSDLFile**  
 指示是否可以覆盖 Web 服务任务的 WSDL 文件。  
  
 如果要使用 "**下载 wsdl** " 按钮下载 WSDL 文件，请将此值设置为`True`。  
  
 **名称**  
 为 Web 服务任务提供唯一的名称。 此名称用作任务图标中的标签。  
  
> [!NOTE]  
>  任务名称在一个包内必须是唯一的。  
  
 **说明**  
 键入 Web 服务任务的说明。  
  
 **“下载 WSDL”**  
 下载 WSDL 文件。  
  
 当您在 **WSDLFile** 框中提供现有本地文件的名称后，该按钮才会启用。  
  
## <a name="see-also"></a>另请参阅  
 [Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Web 服务任务编辑器 &#40;输入页&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Web 服务任务编辑器 &#40;输出页&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [“表达式”页](expressions/expressions-page.md)  
  
  
