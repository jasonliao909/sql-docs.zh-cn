---
title: 获取 R 包信息
description: 学习如何了解在 SQL Server 机器学习服务和 SQL Server R Services 中安装的 R 包。
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 41e5f384878dfb284c31d6ba2886c9e223d03ca3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "74479418"
---
# <a name="get-r-package-information"></a>获取 R 包信息

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

本文介绍如何了解在 SQL Server 机器学习服务和 SQL Server R Services 中安装的 R 包。 示例 R 脚本显示如何列出包信息，如安装路径和版本。

## <a name="default-r-library-location"></a>默认 R 库位置

使用 SQL Server 安装机器学习时，会在实例级别为安装的每种语言创建一个包库。 在 Windows 上，实例库是通过 SQL Server 注册的安全文件夹。

在 SQL Server 上的数据库内运行的所有脚本都必须加载实例库中的函数。 SQL Server 无法访问安装到其他库的包。 这也适用于远程客户端：在服务器计算上下文中运行的任何 R 脚本只能使用实例库中安装的包。
若要保护服务器资产，只能由计算机管理员修改默认实例库。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
R 的二进制文件的默认路径为：

`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
R 的二进制文件的默认路径为：

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
R 的二进制文件的默认路径为：

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

这里假设默认 SQL 实例为 MSSQLSERVER。 如果将 SQL Server 安装作为用户定义的命名实例，则改用给定名称。

<!-- I don't think this note is necessary. If you have these other products installed, you'd already know about them.
> [!NOTE]
> If you find other folders having similar subfolder names and files, you probably have a standalone installation of  Microsoft R Server or Machine Learning Server. These server products have different installers and paths: C:\Program Files\Microsoft\R Server\R_SERVER or C:\Program Files\Microsoft\ML SERVER\R_SERVER. For more information, see [Install R Server 9.1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) or [Install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).
-->

运行以下语句来验证当前实例的默认 R 包库：

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

以下语句使用 [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) 返回实例库的路径和 SQL Server 使用的 RevoScaleR 版本：

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) 函数只能在本地计算机上执行。 函数无法返回远程连接的库路径。

## <a name="default-r-packages"></a>默认 R 包

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

以下 R 包与 SQL Server R Services 一起安装。

|包 | 版本 | 说明 |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 用于远程计算上下文、流式处理、并行执行进行数据导入和转换的 rx 函数、建模、可视化和分析。 |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 1.0.0 | 用于在存储过程中包含 R 脚本。 |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

在安装过程中选择 R 功能时，将随 SQL Server 机器学习服务一起安装以下 R 包。

|包 | 版本 | 说明 |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 9.2 | 用于远程计算上下文、流式处理、并行执行进行数据导入和转换的 rx 函数、建模、可视化和分析。 |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 1.0.0 | 用于在存储过程中包含 R 脚本。 |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| 1.4.0 | 在 R 中添加机器学习算法。 | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0.0 | 用于在 R 中编写 MDX 语句。 |

::: moniker-end

### <a name="component-upgrades"></a>组件升级

默认情况下，会通过服务包和累积更新刷新 R 包。 只能通过产品升级或将 R 支持绑定到 Microsoft Machine Learning Server 来实现核心 R 组件的其他包和完整版本升级。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
此外，还可以通过组件升级将 MicrosoftML 和 olapR 包添加到 SQL Server 实例中。
::: moniker-end

有关详细信息，请参阅[升级 SQL Server 中的 R 和 Python 组件](../install/upgrade-r-and-python.md)。

## <a name="default-open-source-r-packages"></a>默认开放源代码 R 包

R 支持包括开源 R，因此可调用基本 R 函数并安装其他开源和第三方包。 R 语言支持多种核心功能，例如 base、stats 和 utils 等    。 R 的基本安装还包括许多示例数据集和标准 R 工具，如 RGui（轻量级交互式编辑器）和 RTerm（R 命令提示符）   。

安装中包含的开源 R 的分发是 [Microsoft R Open (MRO)](https://mran.microsoft.com/open)。 MRO 通过包含其他开源包，如 [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library)（数学核心函数库），将值添加到基础 R 中。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
使用 SQL Server R Services 安装程序的 MRO 提供的 R 版本为 3.2.2。
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
使用 SQL Server 机器学习服务安装程序的 MRO 提供的 R 版本为 3.3.3。
::: moniker-end

> [!IMPORTANT]
> 请勿手动使用 Web 上的更新版本覆盖 SQL Server 安装程序安装的 R 版本。 Microsoft R 包基于 R 的特定版本。修改安装可能会使其不稳定。

## <a name="list-all-installed-r-packages"></a>列出所有已安装的 R 包

以下示例在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程中使用 R 函数 `installed.packages()` 来显示已安装在当前 SQL 实例的 R_SERVICES 库中的 R 包的列表。 该脚本在 DESCRIPTION 文件中返回包名称和版本字段。

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);',
@input_data_1 = N'
  '
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

若要详细了解 R 包 DESCRIPTION 字段的可选字段和默认字段，请参阅 [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)。

## <a name="find-a-single-r-package"></a>查找单个 R 包

如果已安装 R 包，并且想要确保它可用于特定的 SQL Server 实例，则可以执行存储过程以加载包并返回消息。

例如，以下语句查找并加载 [glue](https://cran.r-project.org/web/packages/glue/) 包（如果可用）。
如果无法找到或加载该包，则会收到一个错误，其中包含文本“没有名为‘glue’的包。”

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("glue")'
GO
```

要查看有关包的详细信息，请查看 `packageDescription`。
以下语句返回 glue 包的信息  。

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("glue"))
  '
```

## <a name="next-steps"></a>后续步骤

::: moniker range="<=sql-server-2017||=sqlallproducts-allversions"
+ [使用 R 工具安装包](install-r-packages-standard-tools.md)
::: moniker-end
::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
+ [使用 sqlmlutils 安装新的 R 包](install-additional-r-packages-on-sql-server.md)
::: moniker-end
+ [获取 Python 包信息](python-package-information.md)
+ [安装新 Python 包](../python/install-additional-python-packages-on-sql-server.md)
+ [R 和 Python 教程](../tutorials/machine-learning-services-tutorials.md)
