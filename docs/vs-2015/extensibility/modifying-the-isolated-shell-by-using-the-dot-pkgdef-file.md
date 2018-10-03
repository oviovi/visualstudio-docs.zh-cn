---
title: 通过使用修改独立的 Shell。Pkgdef 文件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f70036f91eb52d85054465e6eea9f82672d851f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47479552"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>通过使用修改独立的 Shell。Pkgdef 文件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[修改独立 Shell 的使用。Pkgdef 文件](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file)。  
  
.Pkgdef 文件支持可用于自定义独立的 shell 应用程序的设置。 它指定应用程序的计算机上安装并启动应用程序时所引用的 Visual Studio shell 时创建的值。 设置组织根据适用的注册表项在文件中。  
  
> [!WARNING]
>  请注意 Visual Studio 启动时不会扫描 VSPackage 的.vsixmanifest 文件中未声明的.pkgdef 文件。  
  
 .Pkgdef 文件包含部分，每个由键标识，或者`[$RootKey$]`或`[$RootKey$\`*子项*`]`，其中 $RootKey$ 是应用程序的根键。  
  
 每个部分包含具有以下格式的名称/值对： `"` *ValueName*`"=`*值*。  
  
 值为字符串括在引号中或一个 32 位整数，它表示为一个 dword 值。 值具有以下约束：  
  
-   所有的 dword 值是以十六进制格式，例如`dword:00000001`。  
  
     对于布尔值，1 表示 true，，0 表示 false。  
  
-   所有 GUID 字符串都位于注册表格式，例如， `"{00000000-0000-0000-0000-000000000000}"`。  
  
-   所有可本地化的资源标识符具有窗体"@*resourceID*"或"#*resourceID*"，其中*resourceID*是应用程序用户界面包中的资源标识符例如， `"@102"`。 应用程序用户界面包是 AppLocalizationPackage 设置中引用的包。  
  
 例如，应用于对象的  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 可以将注释添加到.pkgdef 文件。 单行注释与前两个字符具有两个斜杠。  
  
 替换字符串的列表，请参阅[中使用的替换字符串。Pkgdef 和。Pkgundef 文件](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
 以下各节介绍影响 Visual Studio shell 在独立模式下的行为的特定注册表值。 此外可以在此文件中定义应用程序的其他注册表值。  
  
> [!NOTE]
>  如果.pkgdef 文件中未提供一种设置，则没有对应的条目进行在注册表中。  
  
## <a name="settings"></a>设置  
 下表介绍 [$RootKey$] 下定义的值。  
  
|name|类型|“值”|  
|----------|----------|-----------|  
|AddinsAllowed|dword|如果可以加载外接程序; 则为 true否则为 false。<br /><br /> 默认值为 true。|  
|AllowsDroppedFilesOnMainWindow|dword|如果主窗口可以接受拖放的文件; 则为 true否则为 false。 通过使用打开的文件放置在主窗口上<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>方法。 这相当于使用打开的文档**开放**命令**文件**应用程序中的菜单。<br /><br /> 默认值为 true。|  
|AppIcon|字符串|程序图标的完整路径。 此图标将出现在左侧的应用程序名称的标题栏。<br /><br /> 默认值是"$RootFolder$\\*solutionName*.ico"，其中*solutionName*是应用程序解决方案文件的名称。|  
|AppLocalizationPackage|字符串|包含应用程序的用户界面附属程序集的 VSPackage 的 GUID。 此 VSPackage 包含.vsct 文件的已编译的版本，并且可以包括其他的本地化的字符串。 功能集和菜单命令组可以启用或禁用通过更改 UI 项目.vsct 文件中的设置。<br /><br /> 默认值为"{*vsUiPackageGuid*}"，其中*vsUiPackageGuid*是分配给应用程序用户界面包的 GUID。|  
|应用程序名|字符串|应用程序的名称。 应用程序窗口的标题栏中显示名称。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
|CommandLineLogo|字符串|在控制台窗口中运行应用程序时在横幅文本。 此设置会影响仅支持命令行生成操作的应用程序。<br /><br /> 默认值是"*companyName * * solutionName* 1.0 版。"，其中*companyName*是提供安装 Windows 时，该公司的名称和*solutionName*是应用程序解决方案文件的名称。|  
|DefaultDebugEngine|字符串|默认 GUID 调试引擎以使用该应用程序。<br /><br /> 注意： 应用程序未指定默认调试引擎指示一个空的 GUID （均为零）。 这使调试器能够选择要使用的调试引擎。<br /><br /> 默认值为“{00000000-0000-0000-0000-000000000000}”。|  
|DefaultHomePage|字符串|内部 Web 浏览器窗口默认主页 URL。<br /><br /> 如果**主页上**选项现已推出应用程序，则此设置还会影响该选项的默认状态。 有关详细信息，请参阅[Web 浏览器中，环境中，Options Dialog Box](../ide/reference/web-browser-environment-options-dialog-box.md)。<br /><br /> 默认值为 Windows 安装时提供的公司的 URL。|  
|DefaultProjectsLocation|字符串|默认项目文件夹的完整路径。 例如，应用于对象的<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> 如果**Visual Studio 项目位置**选项现已推出应用程序，则此设置还会影响该选项的默认状态。 有关详细信息，请参阅[NIB： 常规、 项目和解决方案选项对话框](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。<br /><br /> 默认值是"$MyDocuments$\\*solutionName*"，其中*solutionName*是应用程序解决方案文件的名称。|  
|DefaultSearchPage|字符串|内部 Web 浏览器窗口默认搜索页 URL。<br /><br /> 如果**搜索页**选项现已推出应用程序，则此设置还会影响该选项的默认状态。 有关详细信息，请参阅[Web 浏览器中，环境中，Options Dialog Box](../ide/reference/web-browser-environment-options-dialog-box.md)。<br /><br /> 默认值为“http://search.live.com”。|  
|DefaultUserFilesFolderRoot|字符串|相对于当前用户的用户文件夹的名称的我的文档文件夹。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
|DisableOutputWindow|dword|指示为已禁用独立的 shell 是否应将输出窗口。<br /><br /> 如果此值设置为 true，Visual Studio 不显示在解决方案生成管理器输出**输出**窗口和隐藏**显示输出窗口在生成开始时**中的复选框**项目和解决方案**中的类别**选项**对话框。<br /><br /> 默认值为 False。|  
|HideMiscellaneousFilesByDefault|dword|为 true，则隐藏**杂项文件**默认情况下的文件夹**解决方案资源管理器**; 否则为 false。<br /><br /> 如果**解决方案资源管理器中的显示杂项文件**选项现已推出应用程序，则此设置还会影响该选项的默认状态。 有关详细信息，请参阅[文档，环境中，Options Dialog Box](../ide/reference/documents-environment-options-dialog-box.md)。<br /><br /> 默认值为 False。|  
|HideSolutionConcept|dword|若要创建的所有项目作为独立项目和隐藏的解决方案和解决方案相关的命令，为独立的项目默认设置。否则为 false。<br /><br /> 如果**总是显示解决方案**选项现已推出应用程序，则此设置还会影响该选项的默认状态。 有关详细信息，请参阅[NIB： 常规、 项目和解决方案选项对话框](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。<br /><br /> 默认值为 False。|  
|NewProjDlgInstalledTemplatesHdr|字符串|中的 Visual Studio 安装模板标头名称**模板**列表中**新项目**对话框。 这是一个字符串或从应用程序用户界面包加载的可本地化的资源标识符。<br /><br /> 默认值是"*solutionName*已安装的模板"，其中*solutionName*是应用程序解决方案文件的名称。|  
|NewProjDlgSlnTreeNodeTitle|字符串|名称**Visual Studio 解决方案**中的节点**项目类型**树中**新项目**对话框。 这是一个字符串或从应用程序用户界面包加载的可本地化的资源标识符。<br /><br /> 默认值是"*solutionName*已安装的模板"，其中*solutionName*是应用程序解决方案文件的名称。|  
|SolutionFileCreatorIdentifier|字符串|应用程序标识符，将显示为第二行中的应用程序生成的解决方案文件。 这条线指示创建该文件的应用程序。 按照约定，此值包含名称的应用程序和应用程序版本号。 例如，应用于对象的<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> VSLauncher.exe 程序，这是用于打开 Visual Studio 解决方案文件的默认程序，使用此第二行来确定要在其中打开解决方案文件的 Visual Studio 版本。 应用程序将需要自己启动程序来处理其关联的解决方案文件。 启动器无法还使用此第二行在解决方案文件以确定哪一个版本的应用程序打开该解决方案。<br /><br /> 注意： Visual Studio VSLauncher.exe 程序不处理独立的 shell 应用程序创建的.sln 文件。<br /><br /> 默认值是"*solutionName*解决方案文件，格式版本 10.00"，其中*solutionName*是应用程序解决方案文件的名称。|  
|SolutionFileExt|字符串|应用程序解决方案文件扩展名。 我们建议选择唯一的文件名扩展 (not.sln)。<br /><br /> 默认值是"*solutionName*_sln"，其中*solutionName*是应用程序解决方案文件的名称。|  
|SplashScreenBitmap|字符串|应用程序的初始屏幕的位图文件的完整路径。<br /><br /> 默认值为"$RootFolder$\Splash.bmp"。|  
|ThisVersionDTECLSID|字符串|应用程序的自动化对象类标识符 (CLSID)。<br /><br /> 应用程序自动化对象是在 Visual Studio shell 自动化模型并实现应用程序的顶级对象<xref:EnvDTE._DTE?displayProperty=fullName>接口。<br /><br /> 如果应用程序自动化对象已正确注册下 HKEY_CLASSES_ROOT\CLSID 注册表项，则可以使用[CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)函数来直接创建的应用程序的实例。<br /><br /> 在 Visual Studio shell 使用此 CLSID 来注册应用程序自动化对象在运行对象表 (ROT) 中使用 ACTIVEOBJECT_WEAK 标志。 这使您可以使用[GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)函数以检索正在运行的应用程序实例的指针。 此外，如果定义的应用程序自动化对象的 ProgID，然后在 Visual Studio shell 还会注册应用程序的每个实例在 ROT 中通过使用窗体项标记*progID*:*processID*，其中*progID*是应用程序自动化对象的 ProgID 和*processID*是应用程序实例的进程标识符。 例如，如果您创建一个名字对象，如下所示：<br /><br /> `CreateItemMoniker(L"!",`  *instanceString* `, &instanceMoniker)`<br /><br /> 其中`instanceString`是*progID*:*processID*字符串。 然后，您可以使用`instanceMoniker`ROT GetObject 函数来获取的实例。<br /><br /> 如果省略 ThisVersionDTECLSID 设置，则该应用程序不是公开通过组件对象模型 (COM)。 在这种情况下，不能通过调用创建的应用程序实例[CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)函数并不能在 ROT 中注册。<br /><br /> 每个版本的 VSPackage 必须具有不同的 CLSID。<br /><br /> 默认值为 Visual Studio 生成应用程序的自动化对象的 GUID。|  
|ThisVersionSolutionCLSID|字符串|应用程序的解决方案对象的 CLSID。<br /><br /> 解决方案自动化对象包含有关应用程序和实现的实例中当前打开的解决方案信息<xref:EnvDTE._Solution?displayProperty=fullName>接口。<br /><br /> 如果解决方案自动化对象已正确注册下 HKEY_CLASSES_ROOT\CLSID 注册表项，则可以使用[CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)函数来直接创建应用程序的解决方案对象。<br /><br /> 在 Visual Studio shell 使用此 CLSID 来使用 ACTIVEOBJECT_WEAK 标志在 ROT 中注册解决方案自动化对象。<br /><br /> 如果省略此设置，则解决方案类没有注册与组件对象模型 (COM) 中，并且不能通过调用创建一个解决方案对象[CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)函数并不能在中注册在 ROT 中。<br /><br /> 默认值为 Visual Studio 生成应用程序的解决方案对象的 GUID。|  
|UserFilesSubFolderName|字符串|应用程序会创建用户文件和子文件夹的用户的 My Documents 文件夹下的子文件夹的名称。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
|UserOptsFileExt|字符串|适用于应用程序的解决方案用户选项文件的扩展。<br /><br /> 默认值为应用程序解决方案文件的名称。|  
  
## <a name="binding-path-settings"></a>绑定路径设置  
 [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] 键包含的外壳将检查程序集的目录列表。 这些目录将添加到 shell 探测专用程序集的应用程序的目录的列表。  
  
 默认情况下，没有绑定路径项添加到.pkgdef 文件中。 但是，Visual Studio 安装目录的以下子目录自动添加到注册表中的应用程序绑定路径列表中。  
  
-   Common7\ide \  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 若要将目录添加到绑定路径，将添加窗体的条目"*directoryName*"=""，其中*directoryName*是绝对路径。 例如，应用于对象的  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>配置文件设置  
 下表介绍了为每个关联的包 [$RootKey$ \Profile] 下定义的值。  
  
|name|类型|“值”|  
|----------|----------|-----------|  
|AutoSaveFile|字符串|在应用程序将自动保存文件存储在其中的目录。<br /><br /> 默认值为"$RootFolder$\Profiles\CurrentSettings.vssettings"。|  
  
## <a name="package-satellite-dll-settings"></a>包附属 DLL 设置  
 下表描述了下定义的值 [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] 来获得附属 DLL 的每个关联的包，其中*vsPackageGuid*关联的包的 guid。  
  
|name|类型|“值”|  
|----------|----------|-----------|  
|Dll 名称|字符串|DLL 的文件名。<br /><br /> 默认值是"*solutionName*ui.dll"，其中*solutionName*是应用程序解决方案文件的名称。|  
|路径|字符串|包含附属 DLL 的目录。<br /><br /> 默认值为"$PackageFolder$"。|  
  
## <a name="package-menu-item-settings"></a>包菜单项设置  
 [$RootKey$ \Menus] 注册表项定义的应用程序的用户界面资源文件。  
  
 菜单项值具有窗体"{*vsUiPackageGuid*}"=" *resourceId*， *versionNumber*"，其中*vsUiPackageGuid*的 guid应用程序用户界面包， *resourceId*是包含 UI 元素的 CTMENU 资源的资源标识符和*versionNumber* CTMENU 是虚拟的版本号资源。 有关详细信息，请参阅[注册互操作程序集命令处理程序](../extensibility/internals/registering-interop-assembly-command-handlers.md)。  
  
 默认情况下，应用程序用户界面包的.pkgdef 文件中创建一个菜单项条目。  
  
 每个包，它提供菜单项和的分布式应用程序的一部分，将添加为包的菜单项项。  
  
## <a name="see-also"></a>请参阅  
 [自定义独立的 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgundef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)
