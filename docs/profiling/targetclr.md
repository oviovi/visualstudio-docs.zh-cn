---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed0891715f6c9a0f4f89249a6ca5ac6415bad038
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967117"
---
# <a name="targetclr"></a>TargetCLR
“TargetCLR”选项指定应用程序中加载 CLR 的多个版本时要分析的公共语言运行时 (CLR) 的版本。  
  
 默认情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具以应用程序加载的第一个 CLR 版本为目标。  
  
## <a name="syntax"></a>语法  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>参数  
 `ClrVersion`  
 CLR 的版本号。 使用版本格式 vN.N.NNNNN。  
  
## <a name="required-options"></a>必需选项  
 “TargetCLR”选项只能与“启动”或“附加”选项一起使用。  
  
 **Launch：**`AppName`  
 启动指定的应用程序并开始分析。  
  
 **Attach:** `PID`  
 开始分析指定的进程。  
  
## <a name="example"></a>示例  
 在此示例中，使用 TargetCLR 选项以确保分析 CLR 版本 4.0.11003。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```