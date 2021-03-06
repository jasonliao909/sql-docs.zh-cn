---
title: Word 设备信息设置 | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 776a825c480568be2640d1309c7c3a48970e2c54
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "65571132"
---
# <a name="word-device-information-settings"></a>Word 设备信息设置
  下表列出以 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 格式呈现时的设备信息设置。  
  
|设置|值|  
|-------------|-----------|  
|**AutoFit**|**False**。 自动调整对于任何 Word 表都设置为 **false** 。<br /><br /> **True**。 自动调整对于每个 Word 表都设置为 **true** 。<br /><br /> **Never**。 对任何 Word 表均未设置自动调整值并且行为还原为 Word 默认值。<br /><br /> **Default**。 自动调整设置于窄于每个逻辑页上物理绘图区（不包括边距的物理页宽）的表。|  
|**ExpandToggles**|指示可以滚动的所有项是否以其完全展开的状态呈现。 默认值是 **false**秒。|  
|**FixedPageWidth**|指示写入 DOC 文件的页宽是否将增大以适合表体中最大页的宽度。 默认值是 **false**秒。|  
|**OmitHyperlinks**|指示是否忽略对所有项的超链接操作（如果设置）。 默认值为 **false**。|  
|**OmitDrillthroughs**|指示是否忽略对所有项的钻取操作（如果设置）。 默认值为 **false**。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [将设备信息设置传递给呈现扩展插件](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [在 RSReportServer.Config 中自定义呈现扩展插件参数](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [技术参考 (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
