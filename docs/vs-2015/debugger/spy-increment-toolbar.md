---
title: Spy + + 工具栏 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05dc7dd74af20c76a3b673d5960cd88331ad7d51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763328"
---
# <a name="spy-toolbar"></a>Spy++ 工具栏
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

该工具栏显示在 Spy + + 中的菜单栏下。 若要显示或隐藏工具栏上**视图**菜单上，单击**工具栏**。  
  
 在工具栏上提供了以下控件。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|Button|效果|  
|------------|------------|  
|![Spy&#43; &#43; Windows 按钮](../debugger/media/icon-spy-windows.gif "Icon_Spy + + （_w)")|在系统中显示的窗口和控件的树视图。 有关详细信息，请参阅[Windows 视图](../debugger/windows-view.md)。|  
|![Spy&#43; &#43;处理按钮](../debugger/media/icon-spy-processes.gif "Icon_Spy + + _Processes")|显示系统中的流程的树视图。 有关详细信息，请参阅[进程视图](../debugger/processes-view.md)。|  
|![Spy&#43; &#43;线程按钮](../debugger/media/icon-spy-threads.gif "Icon_Spy + + _Threads")|显示系统中的线程的树视图。 有关详细信息，请参阅[线程视图](../debugger/threads-view.md)。|  
|![Spy&#43; &#43;按钮的消息](../debugger/media/icon-spy-messages.gif "Icon_Spy + + 消息 （_m)")|创建窗口来显示窗口消息，并打开**消息选项**对话框中，以便你可以选择的窗口的消息将显示，并且还选择其他选项。 有关详细信息，请参阅[消息视图](../debugger/messages-view.md)。|  
|![Spy&#43; &#43;启动日志按钮](../debugger/media/icon-spy-startlog.gif "Icon_Spy + + _StartLog")|启动消息日志记录并显示消息流。 此控件是时才可用**消息**窗口是活动窗口。 有关详细信息，请参阅[如何： 启动和停止显示消息日志](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![Spy&#43; &#43;停止日志按钮](../debugger/media/icon-spy-stoplog.gif "Icon_Spy + + _StopLog")|停止消息日志记录和显示的消息流。 此控件是时才可用**消息**窗口是活动窗口。 有关详细信息，请参阅[如何： 启动和停止显示消息日志](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![Spy&#43; &#43;日志选项按钮](../debugger/media/icon-spy-logoptions.gif "Icon_Spy + + _LogOptions")|显示[消息选项](../debugger/message-options-dialog-box.md)对话框。 使用此对话框中选择 windows 和消息类型以供查看。 此控件是时才可用**消息**窗口是活动窗口。|  
|![Spy&#43; &#43;清除日志按钮](../debugger/media/spy-clearlog.gif "Spy + + _ClearLog")|清除活动的内容**消息**窗口。 此控件是时才可用**消息**窗口是活动窗口。|  
|![Spy&#43; &#43;查找窗口按钮](../debugger/media/icon-spy-findwindow.gif "Icon_Spy + + _FindWindow")|此时将打开[查找窗口](../debugger/find-window-dialog-box.md)对话框中，您可以设置窗口搜索条件并显示属性或消息。 有关详细信息，请参阅[如何： 使用查找程序工具](../debugger/how-to-use-the-finder-tool.md)。|  
|![Spy&#43; &#43;查找第一个窗口按钮](../debugger/media/icon-spy-window.gif "Icon_Spy + + _Window")|搜索匹配的窗口、 进程、 线程或消息的当前视图。|  
|![Spy&#43; &#43;查找窗口下一步按钮](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy + + _NextWindow")|搜索下一个匹配的窗口、 进程、 线程或消息的当前视图。 仅当不是唯一有效的搜索结果时，此控件 （及相关的菜单命令） 才可用。 例如，作为窗口树中的搜索条件中使用窗口句柄时，它生成唯一的结果是因为只有一个窗口在窗口树中具有该句柄;在本例中，**查找下一个**不可用。|  
|![Spy&#43; &#43;查找上一个窗口按钮](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy + + _PrevWindow")|搜索上一个匹配的窗口、 进程、 线程或消息的当前视图。 仅当不是唯一有效的搜索结果时，此控件 （及相关的菜单命令） 才可用。 例如，作为窗口树中的搜索条件中使用窗口句柄时，它生成唯一的结果是因为只有一个窗口在窗口树中具有该句柄;在本例中，**查找上一个**不可用。|  
|![Spy&#43; &#43;属性资源管理器按钮](../debugger/media/icon-spy-propexp.gif "Icon_Spy + + _PropExp")|显示在 Windows 视图中选择窗口的属性。|  
|![Spy&#43; &#43;刷新按钮](../debugger/media/icon-spy-refresh.gif "Icon_Spy + + （_r)")|刷新系统视图。|  
  
## <a name="see-also"></a>请参阅  
 [使用 Spy + +](../debugger/using-spy-increment.md)   
 [Spy + + 视图](../debugger/spy-increment-views.md)   
 [Spy++ 参考](../debugger/spy-increment-reference.md)



