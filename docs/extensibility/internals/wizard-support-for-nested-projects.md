---
title: 嵌套项目的向导支持 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3231dd48cea43f517a5e59f33c80df655032ec0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990119"
---
# <a name="wizard-support-for-nested-projects"></a>嵌套项目的向导支持
IDE 将运行两个向导，可以实现嵌套项目的父项目：**新的项目**向导并**添加项**向导。  
  
 如果用户启动**新的项目**向导通过选择**添加项目**，然后单击**新项目**文件菜单或通过选择**添加**右键单击**新的项目**在解决方案资源管理器，IDE 将运行**AddProject**命令和父项目的实施**AddProject**命令返回模板项目文件中或具有组的上下文参数的向导 (.vsz) 文件。  
  
 同样，父项目的实现**AddItem**向导返回具有一组不同的上下文参数的.vsz 文件。  
  
 有关向导的详细信息，请参阅[向导 (。在 Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)，[上下文参数](../../extensibility/internals/context-parameters.md)并[注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## <a name="see-also"></a>请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)