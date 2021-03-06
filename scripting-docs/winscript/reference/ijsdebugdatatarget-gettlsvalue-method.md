---
title: 'Ijsdebugdatatarget:: Gettlsvalue 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f81e9ea6cca9bf54753a496e07903d23bb913fc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095324"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 方法
有关正在调试的线程，检索指定的 TLS 索引的线程本地存储 (TLS) 槽中的值。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>参数  
 `threadId`  
 [in]若要读取从目标进程中运行的线程。  
  
 `tlsIndex`  
 [in]目标进程调用 TlsAlloc 函数时分配 TLS 索引。  
  
 `pValue`  
 [out]指针大小的值已存储在线程的 TLS 槽中。 如果目标线程为 32 位，32 位的此值将为零。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 进程的每个线程具有其自己的每个 TLS 索引的槽。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)