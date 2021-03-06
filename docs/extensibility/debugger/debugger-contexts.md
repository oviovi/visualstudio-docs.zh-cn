---
title: 调试器上下文 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 80e37d2994d446588de511c4f341381ca8611f1f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930175"
---
# <a name="debugger-contexts"></a>调试器上下文
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试，调试引擎 (DE) 同时在内运行多个不同的上下文中，按如下所示：  
  
-   代码上下文，其中描述了用于控制程序执行流中的当前位置。  
  
-   文档上下文或位置，其中描述了源文档中的当前位置。  
  
-   表达式计算上下文描述中的表达式求值将发生的上下文。  
  
## <a name="in-this-section"></a>本节内容  
 [代码上下文](../../extensibility/debugger/code-context.md)  
 今天的运行时体系结构中与非传统的语言，其中代码可能不表示的说明，但某些其他方式的程序的指令流中的地址作为讨论代码上下文。  
  
 [文档位置](../../extensibility/debugger/document-position.md)  
 定义源文件因为识别到 IDE 中的位置的抽象，通过调试 Visual Studio 中的文档位置。  
  
 [文档上下文](../../extensibility/debugger/document-context.md)  
 讨论了哪些文档上下文表示在 Visual Studio 调试相对于源文件中。 此外讨论了符号处理程序如何映射到文档上下文的代码上下文。  
  
 [表达式计算上下文](../../extensibility/debugger/expression-evaluation-context.md)  
 提供有关在 Visual Studio 中的表达式计算上下文信息。 例如，与堆栈帧关联表达式计算上下文提供有关评估本地变量、 方法参数和类成员的上下文。  
  
## <a name="related-sections"></a>相关章节  
 [调试概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
 [调试组件](../../extensibility/debugger/debugger-components.md)  
 概述 Visual Studio 调试组件，包括调试引擎 (DE)、 表达式计算器 (EE) 和符号处理程序 (SH)。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向不同的调试任务，如启动程序和计算表达式。