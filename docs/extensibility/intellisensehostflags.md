---
title: IntelliSenseHostFlags |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7482e312dd767a62a18914f496e9b0835f7622b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833227"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
指定 IntelliSense 主机标志。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
### <a name="parameters"></a>参数  
  
|成员|描述|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|上下文缓冲区是只读的。|  
|`IHF_NOSEPARATESUBJECT`|没有使用者的文本。 上下文缓冲区包含 IntelliSense 目标 (意味着`!IHF_READONLYCONTEXT`)。|  
|`IHF_SINGLELINESUBJECT`|不支持多行的主题文本。|  
|`IHF_FORCECOMMITTOCONTEXT`|与 `CanCommitIntoReadOnlyBuffer` 相同。|  
|`IHF_OVERTYPE`|应在改写模式下编辑 （在使用者或上下文）。|  
  
## <a name="requirements"></a>要求  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop>