---
title: 服务提供商和组件 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a78db07f5ba445c54108558b2ff222bd217c2bbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924246"
---
# <a name="service-providers-and-components"></a>服务提供商和组件
服务提供程序是通过实现不受数据存储本机支持的扩展接口来扩展数据提供程序功能的组件。  
  
 通用数据访问提供了一个*组件体系结构，该体系结构*允许单个专用组件在不太适用的存储区之上实现一组不连续的数据库功能或 "服务"。 因此，服务组件可以提供一个公共实现，而无需强制每个数据存储提供自己的扩展功能实现或强制一般应用程序在内部实现数据库功能，在访问任何数据存储时使用。 数据存储本身实现了某些功能，而某些功能是通过一般组件实现的，对应用程序而言是透明的。  
  
 例如，游标引擎（如[OLE DB 的游标服务](https://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44)）是一个服务组件，它可以使用顺序的只进数据存储中的数据来生成可滚动的数据。 ADO 通常使用的其他服务提供程序包括[microsoft OLE DB 永久性提供程序（Ado 服务提供程序）](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) 、用于[OLE DB 的 Microsoft 数据定形服务（Ado 服务提供程序）](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) （用于分层**记录集**）和[MICROSOFT OLE DB 远程处理提供程序（ado 服务提供程序）](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) （用于调用远程计算机上的数据访问接口）。  
  
 有关服务和数据提供程序的详细信息，请参阅[附录 A： providers](../../../ado/guide/appendixes/appendix-a-providers.md)。
