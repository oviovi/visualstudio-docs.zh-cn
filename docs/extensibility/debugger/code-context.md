---
title: 代码上下文 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbbeb9eab33bbdad7264a0296a4f6c9f86fb8a5d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851282"
---
# <a name="code-context"></a>代码上下文
在中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试**代码上下文**:  
  
-   已知的调试引擎 (DE) 提供了代码中的位置的抽象。 为大多数运行时体系结构现在，代码上下文可以认为的程序的指令流中的地址。 对于非传统的语言，其中介绍了如何不可能表示代码，可以通过某些其他方法来表示代码上下文。  
  
-   描述中进行调试的程序的执行流的当前位置。  
  
-   存在仅当程序停止在断点处。  
  
-   将具有关联的文档上下文。  
  
-   由实现[IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)接口。  
  
## <a name="see-also"></a>请参阅  
 [文档上下文](../../extensibility/debugger/document-context.md)   
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)