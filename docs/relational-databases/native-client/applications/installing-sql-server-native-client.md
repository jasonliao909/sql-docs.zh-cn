---
title: 正在安装 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: MightyPen
ms.author: genemi
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 677450c306cdd85f3fec34b09ab8da9b45181844
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788444"
---
# <a name="installing-sql-server-native-client"></a>安装 SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  在安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时，将同时安装 Microsoft [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] Native Client 11.0。 
 
 没有 SQL Server 2016 Native Client。 有关详细信息，请参阅[SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md)。 
 
你还可以从 SQL Server 2012 功能包网页获取 sqlncli.msi。 若要下载最新版本的 SQL Server Native Client，请参阅[Microsoft® SQL Server®2012功能包](https://www.microsoft.com/download/confirmation.aspx?id=29065)。 如果计算机上还安装[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]了早于 SQL Server 2012 以前版本的 native client， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]则 native client 11.0 将与早期版本并行安装。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 文件（sqlncli11、sqlnclir11.rll、msmdsrv.rll 和 s11ch_sqlncli）安装到以下位置：  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client OLE DB 提供程序和[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client ODBC 驱动程序的所有相应注册表设置都是在安装过程中进行的。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 头文件和库文件（sqlncli.msi 和 sqlncli11）安装在以下位置：  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 除了作为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装过程的一部分安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 以外，还可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装磁盘的以下位置找到名为 sqlncli.msi 的可再发行安装程序：`%CD%\Setup\`。  
  
 您可以通过 sqlncli.msi 分发 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 在您部署某一应用程序时，可能需要安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 安装多个包（对于用户而言就像是一次安装）的一种方法就是使用链接器和引导程序技术。 有关详细信息，请参阅为[Visual Studio 2005 创作自定义引导程序包](https://go.microsoft.com/fwlink/?LinkId=115667)和[添加自定义必备组件](https://go.microsoft.com/fwlink/?LinkId=115668)。  
  
 sqlncli.msi 的 x64 和 Itanium 版本也会安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的 32 位版。 如果您的应用程序所针对的目标平台并非其开发时所使用的平台，则可以从 Microsoft 下载中心下载针对 x64、Itanium 和 x86 的 sqlncli.msi 版本。  
  
 在调用 sqlncli.msi 时，默认情况下只会安装客户端组件。 客户端组件是支持运行使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client 开发的应用程序的文件。 若还要安装 SDK 组件，请在命令行中指定 `ADDLOCAL=All`。 例如：  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>无提示安装  
 如果您将 /passive、/qn、/qb 或 /qr 选项与 msiexec 一起使用，则必须还指定 IACCEPTSQLNCLILICENSETERMS=YES，以便显式指示您接受最终用户许可协议条款。 必须以全大写字母指定此选项。  
  
## <a name="uninstalling-sql-server-native-client"></a>卸载 SQL Server Native Client  
 由于[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]服务器和[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]工具等应用程序依赖于[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client，因此在卸载所有从属应用程序[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]之前，不要卸载 Native client。 若要向用户提供应用程序依赖于[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的警告，请使用 MSI 中的 APPGUID 安装选项，如下所示：  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 传递给 APPGUID 的值是您的特定产品代码。 当使用 Microsoft Installer 捆绑应用程序安装程序时，必须创建产品代码。  
  
## <a name="see-also"></a>另请参阅  
 [构建具有 SQL Server Native Client 的应用程序](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [安装操作指南主题](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
