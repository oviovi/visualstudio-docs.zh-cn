---
title: 端口供应商 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e134b9b4adeb45693a9841a0a867a9c3630bf2aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835099"
---
# <a name="port-suppliers"></a>端口提供程序
在调试器体系结构中，*端口供应商*:  
  
- 包含由服务器并提供有关对该服务器的请求的端口。  
  
- 可以添加和删除包含服务器的端口。  
  
- 可以枚举具有提供给服务器的所有端口。  
  
- 为由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)接口，通过在注册表中注册与 Visual Studio。 此接口可以通过调用来获取[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)。  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供了默认端口提供程序和默认端口。 如果需要实现自定义端口，则自定义端口提供程序还需要实现以提供这些自定义端口。  
  
## <a name="see-also"></a>请参阅  
 [服务器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [端口](../../extensibility/debugger/ports.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)