---
title: IBindEventHandler::BindHandler |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62ac6de8342f0a436d984f4194351507fdcd5edd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090709"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
将事件绑定到一个对象。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrEvent`  
 [in]指定要处理的事件。  
  
 `pdisp`  
 [in]指定要处理的事件的对象。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法将事件绑定到一个对象。  
  
## <a name="see-also"></a>请参阅  
 [IBindEventHandler 接口](../../winscript/reference/ibindeventhandler-interface.md)