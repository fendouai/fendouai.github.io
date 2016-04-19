##NuGet 简介

NuGet 是一种 Visual Studio 扩展，它能够简化在 Visual Studio 项目中添加、更新和删除库（部署为程序包）的操作。  NuGet 程序包是打包成一个文件的文件集，扩展名是 .  nupkg，使用开放打包约定 (OPC) 格式。  

OPC 仅仅是具有某些元数据的 zip 文件的首字母缩写词。  事实上，您可能早已熟悉 OPC，因为 Word 和 Excel 文档正是使用此格式。  如果您取一个 .docx 文件并将文件扩展名改为 .zip，您实际可以打开它并浏览里面的内容。  .  nupkg 文件同样如此。  

>使用 NuGet 管理项目库 : 
https://msdn.microsoft.com/zh-cn/magazine/hh547106.aspx

##注册 NuGet

>注册地址：https://www.nuget.org/
>管理地址：https://www.nuget.org/account/Packages
>上传地址：https://www.nuget.org/packages/upload

##下载和安装 NuGet

>下载地址：https://dist.nuget.org/index.html
>NuGetPackageExplorer下载地址：
https://github.com/NuGetPackageExplorer/NuGetPackageExplorer

* 获取 API Key，获取页面：https://www.nuget.org/account
* 下载 NuGet.exe，将设置机器的 PATH 环境变量，将其 NuGet.exe 的路径添加到 PATH变量中。

![QQ图片20160414150237.png](http://upload-images.jianshu.io/upload_images/76451-ee3abd93ed5c1b7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 设置 API Key，打开 Windows PowerShell，找到 NuGet.exe的路径，然后输入下面的命令：
`
nuget setApiKey your-api-key
`

##项目库的设置

* 在 Properties 下找到 AssemblyInfo.cs。

![assemblyinfo.png](http://upload-images.jianshu.io/upload_images/76451-9787ad93abeafc84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 编辑 Title，Description，Version 等内容
`
using System.Reflection;
using System.Runtime.CompilerServices;
using System.Runtime.InteropServices;
// 有关程序集的一般信息由以下
// 控制。更改这些特性值可修改
// 与程序集关联的信息。
[assembly: AssemblyTitle("ConsoleApplication60")]
[assembly: AssemblyDescription("")]
[assembly: AssemblyConfiguration("")]
[assembly: AssemblyCompany("Microsoft")]
[assembly: AssemblyProduct("ConsoleApplication60")]
[assembly: AssemblyCopyright("Copyright © Microsoft 2016")]
[assembly: AssemblyTrademark("")]
[assembly: AssemblyCulture("")]
//将 ComVisible 设置为 false 将使此程序集中的类型
//对 COM 组件不可见。  如果需要从 COM 访问此程序集中的类型，
//请将此类型的 ComVisible 特性设置为 true。
[assembly: ComVisible(false)]
// 如果此项目向 COM 公开，则下列 GUID 用于类型库的 ID
[assembly: Guid("d866cf73-5bfd-4e84-855b-79f6d3aae38d")]
// 程序集的版本信息由下列四个值组成: 
//
//      主版本
//      次版本
//      生成号
//      修订号
//
//可以指定所有这些值，也可以使用“生成号”和“修订号”的默认值，
// 方法是按如下所示使用“*”: :
// [assembly: AssemblyVersion("1.0.*")]
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyFileVersion("1.0.0.0")]
`

##NuGet 发布项目库

* 进入项目目录，找到　.csproj　文件，例如：cn.jpush.api.csproj
* 进入 Windows PowerShell命令行，在项目目录中运行
`
nuget spec
`

![spec.png](http://upload-images.jianshu.io/upload_images/76451-378129d79852e054.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 查看生成的 .nuspec 文件，例如：cn.jpush.api.nuspec
* 生成类库包，在项目目录运行
`
nuget pack yourproject.csproj
`

![pack.png](http://upload-images.jianshu.io/upload_images/76451-97a4b8cc0653bb22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 查看生成的 .nupkg文件，例如：cn.jpush.api.1.0.0.0.nupkg
* 发布类库包，在项目目录运行
`
nuget push yourproject.1.0.0.0.nupkg
`

![push.png](http://upload-images.jianshu.io/upload_images/76451-a7ffedf10f973476.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 发布成功，登录NuGet 在https://www.nuget.org/account/Packages 可以管理发布的Packages
`
Your package was pushed.
`

##在新项目中使用 NuGet
* 在项目->引用，右键选择 管理 NuGet 程序包

![QQ图片20160414145437.png](http://upload-images.jianshu.io/upload_images/76451-7f1230380e7be941.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 搜索刚才上传的程序包名，即可下载使用。

![QQ图片20160414145711.png](http://upload-images.jianshu.io/upload_images/76451-19f512cc87813fc8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##参考资料
>Creating and Publishing a Package
https://docs.nuget.org/Create/Creating-and-Publishing-a-Package
>NuGet：https://www.nuget.org/
>使用 NuGet 管理项目库 : 
https://msdn.microsoft.com/zh-cn/magazine/hh547106.aspx
>手把手教你用 Nuget 管理自己的项目库:
http://blog.jobbole.com/92150/
