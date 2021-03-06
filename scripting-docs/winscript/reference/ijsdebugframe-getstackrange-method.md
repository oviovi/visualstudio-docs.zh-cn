---
title: 'Ijsdebugframe:: Getstackrange 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090280"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange 方法
返回逻辑 JavaScript 堆栈帧的绝对地址范围。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pStart`  
 [out]底端对齐框架的大多数堆栈指针。  
  
 `pEnd`  
 [out]大多数堆栈指针顶端的帧。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 此方法可对于拼凑从多个运行时收集的交错的堆栈跟踪。 开始时，结束堆栈指针能够包含多个物理计算机堆栈帧 （对于解释型 JavaScript 运行时帧）。 启动 > 结束随着堆栈从高到低地址。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)