---
title: IActiveScriptProfilerCallback3::SetWebWorkerId 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094428"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId 方法
通知事件探查器关于要使用此分析会话的辅助 ID。 如果该函数不在页面的上下文中执行的则不调用此方法。 值`webWorkerId`每个辅助角色，从 1 开始的 1 为增量。 ID 值不应保持不变超过一个会话，并仅对辅助角色已创建的顺序相对应。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>参数  
 `webWorkerId`  
 Web 工作线程 id。  
  
## <a name="return-value"></a>返回值  
 此方法的返回值是脚本引擎忽略。