---
title: IActiveScriptSite::OnLeaveScript |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d08d58fc788d2d10ed044808ca40a5f4ea929c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093153"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
通知主机脚本引擎已返回执行脚本代码。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `S_OK`。  
  
## <a name="remarks"></a>备注  
 脚本引擎必须在将控制权返还给调用应用程序输入脚本引擎之前调用此方法。 例如，如果该脚本调用一个对象，然后触发由脚本引擎处理事件，脚本引擎必须调用[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)方法，然后再执行该事件时，必须调用`IActiveScriptSite::OnLeaveScript`后返回到触发事件的对象之前执行该事件。 可以嵌套调用此方法。 每次调用`IActiveScriptSite::OnEnterScript`需要相应地调用此方法。  
  
## <a name="see-also"></a>请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)