---
title: 定期评估基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ad7d22492411538a1f397f1a7d02436d1a02bde7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "67901156"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>定期评估基于策略的管理策略
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中按计划评估基于策略的管理策略。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [安全性](#Security)  
  
-   **若要按计划评估策略，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 权限  
 要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>按计划评估策略  
  
1.  在 **“对象资源管理器”** 中，单击加号以展开包含要评估的策略计划的服务器。  
  
2.  单击加号以便展开 **“管理”** 文件夹。  
  
3.  单击加号以便展开 **“策略管理”** 。  
  
4.  单击加号以便展开 **“策略”** 文件夹。  
  
5.  右键单击要评估其计划的策略，然后选择“属性”  。  
  
6.  在“打开策略 - policy_name”对话框的“评估模式”列表中，选择“按计划”     。  
  
7.  在 **“计划”** 中，单击 **“选取”** 指定现有的计划，或 **“新建”** 创建新的计划。  
  
8.  完成后，单击 **“确定”** 。  
  
  
