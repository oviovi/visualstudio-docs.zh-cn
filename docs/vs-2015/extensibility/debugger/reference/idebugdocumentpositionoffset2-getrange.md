---
title: IDebugDocumentPositionOffset2::GetRange |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eca754c3154267629a1d6567c3412ec44a0784f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809241"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

检索当前的文档位置的范围。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwBegOffset`  
 [in、 out]为范围的起始位置的偏移量。 如果不需要此信息，请将此参数设置为 null 值。  
  
 `pdwEndOffset`  
 [in、 out]为范围的结束位置的偏移量。 如果不需要此信息，请将此参数设置为 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 在一个位置断点的文档位置中指定的范围是调试引擎 (DE) 用于实际影响代码的语句继续搜索。 例如，考虑以下代码：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行分配到正在调试的程序的任何代码。 如果行 5 设置断点调试器想 DE 向前搜索一定影响代码的第一行，调试器会指定一系列，包括其他候选行断点可能会正确放。 DE 将然后向前搜索这些行直到找到可接受断点的行。  
  
## <a name="see-also"></a>请参阅  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

