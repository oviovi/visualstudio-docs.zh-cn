---
title: 调试 DLL 项目 |Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f35a04620da94efca70fb33933f3940005996e29
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561689"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>调试 Visual Studio 中的 Dll (C#，c + +、 Visual Basic 中， F#)

DLL （动态链接库） 是一个库，包含代码和可由多个应用的数据。 您可以使用 Visual Studio 来创建、 构建、 配置，并调试 Dll。 

## <a name="create-a-dll"></a>创建一个 DLL

以下 Visual Studio 项目模板可以创建 Dll:

- C#Visual Basic 中，或F#类库 
- C#Visual Basic Windows 窗体控件 (WCF) 库或 
- C + + 动态链接库 (DLL)

有关详细信息，请参见 [MFC 调试技术](../debugger/mfc-debugging-techniques.md)。

调试 WCF 库是类似于调试类库。 有关详细信息，请参阅[Windows 窗体控件](/dotnet/framework/winforms/controls/index)。  

通常从另一个项目中调用 DLL。 当调试调用项目，具体取决于 DLL 配置中，可以单步执行和调试 DLL 代码。 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL 的调试配置

当你使用 Visual Studio 项目模板创建一个应用程序、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自动为调试和发布生成配置创建所需的设置。 如有必要，您可以更改这些设置。 有关详细信息，请参阅以下文章：

- [C++ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [如何：设置调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>设置 c + + DebuggableAttribute

为了使调试器附加到 c + + DLL，c + + 代码必须发出`DebuggableAttribute`。 

**若要设置`DebuggableAttribute`:**

1. 选择中的 c + + DLL 项目**解决方案资源管理器**，然后选择**属性**图标，或右键单击该项目并选择**属性**。 
   
1. 在中**属性**窗格下**链接器** > **调试**，选择**是 (/ ASSEMBLYDEBUG)** 为**可调试的程序集**。 

有关详细信息，请参阅[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)。  

### <a name="vxtskdebuggingdllprojectsexternal"></a> 设置 C/c + + DLL 文件位置 

若要调试外部 DLL，调用项目必须能够找到 DLL，其[.pdb 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)，和 DLL 要求的任何其他文件。 可以创建自定义生成任务来复制这些文件复制到您*\<项目文件夹 > \Debug*输出文件夹中，也可以手动复制文件存在。

对于 C/c + + 项目，可以在项目属性页中，而不是将其复制到输出文件夹设置标头和 LIB 文件位置。 

**若要设置 C/c + + 标头和 LIB 文件位置：**

1. 选择 C/c + + DLL 项目中的**解决方案资源管理器**，然后选择**属性**图标，或右键单击该项目并选择**属性**。 
   
1. 在顶部**属性**窗格下**配置**，选择**所有配置**。
   
1. 下**C/c + +** > **常规** > **附加包含目录**，指定具有标头文件的文件夹。
   
1. 下**链接器** > **常规** > **附加库目录**，指定具有 LIB 文件的文件夹。 
   
1. 下**链接器** > **输入** > **附加依赖项**，指定完整路径和 LIB 文件的文件名。

1. 选择“确定”。

有关 c + + 项目设置的详细信息，请参阅[属性页 （Visual c + +）](/cpp/ide/property-pages-visual-cpp)。
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> 生成的调试版本  

请确保在开始调试之前生成的 dll 的调试版本。 若要调试 DLL，调用应用程序必须能够找到其[.pdb 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)和 DLL 要求的任何其他文件。 

可以创建自定义生成任务的 DLL 文件复制到您*\<调用项目文件夹 > \Debug*输出文件夹中，也可以手动复制文件存在。

请确保在正确的位置中调用该 DLL。 这似乎很明显，但如果调用应用找到并加载的 DLL 的不同副本时，调试器将永远不会命中您设置的断点。 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> 调试 DLL  

不能直接运行 DLL。 它必须由调用应用程序，通常 *.exe*文件。 有关详细信息，请参阅[创建和管理 Visual c + + 项目](/cpp/ide/creating-and-managing-visual-cpp-projects)。 

若要调试 DLL，你可以[从调用应用开始调试](#vxtskdebuggingdllprojectsthecallingapplication)，或[调试 DLL 项目从](how-to-debug-from-a-dll-project.md)通过指定其调用的应用。 此外可以使用调试器[即时窗口](#vxtskdebuggingdllprojectstheimmediatewindow)要在设计时计算的 DLL 函数或方法，而无需使用调用应用。

有关详细信息，请参阅[先来看一下调试器](../debugger/debugger-feature-tour.md)。

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 开始调试从调用应用程序

调用 DLL 的应用可以是：  
  
- 应用程序从[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]相同或不同的解决方案从 DLL 中的项目。  
- 一个已部署的现有应用程序和测试或生产计算机上的运行。  
- 位于 Web 上并通过 URL 访问。  
- 使用嵌入了 DLL 的网页的 web 应用。  
  
若要调试从调用应用程序的 DLL，你可以：  
  
- 打开调用应用程序项目，并开始通过选择调试**调试** > **开始调试**或按**F5**。  

  或  

- 将附加到已部署且正在测试或生产计算机上运行的应用。 使用此方法的 Dll 中，在网站上或在 web 应用中。 有关更多信息，请参见[如何：附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
在开始调试调用应用程序之前，请在 DLL 中设置断点。 请参阅[使用断点](../debugger/using-breakpoints.md)。 DLL 断点命中时，可以逐句通过代码，观察操作在每个行。 有关详细信息，请参阅[在调试器中导航代码](../debugger/navigating-through-code-with-the-debugger.md)。
  
在调试期间，可以使用**模块**窗口以验证 Dll 并 *.exe*文件在应用加载。 若要打开**模块**窗口中的，调试时，选择**调试** > **Windows** > **模块**。 有关更多信息，请参见[如何：使用模块窗口](../debugger/how-to-use-the-modules-window.md)。 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 使用即时窗口  

可以使用**即时**窗口，以在设计时计算的 DLL 函数或方法。 **即时**窗口充当的角色调用的应用。 

>[!NOTE]
>可以使用**即时**在设计时与大多数项目类型的窗口。 它不支持 SQL、 web 项目或脚本。

例如，若要测试的方法名为`Test`类中`Class1`:

1. 打开 DLL 项目中，打开**即时**通过选择窗口**调试** > **Windows** > **即时**或按**Ctrl**+**Alt**+**我**。  
   
1. 实例化类型的对象`Class1`键入以下命令C#中的代码**即时**窗口，然后按**Enter**。 此托管的代码也适用于C#和 Visual Basic 中，使用合适的语法更改：  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   在 C# 中，所有名称必须是全限定名称。 任何方法或变量必须是当前作用域和上下文中的语言服务会尝试计算表达式的值。  
   
1. 假设 `Test` 带有一个 `int` 参数，使用 `Test` “即时” **窗口计算** ：  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   将结果打印**即时**窗口。  
   
1. 可以继续调试 `Test`，方法为在其中设置断点，然后再次计算函数。  
   
   将命中断点，并可以单步执行`Test`。 `Test` 执行后，调试器将回到设计模式。

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>混合模式调试  

可以为托管或本机代码中的 DLL 编写调用应用。 如果本机应用调用的托管的 DLL，并且你想要调试两者，则可以启用在项目属性中的托管和本机调试器。 确切流程取决于是否想要从 DLL 项目或调用应用程序项目开始调试。 有关更多信息，请参见[如何：在混合模式下调试](../debugger/how-to-debug-in-mixed-mode.md)。 

此外可以调试托管的调用项目中的本机 DLL。 有关详细信息，请参阅[如何调试托管和本机代码](how-to-debug-managed-and-native-code.md)。 

## <a name="see-also"></a>请参阅  
 [调试托管代码](../debugger/debugging-managed-code.md)   
 [Visual C++ 项目类型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F# 和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [调试器安全](../debugger/debugger-security.md)
