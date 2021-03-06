---
title: 为数据区域设置“无数据”消息（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2660582b03a121a81976d6bbc12afc1213877c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107089"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a>为数据区域设置“无数据”消息（报表生成器和 SSRS）
  如果希望指定在呈现的报表中所显示的文本来代替没有数据的数据区域，请为表、矩阵或列表数据区域设置 NoRowsMessage 属性，为图表数据区域设置 NoDataMessage 属性，以及为地图的色阶设置 NoDataText 属性。 运行时，报表处理器会针对报表中每个数据集运行查询，并且该数据集查询可能不生成结果集。 对于绑定到空数据集的数据区域，可以指定显示文本，而不是显示空数据区域。 如果在运行时子报表的数据集中没有数据，则还可以设置子报表的 NoRowsMessage 属性。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a>设置表、矩阵或列表的 NoRowsMessage 属性  
  
1.  在“设计”视图中，单击设计图面上的表、矩阵或列表数据区域或子报表以将其选中。 “属性”窗格将显示选定项的属性。  
  
2.  在 "属性" 窗格中，在 "属性" 字段中`NoRowsMessage`键入要显示为消息的文本。  
  
     此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a>设置图表的 NoDataMessage 属性  
  
1.  在“设计”视图中，单击并选中设计图面上的图表。 “属性”窗格将显示选定项的属性。  
  
2.  在 "属性" 窗格中，展开的`NoDataMessage`节点。  
  
3.  在 "**标题**" 中，在 "属性" 字段中`NoDataMessage`键入要显示为消息的文本。  
  
     此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a>设置子报表的 NoRowsMessage  
  
1.  在“设计”视图中，单击并选中设计图面上的子报表。 “属性”窗格将显示选定项的属性。  
  
2.  在 "属性" 窗格中，在 "属性" 字段中`NoRowsMessage`键入要显示为消息的文本。  
  
     此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a>设置地图色阶的 NoDataText 属性  
  
1.  在“设计”视图中，单击地图上的色阶以将其选中。 “属性”窗格将显示选定项的属性。  
  
2.  在的 "属性" 窗格`NoDataText`中，键入要显示为没有数据值的颜色的标签的文本。  
  
     此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。  
  
## <a name="see-also"></a>另请参阅  
 [子报表（报表生成器和 SSRS）](../report-design/subreports-report-builder-and-ssrs.md)   
 [表、矩阵和列表（报表生成器和 SSRS）](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [图表（报表生成器和 SSRS）](../report-design/charts-report-builder-and-ssrs.md)   
 [地图（报表生成器和 SSRS）](../report-design/maps-report-builder-and-ssrs.md)   
 [子报表（报表生成器和 SSRS）](../report-design/subreports-report-builder-and-ssrs.md)  
  
  
