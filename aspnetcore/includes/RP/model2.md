<a name="dc"></a>

### <a name="add-a-database-context-class"></a>添加数据库上下文类

在 RazorPagesMovie 项目中，创建名为“数据”的新文件夹  。 将以下 `RazorPagesMovieContext` 类添加到“数据”文件夹  ：

[!code-csharp[](~/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie22/Data/RazorPagesMovieContext.cs)]

前面的代码为实体集创建 `DbSet` 属性。 在 Entity Framework 中，实体集通常与数据表相对应，具体实体与表中的行相对应。

<a name="cs"></a>

### <a name="add-a-database-connection-string"></a>添加数据库连接字符串

向 appsettings.json 文件添加一个连接字符串，如以下突出显示的代码所示： 

::: moniker range=">= aspnetcore-3.0"

[!code-json[](~/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie30/appsettings_SQLite.json?highlight=10-12)]

### <a name="add-nuget-packages-and-ef-tools"></a>添加 NuGet 包和 EF 工具

打开 RazorPagesMovie 项目的终端。  右键单击设计/布局栏中的项目名称，然后转到终端中的“工具”>“打开”  。 在终端中运行以下 .NET Core CLI 命令：

```dotnetcli
dotnet tool install --global dotnet-ef --version 3.0.0-*
dotnet add package Microsoft.EntityFrameworkCore.SQLite --version 3.0.0-*
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design --version 3.0.0-*
dotnet add package Microsoft.EntityFrameworkCore.Design --version 3.0.0-*
dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 3.0.0-*
```

上述命令为 .NET CLI 添加了 Entity Framework Core 工具，并为项目添加了多个包。 `Microsoft.VisualStudio.Web.CodeGeneration.Design` 包对基架是必需的。

<a name="reg"></a>

### <a name="register-the-database-context"></a>注册数据库上下文

将以下 `using` 语句添加到 Startup.cs 顶部  ：

```csharp
using RazorPagesMovie.Models;
using Microsoft.EntityFrameworkCore;
```

使用 `Startup.ConfigureServices` 中的[依赖关系注入](xref:fundamentals/dependency-injection)容器注册数据库上下文。

[!code-csharp[](~/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie30/Startup.cs?name=snippet_UseSqlite&highlight=11-12)]

::: moniker-end

::: moniker range="< aspnetcore-3.0"

[!code-json[](~/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie/appsettings_SQLite.json?highlight=8-9)]

### <a name="add-required-nuget-packages"></a>添加所需的 NuGet 包

运行以下 .NET Core CLI 命令，以将 SQLite 和 CodeGeneration.Design 添加到项目中：

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SQLite
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.Design
```

`Microsoft.VisualStudio.Web.CodeGeneration.Design` 包对基架是必需的。

<a name="reg"></a>

### <a name="register-the-database-context"></a>注册数据库上下文

将以下 `using` 语句添加到 Startup.cs 顶部  ：

```csharp
using RazorPagesMovie.Models;
using Microsoft.EntityFrameworkCore;
```

使用 `Startup.ConfigureServices` 中的[依赖关系注入](xref:fundamentals/dependency-injection)容器注册数据库上下文。

[!code-csharp[](~/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie22/Startup.cs?name=snippet_UseSqlite&highlight=11-12)]

生成项目以检查错误。
::: moniker-end
