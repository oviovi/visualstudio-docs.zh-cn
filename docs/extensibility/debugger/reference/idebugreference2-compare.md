---
title: IDebugReference2::Compare |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ce8420c3ed2703a32e7422e9bee6b4e1815c134
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869871"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
比较对另一个引用。 留待将来使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwCompare`  
 [in]中的值[REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)枚举，用于指定的比较操作，例如，等于、 小于或大于。  
  
 `pReference`  
 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)对象，表示要进行比较的引用。  
  
## <a name="return-value"></a>返回值  
 始终返回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)