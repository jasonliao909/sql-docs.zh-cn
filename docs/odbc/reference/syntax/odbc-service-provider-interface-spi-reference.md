---
title: ODBC 服务提供程序接口（SPI）参考 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88053620fa413c50a8faff4cc47cbbe1457249f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073836"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC 服务提供程序接口 (SPI) 参考
传统上，ODBC 定义了应用程序编程接口（API）。 API 中的函数可以由应用程序调用，它们应在驱动程序管理器和驱动程序内实现。  
  
 添加了驱动程序感知连接池功能后，ODBC 会引入服务提供程序接口（SPI）。 SPI 中的函数用于驱动程序管理器和驱动程序之间的通信。 SPI 函数由驱动程序实现;驱动程序管理器不会向应用程序公开 SPI 函数。 应用程序不应直接调用这些函数。  
  
 包括用于 ODBC 驱动程序开发的 sqlspi。  
  
 本节包含下列主题  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>另请参阅  
 [开发 ODBC 驱动程序](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [在 ODBC 驱动程序中开发连接池感知](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [驱动程序管理器连接池](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
