---
title: VS 2017 中的调试入门
description: 开始使用 Visual Studio 调试器调试应用程序
ms.custom: mvc
ms.date: 06/15/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf7bcba0ceaa71b933d4875cd5eee28d7cea0028
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904963"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>初步了解 Visual Studio 调试器

本主题介绍 Visual Studio 提供的调试器工具。 在 Visual Studio 上下文中，当调试应用时，这通常意味着你在附加了调试器的情况下（即在调试器模式下）运行应用程序。 执行此操作时，调试器在运行过程中可提供许多方法让你查看代码的情况。 你可以逐步执行代码、查看变量中存储的值、设置对变量的监视以查看值何时改变、检查代码的执行路径等。如果这是你第一次尝试调试代码，建议在学习本主题之前阅读[零基础调试](../debugger/debugging-absolute-beginners.md)。

此处所述的功能适用于 C#、C++、Visual Basic、JavaScript 和 Visual Studio 支持的其他语言（除非另有说明）。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>设置断点并启动调试器

要进行调试，需要在调试器附加到应用进程的情况下启动应用。 F5（“调试”>“开始调试”）是执行该操作最常见的方法。 但是，现在你可能没有设置任何断点来检查应用代码，因此我们首先设置断点再开始调试。 断点是可靠调试的最基本和最重要的功能。 断点指示 Visual Studio 应在哪个位置挂起你的运行代码，以使你可以查看变量的值或内存的行为，或确定代码的分支是否运行。 

若代码编辑器中打开了文件，则可通过单击代码行左侧的边缘来设置断点。

![设置断点](../debugger/media/dbg-tour-set-a-breakpoint.gif "Set a breakpoint")

按 F5（“调试”>“开始调试”）或调试工具栏中的“开始调试”按钮 ![开始调试](../debugger/media/dbg-tour-start-debugging.png "Start Debugging")，调试器将运行至它遇到的第一个断点。 如果应用尚未运行，则按 F5 会启动调试器并在第一个断点处停止。

当你知道要详细检查的代码行或代码段时，断点功能非常有用。

## <a name="navigate"></a> 使用单步执行命令在调试器中移动浏览代码

我们为大多数命令提供键盘快捷键，便于你更快地移动浏览应用代码。 （括号中显示了等效命令，如菜单命令。）

要在附加了调试器的情况下启动应用，请按 F11（“调试”>“单步执行”）。 F11 是“单步执行”命令，每按一次，应用就执行下一个语句。 使用 F11 启动应用时，调试器会在执行的第一个语句上中断。

![F11 单步执行](../debugger/media/dbg-tour-f11.png "F11 Step Into")

黄色箭头表示调试器暂停处的语句，它还在同一点上暂停应用执行（此语句尚未执行）。

F11 是一种以最详尽方式检查执行流的好方法。 （为了更快地浏览代码，我们还向你展示了一些其他选项。）默认情况下，调试器会跳过非用户代码（如果需要更多详细信息，请参阅[仅我的代码](../debugger/just-my-code.md)）。

>[!NOTE]
> 在托管代码中将看到一个对话框，询问你是否希望在自动跳过属性和运算符时收到通知（默认行为）。 若稍后想更改设置，请在“调试”下的“工具”>“选项”菜单中禁用“单步跳过属性和运算符”设置。

## <a name="step-over-code-to-skip-functions"></a>单步跳过代码以跳过函数

如果所在的代码行是函数或方法调用，则可以按 F10（“调试”>“单步跳过”）而不是 F11。

按 F10 将使调试器前进，但不会单步执行应用代码中的函数或方法（代码仍将执行）。 按 F10 可跳过你不感兴趣的代码。 这样就可以快速转到更感兴趣的代码。

## <a name="step-into-a-property"></a>单步执行属性

如前所述在默认情况下，调试器会跳过托管属性和字段，但通过“单步执行特定内容”命令可替代此行为。

右键单击属性或字段，选择“单步执行特定内容”，然后选择一个可用选项。

![单步执行特定内容](../debugger/media/dbg-tour-step-into-specific.png "Step Into Specific")

在此示例中，通过“单步执行特定内容”将转到 `Path.set` 的代码。

![单步执行特定内容](../debugger/media/dbg-tour-step-into-specific-2.png "Step Into Specific")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>使用鼠标快速运行到代码中的某个点

在调试器中，将鼠标悬停在代码行上，直到“运行到单击处”（将执行运行到此处）按钮![运行到单击处](../debugger/media/dbg-tour-run-to-click.png "RunToClick")出现在左侧。

![运行到单击处](../debugger/media/dbg-tour-run-to-click-2.png "Run to Click")

> [!NOTE]
> “运行到单击处”（将执行运行到此处）按钮是 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中的新增功能。

单击“运行到单击处”（将执行运行到此处）按钮。 调试器将前进到单击的代码行。

使用此按钮类似于设置临时断点。 此命令对于快速到达应用代码的可见区域也很方便。 你可在任何打开的文件中使用“运行到单击处”。

## <a name="advance-the-debugger-out-of-the-current-function"></a>使调试器从当前函数中跳出

有时你可能希望继续调试会话，但在整个当前函数中一直使调试器前进。

按 Shift+F11（或“调试”>“单步跳出”）。

此命令将恢复应用执行（并使调试器前进），直到当前函数返回。

## <a name="run-to-cursor"></a>运行到光标处

按“停止调试”红色按钮![停止调试](../debugger/media/dbg-tour-stop-debugging.png "Stop Debugging")或 Shift + F5 来停止调试器。

右键单击应用中的代码行，然后选择“运行到光标处”。 此命令将启动调试并在当前代码行上设置临时断点。

![运行到光标处](../debugger/media/dbg-tour-run-to-cursor.png "Run to Cursor")

如果设置了断点，则调试器会在其命中的第一个断点处暂停。

按 F5，直至到达在其上选择了“运行到光标处”的代码行。

当编辑代码并希望快速设置临时断点并同时启动调试器时，此命令很有用。

> [!NOTE]
> 调试时可使用“调用堆栈”窗口中的“运行到光标处”。

## <a name="restart-your-app-quickly"></a>快速重启应用

单击调试工具栏中的“重启”按钮![重启应用](../debugger/media/dbg-tour-restart.png "Restart App") (Ctrl+Shift+F5)。

当你按下“重启”时，与停止应用并重启调试器相比，它节省了时间。 调试器在执行代码命中的第一个断点处暂停。

若确实要停止调试器并返回到代码编辑器，可以按红色停止![停止调试](../debugger/media/dbg-tour-stop-debugging.png "Stop Debugging")按钮而不是“重启”。

## <a name="inspect-variables-with-data-tips"></a>使用数据提示检查变量

既然你已经有了粗略的了解，那么就有机会开始使用调试器检查应用状态（变量）。 那些允许你检查变量的功能是调试器的一些最有用的功能，并且有不同方法可执行此操作。 通常，当尝试调试问题时，你试图找出变量是否存储了你期望它们在特定应用状态具有的值。

在调试器中暂停时，将鼠标悬停在对象上并看到其默认属性值（在此示例中，文件名 `market 031.jpg` 是默认属性值）。

![查看数据提示](../debugger/media/dbg-tour-data-tips.gif "View a data tip")

展开对象以查看其所有属性（例如本示例中的 `FullPath` 属性）。

通常，在调试时，你需要快速检查对象的属性值，数据提示是一种实现此目的的好方法。

> [!TIP]
> 在大多数受支持的语言中，可在调试会话中途编辑代码。 有关详细信息，请参阅[编辑并继续](../debugger/edit-and-continue.md)。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>使用“自动”和“局部变量”窗口检查变量

调试时，查看代码编辑器底部的“自动”窗口。

![“自动”窗口](../debugger/media/dbg-tour-autos-window.png "Autos window")

在“自动”窗口中，可看到变量及其当前值和类型。 “自动”窗口显示当前行或前一行使用的所有变量（在 C++ 中，该窗口显示前三个代码行中的变量。 查看文档以了解特定于语言的行为）。

> [!NOTE]
> 在 JavaScript 中，支持“局部变量”窗口，但不支持“自动”窗口。

接下来，查看“局部变量”窗口。 “局部变量”窗口显示当前范围中的变量。

![“局部变量”窗口](../debugger/media/dbg-tour-locals-window.png "Locals window")

在此示例中，`this` 对象和 `f` 对象处于范围内。 有关详细信息，请参阅[在“自动”窗口和“局部变量”窗口中检查变量](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>设置监视

可使用“监视”窗口指定要关注的变量（或表达式）。

在调试时，右键单击对象并选择“添加监视”。

![“监视”窗口](../debugger/media/dbg-tour-watch-window.png "Watch window")

在本示例中，你在 `f` 对象上设置了监视，当在调试器中移动时，可看到其值发生了变化。 与其他变量窗口不同，“监视”窗口始终显示正在监视的变量（当超出范围时，它们会变灰）。

有关详细信息，请参阅[使用“监视”窗口和“快速监视”窗口设置监视](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>检查调用堆栈

调试时单击“调用堆栈”窗口，默认情况下，该窗口在右下方窗格中打开。

![检查调用堆栈](../debugger/media/dbg-tour-call-stack.png "Examine the call stack")

“调用堆栈”窗口显示方法和函数被调用的顺序。 最上面一行显示当前函数（此示例中的 `Update` 方法）。 第二行显示 `Update` 是从 `Path.set` 属性调用的，依此类推。 调用堆栈是检查和理解应用执行流的好方法。

> [!NOTE]
> “调用堆栈”窗口类似于某些 IDE（如 Eclipse）中的调试透视图。

可双击代码行来查看该源代码，这也会更改调试器正在检查的当前范围。 此操作不会使调试器前进。

还可使用“调用堆栈”窗口中的右键单击菜单执行其他操作。 例如，你可将断点插入到指定的函数中，使用“运行到光标处”重启应用，然后检查源代码。 请参阅[操作说明：检查调用堆栈](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="exception"></a> 检查异常

应用引发异常时，调试器会将你转至引发异常的代码行。

![异常帮助程序](../debugger/media/dbg-tour-exception-helper.png "Exception Helper")

在此示例中，异常帮助程序向你显示 `System.Argument` 异常以及一条错误消息，指出该路径不是合法形式。 因此，我们知道方法或函数参数发生了错误。

在此示例中，`DirectoryInfo` 调用在存储于 `value` 变量中的空字符串上引发了错误。

异常帮助程序是帮助调试错误的好功能。 你还可以执行其他操作，如查看错误详细信息及从异常帮助程序添加监视。 或者，如有需要可更改引发特定异常的条件。

> [!NOTE]
> 异常帮助程序取代 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中的异常情况助手。

展开“异常设置”节点以查看有关如何处理此异常类型的更多选项，但对于本教程无需更改任何内容！

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>在 Azure 应用服务中调试实时 ASP.NET 应用

当执行感兴趣的代码时，Snapshot Debugger 会为生产中的应用拍摄快照。 要指示调试程序拍摄快照，可在代码中设置 snappoints 和 logpoints。 使用调试程序，可精确查看出错的内容，而不影响生产应用程序的流量。 快照调试程序有助于大幅减少用于解决生产环境中发生的问题的时间。

![启动快照调试程序](../debugger/media/snapshot-launch.png "Launch the snapshot debugger")

快照集合适用于在 Azure 应用服务中运行的 ASP.NET 应用程序。 ASP.NET 应用程序必须在 .NET Framework 4.6.1 或更高版本上运行，并且 ASP.NET Core 应用程序必须在 Windows 上的 .NET Core 2.0 或更高版本上运行。

有关详细信息，请参阅[使用 Snapshot Debugger 调试实时 ASP.NET 应用](../debugger/debug-live-azure-applications.md)。

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>使用 IntelliTrace 后退查看快照 (Visual Studio Enterprise)

IntelliTrace 后退会在每个断点处及调试器步骤事件发生时自动拍摄应用程序的快照。 凭借记录的快照便可以返回到上一个断点或步骤，并查看当时应用程序的状态。 如果希望查看以前的应用程序状态，但不想重新启动调试或重新创建所需应用状态，使用 IntelliTrace 后退可以节省时间。

可以通过使用调试工具栏中的“后退”和前进”按钮浏览和查看快照。 这些按钮用于浏览“诊断工具”窗口中“事件”选项卡上显示的事件。

![“后退”和“前进”按钮](../debugger/media/intellitrace-step-back-icons-description.png  "Step Backward and Forward buttons")

有关详细信息，请参阅[使用 IntelliTrace 检查上一应用状态](../debugger/view-historical-application-state.md)页。

## <a name="next-steps"></a>后续步骤

在本教程中，你已快速了解了许多调试器功能。 你可能会需要更深入地了解其中一个功能，例如断点。

> [!div class="nextstepaction"]
> [了解如何使用断点](../debugger/using-breakpoints.md)
