---
title: IDebugDocumentTextExternalAuthor::GetPathName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e17d27a320eac95445c083c718f5abcebbbc46cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088837"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
返回文档的完整路径和文件名称。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstrLongName`  
 [out]包含完整路径和文件名的字符串。  
  
 `pfIsOriginalFile`  
 [out]一个布尔值，该值指示是否路径和文件名称，请参阅对原始文档。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|“值”|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|无法创建或确定源文件。|  
  
## <a name="remarks"></a>备注  
 此方法返回文档的完整路径和文件的名称。  
  
 如果`pfIsOriginalFile`是 FALSE、 路径和文件名中`pbstrLongName`引用新创建的临时文件。  
  
## <a name="see-also"></a>请参阅  
 [IDebugDocumentTextExternalAuthor 接口](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)