---
title: IDebugExpressionEvaluator::GetMethodProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0569c3e6a3d79279533c1c1c6717e8e5c3ce059
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820769"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
此方法获取包含局部变量、 参数以及方法的其他属性的属性对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pSymbolProvider`  
 [in]符号提供程序使用，以表示[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)对象。  
  
 `pAddress`  
 [in]在代码中，表示为地址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)对象应被解析为最接近的包含函数。  
  
 `pBinder`  
 [in]要使用的联编程序表示为[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)对象。  
  
 `fIncludeHiddenLocals`  
 [in]非零值 (`TRUE`) 表示包含隐藏局部变量; 零 (`FALSE`) 意味着若要忽略隐藏局部变量  
  
 `ppProperty`  
 [out]返回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示的方法的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 隐藏局部变量通常是由编译器生成的变量。  
  
## <a name="see-also"></a>请参阅  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)