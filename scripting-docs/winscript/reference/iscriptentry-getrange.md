---
title: IScriptEntry::GetRange |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4e053817ed4c503ebb41e2f3828da421e69ec7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088733"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
返回的起始位置和长度的一个条目。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pichMin`  
 [out]有关`IScriptEntry`对象指定脚本块，则返回 0。  
  
 有关`IScriptEntry`当前脚本块中指定一个函数对象的对象返回该函数的起始位置。  
  
 有关`IScriptScriptlet`对象，则返回 0。  
  
 `pcch`  
 [out]有关`IScriptEntry`这些对象指定脚本块中，返回文本的长度。  
  
 有关`IScriptEntry`指定一个函数对象的对象返回的函数定义长度。  
  
 有关`IScriptScriptlet`对象，则返回项的长度。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|“值”|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)