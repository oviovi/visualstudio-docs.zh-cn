---
title: IDebugObject::IsNullReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 027d6364ad3d6277b716d6716d9d02d1390cde6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962936"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
测试此对象是否为 null 引用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pfIsNull`  
 [out]返回非零值 (`TRUE`) 如果此对象为 null 的引用; 否则，返回零 (`FALSE`)。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 Null 引用表示一个空的对象或未分配给的对象。  
  
## <a name="see-also"></a>请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)