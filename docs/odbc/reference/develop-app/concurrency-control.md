---
title: 并发控制 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c541bf28c1d4c7ec2e2041201bd7c168625bb34
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083265"
---
# <a name="concurrency-control"></a>并发控制
*并发*是指两个事务同时使用相同数据的能力，提高事务隔离通常会降低并发性。 这是因为事务隔离通常是通过锁定行来实现的，并且随着更多的行被锁定，可以完成更少的事务，而不会被锁定的行至少临时阻止。 尽管降低并发性对于维护数据库完整性所必需的更高的事务隔离级别，但对于维护数据库完整性所需的更高的事务隔离级别，但在使用游标的高读/写活动时，这可能会成为一个问题。  
  
 例如，假设应用程序执行 SQL 语句 "**从订单\* " 中选择**。 它调用**SQLFetchScroll**以在结果集的周围滚动，并允许用户更新、删除或插入订单。 用户更新、删除或插入订单后，应用程序将提交该事务。  
  
 如果隔离级别是可重复读取，则事务可能会根据其实现方式-锁定**SQLFetchScroll**返回的每一行。 如果隔离级别是可序列化的，则事务可能会锁定整个 Orders 表。 在任一情况下，事务仅在提交或回滚时才释放其锁。 因此，如果用户花费了大量时间来阅读订单，并且很少需要更新、删除或插入它们，则事务可以轻松地锁定大量的行，使其不可供其他用户使用。  
  
 即使游标是只读的并且应用程序允许用户只读取现有订单，这也是一个问题。 在这种情况下，应用程序会在调用**SQLCloseCursor** （处于自动提交模式时）或**SQLEndTran** （在手动提交模式下）时提交事务并释放锁。  
  
 本部分包含下列主题。  
  
-   [并发类型](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [乐观并发](../../../odbc/reference/develop-app/optimistic-concurrency.md)
