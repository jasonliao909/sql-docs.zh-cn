---
title: 选择 " &lt;从&gt;模型"。SAMPLE_CASES （DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0838c688b0518bf1fc7ed6c5d65c3ef03d0a7aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928312"
---
# <a name="select-from-ltmodelgtsample_cases-dmx"></a>选择 " &lt;从&gt;模型"。SAMPLE_CASES （DMX）
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  返回示例事例，用于代表为数据挖掘模型定型所用的事例。  
  
 若要使用此语句，必须在创建挖掘模型时启用钻取功能。 有关启用钻取的详细信息，请参阅[创建挖掘模型 &#40;dmx&#41;](../dmx/create-mining-model-dmx.md)，[选择 INTO &#40;dmx&#41;](../dmx/select-into-dmx.md)，并[更改挖掘结构 &#40;dmx&#41;](../dmx/alter-mining-structure-dmx.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>参数  
 *n*  
 可选。 一个指定返回行数的整数。  
  
 *表达式列表*  
 相关列标识符的逗号分隔列表。  
  
 *model*  
 模型标识符。  
  
 *条件列表*  
 可选。 限制条件，用于限制从列列表返回的值。  
  
 *表达式*  
 可选。 一个返回标量值的表达式。  
  
## <a name="remarks"></a>备注  
 可能生成样本事例，但其可能并不实际存在于定型数据中。 返回的事例代表指定的内容节点。  
  
 尽管[!INCLUDE[msCoName](../includes/msconame-md.md)]顺序分析和聚类分析算法[!INCLUDE[msCoName](../includes/msconame-md.md)]是唯一支持使用 SELECT FROM \<model> 的算法。SAMPLE_CASES，第三方算法还可以支持该算法。  
  
## <a name="examples"></a>示例  
 以下示例可返回为目标邮件挖掘模型定型所用的样本事例。 在**WHERE**子句中使用[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)函数只返回与 "000000003" 节点关联的事例。 可以在架构行集的 NODE_UNIQUE_NAME 列中找到节点字符串。  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>另请参阅  
 [选择 &#40;DMX&#41;](../dmx/select-dmx.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 数据定义语句](../dmx/dmx-statements-data-definition.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 数据操作语句](../dmx/dmx-statements-data-manipulation.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 语句参考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
