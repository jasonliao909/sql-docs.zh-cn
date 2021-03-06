---
title: 安装新 R 包
description: 了解如何使用 sqlmlutils 将新的 R 包安装到 SQL Server 机器学习服务或 SQL Server R Services 的实例。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/20/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff2d40dab5fa2d8f03bf3d1fa32b08e66a0ccdbc
ms.sourcegitcommit: 7008c7fe451a20d6610e40bb8f61dece86c0f17e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79027938"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>使用 sqlmlutils 安装新的 R 包

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

本文介绍如何使用 [sqlmlutils](https://github.com/Microsoft/sqlmlutils) 包中的函数以将新的 R 包安装到 SQL Server 机器学习服务或 SQL Server R Services 的实例  。 安装的包可用于使用 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) T-SQL 语句在数据库中运行的 R 脚本。

> [!NOTE]
> 不建议使用标准 R `install.packages` 命令在 SQL Server 上添加 R 包。 请改用本文中所述的 sqlmlutils  。

## <a name="prerequisites"></a>先决条件

- 在用于连接到 SQL Server 的客户端计算机上安装 [R](https://www.r-project.org) 和 [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/)。 可以使用任何 R IDE 来运行脚本，但本文假定使用 RStudio。

- 在用于连接到 SQL Server 的客户端计算机上安装 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) 或 [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS)。 可以使用其他数据库管理或查询工具，但本文假定使用 Azure Data Studio 或 SSMS。

### <a name="other-considerations"></a>其他注意事项

- 在 SQL Server 中运行的 R 脚本只能使用在默认实例库中安装的包。 SQL Server 无法从外部库加载包，即使该库位于同一台计算机上也是如此。 这包括与其他 Microsoft 产品一起安装的 R 库。

- 在强化的 SQL Server 环境中，可能希望避免使用以下包：
  - 需要网络访问权限的包
  - 需要提升的文件系统访问权限的包
  - 用于 Web 开发或不受益于在 SQL Server 内部运行的其他任务的包

## <a name="install-sqlmlutils-on-the-client-computer"></a>在客户端计算机上安装 sqlmlutils

若要使用 sqlmlutils，首先需要将其安装在用于连接到 SQL Server 的客户端计算机上  。

sqlmlutils 包依赖于 RODBCext 包，RODBCext 依赖于许多其他包    。 请参照以下过程，按正确顺序安装所有这些包。

### <a name="install-sqlmlutils-online"></a>联机安装 sqlmlutils

如果客户端计算机可以访问 Internet，则可以联机下载并安装 sqlmlutils 及其依赖的包  。

1. 从 https://github.com/Microsoft/sqlmlutils/tree/master/R/dist 将最新的 sqlmlutils zip 文件下载到客户端计算机  。 请勿解压缩文件。

1. 打开“命令提示符”并运行以下命令，安装 sqlmlutils 和 RODBCext 包    。 将下载的 sqlmlutils zip 文件的完整路径替换进去（此示例假定该文件位于“文档”文件夹中）  。 已联机查找到 RODBCext 包，并安装它  。

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>脱机安装 sqlmlutils

如果客户端计算机没有 Internet 连接，则需要使用能够访问 Internet 的计算机预先下载 sqlmlutils 和 RODBCext 包   。 然后，可以将这些文件复制到客户端计算机上的一个文件夹中，并脱机安装这些包。

RODBCext 包具备许多存在依赖关系的包，并且识别包的所有依赖关系很复杂  。 建议使用 [miniCRAN](https://andrie.github.io/miniCRAN/) 来为包含所有依赖包的包创建本地存储库文件夹  。
有关详细信息，请参阅[使用 miniCRAN 创建本地 R 包存储库](create-a-local-package-repository-using-minicran.md)。

**sqlmlutils** 包包含一个 zip 文件，可以将该文件复制到客户端计算机并进行安装。

在能够访问 Internet 的计算机上执行以下操作：

1. 安装 miniCRAN  。 有关详细信息，请参阅[安装 miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran)。

1. 在 RStudio 中，运行以下 R 脚本，以创建 RODBCext 包的本地存储库  。 此示例在 `c:\downloads\rodbcext` 文件夹中创建存储库。

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end

   至于 `Rversion` 值，请使用安装在 SQL Server 上的 R 版本。 若要验证已安装的版本，请使用以下 T-SQL 命令。

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. 从 [https://github.com/Microsoft/sqlmlutils/tree/master/R/dist](https://github.com/Microsoft/sqlmlutils/tree/master/R/dist) 下载最新的 sqlmlutils zip 文件（请勿解压缩文件）  。 例如，将文件下载到 `c:\downloads\sqlmlutils_0.7.1.zip`。

1. 将整个 RODBCext 存储库文件夹 (`c:\downloads\rodbcext`) 和 sqlmlutils zip 文件 (`c:\downloads\sqlmlutils_0.7.1.zip`) 复制到客户端计算机   。 例如，将它们复制到客户端计算机上的 `c:\temp\packages` 文件夹中。

在用于连接到 SQL Server 的客户端计算机上，打开命令提示符并运行以下命令依次安装 RODBCext 和 sqlmlutils   。

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>在 SQL Server 上添加 R 包

在下面的示例中，将 [glue](https://cran.r-project.org/web/packages/glue/) 包添加到 SQL Server  。

### <a name="add-the-package-online"></a>联机添加包

如果用于连接到 SQL Server 的客户端计算机具有 Internet 访问权限，则可以使用 sqlmlutils 在 Internet 上查找 glue 包及任何依赖项，然后将该包远程安装到 SQL Server 实例   。

1. 在客户端计算机上，打开 RStudio 并创建一个新 R 脚本文件  。

1. 通过 sqlmlutils 使用以下 R 脚本安装 glue 包   。 请将相应部分替换为自己的 SQL Server 数据库连接信息。

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server   = "server",
     database = "database",
     uid      = "username",
     pwd      = "password")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > 范围可为 PUBLIC（公共）或 PRIVATE（私有）    。 当数据库管理员需要安装所有用户都能使用的包时，公共范围就非常有用。 若采用私有范围，则只有安装这个包的用户才能使用它。 如果未指定范围，则默认范围为 PRIVATE（私有）  。

### <a name="add-the-package-offline"></a>脱机添加包

如果客户端计算机没有 Internet 连接，则需要通过能够访问 Internet 的计算机使用 miniCRAN 下载 glue 包   。 然后将包复制到客户端计算机，可以在其中脱机安装该包。
有关安装 miniCRAN 的信息，请参阅[安装 miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran)  。

在能够访问 Internet 的计算机上执行以下操作：

1. 运行以下 R 脚本，为 glue 创建本地存储库  。 此示例在 `c:\downloads\glue` 中创建存储库文件夹。

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end


   至于 `Rversion` 值，请使用安装在 SQL Server 上的 R 版本。 若要验证已安装的版本，请使用以下 T-SQL 命令。

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. 将整个 glue 存储库文件夹 (`c:\downloads\glue`) 复制到客户端计算机  。 例如，将它复制到 `c:\temp\packages\glue` 文件夹。

在客户端计算机上执行以下操作：

1. 打开 RStudio 并创建一个新 R Script 文件  。

1. 通过 sqlmlutils 使用以下 R 脚本安装 glue 包   。 将自己的 SQL Server 数据库连接信息替换进去（如果不使用 Windows 身份验证，请添加 `uid` 和 `pwd` 参数）。

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > 范围可为 PUBLIC（公共）或 PRIVATE（私有）    。 当数据库管理员需要安装所有用户都能使用的包时，公共范围就非常有用。 若采用私有范围，则只有安装这个包的用户才能使用它。 如果未指定范围，则默认范围为 PRIVATE（私有）  。

## <a name="use-the-package"></a>使用包

安装 glue 包后，可以通过 T-SQL sp_execute_external_script 命令在 SQL Server 中的 R 脚本中使用它   。

1. 打开 Azure Data Studio 或 SSMS 并连接到 SQL Server 数据库。

1. 运行以下命令：

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
       , @script = N'
   library(glue)

   name <- "Fred"
   birthday <- as.Date("2020-06-14")
   text <- glue(''My name is {name} '',
   ''and my birthday is {format(birthday, "%A, %B %d, %Y")}.'')

   print(text)
         ';
   ```

    **结果**

    ```text
    My name is Fred and my birthday is Sunday, June 14, 2020.
    ```

## <a name="remove-the-package"></a>删除包

如果要删除 glue 包，请运行以下 R 脚本  。 使用与之前的定义一致的 connection 变量  。

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>后续步骤

- 有关已安装的 R 包的信息，请参阅[获取 R 包信息](r-package-information.md)
- 有关使用 R 包的帮助信息，请参阅[使用 R 包的技巧](tips-for-using-r-packages.md)
- 有关安装 Python 包的信息，请参阅[通过 pip 安装 Python 包](install-additional-python-packages-on-sql-server.md)
- 有关 SQL Server 机器学习服务的详细信息，请参阅[什么是 SQL Server 机器学习服务（Python 和 R）？](../what-is-sql-server-machine-learning.md)
