---
title: IJsDebugBreakPoint 接口 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c43d23d0ba89e6b85a3dd4da688fa89fed4dd99
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093842"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint 接口
表示一个断点。  
  
## <a name="syntax"></a>语法  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete 方法](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|删除断点。|  
|[IJsDebugBreakPoint::Disable 方法](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|禁用断点。|  
|[IJsDebugBreakPoint::Enable 方法](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|启用断点。|  
|[IJsDebugBreakPoint::GetDocumentPosition 方法](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|返回绑定断点语句的位置。|  
|[IJsDebugBreakPoint::IsEnabled 方法](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|确定是否启用断点。|  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)