---
title: Issue 元素（ssbdiagnose） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69b9e356fcaf4b5abd97b56c69ecdd9881aaaee2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63285770"
---
# <a name="issue-element-ssbdiagnose"></a>Issue 元素 (ssbdiagnose)
  报告 **ssbdiagnose** 实用工具发现的问题。 在 **ssbdiagnose** XML 输出文件中，所报告的每个问题都有一个 Issue 元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a>元素属性  
  
|Attribute|说明|  
|---------------|-----------------|  
|`type`|标识 Issue 元素报告的问题类别：<br /><br /> **"诊断"** 报告在分析[!INCLUDE[ssSB](../../includes/sssb-md.md)]配置时发现的配置问题。<br /><br /> **"问题"** 报告已阻止**ssbdiagnose**完成其分析的问题。 更正问题并重新运行 **ssbdiagnose**。<br /><br /> **"事件"** 报告运行[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **时**检查时发现的事件。 仅当指定了 **-SHOWEVENTS** 时才报告事件。|  
|`code`|标识消息的错误号。|  
|`server`|标识在其中发现了问题的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例。 如果问题在默认实例中，则服务器属性只具有计算机名称。 如果问题在命名实例中，则服务器属性的格式为 ComputerName\InstanceName。|  
|`database`|标识在其中发现了问题的数据库的名称。|  
|`object`|标识在其中发现了问题的对象的名称。 如果问题为实例或数据库级别的问题，则对象属性将重复该实例或数据库名称。|  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|**数据类型和长度**|`string`，长度不受限制。|  
|**值**|返回错误消息的文本。|  
|**出现次数**|每个报告错误一次。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|[DiagnosticInformation 元素 (ssbdiagnose)](diagnosticinformation-element-ssbdiagnose.md)|  
|**子元素**|无|  
  
## <a name="example"></a>示例  
 此元素报告没有主密钥的数据库的 1102 错误，分析 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 配置时在该数据库中发现了错误。  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>另请参阅  
 [ssbdiagnose 实用工具 (Service Broker)](ssbdiagnose-utility-service-broker.md)  
  
  
