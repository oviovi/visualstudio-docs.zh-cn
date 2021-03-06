---
title: WinCounter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51cb5aa0a41f311ea9c24a4ed512d6df4fe2e10f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875214"
---
# <a name="wincounter"></a>WinCounter
**WinCounter** 选项指定在分析运行过程中以设定时间间隔收集的 Windows 性能计数器或应用程序性能计数器。 Windows 性能计数器和应用程序性能计数器在分析数据文件中列为标记。 可以用单独的选项指定多个要收集的性能计数器。  
  
 默认情况下，每 500 毫秒收集一次计数器。 使用 **AutoMark** 选项可以指定其他收集时间间隔。  
  
 只能使用一个 **AutoMark** 选项。 如果指定多个 **AutoMark** 选项，则使用最后一个。  
  
 **WinCounter** 选项只能与 **Start** 选项一起使用。  
  
## <a name="syntax"></a>语法  
  
```cmd  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>参数  
 `Path`  
 PDH 计数器路径格式的 Windows 性能计数器。  
  
## <a name="required-options"></a>必需选项  
 **WinCounter** 选项只能与 **Start** 选项一起使用。  
  
 **Start:** `Method`  
 “Start”选项可将探查器初始化为指定的分析方法。  
  
## <a name="exclusive-options"></a>独占选项  
 **AutoMark** 选项只能与 **WinCounter** 选项一起使用。  
  
 **AutoMark:** `Milliseconds`  
 指定两次 Windows 性能计数器数据收集相隔的毫秒数。  
  
## <a name="example"></a>示例  
 在下面的示例中，将两个 Windows 性能计数器收集时间间隔指定为 1000 毫秒。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)