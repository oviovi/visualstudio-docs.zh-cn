---
title: IDebugDocumentTextExternalAuthor::NotifyChanged |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6338a4f88435f47ef33abe593c0bb4e000ae6ee2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094102"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
通知主机已更改的文档源。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>参数  
 此方法需要任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 基于文件的调试器文档是修改并保存用于通知宿主已更改的文档源后，通过外部编辑器调用此方法。 然后，主机刷新的源文件中的文档。  
  
## <a name="see-also"></a>请参阅  
 [IDebugDocumentTextExternalAuthor 接口](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)