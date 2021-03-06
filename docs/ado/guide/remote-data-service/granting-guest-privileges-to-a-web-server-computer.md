---
title: 向 Web 服务器计算机授予来宾权限 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bddf6ce0bbfb78435118ef3d87303a94c792c96d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922647"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>授予 Web 服务器计算机来宾特权
必须将匿名 Web 服务器帐户（IUSR_*ComputerName*）添加到 Web 服务器计算机上的来宾本地组，才能使用 RDS。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件（有关详细信息，请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)）。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>向 Web 服务器计算机授予来宾特权  
  
1.  在 Microsoft Windows 2000 服务器计算机上，单击 "**开始**"，指向 "**程序**"，指向 "**管理工具**"，然后单击 "**计算机管理**"。  
  
2.  在控制台树中的 "**本地用户和组**" 中，单击 "**组**"。  
  
3.  选择**来宾**本地组。 从 "**操作**" 菜单中选择 "**属性**"。  
  
4.  在 "**来宾属性**" 对话框中，单击 "**添加**"。  
  
5.  如果 "**选择用户或组**" 对话框的列表中没有显示 "匿名 Web 服务器" 帐户，请在底部的空白框中键入其名称（IUSR_*ComputerName*），然后单击 "**添加**"。  
  
6.  单击“确定”。 


