---
title: 图表故障排除（报表生成器）| Microsoft Docs
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96579c7dadc33c9d8dd74e823cee9cc5ef8e3367
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "77078453"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>图表故障排除（报表生成器和 SSRS）
  对以下问题的解答可能在您使用图表时对您有所帮助。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>为什么我的图表对值轴上的值进行计数，而不是求和？  
 大多数图表类型都要求数值放置在通常作为 y 轴的值轴上，以便能够正确地绘制图表。 如果值字段的数据类型是 **String**，则图表将无法显示数值，即使这些字段中包含数字也是如此。 相反，该图表将显示包含该字段中值的行的总行数。 若要避免出现此情况，请确保用于值序列的字段是数字数据类型的，而不是包含格式化数字的字符串。  

## <a name="need-more-help"></a>需要更多帮助？  
   
  请尝试：  
 * Stack Overflow 上的 [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services)  
 * 在 [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server) 上提出问题或建议。  
  
## <a name="see-also"></a>另请参阅  
 [图表&#40;报表生成器和 SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
