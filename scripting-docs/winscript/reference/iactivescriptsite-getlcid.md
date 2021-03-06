---
title: IActiveScriptSite::GetLCID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 959989d14d2a71f9c9eab4c78ef1b1bd9078362f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094999"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
检索与主机的用户界面相关联的区域设置标识符。 脚本引擎使用标识符来确保错误字符串和引擎生成的其他用户界面元素出现在相应的语言。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>参数  
 `plcid`  
 [out]一个变量来接收脚本引擎所显示的用户界面元素的区域设置标识符的地址。  
  
## <a name="return-value"></a>返回值  
 返回以下值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|未实现此方法。 使用的系统定义的区域设置。|  
|`E_POINTER`|指定了无效的指针。|  
  
## <a name="remarks"></a>备注  
 如果此方法返回`E_NOTIMPL`，应使用的系统定义的区域设置标识符。  
  
## <a name="see-also"></a>请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)