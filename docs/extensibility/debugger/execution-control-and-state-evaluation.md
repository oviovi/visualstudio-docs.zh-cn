---
title: 执行控件和状态计算 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a90f1fa098cfb60e6a3939332095dca5e52e3eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852094"
---
# <a name="execution-control-and-state-evaluation"></a>执行控件和状态评估
调试应用程序要求实现单步执行函数，在断点处停止和继续执行此类执行控制功能。 Visual Studio 调试基事件在其执行控制调试器组件之间发送。  
  
## <a name="in-this-section"></a>本节内容  
 [程序控制](../../extensibility/debugger/program-control.md)  
 列出了出现在程序级别上的以下例程： 设置下一条语句、 执行、 单步执行、 继续、 挂起，和恢复。  
  
 [断点相关的方法](../../extensibility/debugger/breakpoint-related-methods.md)  
 定义的和挂起的类型的 Visual Studio 支持的断点。  
  
 [调用堆栈计算](../../extensibility/debugger/call-stack-evaluation.md)  
 讨论允许在中断模式下查看调用堆栈的堆栈帧的方法的实现。  
  
 [表达式计算](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 介绍如何调试引擎 (DE) 中，表达式评估版 (EE) 和会话调试管理器所涉及的分析和表达式的计算输入到其中一个 IDE 的窗口。  
  
 [控件事件](../../extensibility/debugger/control-events.md)  
 讨论用于将事件发送程序的受控的执行期间的接口。