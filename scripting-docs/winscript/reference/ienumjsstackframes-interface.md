---
title: IEnumJsStackFrames 接口 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c26470e02f6c7e5d8911df7e743bce0cb0e560bb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087875"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames 接口
由调试器提供堆栈实现适用于 JavaScript 的 jscript9diag.dll 展开。  
  
## <a name="syntax"></a>语法  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next 方法](../../winscript/reference/ienumjsstackframes-next-method.md)|获取指定的帧数。|  
|[IEnumJsStackFrames::Reset Method](../../winscript/reference/ienumjsstackframes-reset-method.md)|将堆栈帧重置为第一个元素之前的位置。|  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)